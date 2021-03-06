## 设置vim环境 ##

**1.** 基本环境配置

```
set shiftwidth=4     " (自动) 缩进使用的4个空格 
set tabstop=4        " 设置制表符(tab键)的宽度
set showmatch        " 设置匹配模式，显示匹配的括号 
set linebreak        " 整词换行 
set whichwrap=b,s,<,>,[,] 
                     " 光标从行首和行末时可以跳到另一行去 
set mouse=a          " Enable mouse usage (all modes) "使用鼠标 
set number           " Enable line number "显示行号 
set relativenumber   " 显示相对行号，于上面结合可以继显示相对行号，在当前行显示绝对行号
"set previewwindow   " 标识预览窗口
set history=2000     " set command history to 2000 "历史记录2000条
set ruler            " 标尺
"--命令行设置--  
set showcmd          " 命令行显示输入的命令  
set showmode         " 命令行显示vim当前模式  
set nocp             " 让vim工作在不兼容模式，不去模仿vi的动作
set et               " 在编辑的时候将tab替换为空格,并不会将已经存在的tab替换掉，替换全局的话输入:retab
set cin              " 设置c/c++格式的自动缩进
set ai               " 设置普通文件模式的自动缩进
set nowrap           " 设置文本显示超过屏幕的部分不换行显示。
set guioptions+=b    " 在gui中在有文本显示超过屏幕的时候添加滚动条
set scrolloff=7      " 设置光标在滚动时上下最少显示7行
syntax on            " 语法高亮  
```

**2.** vim快捷键记录
```
:Ex 开启目录浏览器，可以浏览当前目录下的所有文件，并可以选择
:Sex 水平分割当前窗口，并在一个窗口中开启目录浏览器

:shell 可以在不关闭vi的情况下切换到shell命令行
:exit 从shell回到vi
```