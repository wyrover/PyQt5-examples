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

```
eric6.bat
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

## 继承 QWidget

``` python
import sys
from PyQt5.QtWidgets import QApplication, QWidget 


class GUI(QWidget):                 # inherit from QWidget
 def __init__(self): 
     super().__init__()          # initialize super class, which creates the Window
       
     self.initUI()               # refer to Window as self

       
 def initUI(self):   
     self.setWindowTitle('PyQt5 GUI')    # add widgets and change properties


if __name__ == '__main__':     
 app = QApplication(sys.argv)        # create Application     
 gui = GUI()                         # create instance of class
 gui.show()                          # show the constructed PyQt window
 sys.exit(app.exec_())               # execute the application
    
```


## 继承 QMainWindow

``` python
import sys
from PyQt5.QtWidgets import QApplication, QMainWindow 


class GUI(QMainWindow):             # inherit from QMainWindow
 def __init__(self): 
     super().__init__()          # initialize super class, which creates the Window
       
     self.initUI()               # refer to Window as self

       
 def initUI(self):   
     self.setWindowTitle('PyQt5 GUI')    # add widgets and change properties


if __name__ == '__main__':     
 app = QApplication(sys.argv)        # create Application     
 gui = GUI()                         # create instance of class
 gui.show()                          # show the constructed PyQt window
 sys.exit(app.exec_())               # execute the application
```

## 带一个菜单

``` python
import sys
from PyQt5.QtWidgets import QApplication, QMainWindow, QAction 

class GUI(QMainWindow):             # inherit from QMainWindow
 def __init__(self): 
     super().__init__()          # initialize super class, which creates the Window
        
     self.initUI()                           
           
 def initUI(self):                       # set properties and add widgets        
     self.setWindowTitle('PyQt5 GUI')    # refer to Window as self
       
     self.statusBar().showMessage('Text in statusbar')
       
     menubar = self.menuBar()                # create menu bar
     file_menu = menubar.addMenu('File')     # add menu to menu bar
       
     new_action = QAction('New', self)       # create an Action      
     file_menu.addAction(new_action)         # add Action to menu
       
     new_action.setStatusTip('New File')     # statusBar updated
       
     self.resize(400,300)                    # resize window (width, height) 
         
if __name__ == '__main__':     
 app = QApplication(sys.argv)        # create Application     
 gui = GUI()                         # create instance of class
 gui.show()                          # show the constructed PyQt window
 sys.exit(app.exec_())               # execute the application    

```


## QLabel, QPushButton

``` python
from PyQt5.Qt import QLabel, QPushButton

label_1 = QLabel('Our first label', self)   
label_1.move(10, mbar_height)       

button_1 = QPushButton('click 1', self)
button_2 = QPushButton('click 2', self)
  
button_1.move(label_1.width(), label_1.height())
button_2.move(label_1.width(), label_1.height() * 2)
```


## 布局

``` python
import sys
from PyQt5.QtWidgets import QApplication, QMainWindow, QAction, QWidget 
from PyQt5.Qt import QLabel, QPushButton, QHBoxLayout, QVBoxLayout
from PyQt5.QtGui import QIcon
 
class GUI(QMainWindow):             
 def __init__(self): 
     super().__init__()          
     self.initUI()                           
 
 def initUI(self):                              
     self.setWindowTitle('PyQt5 GUI')    
     self.resize(400,300)                  
     self.add_menus_and_status()
   
     self.horizontal_vertical_box_layout()
       
   
 def horizontal_vertical_box_layout(self):
     label_1 = QLabel('First label')
     label_2 = QLabel('Another label')
       
     button_1 = QPushButton('Click 1')
     button_2 = QPushButton('Click 2')
       
     hbox_1 = QHBoxLayout()
     hbox_2 = QHBoxLayout()
       
     hbox_1.addWidget(label_1)
     hbox_1.addWidget(button_1)

     hbox_2.addWidget(label_2)
     hbox_2.addWidget(button_2)
               
     vbox = QVBoxLayout()
     vbox.addLayout(hbox_1)
     vbox.addLayout(hbox_2)
       
     layout_widget = QWidget()       # create QWidget object
     layout_widget.setLayout(vbox)   # set layout
       
     self.setCentralWidget(layout_widget)    # make QWidget the central widget
       
       
                  
 def add_menus_and_status(self):        
     self.statusBar().showMessage('Text in statusbar')
        
     menubar = self.menuBar()                
     file_menu = menubar.addMenu('File')          
     new_icon = QIcon('icons/new_icon.png')          
     new_action = QAction(new_icon, 'New', self)      
     new_action.setStatusTip('New File')                 
     file_menu.addAction(new_action)                 
        
     file_menu.addSeparator()               
        
     exit_icon = QIcon('icons/exit_icon.png')          
     exit_action = QAction(exit_icon, 'Exit', self)    
     exit_action.setStatusTip('Click to exit the application')
     exit_action.triggered.connect(self.close)       
     exit_action.setShortcut('Ctrl+Q')                     
     file_menu.addAction(exit_action)
        
     menubar.addMenu('Edit')     

if __name__ == '__main__':     
 app = QApplication(sys.argv)            
 gui = GUI()                         
 gui.show()                          
 sys.exit(app.exec_())  

```