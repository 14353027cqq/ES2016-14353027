##Lab5-安装ROS

>陈绮晴14353027

####1.配置Ubuntu存储库，使其允许 "restricted" "universe" 和 "multiverse."
![](http://7xrn7f.com1.z0.glb.clouddn.com/16-11-2/46406409.jpg)
####2. 设置source.list
设置虚拟机使其允许从packages.ros.org. ROS Jade来的软件
 ` sudo sh -c 'echo "deb http://packages.ros.org/ros/ubuntu $(lsb_release -sc) main" > /etc/apt/sources.list.d/ros-latest.list' `

![](http://p1.bpimg.com/567571/f462a3844ba5ffdb.png)

####3.设置密钥
 ` sudo apt-key adv --keyserver hkp://ha.pool.sks-keyservers.net:80 --recv-key 0xB01FA116 `

![](http://p1.bpimg.com/567571/9e18324ef06d6e12.png)

####4.安装
* 首先确保我的Debian包索引是最新的：
 	
	` sudo apt-get update `

* 安装所有内容：ROS, rqt, rviz, robot-generic libraries, 2D/3D simulators, navigation and 2D/3D perception


	`sudo apt-get install ros-jade-desktop-full`

	![](http://p1.bpimg.com/567571/3bf5fce761c08242.png)

* 寻找可用的包

	`apt-cache search ros-jade`
####5.初始化rosdep
在使用ROS之前，需要初始化rosdep, rosdep使我们能够轻松地为需要编译的源安装系统依赖项，而且在运行一些核心组件时我们需要rosdep。

`sudo rosdep init`

`rosdep update`

![](http://p1.bpimg.com/567571/db12ad40de5fb4d2.png)


####6.设置环境
为了方便使用，每次启动一个新的shell的时候ROS环境变量会自动地添加到bash session。

`echo "source /opt/ros/jade/setup.bash" >> ~/.bashrc`

`source ~/.bashrc`

![](http://p1.bqimg.com/567571/0dbcafe14e09c3de.png)

改变当前shell的环境：
`source /opt/ros/jade/setup.bash`

![](http://p1.bpimg.com/567571/345f573017b03cb8.png)

####7.获取rosinstall
rosinstall是ROS中经常使用的命令工具，它是单独分发的。它可以让我们使用一个命令就可以下载很多ROS软件包的源代码树。

安装rosinstall: `sudo apt-get install python-rosinstall`

![](http://p1.bqimg.com/567571/65070750309374f1.png)