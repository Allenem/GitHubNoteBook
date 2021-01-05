# python 打包 exe 文件

1.pyInstaller 

```
pip install pyinstaller
```

```bash
pyinstaller -F xxx.py  打包exe命令，但是会有黑窗口
pyinstaller -F -w xxx.py去除黑窗口
```

2.py2exe

打包命令，整个dist文件夹一起发布。

```bash
python setup.py py2exe 
```

setup.py编写：

```py
from distutils.core import setup
import py2exe
 
setup(console=["xx.py"])
```

---

下一节：无