1.排版
1.1缩进
程序块要采用缩进风格编写，缩进大小为4个空格，不要使用Tab作为缩进的单位。

说明：不同的编辑器阅读程序时，可能会因TAB键所设置的空格数目不同而造成程序布局不整齐。另外，对于由开发工具自动生成的代码可以有例外。

1.2对齐
程序的分界符‘{’和‘}’应独占一行并且位于同一列，同时与引用它们的语句左对齐。 

“{ }”之内的代码块在‘{’右边4个空格处左对齐。

示例：如下表

    for (i = 0; i < SIZE - 1; i++)
    {
        index = i;
        
        for (j = i + 1; j < SIZE; j++)
        {
            if (number[index] > number[j])
            {
                index = j;
            }
        }
        
        if (index != i)
        {
            temp = number[i];
number[i] = number[index];
number[index] = temp;
        }
    }
    If (condition) 
    { 
        // program code 
    } 
    else 
    { 
        // program code 
    }

1.3空行
相对独立的程序块之间空行。

示例：如下表

    for (i = 0; i < SIZE - 1; i++)
    {
        index = i;
        
        for (j = i + 1; j < SIZE; j++)
        {
            if (number[index] > number[j])
            {
                index = j;
            }
        }
        
        if (index != i)
        {
            temp = number[i];
number[i] = number[index];
 number[index] = temp;
        }
    }
1.4代码行内的空格 
if、for、while 等关键字之后应留一个空格再跟左括号‘（’，以突出关键字。

函数名之后不要留空格，紧跟左括号‘（’，以与关键字区别。

‘，’之后要留空格，如 function(x, y, z)。如果‘;’不是一行的结束符号，其后也要留空格，如 for (initialization; condition; update)。

赋值操作符、比较操作符、算术操作符、逻辑操作符，如“=”、“！=”  “>=”、“<=”、“+”、“*”、“%”、“&&”、“||”、“<<”,“^”等二元操作符的前后应当加空格。

一元操作符如“++”、“--”、“&”（地址运算符）等前后不加空格。

“［］”、“.”、“->”这类操作符前后不加空格。

对于表达式比较长的 for 语句和 if 语句，为了紧凑起见可以适当地去掉一些空格，如 for (i=0; i<10; i++)和 if ((a<=b) && (c<=d))。

1.5长行划分
较长的语句（>80字符）要分成多行书写，长表达式要在低优先级操作符处划分新行，操作符放在新行之首，划分出的新行要进行适当的缩进。

示例：

if ((very_longer_variable1 >= very_longer_variable12) 
&& (very_longer_variable3 <= very_longer_variable14) 
&& (very_longer_variable5 <= very_longer_variable16)) 
{ 
    dosomething(); 
}

for (very_longer_initialization; 
     very_longer_condition; 
     very_longer_update) 
{ 
  dosomething(); 
}

1.6独占一行
if、for、do、while、case、switch、default等语句自占一行，且if、for、do、while等语句的执行语句部分无论多少都要加括号{}。 

示例：如下表左边的例子不符合规范，应该写成下表右边的例子

if (index == SIZE) return;

if (index == SIZE)
{
    return;
}

不建议把多个短语句写在一行中，即一行只写一条语句。

示例：如下表左边的例子不符合规范，应该写成下表右边的样式
rect.length = 0;  rect.width = 0;
rect.length = 0;
rect.width  = 0;
2.注释
2.1文件注释
源文件头部应进行注释，至少列出：文件名称、创建日期、作者、模块目的/功能、最后修改时间等信息

示例：

/*
 * CREATE DATE:    // 填写创建日期
 * AUTHOR:         // 填写作者
 * PURPOSE: 
 *     // 填写文档功能，作用
 * LAST MODIFY DATE:     // 填写最后修改时间
 * REMARK:
 *     // 备注
 */

2.2函数注释
每个函数应进行注释，至少列出：函数的目的/功能、输入参数、输出参数、返回值等信息。

示例：

/*
 * DESCRIPTION:     // 填写函数功能、性能等的描述
 * INPUT:            // 填写输入参数说明，包括每个参数的作用、取值说明及参数间关系。
 * OUTPUT:          // 填写对输出参数的说明。
 * RETURN:          // 填写函数返回值的说明
 * OTHERS:          // 其它说明
 */


2.3块结束注释
建议在程序块的结束行右方加注释标记，以表明某程序块的结束。
说明：当代码段较长，特别是多重嵌套时，这样做可以使代码更清晰，更便于阅读。

示例：

if (...)
{
    // program code

    while (index < MAX_INDEX)
    {
        // program code
    } /* end of while (index < MAX_INDEX) */     // 指明该条while语句结束
} /* end of  if (...)*/     // 指明是哪条if语句结束



2.4其他注释书写规范
一般情况下，源程序有效注释量必须在20％以上。

边写代码边注释，修改代码同时修改相应的注释，以保证注释与代码的一致性。不再有用的注释要删除。

注释的内容要清楚、明了，含义准确，防止注释二义性。

注释应与其描述的代码相近，对代码的注释应放在其上方或右方（对单条语句的注释）相邻位置，不可放在下面，如放于上方则需与其上面的代码用空行隔开。

避免在一行代码或表达式的中间插入注释。

3.标识符
3.1命名方式
常量所有字母大写；
除常量外的所有变量名、函数名称小写开头，单词与单词之间用下划线隔开，或者除第一个单词外其他单词第一个字母大写。
int the_number_of_class;
int theNumberOfClss;

3.2循环专用变量
说明：i, j, k 是循环语句专用变量，除特殊情况外不得用作其他用途，一般也不用其他名称作为循环变量