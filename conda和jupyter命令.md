### Conda
#### 什么是conda？
- 应用程序 conda 是包和环境管理器。
- conda 只能通过命令行来使用。
- 包管理器用于在计算机上安装库和其他软件。比如pip，它是Python库的默认包管理器。conda 与pip相似，不同之处是可用的包以数据科学包为主，而pip适合一般用途。与此同时，conda并非像pip那样专门适用于Python，它也可以安装非Python的包。它是支持任何软件的包管理器。
- Conda安装了预编译的包。例如，Anaconda发行版附带了使用MKL库编译的Numpy、Scipy和 Scikit-learn，从而加快了各种数学运算的速度。
- conda 还是虚拟环境管理器，让你能够分隔用于不同项目的包。
- conda list : 查看conda里所有的内容
- conda update -all : 更新所有的包
#### conda包管理
- conda install package_name : 包安装，会自动安装依赖包
- conda install package_name=版本号 : 按包的版本安装
- conda remove package_name : 包卸载
- conda update package_name : 包更新
- conda update -all : 更新所有包
- conda search search_term : 如果不知道包的具体名称，可以搜索一下试试
#### conda环境管理
- conda create -n env_name list_of_packages : 新建一个环境，env_name是环境的名字，后面列出所有该环境下需要的包，空格分隔
- conda create -n py3 python=3 或 conda create -n py2 python=2 : 分别创建两个使用python 2.X 和 python 3.X 的环境
- source activate env_name : Linux和Mac上进入环境
- activate env_name : windows上进入环境
- source deactivate :  Linux和Mac上退出环境
- deactivate : windows上退出环境
- conda env_name export > environment.yaml : 前半段export输出env_name环境的所有包名称，后半段将环境导出至YAML文件，该文件可用于分享环境
- conda env create -f environment.yaml : 通过YAML文件创建环境
- conda env list : 列出创建的所有环境。当前所在环境的旁边会有一个星号。默认的环境名为 root
- pip freeze > requirements.txt : 也可以实现将环境保存下来用来分享
- pip install -r requirements.txt : pip通过txt文件创建环境，详情见 https://pip.pypa.io/en/stable/reference/pip_freeze/
- conda env remove -n env_name : 删除环境

### Jupyter Notebook
#### 什么是Jupyter Notebook
- Jupyter notebook 是一种 Web 应
- 你通过浏览器连接到该服务器，而 notebook 呈现为 Web 应用。你在 Web 应用中编写的代码通过该服务器发送给内核（kernel），内核运行代码，并将结果发送回该服务器。之后，任何输出都会返回到浏览器中。保存 notebook 时，它将作为 JSON 文件（文件扩展名为 .ipynb）写入到该服务器中。
- 在终端或控制台中输入 jupyter notebook。服务器会在你运行此命令的目录中启动。这意味着任何 notebook 文件都会保存在该目录下。
- 默认情况下，notebook 服务器的运行地址是 http://localhost:8888。
- 若要在conda环境下使用notebook，需要先激活该环境。
- Notebook 只是扩展名为 .ipynb 的大型 JSON 文件。
#### Jupyter Notebook使用
- 命令模式中按 H，会弹出快捷键面板
- 通过按Shift + Control或者Command + P，可以很轻松地访问命令面板。
- 在一行连续按两次 D 可以删除单元格。
- 在命令模式中的代码单元格按 L 打开代码行号。
- jupyter nbconvert --to html notebook.ipynb : 将notebook转换成html格式
#### Magic关键字
- Magic 关键字是可以在单元格中运行的特殊命令，能让你控制 notebook 本身或执行系统调用（例如更改目录）。
- Magic 命令的前面带有一个或两个百分号（% 或 %%），分别对应行 Magic 命令和单元格 Magic 命令。
- 可以使用 Magic 命令 %timeit 测算函数的运行时间，用%%timeit 测算整个单元的时间。
- 在 notebook 中可以使用 %matplotlib 将 matplotlib 设置为以交互方式工作。默认情况下，图形呈现在各自的窗口中。但是，你可以通过命令传递参数，以选择特定的“后端”（呈现图像的软件）。要直接在 notebook 中呈现图形，应将通过命令 %matplotlib inline 内联后端一起使用。
- 在分辨率较高的屏幕（例如 Retina 显示屏）上，notebook 中的默认图像可能会显得模糊。可以在 %matplotlib inline 之后使用 %config InlineBackend.figure_format = 'retina' 来呈现分辨率较高的图像。
