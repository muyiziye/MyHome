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
"set previewwindow   " 标识预览窗口
set history=2000     " set command history to 2000 "历史记录2000条
set ruler            " 标尺
"--命令行设置--  
set showcmd          " 命令行显示输入的命令  
set showmode         " 命令行显示vim当前模式  
syntax on            " 语法高亮  
```