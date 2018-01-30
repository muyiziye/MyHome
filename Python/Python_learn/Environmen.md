---
title: 配置python虚拟环境

date: 2018-01-28 23:45
tags:
- python
- 环境
categories:
- python

---

## 配置python的虚拟环境

1.首先安装python和pip，pip安装需要下载包，解压后运行python setup.py install即可安装pip。有时候pip和setuptools的版本太低了，升级方法为:pip install -U setuptools, pip install -U pip

2.然后安装虚拟环境，pip install virtualenv. 安装完成之后可以使用pip freeze来查看所有使用pip安装的软件的版本号。这些就是安装在/usr/local/lib/python2.7下的所有包的信息。

3.创建一个文件mkdir work，然后在work目录下面运行命令virtualenv env. 这时候已经建立了一个叫做env的虚拟python环境了。在此处请注意，可以-p参数来指定生成的虚拟环境的python版本，virtualenv -p /usr/bin/python2.7 env

4.运行命令source env/bin/activate即可开启虚拟环境。

<!-- more -->

5.在虚拟环境下面输入deactive命令即可退出虚拟环境。

---

## 使用virtualenvwrapper来对virtualenv进行二次封装使得其更加的好用。

1.首先使用命令pip install virtualenvwrapper来安装virtualenvwrapper这个工具。此时会在/usr/local/bin/virtualenvwrapper.sh的脚本。

2.因为需要修改配置使其登录有效，所以需要修改.bashrc文件，添加下面信息：
``` bash
if [ -f /usr/local/bin/virtualenvwrapper.sh ]; then

  export WORKON_HOME=$HOME/.virtualenvs

  source /usr/local/bin/virtualenvwrapper.sh

fi
```


3.运行命令source ～/.bashrc让上述配置生效。

4.使用命令mkvirtualenv newenv,此时就会生成相应的需要的环境，该工作目录即在$HOME/.virtualenvs目录下面了。

5.可以使用workon newenv来使得新创建的虚拟环境生效。

6.如果需要删除虚拟环境使用命令:rmvirtualenv newenv

---

## END
<!--blog-->