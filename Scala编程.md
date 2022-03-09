# Scala安装及环境配置（IntelliJ IDEA版）



1. 安装 Java8 JDK （Java1.8）
2. 下载IntelliJ IDEA
3. 打开IDEA，在创建项目的页面左侧找到Plugins，搜索Scala插件并安装
4. 在左侧栏找到scala，点击，然后在右侧找到IDEA，然后点击NEXT

![1640574244051](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1640574244051.png)

5. 在Scala SDK处点击create，然后download，下载最新版本的scala（2.13.7）
6. 下载完成后点击finish
7. 开始编程

# Scala 简介

Scala是一门现代的多范式语言，志在以简洁、优雅及类型安全的方式来表达常用的编程模型。它平滑地集成了面向对象和函数式语言的特性。 

- 面向对象：

  Scala是一种**纯面向对象**的语言，每个值都是对象。对象的数据类型以及行为由类和特质描述。

  类抽象机制的扩展有两种途径：一种途径是子类继承，另一种途径是灵活的混入机制。这两种途径能避免多重继承的种种问题。

- 函数式：

  Scala也是一种函数式语言，其函数也能当成值来使用。Scala提供了轻量级的语法用以定义匿名函数，支持高阶函数，允许嵌套多层函数，并支持柯里化。Scala的case class及其内置的模式匹配相当于函数式编程语言中常用的代数类型。 

- 静态类型的：

  Scala配备了一个拥有强大表达能力的类型系统，它可以静态地强制以安全、一致的方式使用抽象。 

  型系统具体支持以下特性：

  - 泛型类
  - 协变和逆变
  - 标注
  - 类型参数的上下限约束
  - 把类别和抽象类型作为对象成员
  - 复合类型
  - 引用自己时显式指定类型
  - 视图
  - 多态方法

- 扩展性：

  Scala的设计秉承一项事实，即在实践中，某个领域特定的应用程序开发往往需要特定于该领域的语言扩展。Scala提供了许多独特的语言机制，可以以库的形式轻易无缝添加新的语言结构：

  - 任何方法可用作前缀或后缀操作符
  - 可以根据预期类型自动构造闭包。

- 并发性：

  Scala使用Actor作为其并发模型，Actor是类似线程的实体，通过邮箱发收消息。Actor可以复用线程，因此可以在程序中可以使用数百万个Actor,而线程只能创建数千个。在2.10之后的版本中，使用Akka作为其默认Actor实现。 

# Scala 基础语法

Scala 与 Java 的最大区别是：Scala 语句末尾的分号 ; 是可选的。 

- **对象 -** 对象有属性和行为。例如：一只狗的状属性有：颜色，名字，行为有：叫、跑、吃等。对象是一个类的实例。
- **类 -** 类是对象的抽象，而对象是类的具体实例。
- **方法 -** 方法描述的基本的行为，一个类可以包含多个方法。
- **字段 -** 每个对象都有它唯一的实例变量集合，即字段。对象的属性通过给字段赋值来创建。

Scala 基本语法需要注意以下几点：

- **区分大小写** -  Scala是大小写敏感的，这意味着标识Hello 和 hello在Scala中会有不同的含义。
- **类名** - 对于所有的类名的第一个字母要大写。
  如果需要使用几个单词来构成一个类的名称，每个单词的第一个字母要大写。
- **方法名称** - 所有的方法名称的第一个字母用小写。
- **程序文件名** - 程序文件的名称应该与对象名称完全匹配(新版本不需要了，但建议保留这种习惯)。 
- **def main(args: Array[String])** - Scala程序从main()方法开始处理，这是每一个Scala程序的强制程序入口部分。

## Scala 包

Scala 使用 package 关键字定义包，在Scala将代码定义到某个包中有两种方式：

第一种方法和 Java 一样，在文件的头定义包名，这种方法就后续所有代码都放在该包中。

```scala
package com.runoob
class HelloWorld
```

第二种方法有些类似 C#，如：

```scala
package com.runoob {
  class HelloWorld 
}
```

## 引用

Scala 使用 import 关键字引用包。 

import语句可以出现在任何地方，而不是只能在文件顶部。import的效果从开始延伸到语句块的结束。这可以大幅减少名称冲突的可能性。

如果想要引入包中的几个成员，可以使用selector（选取器）：

```scala
import java.awt.{Color, Font}
 
// 重命名成员
import java.util.{HashMap => JavaHashMap}
 
// 隐藏成员
import java.util.{HashMap => _, _} // 引入了util包的所有成员，但是HashMap被隐藏了
```

# Scala 数据类型

