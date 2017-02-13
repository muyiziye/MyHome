## 配置python的虚拟环境

1.首先安装python和pip，pip安装需要下载包，解压后运行python setup.py install即可安装pip。

2.然后安装虚拟环境，pip install virtualenv. 安装完成之后可以使用pip freeze来查看所有使用pip安装的软件的版本号。这些就是安装在/usr/local/lib/python2.7下的所有包的信息。

3.创建一个文件mkdir work，然后在work目录下面运行命令virtualenv env. 这时候已经建立了一个叫做env的虚拟python环境了。

4.运行命令source env/bin/activate即可开启虚拟环境。

5.在虚拟环境下面输入deactive命令即可退出虚拟环境。
---

