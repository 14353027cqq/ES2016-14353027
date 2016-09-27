## 嵌入式系统实验文档  

> 陈绮晴14353027

1. #### DOL框架描述  

   DOL(distributed operation layer) 是是一种支持平行应用编程的软件开发框架，它支持(半)自动地将应用部署到多处理器SHAPES架构平台中。

   ![DOL框架](http://i1.piimg.com/567571/fb21ac8294e74535.png)

   DOL分成三个部分：

   * **DOL应用程序编程接口** 

     DOL定义了一组计算和通信例程分层式编程，可以让SHAPES平台上分布式的并行应用的编程得以进行。有了这个例程，应用层的程序员可以不用十分了解底层架构具体的内容就可以编写程序。事实上，这些例程在硬件相关的软件层面还有待进一步的细化。

   * **DOL功能仿真** 

      为了给程序员测试他们的应用程序，DOL开发了一个功能仿真框架。这个功能仿真框架不仅可以用来测试验证应用程序的功能，还可以获得在应用层的性能参数。

   * **DOL映射优化** 

     DOL映射优化的目的是计算一个应用程序映射到SHAPES架构平台的一组最优映射。DOL能够借助XML完成将应用映射到底层硬件的功能。通过XML,DOL使得应用和架构的抽象化成为可能，还能提供准确的性能测评参数。

2. #### **DOL安装笔记** 

   * **VMWARE安装**

     上学期学习操作系统曾经安装过VMWARE，但是由于电脑重装了，打开VMWARE之后出现了如下图的提示，尝试过很多的祖册码都不能解决这个办法。

     ![](http://p1.bqimg.com/567571/3ccafb73218207cf.png)

     ![](http://p1.bqimg.com/567571/aa17d2ad979afda0.png)

     所以重装了一下，使用*VY1DU-2VXDH-08DVQ-PXZQZ-P2KV8VF58R-28D9P-0882Z-5GX7G-NPUTFYG7XR-4GYEJ-4894Y-VFMNZ-YA296*这个注册码，成功。

   * **Ubuntu虚拟机安装**

     本以为要重装Ubuntu，发现可以直接在VMWARE上面打开之前安装的ubuntu，暂时还没有遇到问题，所以没有重装。

   * **在ubuntu安装必要的环境**

     ​         在windows下安装软件，我们只需要有exe文件，然后双击，下一步直接OK就可以了。但是在Linux下是不一样的。流入ubuntu，会维护一个自己的软件仓库，我们常用的几乎所有软件都在这里面，这里面的软件绝对安全，而且绝对的能正常安装。在ubuntu下，我们维护一个源列表，源列表里面都是一些网站信息，每一条网站就是一个源，这个地址指向的数据标识着这台源服务器上有哪些软件可以使用。

     **sudo apt-get update** 

      更新软件列表：这个命令会访问源列表里面的每个网址，并读取软件列表，然后保存在本地电脑。我们在新立得软件包管理器里看到的软件列表都是通过update命令来更新的；

     **sudo apt-get upgrade** 

     更新软件：这个命令会把本地已经安装的软件和刚现在的软件列表里对应软件进行对比，如果发现已安装的软件版本太低，就会提示我们去更新；

     **sudo apt-get install ant**   安装ant工具

     > ​        ant是一种基于java的build工具，用java的类来扩展，它本身就是一个流程脚本引擎，用于自动化调用程序完成项目的编译，打包，测试等。
     >
     >  ant优点：
     >
     > 1. 跨平台性：ant是纯java语言编写的，所示具有很好的跨平台性
     > 2. 操作简单：ant是由一个内置任务和可选任务组成的。ant运行时需要一个xml文件(构建文件)
     > 3. 容易维护和书写，结构清晰
     > 4. ant可以集成到开发环境中

     **sudo apt-get install openjdk-7-jdk**  安装开源java开发包

     **sudo apt-get install unzip**  安装解压软件

   * **解压文件**

     **mkdir dol**   新建dol的文件夹

     **unzip dol_ethz.zip -d dol**  将dolethz.zip解压到dol文件夹中

     **tar -zxvf systemc-2.3.1.tgz**  解压systemc

   * **编译systmec**

     **cd systemc-2.3.1** 进入systemc-2.3.1 目录

     **mkdir objdir** 新建临时文件夹objdir

     **cd objdir** 进入该文件夹

     **../configure CXX=g++ --disable-async-updates**

      运行configure(能根据系统的环境设置一下参数，用于编译)，得到以下结果

     ![](http://p1.bqimg.com/567571/dc352fa96f01c2a1.png)

     **sudo make install** 编译

     **cd ..** 返回上衣目录(注意空格)

     **ls** 查看编译后的文件目录，结果如下图

     ![](http://i1.piimg.com/567571/714721ff39b5d119.png)

     **pwd** 查看当前工作路径并记录

     ![](http://i1.piimg.com/567571/19db5bd3bb4da9db.png)

   * **编译dol**

     **cd ../dol**  进入刚刚dol的文件夹

     **sudo gedit build_zip.xml**  打开build_zip.xml文件

     找到下面代码，修改build_zip.xml文件，将YYY改成前面pwd的结果

     >  <property name="systemc.inc"value="YYY/include"/>
     >
     > <property name="systemc.lib"value="YYY/lib-linux/libsystemc.a"/>

     注意64位系统的机器，lin-linux要改成lin-linux64

     **and -f build_zip.xml all** 编译，若成功会显示Build successful

     **cd build/bin/main **

     **ant -f runexample.xml -Dnumber=1** 运行第一个例子

     ![](http://i1.piimg.com/567571/f1d49ec0adffc763.png)

     出现错误，然后跟着Q&A文档将runexample.xml文件注释了一部分

     ![](http://i1.piimg.com/567571/4a84098710ab3ead.png)

     再运行一次得出的结果依然是fail

     ![](http://i1.piimg.com/567571/b54be259e8ea5997.png)

     后来发现并不用修改，因为错误不在这里，不是因为中文系统的原因。而是因为在前面修改build_zip.xml文件的时候，粘贴目录的时候将空格和换行符都放进去了，所以出现了错误。修改之后就成功了得到以下结果：

     ![](http://i1.piimg.com/567571/274b7ae12bafcca7.png)

     完毕。

3. #### **实验感想** 

   * 命令行的空格不能多也不能少，错了一点都运行不了了
   * 复制粘贴的时候别将多的换行符放进文档里