##51单片机在linux(ubuntu)下的环境搭建。
  

***

    > 写这篇文章的原因：已经从window阵营努力转移到linux阵营，现在在玩51单片机，从网上找的资料不能够解决我的问题，所以就到处尝试，最终可以成功编译，烧写代码。

    > 环境：ubuntu12.04(32位)，使用的单片机芯片stc89c52rc。

    > 工具：sdcc，hex2bin，stcflash
        
        * 1.首先安装sdcc(命令：sudo apt-get install sdcc)，这个是进行编译用的，可以生成.ihx文件(同时会生成很多其他文件，可看sdcc手册)，该命令使用方法：sdcc sourcefile.c。
        
        * 2.然后使用命令  packihx sourcefile.ihx \> sourcefile.hex  这样就生成了.hex文件。
        
        * 3.接着下载hex2bin文件，网址(http://sourceforge.net/projects/hex2bin/files/latest/download)。命令：hex2bin sourcefile.hex。之后就会生成sourcefile.bin文件。
        
        * 4.再然后下载stcflash(网址：github.com/laborer/stcflash)。下载的是zip文档，解压后进入目录，命令行下安装环境：sudo apt-get install python-serial  。目前已经可以使用了。使用方法，进入文件目录，键入命令：sudo python ./stcflash.py ~/sourcefile.bin(即你的.bin文件的位置)。我下载了gSTCISP不能使用，故这里使用stcflash。
        
        * 5.程序已经烧写完成。
        
        * 6.我已经将所有用到的文件打包上传(包括hex2bin，stcflash，可使用的代码)。
