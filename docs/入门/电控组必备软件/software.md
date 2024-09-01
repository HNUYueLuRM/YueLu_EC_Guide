# 电控组必备软件

## 控制软件开发

### Keil
以STM32为例，网上很多教程都是基于Keil进行开发，且Keil上手难度低，适合新人使用。但是Keil鸡肋的高亮显示、代码提示和静态检查，且不支持多线程编译，遭到很多人的诟病。基于Keil进行开发几乎成了一种折磨，因此越来越多的人转向其他IDE进行开发，笔者也不再提倡使用Keil进行开发。

![](assets\Keil5.png)

### [VScode](https://code.visualstudio.com/Download)
微软的亲儿子，也是笔者最喜欢的开发工具，没有之一！其中丰富的插件生态，使其几乎可以在任何系统上实现任意语言的编写，毕竟谁不想 All in One 呢！虽然不像Keil那样开箱即用，但经过一些基本配置，便可实现高度的定制化，使用起来非常方便。

![](assets\vscode.png)

### [CubeMX](https://www.st.com/content/st_com/en/stm32cubemx.html)
STM32CubeMX 是由 STMicroelectronics 开发的图形化工具，用于简化和加速 STM32 微控制器的配置和初始化过程。它提供引脚配置、时钟配置、外设配置等功能，并生成初始化代码，支持中间件集成和实时数据分析，显著提高开发效率，减少错误和开发时间。

![](assets\cubemx.png)

### [Ozone](https://www.segger.com/products/development-tools/ozone-j-link-debugger/)
SEGGER家的调试器（也就是做Jlink的公司），可视化调试是它的大杀器。和大家习惯的串口调试不同，他的调试信息是通过DBG发送的，也就是调试器连接的那几条线，通过这个方式调试不会占用系统的资源，能够以非阻塞的方式全速运行。

![](assets\ozone.png)

### 串口调试助手
推荐串口调试助手（就叫这个名字，Microsoft商店可以直接安装，图标就是一个9线的485串口）和[VOFA+](https://www.vofa.plus/)，后者的图形化做的很好可以支持数据可视化。

![](assets\vofa.png) 

### [ROS](https://www.ros.org/)
ROS全称为Robot Operating System，但其并非真正意义上的操作系统，而是开发机器人所用的一套丰富完整的中间件，可以看作是完整的机器人框架和开发抽象层。ROS封装了各模块之间的消息通信、可视化和仿真等各种功能，使开发者无需关心底层实现，仅专注于上层应用的开发即可。笔者推荐直接学习ROS2，且在Linux系统下使用VScode进行开发。

![](assets\ros.png)

## 硬件PCB绘制

### Altium Designer/立创EDA
对于技术栈偏硬件的同学建议选用Altium Designer，功能完整自定义程度高，支持很多插件，不过上手难度稍大一些。而不常画板子的同学用立创EDA即可，还集成了器件库，方便在制作的同时找到可以购买的器件，不用自己去淘宝或者立创商城搜索。

![](assets\ad.png)

## 仿真测试

### Matlab
说到仿真，就不得不提及Matlab中的神器Simulink，通过它你几乎可以仿真一切的物理系统和控制系统，包括电磁、流体、机械以及刚体运动学仿真等。同时官方也提供了非常丰富详细的教程供你学习，笔者同样推荐使用VScode进行Matlab开发。

![](assets\matlab.png)

### [Webots](https://cyberbotics.com/)
Webots也是一款优秀的机器人仿真软件。官方提供了丰富的机器人模型库、传感器模拟以及多种编程接口，同时Webots具有更加真实的物理仿真，可以在多种环境下进行模拟。官方提供的教程也非常适合新人学习。

![](assets\webots.png)

## 其他

### [Git](https://git-scm.com/)
这是一款开源的版本管理工具，也是每个工程师必须掌握的技能。掌握这项技能后，你将无需在每个文件夹命名时标注日期和版本，git会帮你做好这一切，同时你也能非常方便地进行版本之间的合并，极大地提高了工作开发效率。学习git，笔者推荐[廖雪峰的git教程](https://www.liaoxuefeng.com/wiki/896043488029600)。

![](assets\git.png)

### Markdown
Markdown是一种轻量级标记语言，设计初衷是简化HTML的书写。它使用易读易写的纯文本格式，通过简单的符号和约定来标记文本的结构和格式。本文章就是用Markdown语法进行编写，笔者推荐使用Typora或VScode作为你的Markdown文本编辑器。

![](assets\typora.png)

### [Everything](https://www.voidtools.com/zh-cn/downloads/)
高效搜索文件，你会喜欢的。

![](assets\everything.png)

### 浏览器
推荐默认浏览器为[edge](https://www.microsoft.com/zh-cn/edge/download?form=MA13FJ)，默认搜索引擎为bing，同时养成在官网下载安装软件的好习惯。

![](assets\edge.png)