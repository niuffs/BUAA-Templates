# 北京航空航天大学论文模板

本项目为北京航空航天大学研究生**开题报告**、**文献综述**和**学位论文**模板，包含Word模板和LaTeX模板。

### 参考项目链接

- [1] 开题报告/文献综述：https://github.com/ZhouKanglei/BUAAProposal/tree/main
- [2] 学位论文：https://github.com/CheckBoxStudio/BUAAThesis

在上述项目基础上，对latex模板进行了简化并与Word模板保持一致。

### 本地部署Overleaf

由于在线Overleaf可能出现编译超时等问题，在本地运行docker部署Overleaf，并解决字体安装问题。

#### Overleaf安装

先安装Docker环境，如Docker Desktop。在每个容器中直观展示了：

- Logs：日志记录；
- Bind mounts：将主机文件系统中的文件或目录在容器中的挂载位置；
- Exec：直接进入容器执行shell命令；
- Files：文件和路径。

安装Overleaf镜像参考如下教程：

- 自建Overleaf：
  https://yangzhang.site/Note/NAS/self-hosted-overleaf/
- Windows部署本地版Overleaf教程：
  https://blog.csdn.net/yitingren5764/article/details/121377630

#### 字体安装

由于本地Overleaf缺失部分字体，可能导致模板编译出错。在`fonts`文件夹下提供了Times New Roman、STKaiti等论文模板所需字体。

```shell
# 复制字体到容器(Shell运行)
docker cp N:\\Downloads\\Programs\\Overleaf\\fonts sharelatex:/usr/local/share/fonts/
```

将上述路径修改为本地路径，注意在路径分割处使用双斜杠`\\`，否则会将前一个路径解释为容器，可能报错"copying between containers is not supported"。

```shell
# 刷新字体索引(容器中运行)
fc-cache -f -v
```

如果需要其它字体，可以网络下载相应的`.ttf`文件，重新执行上述操作。

#### 编译环境

注意使用XeLaTeX编译`main.tex`文件，不能使用pdfLaTeX。