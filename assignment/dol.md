## Lab3-DOL实例分析&编程

> 陈绮晴14353027



1. #### 实验要求

   * 修改example2,让3个square模块编程两个
   * 修改example1,使其输出3次方数

   > 提示：修改代码之后要重新编译、运行(sudo ant -f runexample.xml -Dnumber=xxx) xxx是运行example的号码,比如上面是2和1

2. #### 实验步骤

   * **修改example2,让3个square模块变成2个** 

   ​        理解example2的代码内容，打开dol/example2/example2/example2.xml文件

   ​	![](http://p1.bqimg.com/567571/740c0adf7d558065.png)

   ​         这里通过三次迭代，定义了3个square模块

   ​	![](http://p1.bqimg.com/567571/6cf51c48811b283b.png)

   ​	然后通过迭代生成连接connection

   ​	![](http://p1.bqimg.com/567571/3aec08a1947e4d0a.png)

   ​	可以看出example2生成的dot图如上图，generator输出，然后与三个有着输入端和输出端的square连接在一起，最后连接着有着输入端的consumer。

   ​	因此我们知道改变迭代的次数，就可以改变square的数量。

   ​	![](http://p1.bqimg.com/567571/6055a2a67e70021e.png)

   ​	由于不能直接改example2.xml,所以要在命令行中进入到该文件所在位置，然后用gedit +文件名的方式打开example2.xml文件(如上图所示)

   ​	![](http://p1.bqimg.com/567571/c87266331c8767b6.png)

   ​	将迭代次数的变量的值由3改为2

   ​	![](http://p1.bqimg.com/567571/247f9f1f3fe49434.png)

   ​	进入编译运行的目录，输入命令行重新编译、运行，查看结果

   * **修改example1,使其输出3次方数** 

     ![](http://p1.bqimg.com/567571/5dae84e7f64b84d4.png)

     直接将square.c文件里面的i=i * i,改成 i=i * i * i就可以实现

3. #### 实验结果

   * example.2

     ![](http://p1.bpimg.com/567571/21ca9629d0962b90.png)

     看结果可以看到分别是0,1,2,3...数字的四次方的结果，也就是两个二次方，所以可以知道有两个square

     ![](http://p1.bpimg.com/567571/f38a20bdba3d1967.png)

     看example2.dot图可以更加直观地看出example2一共有两个square模块

   * example.1

     ![](http://p1.bpimg.com/567571/b1832bd1f38c0732.png)

     可以看到结果分别是0,1,2,3...数字的三次方的结果

     ![](http://p1.bpimg.com/567571/863a4c49e17bf20d.png)

     example1.dot图如上，由于只是对数据处理改变了一下，没有改变模块和连接，所以dot图没有变化

4. #### 实验感想

   * 打开dot图的办法是在windows下安装graphviz，然后将example2.dot图复制到windows下，然后再用gvedit.exe打开就可以看到

   * 注意example代码文件的目录和运行example的目录不是同一个

     example代码文件目录：dol/examples/

     运行example目录：dol/build/bin/main







​            

