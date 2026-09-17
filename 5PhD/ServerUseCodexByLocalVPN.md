# ServerUseCodexByLocalVPN

让远程 Ubuntu 服务器通过本地 Windows 的 VPN/代理出口访问 OpenAI，从而在 **VS Code Remote SSH** 中正常使用 **Codex Extension**。

> 适用场景：本地 Windows 能访问 OpenAI，但远程 Ubuntu 服务器不能直接访问；希望让远程服务器借用本地网络出口。

---

## 方案 A：Windows + Clash

如果 Clash 已提供本地 HTTP / Mixed Proxy，例如：

```text
127.0.0.1:7890
```

Windows 建立 SSH 反向转发：

```powershell
ssh -R 7890:127.0.0.1:7890 user@Ubuntu_IP
```

链路：

```text
Codex Extension
↓
Ubuntu 127.0.0.1:7890
↓ SSH Reverse Forward
Windows Clash 127.0.0.1:7890
↓
代理节点
↓
OpenAI
```

Ubuntu 测试：

```bash
curl -x http://127.0.0.1:7890 https://ipinfo.io
```

然后编辑：

```bash
nano ~/.profile
```

加入：

```bash
export HTTP_PROXY=http://127.0.0.1:7890
export HTTPS_PROXY=http://127.0.0.1:7890
export http_proxy=http://127.0.0.1:7890
export https_proxy=http://127.0.0.1:7890
```

在 VS Code 中执行：

```text
Ctrl + Shift + P
→ Remote-SSH: Kill VS Code Server on Host
→ 重新连接服务器
```

---

## 方案 B：Windows + LetsVPN + Privoxy

LetsVPN 属于系统级 VPN/TUN，通常没有直接暴露 HTTP Proxy。

### 1. Windows 开启 LetsVPN

先确认出口：

```powershell
curl https://ipinfo.io
```

### 2. 建立反向 SOCKS5

Windows：

```powershell
ssh -R 1080 user@Ubuntu_IP
```

Ubuntu 会得到：

```text
127.0.0.1:1080
```

测试：

```bash
curl --proxy socks5h://127.0.0.1:1080 https://ipinfo.io
```

如果显示与 Windows LetsVPN 相同的出口 IP，说明 SSH 反穿成功。

### 3. 安装 Privoxy，把 SOCKS5 转成 HTTP

Ubuntu：

```bash
sudo apt install privoxy -y
sudo nano /etc/privoxy/config
```

加入：

```text
forward-socks5t / 127.0.0.1:1080 .
```

重启：

```bash
sudo systemctl restart privoxy
```

测试：

```bash
curl -x http://127.0.0.1:8118 https://ipinfo.io
```

链路：

```text
Codex Extension
↓ HTTP_PROXY :8118
Privoxy
↓ SOCKS5 :1080
SSH Reverse Dynamic Forward
↓
Windows
↓
LetsVPN
↓
OpenAI
```

### 4. 给 Codex 配 HTTP Proxy

编辑：

```bash
nano ~/.profile
```

加入：

```bash
export HTTP_PROXY=http://127.0.0.1:8118
export HTTPS_PROXY=http://127.0.0.1:8118
export http_proxy=http://127.0.0.1:8118
export https_proxy=http://127.0.0.1:8118

unset ALL_PROXY
unset all_proxy
```

如果 `~/.bashrc` 里还有：

```bash
export ALL_PROXY=socks5h://127.0.0.1:1080
```

建议删除或注释，避免 Codex 继续读取旧 SOCKS 代理。

然后：

```text
Ctrl + Shift + P
→ Remote-SSH: Kill VS Code Server on Host
→ 重新连接服务器
```

---

## 为什么要 SOCKS5 → HTTP？

SSH：

```powershell
ssh -R 1080 user@Ubuntu_IP
```

提供的是 SOCKS5。

`curl` 对 SOCKS5 支持很好，但 **Terminal 能联网 ≠ VS Code Codex Extension 一定正确使用 SOCKS5**。

实际排查中，Codex 的远程 `app-server` 使用：

```text
HTTP_PROXY
HTTPS_PROXY
```

更稳定。

Privoxy 的作用只有一个：

```text
HTTP Proxy → SOCKS5
```

它不是 VPN，本身不负责提供外网出口。

---

## 如何确认 Codex 真的走代理？

找 Codex 进程：

```bash
ps aux | grep -i codex
```

找到 PID 后：

```bash
cat /proc/<PID>/environ | tr '\0' '\n' | grep -i proxy
```

LetsVPN + Privoxy 方案应看到：

```text
HTTP_PROXY=http://127.0.0.1:8118
HTTPS_PROXY=http://127.0.0.1:8118
```

Clash 方案则应看到对应的 `7890`。

> 关键：不要只检查 Terminal，要检查 Codex 进程自己的环境变量。

---

## 常见问题

### `403 Country, region, or territory not supported`

如果同时出现：

```text
cf-ray: ...-HKG
```

说明 Codex 请求仍然从香港出口，没有正确走代理。

### `stream disconnected before completion`

常见于：

```text
SOCKS5 能用
但 Codex Extension 没稳定使用 SOCKS5
```

LetsVPN 场景推荐：

```text
SOCKS5 → Privoxy → HTTP_PROXY / HTTPS_PROXY
```

### `You have no credits remaining`

通常说明网络已经通了，问题变成认证/计费方式。

如果使用 ChatGPT 计划，可以在 Codex Extension：

```text
Sign Out
→ Sign in with ChatGPT
```

---

## 最终建议

### Clash 用户

```text
Windows Clash HTTP/Mixed
→ SSH -R
→ Ubuntu HTTP_PROXY
→ Codex
```

### LetsVPN 用户

```text
Windows LetsVPN
→ SSH -R 1080
→ Ubuntu SOCKS5
→ Privoxy :8118
→ HTTP_PROXY / HTTPS_PROXY
→ Codex
```

---

## 注意

- Windows VPN/代理和 SSH 隧道必须保持在线。
- 不要把 API Key 写入公开仓库。
- 请遵守 OpenAI、VPN 服务商及所在地区的相关服务条款与法律法规。
