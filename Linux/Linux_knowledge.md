## Linux知识点积累

***

* 1 将ubuntu设置成以字符方式启动，要修改/etc/default/grub文件，在GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"后面添加text，即将双引号内的文本变成"quiet splash text"。使用sudo的方式打开，修改完后使用命令sudo update-grub来进行更新。

* 2 修改ubuntu的语言，修改/etc/default/locale文件，在LANG="en_US.UTF-8"，LANGUAGE="en_US:en"和LANG="en_US.UTF-8"，LANGUAGE="en_US:en"之间进行切换。使用sudo的方式打开，修改完后使用命令sudo update-locale来进行更新。

* 3 rm命令的选项-f的含义是忽略不存在的文件，并且不提是错误信息。

* 4 当gcc编译需要一个以上的.h文件路径的时候，可以使用多个-I 来带路径，（eg，gcc -I /xx/x -I /x/xx -c x.c -o x）
