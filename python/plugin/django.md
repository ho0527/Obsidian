# django架構及簡介及用法

## 介紹


## 主程式架構(原生)
```

```

## 啟動方式
1. 确保已经安装了 Python
可以在终端中输入以下命令来检查 Python 是否已安装并查看其版本：
```cmd
python --version
```

2. 安装虚拟环境工具 virtualenv。您可以使用以下命令来安装：
```cmd
pip install virtualenv
```

3. 创建一个新的虚拟环境。在命令行中，导航到您想要创建虚拟环境的目录，并运行以下命令：
```cmd
virtualenv myenv
```

4. 这将在当前目录下创建一个名为 myenv 的新虚拟环境。

激活虚拟环境。根据您使用的操作系统，运行以下命令激活虚拟环境：

Windows:
```cmd
myenv\Scripts\activate
```

macOS/Linux:
```cmd
source myenv/bin/activate
```

5. 在激活的虚拟环境中安装 Django。运行以下命令来安装最新版本的 Django：
```cmd
pip install django
```
现在，您已经成功安装了 Django 虚拟环境。您可以在该虚拟环境中开发和运行 Django 项目。每次您需要在项目中使用 Django 时，都需要激活虚拟环境。

6. 開啟sever
```cmd
python manage.py runserver
```

7. 如果您想要退出虚拟环境，可以在命令行中运行以下命令：
```cmd
deactivate
```
请注意，虚拟环境是一种隔离的 Python 环境，可以独立于全局 Python 环境安装和管理依赖项。这样可以防止项目之间的依赖冲突，并使每个项目拥有独立的依赖项



## 註解及參見