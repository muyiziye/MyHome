## 学习arm

***

    * 在安装好了交叉编译器arm-linux-gcc之后，发现其不能用，说是找不到命令，可能是因为操作系统是64位的，而交叉编译器是32位的，所以不能使用。

    * 在使用ftp服务的时候，发现不能put文件到arm上，原因可能是arm上的文件没有权限。

    * 在运行命令make menuconfig 的时候出现错误Unable to find the ncurses libraries，此时使用下面命令安装ncurese。

      sudo apt-get install ncurses-dev

    * 在运行命令make zImage的时候出现错误:libstdc++.so.6:con't open，这是因为使用的64位的系统，没有相关的32位的库，

      sudo apt-get install lib32stdc++6     sudo apt-get install lib32z1

      使用这两条命令即可。