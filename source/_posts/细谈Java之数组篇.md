---
title: 细谈Java之数组篇
date: 2020-05-29 15:17:53
categories: Java
tags: [Java,编程]
---

1. ## 概述

数组是编程语言中一种常见的数据结构，不同的语言对其的实现和处理也是不同的。下面将介绍Java中的数组。

<!-- more -->

2. ## 数组类型

1. ###  数组是一种类型

   1. 在Java中，要求所有的数组元素有相同的数据类型，因此，在一个数组中，数组元素的类型是唯一的。
   2. 一旦其被初始化完成后，其所占内存空间也被固定下来了，即其长度不可改变。
   3. 数组是引用类型

2. ### 数组的定义

   1. 两种语法格式

      ```java
      type[] arrayName;（推荐）
      type arranName[];
      ```

   2. 定义数组时不能指定数组的长度

3. ### 数组的初始化

   1. #### 静态初始化

      1. ##### 语法格式

         ```java
         // 第一种方式
         arrayName = new type[]{element1,element2,element3.....};
         // 第二种方式
         type[] arrayName = new type[]{element1,element2,element3.....};
         ```

      2. ##### 示例

         ```java
         public class ArrayTest {
             public static void main(String[] args) {
                 // 定义一个 int 数组类型的变量，变量名为 intArr
                 int[] intArr;
                 // 使用静态初始化，初始化数组时只指定数组元素的初始值，不指定数组长度
                 intArr = new int[]{5, 6, 8, 20};
                 // 定义一个 Object 数组类型的变量，变量名为 objArr
                 Object[] objArr;
                 // 使用静态初始化，初始化数组时数组元素的类型是
                 //定义数组时所指定的数组元素类型的子类
                 objArr = new String[]{"西游记", "吴承恩"};
                 Object[] objArr2;
                 //使用静态初始化
                 objArr2 = new Object[]{"斗破苍穹", "天蚕土豆"};
             }
         }
         ```

   2. #### 动态初始化

      1. ##### 语法格式

         ```java
         arrayName = new type[length];
         ```

      2. ##### 初始值规则

         | 数组元素类型                       | 数组元素默认初始值 |
         | ---------------------------------- | ------------------ |
         | 整数类型（byte、short、int、long） | 0                  |
         | 浮点类型（float、double）          | 0.0                |
         | 字符类型（char）                   | \u0000             |
         | 布尔类型（boolean）                | false              |
         | 引用类型（类，接口和数组）         | null               |

