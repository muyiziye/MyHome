## 学习arm

***

    * 在安装好了交叉编译器arm-linux-gcc之后，发现其不能用，说是找不到命令，可能是因为操作系统是64位的，而交叉编译器是32位的，所以不能使用。

    * 在使用ftp服务的时候，发现不能put文件到arm上，原因可能是arm上的文件没有权限。

    * 在运行命令make menuconfig 的时候出现错误Unable to find the ncurses libraries，此时使用下面命令安装ncurese。

      sudo apt-get install ncurses-dev