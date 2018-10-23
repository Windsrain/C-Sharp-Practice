# C#Practice

基于《C#入门经典》所做的笔记。

## 第3章 变量和表达式

### C#基本语法

C#编译器不考虑代码中的空格、回车符或制表符（统称为空白字符）。

C#是一种块结构的语言，所有语句都是代码块的一部分。这些块用花括号来界定，代码块可以包含任意多行语句，或者根本不包含语句。

```C#
{
    <code line 1,statement 1>;
    <code line 2,statement 2>
        <code line 3,statement 3>;
}
```

其中**<code line x,statement y>**部分并非真正的C#代码，而是作为C#语句的占位符。

```C#
{
    <code line 1>;
    {
        <code line 2>;
        <code line 3>;
    }
    <code line 4>;
}
```

上面代码还使用了缩进格式，提高了C#代码的可读性。

C#注释行的使用和C、C++基本相同。

C#代码也是区分大小写的。



### C#控制台应用程序的基本结构

```C#
using System;
using System.Collections.Generic;
using System.Ling;
using System.Text;
using System.Threading.Tasks;
namespace ConsoleApplication1
{
    class Program
    {
        static void Main(string[] args)
        {
            Console.WriteLine("The first app in Beginning C# Programming!");
            Console.ReadKey();
        }
    }
}
```

我们可以添加语句定义可以展开和折叠的代码区域的开头和结尾，如：

```C#
#region Using directies
using System;
using System.Collections.Generic;
using System.Ling;
using System.Text;
using System.Threading.Tasks;
#endregion
```



### 变量

声明变量的C#语法是指定类型和变量名

```C#
<type> <name>;
```

#### 简单类型

简单类型没有子类型或特性。

许多不同的整数类型可用于存储不同范围的数值。

|  类型  |     别名      |                    允许的值                     |
| :----: | :-----------: | :---------------------------------------------: |
| sbyte  | System.SByte  |             介于-128和127之间的整数             |
|  byte  |  System.Byte  |              介于0和255之间的整数               |
| short  | System.Int16  |           介于-32768和32767之间的整数           |
| ushort | System.UInt16 |             介于0和65535之间的整数              |
|  int   | System.Int32  | 介于-2<sup>31</sup>和2<sup>31</sup>-1之间的整数 |
|  uint  | System.UInt32 |        介于0和2<sup>32</sup>-1之间的整数        |
|  long  | System.Int64  | 介于-2<sup>63</sup>和2<sup>63</sup>-1之间的整数 |
| ulong  | System.UInt64 |        介于0和2<sup>64</sup>-1之间的整数        |

可使用的浮点数变量类型有3种：float、double和decimal。前两种可以用+/-m*2<sup>e</sup>的形式存储浮点数。

decimal使用另一种形式：+/_m*10<sup>e</sup>。

除数值类型外，还有三种简单类型。

|  类型  |      别名      |                允许的值                 |
| :----: | :------------: | :-------------------------------------: |
|  char  |  System.Char   | 一个Unicode字符，存储0和65536之间的整数 |
|  bool  | System.Boolean |           布尔值：true或false           |
| string | System.String  |                一组字符                 |

string的字符数量没有上线，可以使用可变大小的内存。

写出一段如下代码：

```C#
        static void Main(string[] args)
        {
            int myInteger;
            string myString;
            myInteger = 17;
            myString = "\"myInteger\" is";
            Console.WriteLine($"{myString} {myInteger}");
            Console.ReadKey();
        }
```

* 声明两个变量
* 给这两个变量赋值
* 将这两个变量的值输出到控制台

```C#
            Console.WriteLine($"{myString} {myInteger}");
```

这是C#6的一个新功能，称为字符串插入，类似于把文本写到控制台的简单方法。

#### 变量的命名

* 变量名的第一个字符必须是字母、下划线或@
* 其后的字符可以是字母、下划线或数字

注意，变量名不能与关键字重名

#### 字面值

变量类型都有相关的字面值，可以在后面添加一些字符来指定想要的类型。

C#中的转义序列与C相同。



### 表达式

#### 数学运算符

和C相同

P36



