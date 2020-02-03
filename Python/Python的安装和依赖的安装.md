# Python的安装和依赖的安装

> 学习地址：https://github.com/vipstone/python & https://www.runoob.com/python3/python3-tutorial.html

## 一、Python3的安装

### (一)、下载安装python

点击进入，下载地址：https://www.python.org/downloads/

下载进行安装，一直点击下一步即可。我的版本是 `python-3.6.8-amd64.exe` 

### (二)、配置环境python变量

编辑系统变量 **(我的电脑右键属性 => 高级 => 环境变量 => 系统变量)** ，在系统的path变量中添加2个变量目录，假设python3的安装目录为：`E:\Program Files\Python\Python36`，分别添加：`E:\Program Files\Python\Python36`、`E:\Program Files\Python\Python36\Scripts`。

### (三)、安装python3的pip

使用命令：

```bash
python -m pip install -U pip
```

<details>
<summary>显示如下表示成功</summary>

```bash
Collecting pip
  Using cached https://files.pythonhosted.org/packages/54/0c/d01aa759fdc501a58f431eb594a17495f15b88da142ce14b5845662c13f3/pip-20.0.2-py2.py3-none-any.whl
Installing collected packages: pip
  Found existing installation: pip 18.1
    Uninstalling pip-18.1:
      Successfully uninstalled pip-18.1
Successfully installed pip-20.0.2

# 或

Collecting pip
  Downloading https://files.pythonhosted.org/packages/54/0c/d01aa759fdc501a58f431eb594a17495f15b88da142ce14b5845662c13f3/pip-20.0.2-py2.py3-none-any.whl (1.4MB)
    100% |████████████████████████████████| 1.4MB 7.8kB/s
Installing collected packages: pip
  Found existing installation: pip 19.0.3
    Uninstalling pip-19.0.3:
      Successfully uninstalled pip-19.0.3
Successfully installed pip-20.0.2
```

</details>

## 二、Python依赖/库的安装

PS.以下四种方法任选一种即可。个人感觉 [第四种](#四使用国内镜像pip安装) 用国内镜像安装最好用，主要是快和稳

### （一）、直接pip安装


cmd 或者 powershell 输入如下指令

```bash
# xxx 表示你要安装的依赖/库
pip install xxx
```

eg

```bash
pip install numpy
pip install opencv_python
pip install dlib
pip install face_recognition
pip install mkl

...
```

### （二）、通过whl文件安装

Python包主要有.whl和.tar.gz两种格式。第一种，在此处：https://www.lfd.uci.edu/~gohlke/pythonlibs 下载对应依赖/库的.whl文件，然后命令窗口输入如下指令

```bash
# xx 表示你下载的文件路径，xxx 表示你要安装的依赖/库
pip install xx/xxx.whl
```

eg

```bash
# 下载whl时，请注意cp36对应Python版本号3.6，以此类推，与自己Python不匹配将导致安装失败
pip install D:\11download\browser\numpy-1.18.1+mkl-cp36-cp36m-win_amd64.whl
```

### （三）、通过压缩文件文件安装

Python包主要有.whl和.tar.gz两种格式，其中tar.gz文件需要到 https://pypi.org/ 中选择对应格式的文件进行下载，下载下来以后是一个压缩包。

需要进行解压，解压完以后打开命令窗口，同样需要切换到文件所在的路径下，然后运行如下命令进行安装即可。

```bash
python setup.py build
python setup.py install
```

### （四）、使用国内镜像pip安装

**国内镜像地址**

http://pypi.douban.com/simple/　　 豆瓣

http://mirrors.aliyun.com/pypi/simple/ 　　阿里

http://pypi.hustunique.com/simple/ 　　华中理工大学

http://pypi.sdutlinux.org/simple/ 　　山东理工大学

http://pypi.mirrors.ustc.edu.cn/simple/ 　　中国科学技术大学

https://pypi.tuna.tsinghua.edu.cn/simple 　　清华

 
**如何使用**

1、临时使用，添加“-i”或“--index”参数

```bash
pip install -i URL xxx
# OR
pip install xxx -i URL 
```

eg

```bash
pip install -i http://mirrors.aliyun.com/pypi/simple/ face_recognition
# or
pip install face_recognition -i http://mirrors.aliyun.com/pypi/simple
```

2、配制成默认的

在你的 `C:\Users\你的用户名\` 目录下创建 `pip` 目录， `pip` 目录下创建 `pip.ini` 文件（注意：以 `UTF-8` 无 `BOM` 格式编码）；

`pip.ini` 文件内容：

```
[global]

index-url=http://mirrors.aliyun.com/pypi/simple/

[install]

trusted-host=mirrors.aliyun.com
```
注意：`trusted-host` 选项为了避免麻烦是必须的，否则使用的时候会提示不受信任，或者添加 `--trusted-host=mirrors.aliyun.com` 选项

---

下一节：[基础](./基础.md)