| 数据类型 | 描述                                                         |
| :------- | ------------------------------------------------------------ |
| Byte     | 8位有符号补码整数。数值区间为 -128 到 127                    |
| Short    | 16位有符号补码整数。数值区间为 -32768 到 32767               |
| Int      | 32位有符号补码整数。数值区间为 -2147483648 到 2147483647     |
| Long     | 64位有符号补码整数。数值区间为 -9223372036854775808 到 9223372036854775807 |
| Float    | 32 位, IEEE 754 标准的单精度浮点数                           |
| Double   | 64 位 IEEE 754 标准的双精度浮点数                            |
| Char     | 16位无符号Unicode字符, 区间值为 U+0000 到 U+FFFF             |
| String   | 字符序列                                                     |
| Boolean  | true或false                                                  |
| Unit     | 表示无值，和其他语言中void等同。用作不返回任何结果的方法的结果类型。Unit只有一个实例值，写成()。 |
| Null     | null 或空引用                                                |
| Nothing  | Nothing类型在Scala的类层级的最底端；它是任何其他类型的子类型。 |
| Any      | Any是所有其他类的超类                                        |
| AnyRef   | AnyRef类是Scala里所有引用类(reference class)的基类           |

上表中列出的**数据类型都是对象**，也就是说scala没有java中的原生类型。在scala是可以对数字等基础类型调用方法的。

## Scala 基础字面量

### 整型字面量

整型字面量用于 Int 类型，如果表示 Long，可以在数字后面添加 L 或者小写 l 作为后缀。：

```
0
035
21 
0xFFFFFFFF 
0777L
```

### 浮点型字面量

如果浮点数后面有f或者F后缀时，表示这是一个Float类型，否则就是一个Double类型的。实例如下：

```
0.0 
1e30f 
3.14159f 
1.0e100
.1
```

### 布尔型字面量

布尔型字面量有 true 和 false。

### 符号字面量

符号字面量被写成： **'<标识符>** ，这里 **<标识符>** 可以是任何字母或数字的标识（注意：**不能以数字开头**）。这种字面量被映射成预定义类scala.Symbol的实例。

如： 符号字面量 **'x**  是表达式 **scala.Symbol("x")** 的简写，符号字面量定义如下： 

```
package scala
final case class Symbol private (name: String) {
   override def toString: String = "'" + name
}
```

### 字符字面量

在 Scala 字符变量使用单引号 **'** 来定义，如下：

```
'a' 
'\u0041'
'\n'
'\t'
```

其中 **\** 表示转义字符，其后可以跟 **u0041** 数字或者 **\r\n** 等固定的转义字符。

### 字符串字面量

在 Scala 字符串字面量使用双引号 **"** 来定义，如下：

```
"Hello,\nWorld!"
"菜鸟教程官网：www.runoob.com"
```

### 多行字符串的表示方法

多行字符串用三个双引号来表示分隔符，格式为：**""" ... """**。

实例如下：

```
val foo = """菜鸟教程
www.runoob.com
www.w3cschool.cc
www.runnoob.com
以上三个地址都能访问"""
```

### Null 值

空值是 scala.Null 类型。

Scala.Null和scala.Nothing是用统一的方式处理Scala面向对象类型系统的某些"边界情况"的特殊类型。

Null类是null引用对象的类型，它是每个引用类（继承自AnyRef的类）的子类。Null不兼容值类型。

# Scala 变量

## 变量和常量

在 Scala 中，使用关键词 **"var"** 声明变量，使用关键词 **"val"** 声明常量。

实例如下：

```scala
var myVar : String = "Foo"
val myVal : String = "Foo"
```

## 变量类型声明

变量的类型在变量名之后等号之前声明。定义变量的类型的语法格式如下：

```
var VariableName : DataType [=  Initial Value]
```

## 变量类型引用

在 Scala 中声明变量和常量不一定要指明数据类型，在没有指明数据类型的情况下，其数据类型是通过变量或常量的初始值推断出来的。

所以，**如果在没有指明数据类型的情况下声明变量或常量必须要给出其初始值**，否则将会报错。

```scala
var myVar = 10;
val myVal = "Hello, Scala!";
```

以上实例中，myVar 会被推断为 Int 类型，myVal 会被推断为 String 类型。

## Scala 多个变量声明

Scala 支持多个变量的声明：

```scala
val xmax, ymax = 100  // xmax, ymax都声明为100
```

如果方法返回值是元组，我们可以使用 val 来声明一个元组：

```scala
val pa = (400, "Foo")
```

# Scala 访问修饰符

Scala 访问修饰符基本和Java的一样，分别有：private，protected，public。

如果没有指定访问修饰符，默认情况下，Scala 对象的访问级别都是 public。

