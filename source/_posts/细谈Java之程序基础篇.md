---
title: 细谈Java之程序基础篇
date: 2020-05-27 10:18:34
categories: Java
tags: [Java,编程]
---



今天，我们来讲一下Java程序的基础结构，数据类型以及运算符的相关知识。

### Java的基础结构

> 以 HelloWorld 为例

<!-- more -->

```java
/*
这是多行注释。
Java真的很有趣，希望你可以享受在其中。
*/
public class HelloWorld {
    // 这是单行注释
    public static void main(String[] args) {
        // System.out.println("这行代码被注释了，将不会被编译、执行");
        System.out.println("Hello World!");
    }
}
```

3. #### 注释

   1. 单行注释，以 `//` 开头 ，作用范围是当前行

      ```java
      //	单行注释
      ```

   2. 多行注释，以`/*` 开头，`*/` 结尾，作用范围是包含在块内的

      ```java
      /*
      多行注释
      Java真的很有趣！
      */
      ```

   3. 多行注释，以`/**` 开头，`*/`结尾，例：

      ```java
      /**
       * 多行注释的另一种方式
       */
      ```

4. #### 类名命名规范

   1. 必须以英文字母开头，后可跟数字，字母及下划线的组合
   2. 习惯上以大写字母开头
   3. 习惯上多个单词组成的新的单词，多以每个单h词的首字母大写，如 HelloWorld。

5. #### 方法命名规范

   1. 以英文字母开头，后可跟数字，字母及下划线的组合
   2. 习惯上首字母小写

4. #### `static` 静态方法修饰符，具体使用方法后续在介绍

