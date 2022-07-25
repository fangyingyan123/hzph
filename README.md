# pyqt5

## 安装方法

在cmd+r中输入：
pip install pyqt5 -i https://pypi.tuna.tsinghua.edu.cn/simple  
pip install pyqt5-tools -i https://pypi.tuna.tsinghua.edu.cn/simple  

## 在pycharm或者其他编辑器中设置工具

如下所示
![img.png](img.png)
同样设置pyuic
![img_1.png](img_1.png)
在pyqt5中，设置好界面，保存为ui文件
然后在pycharm中右击那个ui文件，然后选择Qt-->pyuic,就生成了一个py文件
这里比如生成的py文件内容如下所示：

```
#login.py
from PyQt5 import QtCore, QtGui, QtWidgets

class Ui_Form(object):
    def setupUi(self, Form):
        Form.setObjectName("Form")
        Form.resize(751, 377)
        self.label = QtWidgets.QLabel(Form)
        self.label.setGeometry(QtCore.QRect(70, 80, 72, 15))
        self.label.setObjectName("label")
        self.label_2 = QtWidgets.QLabel(Form)
        self.label_2.setGeometry(QtCore.QRect(70, 110, 72, 15))
        self.label_2.setObjectName("label_2")
        self.lineEdit = QtWidgets.QLineEdit(Form)
        self.lineEdit.setGeometry(QtCore.QRect(160, 80, 113, 21))
        self.lineEdit.setObjectName("lineEdit")
        self.lineEdit_2 = QtWidgets.QLineEdit(Form)
        self.lineEdit_2.setGeometry(QtCore.QRect(160, 110, 113, 21))
        self.lineEdit_2.setObjectName("lineEdit_2")
        self.pushButton = QtWidgets.QPushButton(Form)
        self.pushButton.setGeometry(QtCore.QRect(100, 180, 93, 28))
        self.pushButton.setObjectName("pushButton")
        self.textBrowser = QtWidgets.QTextBrowser(Form)
        self.textBrowser.setGeometry(QtCore.QRect(390, 30, 256, 192))
        self.textBrowser.setObjectName("textBrowser")
        self.pushButton_2 = QtWidgets.QPushButton(Form)
        self.pushButton_2.setGeometry(QtCore.QRect(220, 180, 93, 28))
        self.pushButton_2.setObjectName("pushButton_2")
        self.retranslateUi(Form)
        QtCore.QMetaObject.connectSlotsByName(Form)

    def retranslateUi(self, Form):
        _translate = QtCore.QCoreApplication.translate
        Form.setWindowTitle(_translate("Form", "Form"))
        self.label.setText(_translate("Form", "用户名"))
        self.label_2.setText(_translate("Form", "密码"))
        self.pushButton.setText(_translate("Form", "登录"))
        self.pushButton_2.setText(_translate("Form", "退出"))
```

这时候设置主程序运行出界面则
主程序为

```
# main.py
import sys
from PyQt5.QtWidgets import QApplication, QMainWindow
import login as lu #导入ui生成的py文件


class Example(QMainWindow):
    def __init__(self):
        self.app = QApplication(sys.argv)
        super().__init__()
        self.ui = lu.Ui_Form()
        self.ui.setupUi(self)
        # 初始化
        self.init_ui()

    # ui初始化
    def init_ui(self):
        # 初始化方法，这里可以写按钮绑定等的一些初始函数
        self.show()


# 程序入口
if __name__ == '__main__':
    e = Example()
    sys.exit(e.app.exec())
```

生成的结果如下：
![img_2.png](img_2.png)