Scala 中的 private 限定符，**比 Java 更严格**，在嵌套类情况下，外层类甚至不能访问被嵌套类的私有成员。

- private：

  ```scala
  class Outer{
      class Inner{
          private def f(){
              println("f")
          }
          class InnerMost{
              f() // 正确
          }
      }
      (new Inner).f() //错误
  }
  ```

  **(new Inner).f( )** 访问不合法是因为 **f** 在 Inner 中被声明为 private，而访问不在类 Inner 之内。

  但在 InnerMost 里访问 **f** 就没有问题的，因为这个访问包含在 Inner 类之内。

  Java 中允许这两种访问，因为它允许外部类访问内部类的私有成员。

- protected：

  在 scala 中，对保护（Protected）成员的访问比 java 更严格一些。因为它只允许保护成员在**定义了该成员的的类的子类中**被访问。而在java中，用protected关键字修饰的成员，除了定义了该成员的类的子类可以访问，**同一个包里的其他类也可以进行访问**。

  ```scala
  package p{
      class Super{
          protected def f() {
              println("f")
          }
      }
      class Sub extends Super{
          f()
      }
      class Other{
          (new Super).f() //错误
      }
  }
  ```

  上例中，Sub 类对 f 的访问没有问题，因为 f 在 Super 中被声明为 protected，而 Sub 是 Super 的子类。相反，Other 对 f 的访问不被允许，因为 other 没有继承自 Super。而后者在 java 里同样被认可，因为 Other 与 Sub 在同一包里。

- public：

  Scala 中，如果没有指定任何的修饰符，则默认为 public。这样的成员在任何地方都可以被访问。 

## 作用域保护

Scala中，访问修饰符可以通过使用限定词强调。格式为:

```
private[x] 

或 

protected[x]
```

这里的x指代某个所属的包、类或单例对象。如果写成private[x],读作"这个成员除了对[…]中的类或[…]中的包中的类及它们的伴生对像可见外，对其它所有类都是private。

这种技巧在横跨了若干包的大型项目中非常有用，它允许你定义一些在你项目的若干子包中可见但对于项目外部的客户却始终不可见的东西。

```SCALA
package bobsrockets{
  package navigation{
    private[bobsrockets] class Navigator{
     protected[navigation] def useStarChart(){}
     class LegOfJourney{
       private[Navigator] val distance = 100
       }
      private[this] var speed = 200
      }
    }
    package launch{
    import navigation._
    object Vehicle{
    private[launch] val guide = new Navigator
    }
  }
}
```



上述例子中，类 Navigator 被标记为 private[bobsrockets] 就是说这个类对包含在 bobsrockets 包里的所有的类和对象可见。

比如说，从 Vehicle 对象里对 Navigator 的访问是被允许的，因为对象 Vehicle 包含在包 launch 中，而 launch 包在 bobsrockets 中，相反，所有在包 bobsrockets 之外的代码都不能访问类 Navigator。

# Scala 方法和函数

Scala 有方法与函数，二者在语义上的区别很小。Scala 方法是类的一部分，而函数是一个对象可以赋值给一个变量。换句话来说在类中定义的函数即是方法。

Scala 中的方法跟 Java 的类似，方法是组成类的一部分。

Scala 中的函数则是一个完整的对象，Scala 中的函数其实就是继承了 Trait 的类的对象。

Scala 中使用 **val** 语句可以定义函数，**def** 语句定义方法。

```scala
class Test{
  def m(x: Int) = x + 3
  val f = (x: Int) => x + 3
}
```

## 方法声明

Scala 方法声明格式如下：

```
def functionName ([参数列表]) : [return type]
```

如果你不写等于号和方法主体，那么方法会被隐式声明为**抽象(abstract)**，包含它的类型于是也是一个抽象类型。

## 方法定义

方法定义由一个 **def** 关键字开始，紧接着是可选的参数列表，一个冒号 **:** 和方法的返回类型，一个等于号 **=** ，最后是方法的主体。

Scala 方法定义格式如下：

```
def functionName ([参数列表]) : [return type] = {
   function body
   return [expr]
}
```

以上代码中 **return type** 可以是任意合法的 Scala 数据类型。参数列表中的参数可以使用逗号分隔。

以下方法的功能是将两个传入的参数相加并求和：

```scala
object add{
  def addInt( a:Int, b:Int ) : Int = {
   var sum:Int = 0
   sum = a + b

   return sum
  }
}
```

如果方法没有返回值，可以返回为 **Unit**，这个类似于 Java 的 **void** 

# Scala 闭包

闭包是一个函数，返回值依赖于声明在函数外部的一个或多个变量。

