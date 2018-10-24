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

#### 赋值运算符

和C相同

#### 运算符的优先级

和C相同

#### 名称空间

名称空间是**.NET**中提供应用程序代码容器的方式，这样就可以唯一地标识代码及其内容。

默认情况下，C#代码包含在全局名称空间中。这意味着对于包含在这段代码中的项，全局名称空间中的其他代码只要通过名称进行引用，就可以访问它们。可使用**namespace**关键字为花括号中的代码块显示定义名称空间。如果在该名称空间代码的外部使用名称空间中的名称，就必须写出该名称空间中的限定名称。

```C#
namespace LevelOne
{
    // code in LevelOne namespace
    namespace NameOne
    {
        // code in NameOne namespace
    }
}
// code in global namespace
```

在名称空间**LevelOne**中编写的代码可以直接使用**NameOne**来引用该名称，但全局名称空间中的代码必须使用限定名称**LevelOne.NameOne**来引用这个名称。

**using**语句本身不能访问另一个名称空间中的名称，除非名称空间中的代码以某种方式链接到项目上，或者代码是在该项目的源文件中定义的，或是在链接到该项目的其他代码中定义的。**using**语句便于我们访问这些名称，减少代码量，以及提高可读性。、



## 第4章 流程控制

### 布尔逻辑

与C相同

```C#
        static void Main(string[] args)
        {
            Console.WriteLine("Enter an integer:");
            int myInt = Convert.ToInt32(Console.ReadLine());
            bool isLessThan10 = myInt < 10;
            bool isBetween0And5 = (0 <= myInt) && (myInt <= 5);
            Console.WriteLine($"Integer less than 10? {isLessThan10}");
            Console.WriteLine($"Integer between 0 and 5 {isBetween0And5}");
            Console.WriteLine($"Exactly one of the above is true? {isLessThan10 ^ isBetween0And5}");
            Console.ReadKey();
        }
```

使用**Convert.ToInt32()**从字符串输入中得到一个整数，该方法是**System.Convert**静态类的一部分。



### 分支

#### 三元运算符

```C#
<test> ? <resultIfTrue> : <resultIfFalse>
```

#### if语句

```C#
if (<test>)
{
    <code executed if <test> is true>;
}
else
{
    <code executed if <test> is false>;
}
```

#### switch语句

```C#
switch (<testVar>)
{
    case <comparisonVar1>:
        <code to execute if <testVar> == <comparisonVal1>>
        break;
    case <comparisonVar2>:
        <code to execute if <testVar> == <comparisonVal2>>
        break;
    ···
    case <comparisonVarN>:
        <code to execute if <testVar> == <comparisonValN>>
        break;
    default:
        <code to execute if <testVar> != comparisonVals>
        break;
}
```

C#与C和C++的不同是，没有**break**语句，导致连续执行**case**块是非法的。可以用**goto**语句跳**case**块。

我们可以把多个**case**语句放在一起，其后加一个代码块，实际上是一次检查多个条件。

假如定义一个字符串变量**name**，我们可以用**name.ToLower()**把字符全部转为小写，方便在**switch**语句中进行匹配。



### 循环

#### do循环

```C#
do
{
    <code to be looped>
} while (<Test>);
```

#### while循环

```C#
while <(Test)>
{
	<code to be looped>
}
```

#### for循环

```C#
for (<initialization>;<condition>;<operation>)
{
    <code to loop>
}
```

#### 循环的中断

* **break**——立即终止循环
* **continue**——立即终止当前的循环（继续执行下一次循环）
* **return**——跳出循环及包含该循环的函数

#### 无限循环

```C#
while (true)
{
    // code in loop
}
```



## 第5章 变量的更多内容

### 类型转换

* **隐式转换：**从类型A到类型B的转换可在所有情况下进行
* **显式转换：**从类型A到类型B的转换只能在某些情况下进行，转换规则比较复杂，应进行额外处理

#### 隐式转换

任何类型A，只要其取值范围完全包含在类型B的取值范围内，就可以隐式转换为类型B。

#### 显式转换

```	C#
(<destinationType>)<sourceVar>
```

作显式转换时，需要了解是否有数据丢失。一种方式是检查源变量的值，另一种方式是迫使系统特别注意运行期间的转换。在将一个值放在一个变量中时，如果该值过大，不能放在该类型的变量中，就会导致溢出，这就需要检查，需要用到两个关键字——**checked**和**unchecked**。

```C#
checked(<expression>)
unchecked(<expression>)
```

使用**checked**检查，若溢出，程序会崩溃，并显示错误信息。

也可以配置应用程序，让这种类型的表达式都和包含**checked**关键字一样，除非明确使用**unchecked**关键字。

**Solution->Explorer**，选择**Properties**选项，打开**Build**设置，选择**Advanced**，进行配置。

#### 使用Convert命令进行显式转换









