## Linux知识点积累

***

* 1 将ubuntu设置成以字符方式启动，要修改/etc/default/grub文件，在GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"后面添加text，即将双引号内的文本变成"quiet splash text"。使用sudo的方式打开，修改完后使用命令sudo update-grub来进行更新。

* 2 修改ubuntu的语言，修改/etc/default/locale文件，在LANG="en_US.UTF-8"，LANGUAGE="en_US:en"和LANG="en_US.UTF-8"，LANGUAGE="en_US:en"之间进行切换。使用sudo的方式打开，修改完后使用命令sudo update-locale来进行更新。

* 3 rm命令的选项-f的含义是忽略不存在的文件，并且不提是错误信息。

* 4 当gcc编译需要一个以上的.h文件路径的时候，可以使用多个-I 来带路径，（eg：gcc -I /xx/x -I /x/xx -c x.c -o x）

* 5 将文件夹的x权限去掉，那么该文件就不可以进入了，将文件夹的r权限去掉，那么就不能使用ls来查看文件夹内的文件。

* 6 使用nl可以显示文件内容，与cat不同的是其代行号。

* 7 bc计算器的使用，可以通过设置obase=10，ibase=16来进行16进制到10进制的转换。

* 8 grep的使用: grep [-acinv] '搜索的字符串' filename

    参数说明

    -a:将binary档案以txt档案的方式搜寻数据。

    -c:计算找到的‘搜索字符串’的次数。

    -i:忽略大小写的不同。

    -n:顺便输出行号。

    -v:反向显示，显示没有‘搜索字符串’的那些行。

* 9 zip的使用: zip 和 unzip 压缩以及解压
    
    zip -r xx.zip ./* 把后面目录中的压缩为xx.zip文件

    unzip -o -d /home/ly/ xx.zip 把xx.zip文件解压到/home/ly/文件中，-o表明不提示直接覆盖，-d则是指明了解压的文件。

* 10 md5sum的使用： 

    md5sum xx.file > xx.md5 此时会将xx.file文件的md5值和文件名一起传入xx.md5中。

    校验时输入md5sum -c xx.md5，此时会就会对文件进行校验，如果没有改变的话会输出ok

* 11 ls简单实用

    ls -alh 实用-h能够更清楚的看数据的单位，K，M，G

* 12 可以使用下面方法来制作usb的启动介质，dd if=disk.img of=/dev/sda1 或者 cat diskboot.img > /dev/sda1