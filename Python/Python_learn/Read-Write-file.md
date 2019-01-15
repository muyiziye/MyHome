## python读写文件

---

### 1. open函数的基本介绍

* 用于打开一个文件，返回file对象。

* 方法: 

  ```
  f = open(name[, mode[, buffering]])
  ```

* name 为打开文件的名字。mode可以为读，写，追加。默认不写为只读r, 加上b为二进制方式的读取通常处理图片和音乐等。

### 2. 读取文件的n种方式

**A.** f.read([size]) 将指定的字节数读取到字符串中，未给定或为负数则全部读取。

**B.** f.readline([size]) 读取整行，其中包括\n 字符。 通常使用方法为

  ```
  with open(file_name, 'r') as f:
    a_str = f.readline()
  ```

**C.** f.readlines([size]) 读取并且返回列表，size设置一次读取多少字节， 有和上面类似的方法。