闭包通常来讲可以简单的认为是可以访问一个函数里面局部变量的另外一个函数

```scala
object Test {  
   def main(args: Array[String]) {  
      println( "muliplier(1) value = " +  multiplier(1) )  
      println( "muliplier(2) value = " +  multiplier(2) )  
   }  
   var factor = 3  
   val multiplier = (i:Int) => i * factor  
}
```

# Scala 字符串

 String 对象是不可变的，如果你需要创建一个可以修改的字符串，可以使用 String Builder 类，如下实例: 

```scala
object Test {
   def main(args: Array[String]) {
      val buf = new StringBuilder;
      buf += 'a'
      buf ++= "bcdef"
      println( "buf is : " + buf.toString );
   }
}
```

注：字符用+=，字符串用++=

# Scala 数组

## 声明数组

以下是 Scala 数组声明的语法格式：

```
var z:Array[String] = new Array[String](3)

或

var z = new Array[String](3)
```

以上语法中，z 声明一个字符串类型的数组，数组长度为 3 ，可存储 3 个元素。我们可以为每个元素设置值，并通过索引来访问每个元素，如下所示：

```
z(0) = "Runoob"; z(1) = "Baidu"; z(4/2) = "Google"
```

最后一个元素的索引使用了表达式 **4/2** 作为索引，类似于 **z(2) = "Google"**。

我们也可以使用以下方式来定义一个数组：

```
var z = Array("Runoob", "Baidu", "Google")
```

## 处理数组

数组的元素类型和数组的大小都是确定的，所以当处理数组元素时候，我们通常使用基本的 for 循环。

## 多维数组

注意： 使用数组方法前要用**import Array._** 引入包。 

多维数组一个数组中的值可以是另一个数组，另一个数组的值也可以是一个数组。矩阵与表格是我们常见的二维数组。

以上是一个定义了二维数组的实例：

```
val myMatrix = Array.ofDim[Int](3, 3)
```

实例中数组中包含三个数组元素，每个数组元素又含有三个值。

接下来我们来看一个二维数组处理的完整实例：

```scala
import Array._

object Test {
   def main(args: Array[String]) {
      val myMatrix = Array.ofDim[Int](3, 3)
     
      // 创建矩阵
      for (i <- 0 to 2) {
         for ( j <- 0 to 2) {
            myMatrix(i)(j) = j;
         }
      }
     
      // 打印二维阵列
      for (i <- 0 to 2) {
         for ( j <- 0 to 2) {
            print(" " + myMatrix(i)(j));
         }
         println();
      }
   
   }
}
```

## 合并数组

我们使用 concat() 方法来合并两个数组，concat() 方法中接受多个数组参数

## 创建区间数组

我们使用了 range() 方法来生成一个区间范围内的数组。range() 方法最后一个参数为步长，默认为 1

```SCALA
import Array._

object Test {
   def main(args: Array[String]) {
      var myList1 = range(10, 20, 2)
      var myList2 = range(10,20)

      // 输出所有数组元素
      for ( x <- myList1 ) {
         print( " " + x )
      }
      println()
      for ( x <- myList2 ) {
         print( " " + x )
      }
   }
}
```

# Scala 集合（Collection）

Scala提供了一套很好的集合实现，提供了一些集合类型的抽象。

Scala 集合分为可变的和不可变的集合。

可变集合可以在适当的地方被更新或扩展。这意味着你可以修改，添加，移除一个集合的元素。

而不可变集合类，相比之下，永远不会改变。不过，你仍然可以模拟添加，移除或更新操作。但是这些操作将在每一种情况下都返回一个新的集合，同时使原来的集合不发生改变。	

| 序号 | 集合及描述                                                   |
| :--- | :----------------------------------------------------------- |
| 1    | Scala List(列表)List的特征是其元素以线性方式存储，集合中可以存放重复对象。参考 [API文档](http://www.scala-lang.org/api/current/scala/collection/immutable/List.html) |
| 2    | Scala Set(集合)Set是最简单的一种集合。集合中的对象不按特定的方式排序，并且没有重复对象。参考 [API文档](http://www.scala-lang.org/api/current/scala/collection/immutable/Set.html) |
| 3    | Scala Map(映射)Map 是一种把键对象和值对象映射的集合，它的每一个元素都包含一对键对象和值对象。参考 [API文档](http://www.scala-lang.org/api/current/scala/collection/immutable/Map.html) |
| 4    | Scala 元组 **元组是不同类型的值的集合**                      |
| 5    | Scala Option Option[T] 表示有可能包含值的容器，也可能不包含值。 |
| 6    | Scala Iterator（迭代器）迭代器不是一个容器，更确切的说是逐一访问容器内元素的方法。 |