6. ### 数组的使用

   1. #### 数组的遍历

      > 由于数组的索引值是从 0 开始的，所以第一个数组元素的索引值为 0，最后一个数组元素的索引值为数组长度减1，因此一个数组的遍历应该如下代码所示：

      1. ##### for循环

         ```java
         public class ArrayTest {
             public static void main(String[] args) {
                 // 定义一个 int 数组类型的变量，变量名为 intArr
                 int[] intArr;
                 // 使用静态初始化，初始化数组时只指定数组元素的初始值，不指定数组长度
                 intArr = new int[]{5, 6, 8, 20};
                 // 数组的遍历
                 for (int i = 0; i < intArr.length; i++) {
                     int i1 = intArr[i];
                     System.out.println("第"+ i + "个数组元素的值是"+"intArr[" + i + "] = " + intArr[i]);
                 }
             }
         }
         /*
         运行结果是：
             第0个数组元素的值是intArr[0] = 5
             第1个数组元素的值是intArr[1] = 6
             第2个数组元素的值是intArr[2] = 8
             第3个数组元素的值是intArr[3] = 20
         */
         ```

      2. ##### foreach循环

         ```java
         public class FroEachTest {
             public static void main(String[] args) {
                 String[] books = {"西游记", "红楼梦", "水浒传", "三国演义"};
                 for (String book : books) {
                     System.out.println("book = " + book);
                 }
             }
         }
         
         /*
         运行结果是
             book = 西游记
             book = 红楼梦
             book = 水浒传
             book = 三国演义
         */
         ```

   2. #### Arrays工具类（Java 8及之后版本）

      > 在Java8及其之后的版本中，提供了一个名为`Arrays`的工具类，在这个工具类中，包含了一些static修饰的方法以此可以直接对数组进行操作。

      1. ##### 包含的方法有：

         1. `int binarySearch(type[] a,type key)`：使用二分法查询key元素只在a数组中出现的索引，如果不包含key数值，则返回false，如使用方法，则数组元素需按照升序排列；
         2. `int binarySearch(type[] a,int fromIndex,int toIndex,type key)`：搜索a数组中fromIndex 到 toIndex 索引的元素，同样要求数组元素按照升序排列；
         3. `type[] copyOf(type[] original,int length)`：将original数组复制组成一个新的数组，length为新数组的长度，`length < original.length ? [取original数组中前length长度的元素] : [original数组所有元素+补充0(数值类型),false(布尔类型),null(引用类型)]；`
         4. `type[] copyOfRange(type[] original,int from,int to)`:只复制 original 数组从 from到to索引的元素；
         5. `boolean equals(type[] a,type[] a2)`：数组a，a2的长度相等及数组元素一一相同的时候，返回true；
         6. `void fill(type[] a,type val):`把a数组的所有元素赋值为val；
         7. `void fill(type[] a,int fromIndex,int toIndex,type val)`：仅仅将a数组的fromIndex到toIndex索引之间的数组元素赋值为val；
         8. `void sort(type[] a)`：对a数组进行排序；
         9. `void sort(type[] a,int fromIndex,int toIndex)`：对a数组从fromIndex到toIndex索引之间的数组元素进行排序；
         10. String toString(type[] a)：将一个数组转换成一个字符串。

      2. ##### 示例

         ```java
         import java.util.Arrays;
         public class ArraysTest {
             public static void main(String[] args) {
                 // 定义一个a数组
                 int[] a = new int[]{3, 4, 5, 6};
                 // 定义一个a2数组
                 int[] a2 = new int[]{3, 4, 5, 6};
                 // a数组和a2数组的长度相等，每个元素依次相等，将输出true
                 System.out.println("a数组和a2数组是否相等：" + Arrays.equals(a,a2));
                 // 通过赋值a数组，生成一个b数组
                 int[] b = Arrays.copyOf(a, 6);
                 System.out.println("a数组和b数组是否相等：" + Arrays.equals(a,b));
                 // 输出b数组的元素
                 System.out.println("b数组的元素为" + Arrays.toString(b));
                 // 将b数组的第3个元素（包括）到底5个元素（不包括）赋值为1
                 Arrays.fill(b,2,4,1);
                 // 输出b数组的元素
                 System.out.println("b数组的元素为" + Arrays.toString(b));
                 // 将b数组进行排序
                 Arrays.sort(b);
                 // 输出b数组的元素
                 System.out.println("b数组的元素为" + Arrays.toString(b));
             }
         }
         /*
         运行结果为：
             a数组和a2数组是否相等：true
             a数组和b数组是否相等：false
             b数组的元素为[3, 4, 5, 6, 0, 0]
             b数组的元素为[3, 4, 1, 1, 0, 0]
             b数组的元素为[0, 0, 1, 1, 3, 4]
         */
         ```

   3. #### 数组的排序

      1. ##### 冒泡排序

         > 冒泡排序的特点是，每一轮循环后，最大的一个数被交换到末尾，因此，下一轮循环就可以“刨除”最后的数，每一轮循环都比上一轮循环的结束位置靠前一位。

         ```java
         import java.util.Arrays;
         public class BubbleSortTest {
             public static void main(String[] args) {
                 int[] ns = { 28, 12, 89, 73, 65, 18, 96, 50, 8, 36 };
                 // 排序前:
                 System.out.println(Arrays.toString(ns));
                 for (int i = 0; i < ns.length - 1; i++) {
                     for (int j = 0; j < ns.length - i - 1; j++) {
                         if (ns[j] > ns[j+1]) {
                             // 交换ns[j]和ns[j+1]:
                             int tmp = ns[j];
                             ns[j] = ns[j+1];
                             ns[j+1] = tmp;
                         }
                     }
                 }
                 // 排序后:
                 System.out.println(Arrays.toString(ns));
             }
         }
         
         /*
         运行结果是：
             [28, 12, 89, 73, 65, 18, 96, 50, 8, 36]
             [8, 12, 18, 28, 36, 50, 65, 73, 89, 96]
         */
         ```

      2. ##### 排序

         > Java 中的Arrays工具类已经提供了sort()这一排序方法

         ```java
         import java.util.Arrays;
         public class Main {
             public static void main(String[] args) {
                 int[] ns = { 28, 12, 89, 73, 65, 18, 96, 50, 8, 36 };
                 Arrays.sort(ns);
                 System.out.println(Arrays.toString(ns));
             }
         }
         
         /*
         运行结果是：
             [8, 12, 18, 28, 36, 50, 65, 73, 89, 96]
         */
         ```

   4. #### 多维数组

      1. ##### 二维数组

         > 本质上来说就是数组的数组

         1. 语法格式

            ```java
            // 定义
            type[][] arrName;
            // 初始化
            arrName = new type[length][];
            ```

         2. 示例

            ```java
            public class TwoDimensionTest {
                public static void main(String[] args) {
                    int[][] a;
                    a = new int[4][];
                    for (int i = 0; i < a.length; i++) {
                        System.out.println(a[i]);
                    }
                    a[0] = new int[2];
                    a[0][1] = 6;
                    for (int i = 0; i < a[0].length; i++) {
                        System.out.println(a[0][i]);
                    }
                }
            }
            ```