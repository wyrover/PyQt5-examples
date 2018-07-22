# PyQt5-examples


```
if not exist "python-3.6.5-amd64.exe" (
    wget https://www.python.org/ftp/python/3.6.5/python-3.6.5-amd64.exe -O python-3.6.5-amd64.exe
)

if not exist "%~dp0python3\python.exe" (    
    python-3.6.5-amd64.exe /quiet InstallAllUsers=1 PrependPath=1 TargetDir="%~dp0python3"
}
```



```
pip install SIP
pip install PyQt5
pip install PyQt5-tools
pip install Qscintilla   
pip install pyenchant 
```

下载太慢用下载工具下载，然后安装

```
pip install whatever.whl
```


## 安装 Eric6

```
wget https://jaist.dl.sourceforge.net/project/eric-ide/eric6/stable/18.07/eric6-18.07.zip -O eric6-18.07.zip
```



用 Eric6 打开文件 F2 就可运行

``` python
import sys 
from PyQt5.QtWidgets import *

app = QApplication(sys.argv)
win = QWidget()
win.show()

app.exec_()
```