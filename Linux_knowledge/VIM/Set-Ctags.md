### 设置Ctags工具

**1.** 首先需要下载Ctags工具

**2.** 编译，安装Ctags

> tar -zxvf Ctagsxxx.tgz .

> cd Ctagsxxx

> ./configure

> make

> make install (该句需要用超级用户来，否则安装可能会失败)

**3.** 生成ctags

> 进入到你的code的顶级目录下面，输入命了ctags -R *， 之后会在该目录下面生成一个文件tags，该文件中记录了代码的跳转路径

**4.** 在~/vimrc中添加下面两句

> set tags=tags;

> set autochdir

**5.** 在code里面进行跳转

> ctrl+\] 即可跳转到定义的地方

> ctrl+t 跳回到原来的地方