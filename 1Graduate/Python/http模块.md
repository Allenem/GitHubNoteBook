# http模块

python 中的 `http/https` 请求使用 `urllib` 库，使用 `urllib` 的 `request` 模块的发送 `get` 和 `post` 请求。

## get请求

请求网页地址并返回网页html内容，写入get.txt文件，示例如下：

```py
from urllib import request

def getHtml(url):
    with request.urlopen(url) as r:
        data = r.read()
        return data.decode("utf-8")

path = "./get.txt"
with open(path, "w", encoding="utf-8") as fi:
    fi.write(getHtml("https://github.com/Allenem"))
```

对返回的数据进行解码处理 `data.decode("utf-8")` 即可。

## post请求

post请求并传递参数，对参数进行encode处理，示例如下：

```py
from urllib import request, parse

params = parse.urlencode([("name", "老王"), ("pwd", "123456")])
req = request.Request("http://127.0.0.1:8360/video/login")
req.add_header("User-Agent", "Mozilla/6.0 (iPhone; CPU iPhone OS 8_0 like Mac OS X) AppleWebKit/536.26 (KHTML, like Gecko) Version/8.0 Mobile/10A5376e Safari/8536.25")

with request.urlopen(req, data=params.encode("utf-8")) as r:
    data = r.read()
    print(data.decode("utf-8"))
```

如上所示，需要使用 `urllib` 的 `parse` 对参数进行编码处理，也可以给 `http` 头添加内容。

---

下一节：[常用内置模块](./常用内置模块.md)