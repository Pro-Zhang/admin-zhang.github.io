---
title: 细谈Java之环境篇
date: 2020-05-20 19:20:10
Categories: Java
tags: [Java,编程]
---

### 本文涉及到的内容主要有：

- JDK的安装及环境变量的配置
- IDE的选择

<!-- more -->

因为**Java**是运行在**JVM**上的，所以无论你是在用**Windows**，还是**MacOS**，亦或者是**Linux**，第一件要做的事情就是安装**JDK**，并为其配置相应的环境变量，两者缺一不可。所以下面我们来完成这两件事。

1. #### JDK的安装

   1. ##### 下载JDK

      目前JDK的最新版本是14，不过我们在这里以**JDK 8** 为例。

      进入[JDK 8下载](https://www.oracle.com/java/technologies/javase/javase-jdk8-downloads.html),下载对应的版本

      ![](https://tva1.sinaimg.cn/large/007S8ZIlly1gez5vmgvj3j30pi0mon2r.jpg)

      待下载完成后，傻瓜式安装即可。

   2. ##### 配置环境变量

      1. ###### Windows系统环境变量配置

         1. **右击计算机 --> 高级系统设置 --> 环境变量 ，即可在此处配置所需的环境变量**

         2. 设置一个名为<font color=red>`JAVA_HOME`</font>的环境变量,其变量值为<font color=red>JDK</font>在本机的安装目录,如：

            ```
            C:\Program Files\Java\jdk1.8.0_241
            ```

         3. 创建名为 <font color=red>CLASSPATH</font>的环境变量，其变量值为：`

            ```
            .;%JAVA_HOME%\lib;%JAVA_HOME%\lib\tools.jar`
            ```

         4. 在名为<font color=red>Path</font>的环境变量中，添加

            ```
            `%JAVA_HOME%\bin; %JAVA_HOME%\jre\bin;`
            ```

            注意：若在原有变量后边添加注意是否 有<font color=red>`;`</font>托没有则添加，若有，则直接添加上述变量值。

         5. 测试JDK是否安装成功

            运行 cmd，在其中分别输入<font color=red> `java -version` </font>和<font color=red> `javac`</font> ，若出现如下结果则证明安装成功，若没有，则检查环境变量的配置是否有错误！

            ![java -version 结果](https://tva1.sinaimg.cn/large/007S8ZIlly1gez6eimxozj30el03ot8r.jpg)

            ![javac结果](https://tva1.sinaimg.cn/large/007S8ZIlly1gez6eijfr0j30hu0gkgo4.jpg)

      2. ###### macOS配置环境

         1. 在 <font color=red>`~/.profile`</font> 或<font color=red> `~/.bash_profile` </font>中添加如下内容

         ```
         #添加Java环境变量
         export JAVA_HOME=/Library/Java/JavaVirtualMachines/jdk1.8.0_251.jdk/Contents/Home
         export PATH=$JAVA_HOME/bin:$PATH
         export CLASSPATH=.:$JAVA_HOME/lib/dt.jar:$JAVA_HOME/lib/tools.jar
         ```

         2. 使用<font color=red> source ~/.profile  </font>或者 <font color=red> `source ~/.bash_profile` </font>来使配置文件生效。
         3. 在终端中分别输入<font color=red> `java -version` </font>和<font color=red> `javac`</font>来进行测试

      <font size=4>**到此，Windows端和macOS端的JDK及环境已完全配置好了。**</font>

2. #### IDE的选择

   工欲善其事，必先利其器，因此如果想提供自己的编码效率，一款优秀IDE是必不可少的，然而市场上可供选择的IDE有很多，笔者在这里列举几个常用的。

   - [NotePad ++](https://notepad-plus-plus.org/downloads/)（免费）
   - [Eclipse](https://www.eclipse.org/downloads/) （免费）
   - [MyEclipse](https://www.myeclipsecn.com/download/) （收费）
   - https://www.jetbrains.com/idea/download/#section=mac（推荐，收费）**

   

   <! -- 添加捐赠图标 -->

   <div class ="post-donate">
     <div id="donate_board" class="donate_bar center">
       <a id="btn_donate" class="btn_donate" href="javascript:;" title="Donate 打赏"></a>
       <span class="donate_txt">
          &uarr;<br>
          读后有收获可以支付宝请作者喝咖啡，
         </span>
   			<br>
     </div>  

   ​    <!-- 支付宝打赏图案 -->

   ![支付宝打赏](https://tva1.sinaimg.cn/large/007S8ZIlly1gez7g14q3sj308n08i40j.jpg)                             ![微信打赏](https://tva1.sinaimg.cn/large/007S8ZIlly1gez8ac8iv3j308o08jmzl.jpg)

   

   

   

   

   

   

   

   

