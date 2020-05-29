---
title: 细谈Java之流程控制篇
date: 2020-05-28 09:19:29
categories: Java
tags: [Java,编程]
---

任何一门编程语言都离不开流程控制，Java也不例外，在Java中提供了以下几种流程结构：

1. 顺序结构

   > 程序从上到下逐行执行，中间没有任何的跳转和判断。

2. 分支结构

   > 根据条件来选择性地执行某段代码。

   1. `if`条件语句

      > `if`、`else`、`else if` 后的条件执行体，建议用一个花括号括起来，以防因为执行体语句过多而造成编译错误。
      >
      > 使用 `if...else` 语句是一定要先处理包含范围更小的情况

      1. 形式一

         ```java
         if(login expression){
         	statement...
         }
         ```

         

      2. 形式二

         ```java
         if (logic expression) {
             statement...
         } else {
             statement...
         } 
         ```

      3. 形式三

         ```java
         if (logic expression) {
             statement...
         }else if (login statement) {
             statement...
         } else {
             statement...
         }
         ```

   2. `switch`条件语句

      > 由一个控制表达式和多个case标签组成，其语句后面的控制表达式的数据类型只能是byte、short、char、int四种整数类型，枚举类型和`java.lang.String`类型（从Java7才允许），**不能**是 **boolean**类型

      1. 语法格式：

         ```java
         switch (expression){
         	case condition1:
         	{
                 statement(s);
                 break;
         	}
         	case condition2:
         	{
                 statement(s);
                 break;
         	}
         	...
         	case conditionN:
         	{
                 statement(s);
                 break;
         	}	
         	default:
         	{
         		statement(s);
         	}
         }
         ```

3. 循环结构

   > 用于实现根据循环条件重复执行某段代码
   >
   > 循环语句包含如下四部分：
   >
   > 	1. 初始化语句（init_statement）
   >  	2. 循环条件（test_expression）：**boolean 表达式**
   >  	3. 循环体（body_statement）
   >  	4. 迭代语句（iteration_statement）

   1. `while`循环语句

      > 先判断循环条件，如果为真则执行循环体，反之则不执行循环体。

      1. 语法格式：

         ```java
         [init_statement]
         while(test_expression){
         	statement;
         	[iteration_statement]
         }
         ```

         

      2. 示例

         ```java
         public class WhileTest {
             public static void main(String[] args) {
                 // 循环的初始化条件
                 int count = 0;
                 // 当 count 小于10时，执行循环体
                 while (count < 10) {
                     System.out.println(count);
                     // 迭代语句
                     count++;
                 }
                 System.out.println("循环结束");
             }
         }
         
         /*
         运行结果是：
             0
             1
             2
             3
             4
             5
             6
             7
             8
             9
             循环结束
         */
         ```

      3. 注意事项

         1. 一般情况下不要省略花括号，这样不仅会降低程序的可读性，还有可能会出现错误；
         2. 保证循环条件有变成false的时候，避免成为死循环；
         3. 避免while循环的循环条件后紧跟一个分号，从而生成死循环。

   2. `do...wihie`循环语句

      > 先执行循环体，再判断循环条件，若循环条件为真，则执行下一次循环，反之则结束循环。

      1. 语法格式

         ```java
         [init_statement]
         do{
         	statement;
         	[iteration_statement]
         }while (test_expression);
         ```

         

      2. 示例

         ```java
         public class DoWhileTest {
             public static void main(String[] args) {
                 // 定义变量count
                 int count = 1;
                 // 执行do while 循环
                 do {
                     System.out.println(count);
                     // 迭代语句
                     count++;
                     // 循环条件紧跟 while 关键字
                 } while (count < 10);
                 System.out.println("循环结束");
             }
         }
         
         /*
         运行结果是：
             1
             2
             3
             4
             5
             6
             7
             8
             9
             循环结束
         */
         ```

   3. `for`循环

      1. 语法格式

         ```java
         for ([init_statement];[test_expression];[iteration_statement]){
         	stetement
         }
         ```

         

      2. 示例

         ```java
         public class ForTest {
             public static void main(String[] args) {
                 // 循环的初始化条件、循环条件、循环迭代语句都在下面一行
                 for (int count = 0; count < 10; count++) {
                     System.out.println(count);
                 }
                 System.out.println("循环结束");
             }
         }
         
         /*
         运行结果是：
             0
             1
             2
             3
             4
             5
             6
             7
             8
             9
             循环结束
         */
         ```

      3. 注意事项

         1. 初始化语句可以同时指定多个初始化语句，循环条件也可以是一个包含逻辑运算符的表达式；
         2. 建议不要在循环体内修改循环变量的值，如有需要，重新定义一个临时变量，将循环变量的值赋给临时变量，再对临时变量进行修改；
         3. 初始化语句、循环跳进以及迭代语句是可以省略的，但切忌省略循环条件，以免造成死循环

   4. 嵌套循环

      > 将一个循环套在另一个循环体内

4. 控制循环结构

   1. `break`

      > 用于：某些时候需要在某种条件出现时强行终止循环，而不是等待循环条件为false时

      1. 直接跳出本次循环

         ```java
         public class BreakTest1 {
             public static void main(String[] args) {
                 for (int i = 0; i < 10; i++) {
                     System.out.println("i 的值是：" + i);
                     if (i == 2) {
                         // 执行该语句时将结束循环
                         break;
                     }
                 }
             }
         }
         
         /*
         运行结果是：
             i 的值是：0
             i 的值是：1
             i 的值是：2
         */
         ```

      2. 结束外层循环

         ```java
         public class BreakTest2 {
             public static void main(String[] args) {
                 // 外层循环，outer作为标识符
                 outer:
                 for (int i = 0; i < 5; i++) {
                     //内层循环
                     for (int j = 0; j < 3; j++) {
                         System.out.println("i = " + i + "，j = " + j);
                         if (j == 1) {
                             // 跳出 outer 标签所标识的循环
                             break outer;
                         }
                     }
                 }
             }
         }
         
         /*
         结果是：
         	i = 0，j = 0
         	i = 0，j = 1
         */
         ```

   2. `continue`

      > 结束本次循环，开始下一次循环，并不会终止循环

      ```java
      public class ContinueTest {
          public static void main(String[] args) {
              for (int i = 0; i < 3; i++) {
                  System.out.println("i 的值是：" + i);
                  if (i == 1) {
                      // 忽略本次循环剩下的语句
                      continue;
                  }
                  System.out.println("continue后的输出语句");
              }
          }
      }
      
      /*
      结果是：
          i 的值是：0
          continue后的输出语句
          i 的值是：1
          i 的值是：2
          continue后的输出语句
      */
      ```

   3. `return`

      > 直接结束该方法，循环也随之结束

      ```java
      public class ReturnTest {
          public static void main(String[] args) {
              for (int i = 0; i < 3; i++) {
                  System.out.println("i = " + i);
                  if (i == 1) {
                      return;
                  }
                  System.out.println("return后的输出语句");
              }
          }
      }
      
      /*
      运行结果是：
          i = 0
          return后的输出语句
          i = 1
       */
      ```

