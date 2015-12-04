##  升级版本

***

  * 1 修改  D:\Code\sub\S733_AG01_900_2100\Y01\make\perl_script中的pac.pl文件，将其版本号+1；

  * 2 修改  D:\Code\sub\S733_AG01_900_2100\Y01\version的SC7702_sc7701_barphone_version.c将其版本号+1；

  * 3 将sub的代码copy到main里面，然后进行编译，代码：make m="fdl1_nf fdl2_nf"  job=4，make new job=4

  * 4 拷贝  D:\Code\main\build\S7011B_AG01_900_2100_128X160BAR_builddir\img中的两个文件nvitem，S733_AM208-DIGITEL_900_2100_Y01_V0.1.pac 到\\192.168.18.68\软件部\软件版本\S733\S733_AG01_900_2100\Y01\V0.2\RELEASE 目录下，此时RELEASE版本已经拷贝到服务器上。

  * 5 修改Makefile文件，D:\Code\sub\S733_AG01_900_2100\Y01\project_S7011B_AG01_900_2100_128X160BAR.mk，（将RELEASE_INFO由TRUE改成FALSE）。

  * 6 将sub代码拷贝到main，编译（步骤同上）。

  * 7 拷贝同上面相同的文件到\\192.168.18.68\软件部\软件版本\S733\S733_AG01_900_2100\Y01\V0.2\DEBUG 目录下，同时还要拷贝两个文件SC7702_S7011B_AG01_900_2100_128X160BAR.axf，SC7702_S7011B_AG01_900_2100_128X160BAR.map。此时DEBUG版本已经拷贝到服务器上。