7. #### 标识符和关键字

   1. ##### 分隔符<font color=red>(英文输入状态下)</font>

      1. 分号<font color=red>`;`</font>

         在Java中，语句之间的分割使用<font color=red>`;`</font>来表示的，多个语句可以写在同一行，但是之间必须以分号间隔开，也可以一条语句跨行写，只要最后以分号结尾即可。如：

         ```java
         int age = 25;String name = "李楠";
         String hello = "Java" +
                 "你好！";
         ```

      2. 花括号<font color=red>`{}`</font>

         作用是定义一个代码块，其实成对出现的，有一个“`{`”，必然会有一个“`}`”，反之亦然

      3. 方括号<font color=red>`[]`</font>

         其主要作用是用于访问数组元素

      4. 圆括号<font color=red>`()`</font>

         1. 定义方法时用圆括号来包含所有的形参声明
         2. 调用方法时使用圆括号来输入参数值
         3. 运算中的优先运算
         4. 强类型转换的运算符

      5. 空格

      6. 圆点<font color=red>`.`</font>

         类/对象和它成员之间的分隔符

   2. ##### 标识符

      规则：

      - 可以由字母、数字、下划线<font color=red>`_`</font>和美元符号<font color=red>`$`</font>组成，且数字不能打头
      - 不能是关键字和保留字，但可以包含关键字和保留字
      - 不能包含空格
      - 符号只能包含美元符<font color=red>`$`</font>

   3. ##### 关键字

      如实例程序中的 <font color=red>`class`</font> ， <font color=red>`public`</font>都是关键字，像这样的关键字Java一共有50个，如下表所示

      |   Java   |    的    |     关     |    键     |      字      |
      | :------: | :------: | :--------: | :-------: | :----------: |
      | abstract | continue |    for     |    new    |    switch    |
      |  assert  | default  |     if     |  package  | synchronized |
      | boolean  |    do    |    goto    |  private  |     this     |
      |  break   |  double  | implements | protected |    throw     |
      |   byte   |   else   |   import   |  public   |    throws    |
      |   case   |   enum   | instanceof |  return   |  transient   |
      |  catch   | extends  |    int     |   short   |     try      |
      |   char   |  final   | interface  |  static   |     void     |
      |  class   | finally  |    long    | strictfp  |   volatile   |
      |  const   |  float   |   native   |   super   |    while     |

   4. ##### 数据类型

      1. 基本类型

         1. boolean类型

            1. 只有 true 和 false 两种数值，用来表示 逻辑上的 "真" 或 "假"
            2. 其类型的值或者变量一般用来进行流程控制，主要有如下几种：
               1. `if` 条件控制语句
               2. `while `循环控制语句
               3. `do while` 循环控制语句
               4. `for` 循环控制语句
               5. 在 三目运算符 `?:` 中使用

         2. 数值类型

            1. 整数类型

               - byte （1个字节） 
               - short （2个字节）
               - int （4个字节）
               - long （8个字节）
                 - 在使用时，通常在这个整数值后增加一个<font color=red>`L`</font>

            2. 字符类型

               - char （2个字节）

                 用于表示单个的字符，字符型的数值必须使用单引号<font color=red>`''`</font>括起来

                 使用 String 类来表示字符串，字符串要用<font color=red>`""`</font>括起来

            3. 浮点类型

               > 浮点数有两种表达方式：
               >
               > ​	1. 十进制数形式
               >
               > ​		如`5.12`，`512.0`，必须包含一个小数点，否则会被当成 `int` 类型处理
               >
               > ​	2. 科学计数法形式
               >
               > ​		如 5.12e2（即5.12 * 10^2)
               >
               > 三个特殊浮点值，用于表示溢出和出错
               >
               > 1. 正无穷大 （POSITIVE_INFINITY）
               >
               > 	2. 负无穷大 （NEGATIVE_INFINITY）
               >  	3. 非数 （NaN）

               - float （单精度浮点数，4个字节）

                 > 如要使用，则须在该类型浮点数后跟一个 <font color=red>`f`</font> 或者 <font color=red>`F`</font>

               - double （双精度浮点数，8个字节）

                 > 默认类型

            4. 数值中的下画线分割

               Java7及之后的版本中，可以在数值中使用下画线，无论是整型，还是浮点型数值，都可以使用，通过使用下画线，可以直观的看到数值中到底包含多少位。

            5. 类型转换

               1. 自动类型转换
               2. 强制类型转换
               
            6. 直接量

               > 直接在程序中通过源码给出的值

               1. 类型
                  1. `int`类型：在程序中直接给出整数数值
                  2. `long`类型：在整型数值后添加 `l` 或 `L`
                  3. `float`类型：在一个浮点数后添加 `f` 或 `F`
                  4. `double`类型：直接给出一个标准小数形式或者科学计数法形式的浮点数
                  5. `boolean`类型：其直接量只有 `true` 和 `false`
                  6. `char`类型：有三种形式，分别是 `单引号括起来的字符`，`转义字符` 和 `Unicode值表示的字符`
                  7. `String`类型：双引号括起来的字符序列
                  8. `null`类型：只有一个值： `null`，可以赋给任何引用类型的变量
               2. 赋值

      2. 引用类型

         1. 类
         2. 接口
         3. 数组
         4. null

   5. ##### 运算符

      1. 算数运算符

         1. `+`：加法运算符
         2. `-`：减法运算符
         3. `*`：乘法运算符
         4. `/`：除法运算符
            1. 两个整数类型之间的除法操作计算结果是整数，且除数不可以是0
            2. 如果有一个是浮点数或者两个都是浮点数，计算结果是浮点数，除数可以是0或者0.0，其结果是正无穷大或负无穷大
         5. `%`：求余运算符
         6. `++`：自加
            1. 单目运算符，只能操作一个操作数
            2. 只能操作单个数值型的变量，不能操作常量或者表达式
            3. 出现在操作数两边有不同的操作，分别是：
               1. 操作数左边：先加 1 后用
               2. 操作数右边：先用再加 1 
         7. `--`：自减

      2. 赋值运算位符

      3. 比较运算符

         > 比较运算结果是一个布尔值

         1. `>`：大于

            ```java
            System.out.println("5 是否大于 4.0：" + (5 > 4.0)); // 将输出 ：5 是否大于 4.0：true
            ```

         2. `>=`：大于等于

         3. `<`：小于

         4. `<=`：小于等于

         5. `==`：等于

            > 基本类型变量、值不能和引用类型变量、值使用 `==`进行比较；
            >
            > boolean类型的变量、值不能和其他任意类型的变量、值使用 `==`进行比较；
            >
            > 若两个引用变量之间没有父子继承关系，其变量也不能使用 `==`进行比较。

            ```java
            System.out.println("5 和 5.0 是否相等：" + (5 == 5.0)); // 将输出 ：5 和 5.0 是否相等：true
            
            System.out.println("97 和 'a' 是否相等：" + (97 == 'a')); // 将输出 ：97 和 'a' 是否相等：true
            
            System.out.println("true 和 false 是否相等：" + (true == false)); // 将输出：true 和 false 是否相等：false
            
            H h1 = new H();
            H h2 = new H();
            
            System.out.println("h1 是否等于 h2：" + (h1 ==h2)); // 将输出：h1 是否等于 h2：false
            
            H h3 =h1;
            
            System.out.println("h3 是否等于 h1：" + (h3 == h1)); // 将输出： h3 是否等于 h1：true
            ```

         6. `!=`：不等于

      4. 逻辑运算符

         1. `&&`：与，同 true 为 true，否则为 false
         2. `&`：不短路或，作用与 `&&`相同，但不会短路
         3. `||`：或，任一为 true 则 结果为 true ，否则为 false
         4. `|`：不短路或
         5. `!`：非，只需一个操作数，操作数为 true(false) 结果为 false(true)
         6. `^`：异或，相同为 false，不同为true

      5. 位运算符

         1. `&`：按位与。同 1 为 1

            ```java
            System.out.println(5 & 9); // 输出1
            ```

         2. `|`：按位或：有一位为 1 则为 1

            ```java
            System.out.println(5 | 9); // 将输出 13
            ```

         3. `~`：按位非。单目运算符，将操作数每个位（包括符号位）全部取反

            ```java
            System.out.println((~-5)); // 将输出 4
            ```

         4. `^`：按位异或。两位相同返回0，不同返回1

            ```java
            System.out.println(5 ^ 9); // 将输出 12
            ```

         5. `<<`：左移运算符

            > 将操作数的二进制码整体向左移动指定位数，左移后右边空出来的位用 `0` 填充，如：

            ```java
            System.out.println(5 << 2); // 将输出 20
            
            System.out.println(-5 << 2); // 将输出 -20
            ```

         6. `>>`：右移运算符

            > 将操作数的二进制码整体向右移动指定位数，左边空出来的用 符号位填充，即正数补 `0`，负数补 `1`,如：

            ```java
            System.out.println(-5 >> 2); // 将输出 -2
            
            System.out.println(5 >> 2); // 将输出 1
            ```

         7. `>>>`无符号右移运算符

            > 将操作数的二进制码右移指定位数，左边空出来的位用 `0`填充

            ```java
            System.out.println(-5 >>> 2); // 将输出 1073741822
            ```

      6. 类型相关运算符

      7. 三目运算符 `?:`

         1. 语法格式为

            ```java
            (expression) ? if-true-statement : if-false-statement;
            ```

         2. 运算规则：

            先对逻辑表达式expression求值，如果值为true，则返回 `if-true-statement`的值，若为false，则返回 `if-false-statement`的值

