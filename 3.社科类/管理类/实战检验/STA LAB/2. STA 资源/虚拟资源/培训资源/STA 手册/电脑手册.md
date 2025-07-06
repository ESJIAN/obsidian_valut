版权声明：本手册经由 STA 队长 ==谢承旭== 以及成员 ==刘子劢== 编写，是在调研了其他实验室以及自己实验室的一些问题后进行编写的，在此对帮助我编写本手册的人表示感谢。编写本手册，主要是为了减轻各大实验室的一个新人培养负担，同时也是帮助新人快速的突破从小白变成大佬的门槛期。同时如果对于该手册有问题的话可以在我们的[网站](www.stalab.fun)进行反馈。（传播遵循 CN-BY-NC 协议）

**首先恭喜你成为STA的一员**，那么你离成为大佬就差那么一步了，而这一步通过学习本文档可以很好的卖出去。作为一名STAer，需要培养的核心能力主要有：==个人能力（思考能力、AI能力、规划能力、写作能力、问题解决能力）团队能力（沟通能力、协调能力）==，围绕这些能力去学习对应的手册去补充自己缺失的能力。

>**引言**：或许你陷入困境的关键，在于还没找到属于自己的方向。当学习失去目标，上课的困惑会像乱麻般难解，课后盲目补习也只是跟着别人的节奏打转，这种无力感慢慢堆积，才会让你对生活失去信心。其实，每个人的成长节奏不同，与其追赶他人的脚步，不如停下来问问自己：“我真正需要的是什么？” 找到内心的方向，才能让努力有意义 —— 毕竟，人生不是复制别人的路线，而是走出一条让自己坚定的路。 

Q：**为什么要写这份文档呢**？
A：为了给部长减轻新人培训的负担，同时该文档也能够作为新人查阅常见电脑使用问题的方案记录手册。

Q：**怎么使用这份手册呢**？
A：1. 去我们搭建的实体主机上做好每一步的练习操作 2. 去练习主机上手动实践手册不要背手册，得学会查手册（因为记忆的负担会很大） 3. 到自己电脑上去重复的实践

Q：**一般得学多久**？
A：0 基础的话学习个 2~3 天就差不多了，因为这个手册是属于极简版本的了，当然，学的慢的话可以适当放慢脚步。如果你大学以前有计算机基础那再好不过了，直接跳过手册内容或者直接把手册摘录到你的 MD 笔记中吧。

```

```

<center><b>表 ：手册编写时测试验证的计算机环境</b></center>

<center><b>
表：手册修订历史</b></center>

|   |   |   |   |   |   |   |
|---|---|---|---|---|---|---|
|**功能**|**家庭版**|**专业版**|**工作站专业版**|**企业版**|**教育版**|**SE**|
|支持的内存（最大）|4GB (32bit) 128GB (64bit)|4GB (32bit) 2TB (64bit)|4GB (32bit) 6TB(64bit)|4GB (32bit) 6TB (64bit)|4GB (32bit) 2TB(64bit)||
|初始设置需要 Microsoft 帐户|✓||||||
|Windows 11 处于 S 模式选项|✓||||||
|仅限云管理||||||✓|
|只有 IT 管理员可以安装应用程序||||||✓|
|需要 OneDrive 云存储||||||✓|
|预装 Microsoft Office||||||✓|
|仅提供预安装（无可用映像）||||||✓|
|运行所有 Windows 应用程序|✓|✓|✓|✓|✓||
|Microsoft Store|✓|✓|✓|✓|✓||
|针对低内存和小屏幕设备进行了优化||||||✓|
|远程桌面||✓|✓|✓|✓||
|Hyper-V 虚拟化||✓|✓|✓|✓||
|Windows 沙盒||✓|✓|✓|✓||
|弹性文件系统 (ReFS)|||✓|✓|✓||
|Bitlocker 设备加密||✓|✓|✓|✓||
|设备加密|✓|✓|✓|✓|✓||
|查找我的设备|✓|✓|✓|✓|✓||
|防火墙和网络保护|✓|✓|✓|✓|✓||
|互联网保护|✓|✓|✓|✓|✓||
|家长控制和保护|✓|✓|✓|✓|✓||
|安全引导|✓|✓|✓|✓|✓||
|Windows Hello|✓|✓|✓|✓|✓||
|Windows 信息保护 (WIP)||✓|✓|✓|✓||
|Windows 安全|✓|✓|✓|✓|✓||
|分配访问||✓|✓|✓|✓||
|动态配置||✓|✓|✓|✓||
|使用 Azure 进行企业状态漫游||✓|✓|✓|✓||
|组策略||✓|✓|✓|✓||
|自助服务终端模式设置||✓|✓|✓|✓||
|适用于企业的 Microsoft Store||✓|✓|✓|✓||
|移动设备管理||✓|✓|✓|✓||
|支持活动目录||✓|✓|✓|✓||
|支持 Azure Active Directory||✓|✓|✓|✓||
|企业版 Windows 更新||✓|✓|✓|✓||
|AppLocker||✓|✓|✓|✓||
|持久内存|||✓|✓|✓||
|中小型企业直通车|||✓|✓|✓||
|服务时间表|自发布之日起 24 个月|自发布之日起 24 个月|自发布之日起 24 个月|自发布之日起 36 个月|自发布之日起 36 个月||


<center><b>
表：各个版本的 W11 对比
</b></center>


>**警告**：经常有人在问学这个有什么用，那么正式开始前我们看一个视频，自己品一下，如果本手册学不好电脑会变成的样子（Obsidian 需要安装MediaExtend插件）

![很久没见过这么干净的电脑了_哔哩哔哩_bilibili](https://www.bilibili.com/video/BV1X3411674X/?spm_id_from=333.337.search-card.all.click&vd_source=4c095a1bfb5e2a56290ec68b55b5d467)

<center><b>
视频：电脑好久没这么干净过了</b></center>

![《电子文盲与赛博孔子的故事》_哔哩哔哩_bilibili](https://www.bilibili.com/video/BV1FuYCeYEUi?spm_id_from=333.788.recommend_more_video.1&vd_source=4c095a1bfb5e2a56290ec68b55b5d467)

<center><b>
视频：电子文盲与赛博孔子的故事</b></center>

![image.png](https://i0.hdslb.com/bfs/openplatform/b7f7d34089bff59adafe88b5f2182f7b59087877.png)

<center><b>
图：相关评论</b></center>

![image.png](https://i0.hdslb.com/bfs/openplatform/1d672c9d4d598f66893e9e757ddc14c0db7de6ac.png)

<center><b>
图：相关评论</b></center>

>**Ps：** 所以，我们有时也挺无奈计算机教育的缺失和手机的过度傻瓜化智能化的，不过问题不大，只要你能够把手册学完，上述情况就可以完全避免。**负面的两个例子介绍完成了下面我来介绍两个正面的例子**。

---

![image.png](https://i0.hdslb.com/bfs/openplatform/309af41f64b9282bf087ab8cac947e03f169292c.png)

<center><b>
图：Win12 概念版</b></center>

打开这个[Windows 12 网页版 (nikai.ltd)](http://win12.nikai.ltd/)网页，你就可以看到网页渲染出了类似上图一个漂亮的操作系统。这个网站的作者是一位在读的初中生，很厉害，可以看到小小年纪UI/UX设计水平很高，也是向他学习了。

![怎样让你的win11任务栏、开始菜单与众不同！_哔哩哔哩_bilibili](https://www.bilibili.com/video/BV1hsUbYFEQB/?spm_id_from=333.337.search-card.all.click)

<center><b>
视频：怎么让你的 Win11 与众不同（极其社死）？
</b></center>

![image.png](https://i0.hdslb.com/bfs/openplatform/f8413a42a6139aff07355c67cd2c69212f999bc8.png)

<center><b>
图：Win 11 美化视频一栏</b></center>

上面这个视频展示了当你对电脑的使用水平更好了以后你甚至能让他变得更加的漂亮起来ξ( ✿＞◡❛)，所以还在等什么，赶紧跟随来一起学习电脑使用（~~虐待电脑~~） 吧！

# 1. 入门阶段

>注意：在开始之前，请先让队长在 Obsidian 中安装好 Media Extend、Admonition 两个插件

## 1.1.  基本系统使用
### 1.1.1 桌面操作基础

#### （1）在桌面上显示我的电脑图标

有些人的电脑桌面可能和下图一样，没有"此电脑图标"，下面教大家怎么打开这个此电脑图标

![image.png](https://i0.hdslb.com/bfs/openplatform/6906ac7d0b1ceec4ab3e5c521a4a6fc802166d07.png)

<center><b>
图：没有此电脑的桌面</b></center>

- 【步骤】
	1.在桌面空白处，右键单击，从打开的菜单项中选择显示设置；
		![](https://img0.pconline.com.cn/pconline/2112/31/14779689_118-211023144422_thumb.jpg)(https://www.pconline.com.cn/images/html/viewpic_pconline.htm?//img0.pconline.com.cn/pconline/2112/31/14779689_118-211023144422_thumb.jpg&channel=11745)
		
	　2、设置窗口，左侧点击个性化；
		[![](https://img0.pconline.com.cn/pconline/2112/31/14779689_118-211023144422-50_thumb.jpg)](https://www.pconline.com.cn/images/html/viewpic_pconline.htm?//img0.pconline.com.cn/pconline/2112/31/14779689_118-211023144422-50_thumb.jpg&channel=11745)
	　3、右侧点击主题（安装、创建、管理）；
		[![](https://img0.pconline.com.cn/pconline/2112/31/14779689_118-211023144422-51_thumb.jpg)](https://www.pconline.com.cn/images/html/viewpic_pconline.htm?//img0.pconline.com.cn/pconline/2112/31/14779689_118-211023144422-51_thumb.jpg&channel=11745)
	　　4、个性化 - 主题，相关设置下，点击桌面图标设置
		[![](https://img0.pconline.com.cn/pconline/2112/31/14779689_118-211023144423_thumb.jpg)](https://www.pconline.com.cn/images/html/viewpic_pconline.htm?//img0.pconline.com.cn/pconline/2112/31/14779689_118-211023144423_thumb.jpg&channel=11745)
	 5、桌面图标设置窗口，点击勾选计算机，然后点击确定，桌面就可以显示此电脑图标了。
	 [![](https://img0.pconline.com.cn/pconline/2112/31/14779689_118-211023144423-50_thumb.jpg)](https://www.pconline.com.cn/images/html/viewpic_pconline.htm?//img0.pconline.com.cn/pconline/2112/31/14779689_118-211023144423-50_thumb.jpg&channel=11745)

按照上述操作做完后，你的桌面应该会变成下图所示的样子，“此电脑”图标出现在了桌面上。

![image.png](https://i0.hdslb.com/bfs/openplatform/6c83ce87dc00576eaacc6c2aeffef075f5816882.png)

<center><b>
图：打开此电脑后的桌面</b></center>

#### （2）关闭小组件

相信有些人对这个东西感到比较烦，那么有没有关闭它的方法呢？有的，下面就来教导大家如何关闭这个桌面组件。

![image.png](https://i0.hdslb.com/bfs/openplatform/3dd80a0d0fd21723bb98b94c81d91559a4afaed7.png)

- 【步骤】
	1、鼠标右键点击任务栏上的任意空白区域，在弹出菜单中选择“任务栏设置”。
	
	2、在打开的任务栏设置页面中，在“任务栏项”中将“小组件”的开关按钮切换至关闭状态即可。
	
	![](https://i-blog.csdnimg.cn/direct/1445386d007044e4adc21520e59e181d.png)

如果你完成上述步骤，你就能和下图一样观察到组件图标消失了，这样你的底部任务栏就更干净了，系统视觉展现效果更好了。

![image.png](https://i0.hdslb.com/bfs/openplatform/4b41c6f7db7e408b8aba621729909f76fa644dc4.png)

#### （3）调整搜索框

有人可能会觉得下图搜索这个框框过大，现在我们来调整一下这个框框的大小

![image.png](https://i0.hdslb.com/bfs/openplatform/93c0d4985de70cfe27f43d586a60b152fff6965d.png)

- 【步骤】
	![image.png](https://i0.hdslb.com/bfs/openplatform/c9abc85424bf6c0cf31837e3eaf2aca6392f025f.png)
	![image.png](https://i0.hdslb.com/bfs/openplatform/3e1d1b5a12a051154947bcccfcebbf3434756066.png)

如果顺利的话，你会看到搜索框变成下图所示的样子，这样是不是变得更加紧凑了？

![image.png](https://i0.hdslb.com/bfs/openplatform/835fae9377bad09a8665030336f2439790087678.png)

#### （4）调整此图片

相信有些人对这个东西感到比较烦，那么有没有关闭它的方法呢？有的，下面就来教导大家如何关闭这个此图片。

![image.png](https://i0.hdslb.com/bfs/openplatform/61d65cc3929c3349230a5196c42881417f617e20.png)

- 【步骤】
	![image.png](https://i0.hdslb.com/bfs/openplatform/dbac386bba2243c0718aaf9b7b2503c80a4156da.png)

如果顺利的话，你会看到桌面的图片换了（不一定是下图我显示的这张图片），且那个烦人的了解此图片消失了。这样一搞，桌面干净不少！

![image.png](https://i0.hdslb.com/bfs/openplatform/a37e4744ab4ecbde9ede70f05758a1e3bd929795.png)

#### （5）新建文件

- # 自我练兵

动手将电脑变得简洁美观吧

### 1.1.2. 资源管理器基础

#### （1）前置知识

随着 Windows 系统的快速迭代，文件资源管理器也在不断进化。首先，我们从直观上对比一下 Win10 和 Win11 的文件资源管理器的**主界面**。

如下图所示，上侧和下侧分别为 Win10 和 Win11 的文件资源管理器。直观上看，Win11 针对**菜单栏**做了不少精简，仅保留显示**新建**、**剪切**、**复制**、**粘贴**、**重命名**、**分享**、**删除**、**排序**以及**查看** 9 个常用选项，而对其他选项则作了隐藏，相比 Win10，变的**简洁高效**了许多。



![](https://img.ithome.com/mpimg/content/11653976/2021/11/20211123_213119_548.png?x-bce-process=image/watermark,image_aW1nL3dhdGVybWFyay9xYy9xYzEwMC5wbmc=,g_9 "Win10/Win11学院：玩转 Windows 文件资源管理器")

<center><b>▼ Win10 vs Win11 的文件资源管理器</b></center>

Win11 针对**右键菜单**也做了类似的改进，如下图所示：微软将最常用的菜单项至于顶部一栏，而将不常用的菜单项做了隐藏，而在点击【显示更多选项】才显示所有菜单。当然，针对这一改变，褒贬不一，这里不再赘述。

![](https://img.ithome.com/mpimg/content/11653976/2021/11/20211123_220743_433.png?x-bce-process=image/watermark,image_aW1nL3dhdGVybWFyay9xYy9xYzEwMC5wbmc=,g_9 "Win10/Win11学院：玩转 Windows 文件资源管理器")

<center><b>
▼ Win11 的文件资源管理器及文件的右键菜单</b></center>

#### （2）显示文件隐藏名

相信你们都遇到了如下图所示的情况，明明下载东西的时候是有后缀的，但是怎么到文件管理器中就没有了呢？别急，下面我们来讲如何开启后缀显示

![image.png](https://i0.hdslb.com/bfs/openplatform/8598dd2e11c263c73a8e25f8fb78a942f4178007.png)

<center><b>
图：未开启文件扩展名的文件显示</b></center>

[^1]Win11 系统中，【文件扩展名】与【隐藏的项目】两个选项都位于【查看】选项下，需要按照下述方法开启。

![](https://img.ithome.com/mpimg/content/11653976/2021/11/20211123_232506_267.png?x-bce-process=image/watermark,image_aW1nL3dhdGVybWFyay9xYy9xYzEwMC5wbmc=,g_7 "Win10/Win11学院：玩转 Windows 文件资源管理器")

<center><b>图： Win11 的文件资源管理器开启文件扩展名和隐藏项目的方法</b></center>

如果你操作顺利的话，那么结果会得到下图所示的样子

![image.png](https://i0.hdslb.com/bfs/openplatform/60673cbcb6bae9b14066cbc1921c566306d0da54.png)

<center><b>
图：开启文件扩展名的文件显示</b></center>

这一个东西在做项目的时候很有用，想一下，如果出现两个重名的文件。那么这个时候识别他们的方法就是文件扩展名，如果你没有开启这个显示功能，那么你很可能用错文件，这是致命的！

#### （3）使用复选框

首先需要打开【项目复选框】的开关，在两个系统中也都位于【查看】选项下。

<center><b>▼ Win10 的文件资源管理器</b></center>

![](https://img.ithome.com/mpimg/content/11653976/2021/11/20211127_173144_788.png?x-bce-process=image/watermark,image_aW1nL3dhdGVybWFyay9xYy9xYzEwMC5wbmc=,g_3 "Win10/Win11学院：玩转 Windows 文件资源管理器")

<center><b>▼ Win11 的文件资源管理器</b></center>

![](https://img.ithome.com/mpimg/content/11653976/2021/11/20211127_173517_596.png "Win10/Win11学院：玩转 Windows 文件资源管理器")

操作演示如下：将鼠标悬浮至某个文件（文件夹）上方时会显现复选框，然后单击其复选框即可选中该文件，可利用该功能进行多选。另外，点击标题栏【名称】左侧的复选框即可全选，再次单击即可取消全选。

![](https://img.ithome.com/mpimg/content/11653976/2021/11/20211127_173835_695.gif "Win10/Win11学院：玩转 Windows 文件资源管理器")

#### （3）使用多标签页

- # 自我练兵
动手将复选框和文件隐藏名打开吧






### 1.1.3. 任务管理器基础

任务管理器的主要使用功能有以下几个方面，下面我们来一一进行介绍

1.  **强制结束问题程序：** 使用任务管理器结束无响应的应用程序及其子进程。
2.  **查找资源占用大户：** 通过 CPU、磁盘、GPU 使用率排序，找出占用资源最多的程序。
3.  **检查电脑性能占用：** 在“性能”页面查看 CPU、内存、磁盘、网络、GPU 的实时使用情况。
4.  **检查显卡工作情况：** 在“性能”选项卡中查看 GPU 温度，判断是否存在散热问题。
5.  **检查驱动器介质类型：** 在“性能”选项卡中查看硬盘或固态硬盘的类型（SATA、NVMe 等）。
6.  **检查网络工作状态：** 在“性能”选项卡中查看网络适配器的详细信息，如利用率、状态等。
7.  **检查每个核心状态：** 在“性能”选项卡中，将 CPU 图表更改为显示每个逻辑处理器的活动情况。
8.  **管理应用和进程自启动：** 在“启动应用程序”部分禁用不需要的开机启动项，或通过 `msconfig` 管理服务。

#### （1）强制结束问题程序

![](https://cn.windows-office.net/common-images/windows-11-task-manager-tips/04dwtm4hFozaDQV4ceacXUR-4.png)

如果您正在运行的程序没有响应并且不允许您关闭它，那么任务管理器是您最好的朋友。只需单击程序列表中的条目，然后点击“结束任务”按钮或右键单击并选择“结束任务”。这会绕过程序中的任何代码，阻止您以正常方式关闭它。

请注意，下次运行该程序时，它可能会弹出一条消息，内容类似于“程序上次异常关闭”，并可能询问您是否要向其制造者发送错误报告。

有时，您可以通过关闭应用程序的子进程而不是整个应用程序来修复无响应的应用程序。 CPU 和其他使用统计数据可能会显示某些子进程的高使用率，这将指出罪魁祸首。只需单击该条目旁边的箭头，如果某个特定进程指示 CPU 或磁盘使用率较高，请终止该进程。您现在可以使用快捷键 Ctrl-E 切换应用程序。

#### （2）查找资源占用大户

任务管理器最常见的用途之一是在您的电脑运行缓慢时找到罪魁祸首。打开任务管理器并单击 CPU 列顶部可按 CPU 使用率排序。如果某个应用程序占用了 CPU，那么它可能就是罪魁祸首。

另一件需要注意的事情是磁盘。按顶部 MB 量最高的列进行排序，以查看应用程序是否对您的存储系统造成过度负担。

对于视频游戏和视频编辑，您需要添加 GPU 列，该列默认情况下不显示。右键单击标题列中的任意位置，然后单击 GPU 左侧。现在，您可以按每个应用程序的 GPU 使用情况进行排序，看看哪些应用程序对其造成了负担。
 
#### （3）检查电脑性能占用

![](https://cn.windows-office.net/common-images/windows-11-task-manager-tips/04dwtm4hFozaDQV4ceacXUR-27.png)

如果您想查看在 PC 上运行应用程序、应用程序或游戏的效果，请前往任务管理器的性能页面。它向您显示 CPU、内存、磁盘、Wi-Fi 和 GPU 使用情况的实时图表。要将日期以文本格式复制到剪贴板，您可以选择右上角的溢出菜单（即省略号或“...”）并选择“复制”，也可以右键单击“CPU”、“内存”标题并选择复制。右键单击还提供摘要视图，其中在小窗口中仅显示四个性能条目。

#### （4）检查显卡工作情况

在“性能”选项中，您还可以找到显卡的温度，这对于那些在使用照片和视频编辑解决方案等渲染软件时排除游戏电脑或散热问题的人来说非常有用。

要检查 GPU 温度，您只需打开**“GPU”**选项卡，然后找到选项卡标题下或页面上的温度读数。

![](https://cn.windows-office.net/common-images/these-are-my-19-tips-to-help-you-get-even-more-from-task-manager-on-windows-11/cmXXn8SXS2pvtyahQKgmF7.jpg.webp)

此信息可能不适用于每个显卡，这是较旧或虚拟化显卡的典型情况。

通常，65 至 85°C 的温度范围是正常的，但持续超过 100°C 的温度应被视为过热。

#### （5）检查驱动器介质类型

虽然有多种方法可以检查连接到设备的存储类型，但任务管理器现在可以告诉您驱动器是否是 SATA、NVMe 等。

要检查计算机上安装的驱动器类型，请打开“性能”。选项卡并单击驱动器。带有类型信息的标签将显示在选项卡标题下以及页面上的**“类型”**字段中。

![](https://cn.windows-office.net/common-images/these-are-my-19-tips-to-help-you-get-even-more-from-task-manager-on-windows-11/tShC4VETjqiRQVbHxVtsnF.jpg.webp)

#### （6）检查网络工作状态

在“性能”选项卡中查看网络适配器活动时，您只会找到有关发送和接收数据包的吞吐量的信息，但您可能不知道您还可以查看其他网络详细信息，例如网络利用率、状态、有关发送和接收的字节和单播数据包的不同类型的信息，这些信息在排除问题或监控网络连接时非常有用。

要查看有关特定网络适配器的更多详细信息，请在“性能”选项卡中单击以太网或 Wi-Fi 适配器，右键单击图表，然后选择**“查看网络详细信息”**选项。

![](https://cn.windows-office.net/common-images/these-are-my-19-tips-to-help-you-get-even-more-from-task-manager-on-windows-11/qPJ3iLYjetvkXauJWXhyUP.jpg.webp)

#### （7）检查每个核心状态

在“性能”选项卡中，查看“CPU”信息时，您可能会看到“总体利用率”视图，该视图将与整个处理器相对应的活动显示为一个实体。但是，您也可以更改每个核心的活动时间的视图。

如果您想查看处理器内每个核心的性能活动，请右键单击“性能”选项卡中的 CPU 图表，选择**将图表更改为** 菜单，然后选择 **>“逻辑处理器”** 选项。

![](https://cn.windows-office.net/common-images/these-are-my-19-tips-to-help-you-get-even-more-from-task-manager-on-windows-11/TZ2SbmdhSWGRP4T8ve69ac.jpg.webp)

#### （8）管理应用和进程自启动

![](https://cn.windows-office.net/common-images/windows-11-task-manager-tips/04dwtm4hFozaDQV4ceacXUR-26.jpg)

通常，当您安装应用程序时，它会将某些进程设置为随您的电脑自动启动。结果可能是，即使您不想使用关联的应用程序，许多进程仍在运行。您可以在任务管理器的启动应用程序部分找到此类自动运行的进程。如果您发现其中的某些内容不需要在每次打开计算机时运行，则只需选择该进程，然后点击“禁用”按钮即可。您还可以右键单击该进程并从上下文菜单中选择“禁用”。

**专业提示：** 任务管理器还有一个服务页面。 服务是为所有用户在后台运行并由 Windows 管理的进程 - 它们没有用户界面。举几个例子，它们对于运行打印机服务、防病毒软件或系统时钟很有用。有些程序会安装它们并让它们运行，无论您是否打开关联的应用程序。如果您不希望该程序运行任何内容，您可以禁用其服务。 

![](https://cn.windows-office.net/common-images/windows-11-task-manager-tips/04dwtm4hFozaDQV4ceacXUR-17.png)

我不喜欢使用任务管理器关闭不需要的服务，而是更喜欢以下方法：打开“开始”菜单，键入“运行”，然后在出现的“运行”文本框中键入_msconfig_，然后切换到“服务”选项卡。最好选中“隐藏所有 Microsoft 服务”复选框，这样就不会关闭重要的系统服务。然后取消选中不需要的服务并重新启动您的电脑以使更改生效。

顺便说一句，对于这两种关闭中的任何一种，您通常不必担心 Windows 之后无法运行，因为 Windows 通常会阻止您禁用必要的进程和服务，或者操作系统会立即将它们重新启动。也就是说，不建议停止您不认识的服务。另外，请注意，下次运行关联的应用程序时，该服务将不会运行，因此您可能需要重新启用它们的功能。

- # 小试牛刀

了解CPU，GPU，显卡，驱动器，网络等基本概念（将搜索结果概括在下面）





### 1.1.4. 任务托盘基础

>**简介**：在 **Windows 11** 中，系统托盘（也称为“通知区域”）位于任务栏右下角，是用户快速访问常用工具和查看系统状态的重要区域。系统托盘通常显示时间、音量、网络连接、电池状态等核心系统图标，并支持用户自定义添加或隐藏其他应用程序的图标。

![image.png](https://i0.hdslb.com/bfs/openplatform/1542e890a3e5ff7a9a8a302b8ea7da313e6892d6.png)

<center><b>
图：展开系统托盘后端样子</b></center>

#### （1） **查看和管理通知**

- 点击任务托盘中的 **“通知中心”图标（时间信息图标）** ，你可以查看最近的系统和应用程序通知。
- 可以点击通知直接跳转到相关应用或执行操作。
- 支持关闭通知、调整通知设置等。

![image.png](https://i0.hdslb.com/bfs/openplatform/dc7a6ca7b77ccc8769285673a465b94059dac3df.png)

<center><b>
图：查看通知面板</b></center>

#### （2） **快速访问常用设置**

- **输入法图标** ：切换中英文输入法或不同语言键盘。
- **网络图标** ：点击可查看当前连接的Wi-Fi或以太网状态，快速切换网络、断开连接或打开网络设置。
- **音量图标** ：调节系统音量、切换音频输出设备（如耳机、扬声器、蓝牙音箱）。
- **电池图标（适用于笔记本）** ：查看电量，切换电源模式（高性能/平衡/节能）。
- **时钟图标** ：显示当前日期和时间，点击可以打开日历和任务视图（包括待办事项）。

![image.png](https://i0.hdslb.com/bfs/openplatform/3d178fb0e65885f9b2fddfcafb862c63ba4b90ce.png)

<center><b>
图：Windows 11 右下角任务栏默认视图</b></center>

#### （3） **隐藏图标的展开与管理**

- 如果部分图标被隐藏，可以点击任务托盘中的 **向上箭头（^）图标** 来展开所有隐藏的图标。
- 将鼠标悬停在图标上可以看到它的提示信息或状态。

**减少后台程序干扰**：比如你微信默认任务图标是在任务栏中的（下图一），每次来消息这个图标都会闪，很影响你工作，我们可以把他拖拽到托盘中这样不管他在怎么闪也不会打扰你了（下图三）。

![image.png](https://i0.hdslb.com/bfs/openplatform/5e18b33fe744193d4206c4294dcb655d251bd74a.png)

<center><b>
图：未放入任务托盘的微信任务图标</b></center>

![image.png](https://i0.hdslb.com/bfs/openplatform/e8b02cb4238e6a3dc6c702db4b4772803980cfcb.png)

<center><b>
图：放入微信任务图标且未折叠的任务托盘</b></center>

![image.png](https://i0.hdslb.com/bfs/openplatform/8a40038a139ecacabb7e472fb9f605bd3799340e.png)

<center><b>
图：放入微信任务图标且折叠的任务托盘</b></center>

【步骤】
	![image.png](https://i0.hdslb.com/bfs/openplatform/68d6e6d86b2757c7379659b3d0ede033517fbd9a.png)

- # 自我练兵

根据上述步骤只留下输入法，网络，音量以及电池状态吧

### 1.1.5. 显示设置基础
#### （1）刷新率设置

1.在Windows搜寻栏输入**[查看高级显示信息]**①，然后点选**[打开]**②。

![](https://km-ap.asus.com/uploads/PhotoLibrarys/279b1926-d2df-4b18-b3b2-c9c4685ef985/20241023163552826_LCD5.jpg)

2.如果要更改显示器的刷新率，请于**选择重新整理的频率**选择您想要的刷新率③。  
**注**: 显示器的刷新率调整会依据您设备的规格，不是每一个型号都可以变更。

![](https://km-ap.asus.com/uploads/PhotoLibrarys/279b1926-d2df-4b18-b3b2-c9c4685ef985/20241023163552925_LCD6.jpg)

#### （2）分辨率设置
1. 在Windows搜寻栏输入**[更改显示器的分辨率]**①，然后点选**[打开]**②。

![](https://km-ap.asus.com/uploads/PhotoLibrarys/279b1926-d2df-4b18-b3b2-c9c4685ef985/20241023161903240_LCD1.jpg)

2. 如果要更改显示器的分辨率，请于**显示器分辨率**选择您想要的分辨率③。  
您也可以选择显示的方向，在**显示方向**选择横向、直向、横向(翻转)或直向(翻转)④。

![](https://km-ap.asus.com/uploads/PhotoLibrarys/279b1926-d2df-4b18-b3b2-c9c4685ef985/20241023163052097_LCD4.jpg)

3. 更改项目后会出现以下提醒窗口，请再点选 **保留变更** 您的设置才会生效。

#### （3）显示器亮度设置

Windows 11 引入了全新的「快速操作」面板，用户可以通过它便捷地调节计算机上的各项设置，包括 Wi-Fi、蓝牙、亮度和音量控制等。以下是使用「快速操作」面板快速调整屏幕亮度的操作步骤：

1. 鼠标单击「任务栏」右侧的电池、声音或互联网图标，打开「快速操作」 面板。

2. 要调整屏幕亮度，可以将「亮度滑块」向左拖动以减小亮度，或向右拖动以增加亮度。

![通过「快速操作」 面板调整 Windows 11 屏幕亮度](https://img.sysgeek.cn/img/2023/10/windows-11-change-brightness-2.jpg)

<center><b>图：通过「快速操作」 面板调整 Windows 11 屏幕亮度
</b></center>

>**注意**:「亮度滑块」仅在移动设备中可用，如果您使用的是连接外部显示器的台式机，该控制滑块会自动隐藏。

#### （4）多屏显示器设置

>**引言**：[^3]在Win11系统中，我们可以通过打开分屏来让多个显示器使用同一款系统，共同操作，这样可以使我们便于操作，提高工作效率，那么该怎么设置分屏呢？

![](https://pic2.zhimg.com/v2-010ef2c2497c88543be93635d681991b_1440w.jpg)

<center><b>
图：双屏工作位预览</b></center>

![](https://pic4.zhimg.com/v2-47a69a4b26b4ecdfce52b3970023369f_1440w.jpg)

<center><b>
图：多屏工作位预览</b></center>

##### 1）多屏模式设置

【步骤】
	1. [^5]确认你的笔记本上有的[显示器接口](https://zhuanlan.zhihu.com/p/681025427)（你至少得保证你有一个屏幕）
		![](https://pica.zhimg.com/v2-66e68a103aabaf9da14480cdca33b7a0_1440w.jpg)
	2. 确定显示器拥有的[显示器视频输入接口](https://diy.pconline.com.cn/582/5823699_all.html)
		![image.png](https://i0.hdslb.com/bfs/openplatform/51334943a9f5a4dda6ae3867ffc7e2baa927933c.png)
	3. 确定好双方的连接方式（是HDMI<-->HDMI，还是HDMI<-->VGA，详情问AI：把你的目的、你的条件告知他）
	4. 连接笔记本与显示器
	5. 使用快捷键Win+P唤起分屏设置菜单
		![](http://ipasoncnknowledge-oss.ipason.com/images/8875ca2b-af46-493f-88c4-f74caa9e0c29.png)
			**仅电脑屏幕**：显示一个屏幕
			**复制**：显示两个画面完全一样的屏幕
			**扩展**：两个显示器共同显示一个完整的屏幕，拼接在一起
			**仅第二屏幕**：仅显示外接屏幕。
	6. 按照需求选择相应的设置

>**注意**：如果是3个及以上屏幕连接后屏幕黑屏，由于带宽的限制，需要将分辨率更改为1080或以下分辨率显示（如果你看不懂我说的，请问AI，我讲的术语都属于通识，必须得知道搞清楚它是什么）

##### 2）**分辨率更改**

复制模式分辨率修改，仅需修改一个屏幕的分辨率即可。
扩展模式分辨率修改，需分别修改显示器1和显示器2两个显示器的分辨率。（此处以此模式介绍）

【步骤】
	进入“设置”-“系统”-“屏幕”，分别使用鼠标单击选中显示器1或显示器2，再修改下方分辨率大小。
	![](http://ipak.ipason.com/images/c8b35a97-d417-45a2-9bb4-6fa7a493904f.png)

##### 3）**显示器切换主屏幕显示**

【步骤】
	   **显示器1：鼠标单击选中“显示器1” ，勾选“设为主显示器”   。**
	   ![](http://ipak.ipason.com/images/412591de-5830-49e1-83e2-4f22ba603b2a.png)
	显示器2：**鼠标单击选中“显示器2” ，勾选“设为主显示器”   。**
	![](http://ipak.ipason.com/images/1891725f-1844-43ed-b11b-0b0792abecf6.png)

#### （5）窗口文字大小设置

1. [^4]在Windows搜寻栏输入 **变更文字、应用程序与其他项目的大小** ①，然后点选**打开**②。

![](https://km-ap.asus.com/uploads/PhotoLibrarys/279b1926-d2df-4b18-b3b2-c9c4685ef985/20241023161903240_LCD1.jpg)

2. 如果要变更文字与窗口的大小，请于**比例**选择您想要的大小③。

![](https://km-ap.asus.com/uploads/PhotoLibrarys/279b1926-d2df-4b18-b3b2-c9c4685ef985/20241023161903240_LCD2.jpg)

3. 如果您只是想将画面上的文字变大但不改变所有影像和应用程序的大小，您可以透过以下方式:  在Windows搜寻栏输入**放大本大小**④，然后点选**打开**⑤。

![](https://kmpic.asus.com/images/2022/03/22/13bd971a-eb06-4cc5-94ed-32473b90b66d.png)

4.在**文字大小**字段中，通过滑动调整文字大小然后再点击应**用**⑥。

![](https://km-ap.asus.com/uploads/PhotoLibrarys/279b1926-d2df-4b18-b3b2-c9c4685ef985/20241023162905015_LCD3.jpg)

- # 自我练兵
有条件的话试着开启自己的第二块屏幕吧

### 1.1.6. 快捷键基础

本文除列举了 [Windows 11](https://win11.ithome.com/) 常用的键盘快捷键之外，还附带描述了**使用方法**和**记忆方法**，读完本文，希望能够帮助[IT之家](https://www.ithome.com/)家友进行快速记忆，以期学以致用，提高工作效率。

如下图所示，以系统的触摸键盘为例，红色框标记的按键即为 **Windows 徽标键**，这个标识很像汉字 “**田**”，因此大家也戏称微软的品牌为 “**田牌**”，下文会用 **Win** 简写来表示该按键，并且会针对该按键展开讲解。

![](https://img.ithome.com/mpimg/content/11653976/2021/11/20211117_141102_945.png?x-bce-process=image/watermark,image_aW1nL3dhdGVybWFyay9xYy9xYzEwMC5wbmc=,g_3 "附使用及记忆方法，Win11 常用快捷键一览")

<center><b>
▲ Windows 11 触摸键盘
</b></center>

#### （1）系统常用快捷键

如下图所示：首先来看红色框标记的 6 个图标，依次为：**开始**、**搜索**、**切换任务与虚拟桌面**、**小组件**、**聊天**、**文件资源管理器**。

![](https://img.ithome.com/mpimg/content/11653976/2021/11/20211117_141223_605.png?x-bce-process=image/watermark,image_aW1nL3dhdGVybWFyay9xYy9xYzEwMC5wbmc=,g_7 "附使用及记忆方法，Win11 常用快捷键一览")

<center><b>▲ Windows 11 任务栏</b></center>

下面将依次列举其键盘快捷键，每个快捷键务必都按一按试试看，要不然记忆是不会深刻的

- **Win**：按下 Windows 徽标键即可打开 “**开始**” 菜单，再次按下即可关闭。记忆方法：**Win**dows 徽标键。
    
- **Win+ S** 或 **Win+ Q**：按下该组合键即可打开**搜索框**。记忆方法：当我们需要搜索（英文为 **S**earch，取其首字母 S）、提问（**Q**uestion，首字母为 Q，下同）时可以使用搜索框。
    
- **Win*+ Tab**：在打开的窗口、应用或虚拟桌面之间**显示**和**切换**（需要进一步点击要切换的应用或虚拟桌面）。
    
- **Win+ W**：打开 / 关闭**小组件**，按下该组合键即可打开小组件面板，再次按下即可关闭。记忆方法：组件的英文为 **W**idget（官方翻译为小组件，个人认为翻译为小部件更佳）。
    
- **Win+ C**：打开聊天软件 **Microsoft Teams**（在 [Windows 10](https://win10.ithome.com/) 中按下该组合键默认打开的是 **Cortana 语音助手**）。记忆方法：如下图所示，该软件主要用于会议（**C**onference）与聊天（**C**hat）。
    

![](https://img.ithome.com/mpimg/content/11653976/2021/11/20211117_141337_349.png?x-bce-process=image/watermark,image_aW1nL3dhdGVybWFyay9xYy9xYzEwMC5wbmc=,g_7 "附使用及记忆方法，Win11 常用快捷键一览")

<center><b>▲ 聊天界面</b></center>


- **Win+ E**：打开**文件资源管理器**。记忆方法：该软件的英文为 **E**xplorer。
    

再来看任务栏右侧，还有三个快捷键与任务栏有关。

- **Win+ A**：打开常用**设置**面板（如下图）。记忆方法：在 Windows 10 中，常用的设置项位于控制中心，Windows 11 将其独立为一个面板，但还可以称之为控制中心，其英文为 **A**ction Center（或者我们称其为助手 **A**ssistant）。
    

<center><b>▼ 常用设置面板</b></center>

![](https://img.ithome.com/mpimg/content/11653976/2021/11/20211117_141410_429.png?x-bce-process=image/watermark,image_aW1nL3dhdGVybWFyay9xYy9xYzEwMC5wbmc=,g_7 "附使用及记忆方法，Win11 常用快捷键一览")

- **Win+ N**：打开**日历**和**通知**面板。Windows 11 将日历和通知面板放在了一个分组，这点我们在日期区域右击即可弹出的【调整日期和时间】及【通知设置】菜单即可看出来（要是没有通知消息，则不显示通知面板）。记忆方法：通知的英文为 **N**otification。
    

![](https://img.ithome.com/mpimg/content/11653976/2021/11/20211117_141513_897.png?x-bce-process=image/watermark,image_aW1nL3dhdGVybWFyay9xYy9xYzEwMC5wbmc=,g_1 "附使用及记忆方法，Win11 常用快捷键一览")

<center><b>▲ 右击日期区域弹出的菜单项</b></center>

- **Win+ D**：**将所有打开的窗口最小化，并转到桌面**，再次按下即刻恢复所有内容。记忆方法：桌面的英文为 **D**esktop。另外，如下图所示，可以将鼠标置于任务栏最右端，即可弹出提示【显示桌面】，点击此区域的效果等同于按下该组合键。
    

![](https://img.ithome.com/mpimg/content/11653976/2021/11/20211117_141624_213.png?x-bce-process=image/watermark,image_aW1nL3dhdGVybWFyay9xYy9xYzEwMC5wbmc=,g_1 "附使用及记忆方法，Win11 常用快捷键一览")

除此之外，还有 10 个好用的系统快捷键：

- **Win+ G**：打开 **Xbox Game Bar**。按下该组合键可以进行录屏（以及设置音频、查看系统性能等信息），一般用于**录制游戏**。记忆方法：由于和游戏有关，而游戏的英文为 **G**ame。
    
- **Win+ H**：按下该组合键即可使用电脑进行**听写**，即使用语音识别将口语转换为文本（中文支持还挺好，并且支持加标点）。记忆方法：让电脑聆听你说话，听的英文为 **H**ear。
    
- **Win+ I**：打开**设置**应用。记忆方法：由于设置的英文为 Setting，和该快捷键没有对应，我想到了快速（即时）设置，该词可以翻译为 **I**nstant Setting，即快速进入设置的意思。
    
- **Win+ L**：**锁定屏幕**，即锁屏。记忆方法：锁的英文为 **L**ock。
    
- **Win+ P**：**投影**，就是**投屏**，开会的时候会经常用，也可以用于**扩展屏幕**。记忆方法：投影的英文为 **P**roject。
    
- **Win+ R**：打开**运行**对话框（如下图所示）。记忆方法：**R**un 就是运行的意思。
    

![](https://img.ithome.com/mpimg/content/11653976/2021/11/20211117_141708_934.png?x-bce-process=image/watermark,image_aW1nL3dhdGVybWFyay9xYy9xYzEwMC5wbmc=,g_7 "附使用及记忆方法，Win11 常用快捷键一览")

- **Win+ V**：打开**系统粘贴板**，上面有最近复制或剪切的项目，可以将其粘贴至其他应用或跨设备同步。记忆方法：系统（即 **Win**dows）粘贴板（结合**粘贴**的快捷键 Ctrl+ **V**，取第二个按键 V 即可）。
    
- **Win+ X**：效果等同于**右击开始菜单**。记忆方法：打开**好多个**（别人问你多少个， 个吧，具体没数过）菜单项。推荐大家使用这个快捷键，它包含了常用的功能菜单。
    

![](https://img.ithome.com/mpimg/content/11653976/2021/11/20211117_141736_465.png?x-bce-process=image/watermark,image_aW1nL3dhdGVybWFyay9xYy9xYzEwMC5wbmc=,g_7 "附使用及记忆方法，Win11 常用快捷键一览")

- **Win+ .**（**句号**）或 **Win ;**（**分号**）：可以快速打开**表情符号面板**。它其实和粘贴板属于同一个面板（位于最后一个选项卡）。
    
- **Win+ Shift+S**：屏幕**截图**，按下该组合键即可打开系统截图应用并按默认方式进行截图。记忆方法：截图工具翻译过来就是 **S**nipping tool。
    

这里再补充一个不常用的快捷键：

**Win+ F**：打开**反馈中心**应用。我们可以按下该组合键快速反馈系统的 bug 以及意见或建议。记忆方法：按中文拼音首字母（**F**ankui）记忆即可，另外反馈的英文为 **F**eedback。

#### （2）快速调整应用窗口位置

**Win+** **←/→**（方向键）：可以自动将应用窗口完全贴靠到屏幕两侧 - 无需手动调整大小或定位。效果等同于点击 “将鼠标悬浮在最大化按钮上方” 弹出的菜单选项。

![](https://img.ithome.com/mpimg/content/11653976/2021/11/20211117_141943_794.png?x-bce-process=image/watermark,image_aW1nL3dhdGVybWFyay9xYy9xYzEwMC5wbmc=,g_9 "附使用及记忆方法，Win11 常用快捷键一览")

**举一反三**：

- **快速将窗口贴靠于屏幕右下角四分之一处**：按住 **Win** 键不放，先按下 **→** 键，再按下 **↓** 键（顺序不能颠倒)，同样地，使窗口快速贴靠左上角、右上角及左下角操作类似，但是需要注意的是：先按下 **←** 或 **→** 键，再按下 **↑** 或 **↓** 键。
    
- **Win+ ↑**：可以将应用**窗口最大化**。
    
- **Win+ ↓**：可以将应用**窗口最小化**。若是当前窗口处于最大化状态，则按住 **Win** 键不放，**连续按两下** ↓ 键即可将窗口最小化。
    

#### （3）切换后台应用

上面提到的 **Win**+ Tab** 快捷键仅仅是打开后台应用和虚拟桌面的界面，不是专门用于快速切换应用的。接下来介绍的两个快捷键，可以用于快速切换打开的应用。

- **Alt+ Tab**：在打开后台应用界面后快速切换应用。为了方便我们需要对相关选项进行设置。如下图，导航至【系统】→【多任务处理】下的【Alt+Tab】选项，并改为【仅打开的窗口】选项。
    

![](https://img.ithome.com/mpimg/content/11653976/2021/11/20211117_142017_448.png?x-bce-process=image/watermark,image_aW1nL3dhdGVybWFyay9xYy9xYzEwMC5wbmc=,g_9 "附使用及记忆方法，Win11 常用快捷键一览")

- **Alt+ Esc**：与 **Alt+Tab** 不同的是，该组合键**并不会打开后台界面**，仅仅按照打开的顺序进行应用的快速切换。使用场景：适合打开应用较少的场景，例如打开了**两个**应用，我们便可以借助该组合键迅速进行应用切换。
    

#### （4）打开任务管理器

**Ctrl+ Shift+Esc**：打开**任务管理器**，也适用于 Windows 10。使用原因：由于 Windows 11 无法在任务栏上右击打开任务管理器，使用该组合键可快速打开任务管理器。记忆方法：==有时打开任务管理器是为了去强制关闭应用==，可以理解为使应用逃离（**Escape**）后台。

- # 自我练兵
试着用快捷键来提高自己使用电脑的效率吧



## 1.2. 浏览器使用基础

>**引言**：浏览器千千万，但是我觉得就 Windows 自带的 Edge 而言，已经足够优秀，不需要再使用其他的浏览器，之后可能会用到 Chrome ，不过那都是后话了。


### 1.2.1. 页面整洁

大部分人的浏览器打开可能会和下图一样，第一眼你会觉得页面元素比较散乱，那么如何整洁这个界面呢？下面直接上步骤

![image.png](https://i0.hdslb.com/bfs/openplatform/f9f8bf209ca84ced39962d1b59d722cbaebbf168.png)

【步骤】
	1. 点击页面设置按钮，依次关闭图中所示的三个按钮
	![image.png](https://i0.hdslb.com/bfs/openplatform/4f10d9d3327590c0275572597c9b163b9b61e7e9.png)
	2. 在上面步骤的基础上依次点击以下几个按钮。
	![image.png](https://i0.hdslb.com/bfs/openplatform/d672fc792ba5af2cf8c398513327ac2e98467028.png)

如果你完成了上述步骤，你的首页就会变成下述界面，这样是不是干净多了？

![image.png](https://i0.hdslb.com/bfs/openplatform/0da9ba37a9e6919c76d7c8f6aba57e452d13348e.png)

>**Ps**：后面插件篇会介绍主页插件，下图是安装了 ITab 主页插件后的页面效果，是不是简洁又漂亮？

![image.png](https://i0.hdslb.com/bfs/openplatform/b41f89a8710cdf3180398cdfd3a3d69246b3f138.png)

### 1.2.2. 页面操作

- **缩放页面​**​：在大多数浏览器中，可通过按下Ctrl键（Windows系统）或Command键（Mac系统）并同时滚动鼠标滚轮来实现页面的放大或缩小，方便查看网页细节或整体布局。也可在浏览器菜单中找到“缩放”选项，手动输入缩放比例。

- ​**​滚动页面​**​：使用鼠标滚轮上下滚动页面浏览内容；对于一些支持横向滚动的网页，可使用Shift键 + 鼠标滚轮进行横向滚动。此外，还可通过点击浏览器窗口两侧的滚动条来快速定位页面位置。

- ​**​前进后退​**​：点击浏览器工具栏上的前进和后退按钮，可在浏览历史记录中向前或向后切换页面。按住Ctrl键（Windows系统）或Command键（Mac系统）再点击前进或后退按钮，可实现在新标签页中打开历史页面。

- ​**​刷新页面​**​：点击浏览器工具栏上的刷新按钮或按下F5键，可重新加载当前页面，获取最新内容。按住Ctrl键（Windows系统）或Command键（Mac系统）再按F5键，可强制刷新页面，绕过浏览器缓存加载最新资源。

- ​**​切换标签页​**​：点击相应的标签页标签可快速切换到对应的页面。还可使用快捷键Ctrl + Tab（Windows系统）或Command + Tab（Mac系统）在打开的标签页之间循环切换，按住Ctrl键（Windows系统）或Command键（Mac系统）再按数字键（如1 - 9）可直接切换到对应序号的标签页。

- ​**​在新窗口或新标签页中打开链接​**​：右键点击网页上的链接，选择“在新窗口中打开”或“在新标签页中打开”；也可在按住Ctrl键（Windows系统）或Command键（Mac系统）的同时点击链接，在新窗口或新标签页中打开。

### 1.2.3. 收藏夹操作

- ​**​添加到收藏夹​**​：浏览到喜欢的网页时，点击浏览器工具栏上的收藏夹图标（通常是一个星星形状），选择“添加到收藏夹”。可在弹出的对话框中设置收藏夹的名称、文件夹位置等，方便后续查找。

![示例](https://img.picui.cn/free/2025/05/13/68232879bbe1f.png)

- ​**​管理收藏夹​**​：进入浏览器的收藏夹管理界面（一般在浏览器菜单中能找到“收藏夹”选项进入），可创建新的文件夹对收藏项进行分类，如“新闻网站”“购物网站”等；还能移动、重命名、删除收藏项，调整其在文件夹中的顺序等。

![示例](https://img.picui.cn/free/2025/05/13/6823299401f9a.png)

- ​**​快速访问收藏夹​**​：将常用的收藏项拖动到浏览器的收藏栏（一般在地址栏下方），这样只需点击收藏栏中的图标即可快速打开对应的网页。

就拿deepseek官网来举个例子，点击浏览器左上角书签，点击添加书签，之后你打开的当前的网站就会出现在网址下面方便打开

![](https://img.picui.cn/free/2025/05/13/68232ad1c0a68.png)

如图：

![](https://img.picui.cn/free/2025/05/13/68232c17c681a.png)

### 1.2.4. 更改搜索引擎

- ​**​选择搜索引擎​**​：常见的搜索引擎有百度、谷歌、必应等。在浏览器设置中找到“搜索引擎”相关选项，会列出可供选择的搜索引擎列表。

![](https://img.picui.cn/free/2025/05/13/68232d1247da1.png)

- ​**​设置为默认搜索引擎​**​：从列表中选择想要设置为默认的搜索引擎，点击“设为默认”按钮。之后在地址栏中输入关键词进行搜索时，浏览器将使用默认搜索引擎进行搜索。

![](https://img.picui.cn/free/2025/05/13/68232d735a6fd.png)


- # 小试牛刀

1.根据教程将Edge浏览器的界面变得简洁
2.收藏[STA LAB](https://www.stalab.fun/)
3.将必应设置为默认搜索引擎
## 1.3. 软件管理基础

按照惯例，我们来看看如果本小节知识欠缺会造成的一个反面案例

![电子扫盲课—网盘下载压缩文件及解压缩教学_哔哩哔哩_bilibili](https://www.bilibili.com/video/BV11w4m1y7kA/?spm_id_from=333.337.search-card.all.click&vd_source=4c095a1bfb5e2a56290ec68b55b5d467)

<center><b>
视频：电子扫盲课—网盘下载压缩文件及解压教学</b></center>

![image.png](https://i0.hdslb.com/bfs/openplatform/716012b92ade6a220d5a755b0bf2a9b1763a9b7d.png)

<center><b>
图片：典型反例</b></center>

### 1.3.1. 前提知识

>**引言**：安装卸载软件前你先得知道文件格式有几种，如果你都不知道文件格式有几种，那你怎么根据对应的文件格式去执行对应的安装办法？更别说安装对应的软件了。

- **直接安装的安装包文件扩展名**有下图所示的四种，主要为 MSI、EXE、Appx、和MSIX 这四个。

![image.png](https://i0.hdslb.com/bfs/openplatform/027dcff6113d371f898a2e7f41096caf867168c0.png)

<center><b>
图：知乎关于直接安装的主要四种格式介绍</b></center>

>**Ps**：新手的话知道有这四个概念就行了，如果你想要详细知道这四种安装文件的区别，请点击[Windows 4种安装程序格式MSI，EXE、AppX和MSIX优缺点对比以及后缀为 .msixbundle的文件怎么安装？](https://zhuanlan.zhihu.com/p/571758477#:~:text=%E4%B8%80%E3%80%81Windows%E5%9B%9B%E7%A7%8D%E5%AE%89%E8%A3%85%E7%A8%8B%E5%BA%8F%E6%A0%BC%E5%BC%8F%EF%BC%9AMSI%EF%BC%8CEXE%E3%80%81AppX%E5%92%8C%E6%9C%80%E6%96%B0%E7%9A%84MSIX%E4%BC%98%E7%BC%BA%E7%82%B9%E5%AF%B9%E6%AF%94%201%201%E3%80%81MSI%E6%98%AFWindows%E6%9C%80%E5%9F%BA%E6%9C%AC%E7%9A%84%E5%AE%89%E8%A3%85%E6%A0%BC%E5%BC%8F%EF%BC%9A%E6%AF%94%E8%BE%83%E7%AE%80%E5%8D%95%20MSI%E6%98%AF%20Microsoft%20Installer%20%E7%9A%84%E7%AE%80%E5%86%99%2C%20%E5%AE%83%E4%BD%BF%E7%94%A8%E5%BE%AE%E8%BD%AF%E6%8F%90%E4%BE%9B%E7%9A%84%E6%A0%87%E5%87%86%E5%AE%89%E8%A3%85%E5%8D%B8%E8%BD%BD%E7%95%8C%E9%9D%A2%EF%BC%8C%E6%9C%AC%E8%B4%A8%E4%B8%8A,%E5%90%8E%E6%8E%A8%E5%87%BA%E7%9A%84%E6%96%B0%E5%AE%89%E8%A3%85%E6%A0%BC%E5%BC%8F%EF%BC%8C%E5%BE%88%E5%A4%9A%E7%BD%91%E5%8F%8B%E5%8F%AF%E8%83%BD%E6%B2%A1%E8%A7%81%E8%BF%87%E8%BF%99%E7%A7%8D%E4%BD%BF%E7%94%A8%E8%BF%99%E7%A7%8D%E6%A0%BC%E5%BC%8F%E7%9A%84%E7%A8%8B%E5%BA%8F%EF%BC%8C%E5%AE%83%E5%B0%B1%E6%98%AF%20UWP%20%E5%BA%94%E7%94%A8%E3%80%82%20...%204%204%E3%80%81MSIX%E7%BB%93%E5%90%88%E4%BA%86MSI%E5%92%8CAppX%E7%9A%84%E4%BC%98%E7%82%B9%E5%8F%8A%E6%9C%80%E4%BD%B3%E6%80%A7%E8%83%BD%20MISX%E6%96%87%E4%BB%B6%E6%A0%BC%E5%BC%8F%E9%9B%86%E6%88%90%E4%BA%86Windows%E4%B9%8B%E5%89%8D%E7%9A%84%E6%96%87%E4%BB%B6%E6%A0%BC%E5%BC%8F%E5%AE%89%E8%A3%85%E6%8A%80%E6%9C%AF%EF%BC%8C%E5%B9%B6%E7%BB%A7%E6%89%BF%E4%BA%86UWP%E7%9A%84%E7%89%B9%E6%80%A7%EF%BC%8C%E6%9B%B4%E5%8A%A0%E5%AE%89%E5%85%A8%E5%92%8C%E5%8F%AF%E9%9D%A0%EF%BC%8C%E7%BD%91%E7%BB%9C%E5%B8%A6%E5%AE%BD%E4%BC%98%E5%8C%96%EF%BC%8C%E7%A3%81%E7%9B%98%E7%A9%BA%E9%97%B4%E4%BC%98%E5%8C%96%EF%BC%8C%E7%A8%8B%E5%BA%8F%E8%87%AA%E5%AE%9A%E4%B9%89%EF%BC%8C%E5%B9%B6%E6%94%AF%E6%8C%81%E5%85%A8%E9%83%A8%E7%9A%84Windows%E5%BA%94%E7%94%A8%E7%A8%8B%E5%BA%8F%EF%BC%8C%E8%80%8C%E4%B8%94MSIX%E4%BD%BF%E7%A8%8B%E5%BA%8F%E5%8F%AF%E6%9B%B4%E5%B9%B2%E5%87%80%E5%9C%B0%E5%8D%B8%E8%BD%BD%E3%80%82%20)，如果你不想要知道直接继续往下看即可。

- **间接安装的安装包文件名**主要以压缩包为主。压缩包格式就比较多了，下面给出一张表简介，想知道详情的请阅读[各种压缩包格式的优缺点：RAR/ZIP/7Z/TAR/GZ/BZ](https://zhuanlan.zhihu.com/p/18951196360)。

| 扩展名                  | 描述                                                                                                                                                                                                                                                                                                                                                |
| -------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **`.zip`**           | 最流行的压缩格式，支持单文件或多文件打包与压缩，Windows 自 XP 起原生支持；压缩率中等，兼容性极佳，可通过右键菜单直接创建或解压，也可使用 7-Zip、WinRAR 等工具。 ([文件信息](https://fileinfo.com/filetypes/compressed?utm_source=chatgpt.com "Compressed File Formats - FileInfo.com"), [Lifewire](https://www.lifewire.com/zip-file-2622675?utm_source=chatgpt.com "What Is a ZIP File?"))                              |
| **`.rar`**           | Roshal Archive 格式，由 WinRAR 开发，压缩率通常高于 ZIP；支持分卷（.r00/.r01…）、恢复记录和加密，需使用 WinRAR 或 7-Zip 等工具解压。 ([文件信息](https://fileinfo.com/filetypes/compressed?utm_source=chatgpt.com "Compressed File Formats - FileInfo.com"))                                                                                                                                  |
| **`.7z`**            | 7-Zip 专用格式，开源且压缩率优异，支持 LZMA/LZMA2 算法和 AES-256 加密；通常用于对压缩率要求较高的场景。 ([Scott Granneman](https://granneman.com/tech/background/compressionfileformats?utm_source=chatgpt.com "Common Compression File Formats - Scott Granneman"), [文件信息](https://fileinfo.com/filetypes/compressed?utm_source=chatgpt.com "Compressed File Formats - FileInfo.com")) |
| **`.tar`**           | “磁带归档”格式，本身不压缩，仅将多个文件打包成一个归档（tarball）；常与其他压缩算法配合使用（如 gzip、bzip2、xz）。 ([维基百科](https://en.wikipedia.org/wiki/List_of_file_formats?utm_source=chatgpt.com "List of file formats"))                                                                                                                                                                   |
| **`.gz`**            | Gzip 压缩格式，仅压缩单个文件；常与 `.tar` 配合生成 `.tar.gz`/`.tgz`，在 Unix/Linux 环境中非常常见。                                                                                                                                                                                                                                                                           |
| **`.tar.gz`/`.tgz`** | 先使用 TAR 打包，再用 Gzip 压缩得来，兼具打包与压缩功能；Windows 下可用内置功能或 7-Zip、PeaZip 等工具直接打开。                                                                                                                                                                                                                                                                          |
| **`.bz2`**           | Bzip2 压缩格式，仅压缩单个文件；压缩率通常优于 Gzip，但处理速度略慢；常与 TAR 配合生成 `.tar.bz2`。 ([维基百科](https://en.wikipedia.org/wiki/List_of_file_formats?utm_source=chatgpt.com "List of file formats"))                                                                                                                                                                        |
| **`.tar.bz2`**       | TAR 打包后用 Bzip2 压缩，兼具打包与高压缩率优势；适用于对空间敏感且可接受较慢压缩/解压速度的场景。 ([维基百科](https://en.wikipedia.org/wiki/List_of_file_formats?utm_source=chatgpt.com "List of file formats"))                                                                                                                                                                                |
| **`.xz`**            | 基于 LZMA2 算法的压缩格式，压缩率优异，速度适中；常与 TAR 配合生成 `.tar.xz`，在 Linux 发行版包管理中广泛使用。 ([维基百科](https://en.wikipedia.org/wiki/List_of_file_formats?utm_source=chatgpt.com "List of file formats"))                                                                                                                                                                 |
| **`.cab`**           | Microsoft Cabinet 格式，用于系统组件和安装包的压缩归档；支持数字签名和多卷；Windows 安装程序常见。 ([维基百科](https://en.wikipedia.org/wiki/List_of_file_formats?utm_source=chatgpt.com "List of file formats"))                                                                                                                                                                         |
| **`.iso`**           | 光盘镜像文件格式，封装了完整的 CD/DVD/BD 文件系统，既可挂载为虚拟盘，也可刻录光盘；并非严格意义上的压缩，但常用作大容量数据分发。 ([维基百科](https://en.wikipedia.org/wiki/List_of_file_formats?utm_source=chatgpt.com "List of file formats"))                                                                                                                                                                 |
| **`.lzh`**           | LHA（Lempel–Ziv–Haruyasu）格式，历史上在日本及早期 Amiga/Mac 系统中流行；Windows 需安装额外插件或使用 7-Zip 等工具支持。 ([Lifewire](https://www.lifewire.com/lzh-file-2621950?utm_source=chatgpt.com "How to Open, Edit, and Convert LZH Files"))                                                                                                                                    |
<center><b>表：常见压缩包介绍</b></center>

> **提示**：选择压缩格式时，需综合考虑压缩率、速度、兼容性及是否需要加密分卷等需求；常用 ZIP 兼容性最好，7Z 和 XZ 提供更高压缩率，TAR 系列在跨平台脚本和 Linux 生态中最为常见。

除了上述压缩包格式文件扩展名之外，系统文件扩展名常见的还有以下扩展名，大致了解下就可以了。

| 扩展名             | 类别     | 描述                                                                                                                                                                                                                               |
| --------------- | ------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `.doc`, `.docx` | 文档     | Microsoft Word 文档，可包含文本、图片和图形等元素([IONOS](https://www.ionos.com/digitalguide/server/know-how/file-extension-overview/ "File extension list \| The most important file types - IONOS"))。                                           |
| `.xls`, `.xlsx` | 表格     | Microsoft Excel 电子表格，用于存储表格数据并支持公式和图表等功能([IONOS](https://www.ionos.com/digitalguide/server/know-how/file-extension-overview/ "File extension list \| The most important file types - IONOS"))。                                   |
| `.ppt`, `.pptx` | 演示文稿   | Microsoft PowerPoint 演示文稿，用于制作幻灯片演示([IONOS](https://www.ionos.com/digitalguide/server/know-how/file-extension-overview/ "File extension list \| The most important file types - IONOS"))。                                        |
| `.pdf`          | 文档     | Adobe Portable Document Format，可跨平台查看并包含文本、图像、视频等([IONOS](https://www.ionos.com/digitalguide/server/know-how/file-extension-overview/ "File extension list \| The most important file types - IONOS"))。                          |
| `.txt`          | 文本     | 纯文本文件，不包含格式信息，适合快速记录和存储日志等([IONOS](https://www.ionos.com/digitalguide/server/know-how/file-extension-overview/ "File extension list \| The most important file types - IONOS"))。                                                 |
| `.md`           | 文本     | Markdown 文档，用于轻量级标记和格式化文本([IONOS](https://www.ionos.com/digitalguide/server/know-how/file-extension-overview/ "File extension list \| The most important file types - IONOS"))。                                                  |
| `.jpg`, `.jpeg` | 图像     | JPEG 图像格式，支持高压缩比同时保持较好图像质量，常用于照片([IONOS](https://www.ionos.com/digitalguide/server/know-how/file-extension-overview/ "File extension list \| The most important file types - IONOS"))。                                           |
| `.png`          | 图像     | Portable Network Graphics，支持无损压缩和透明通道([IONOS](https://www.ionos.com/digitalguide/server/know-how/file-extension-overview/ "File extension list \| The most important file types - IONOS"))。                                      |
| `.gif`          | 图像/动画  | Graphics Interchange Format，支持帧动画和简单图形([IONOS](https://www.ionos.com/digitalguide/server/know-how/file-extension-overview/ "File extension list \| The most important file types - IONOS"))。                                     |
| `.mp3`          | 音频     | MPEG Audio Layer 3，最常见的有损压缩音频格式([IONOS](https://www.ionos.com/digitalguide/server/know-how/file-extension-overview/ "File extension list \| The most important file types - IONOS"))。                                            |
| `.wav`          | 音频     | Waveform Audio File Format，支持无损音频存储([IONOS](https://www.ionos.com/digitalguide/server/know-how/file-extension-overview/ "File extension list \| The most important file types - IONOS"))。                                        |
| `.mp4`          | 视频     | MPEG-4 Part 14，常见的视频容器格式，支持多种编码([IONOS](https://www.ionos.com/digitalguide/server/know-how/file-extension-overview/ "File extension list \| The most important file types - IONOS"))。                                            |
| `.avi`          | 视频     | Audio Video Interleave，微软开发的视频容器格式([IONOS](https://www.ionos.com/digitalguide/server/know-how/file-extension-overview/ "File extension list \| The most important file types - IONOS"))。                                         |
| `.7z`           | 压缩归档   | 7-Zip 格式，开源高压缩比归档格式([IONOS](https://www.ionos.com/digitalguide/server/know-how/file-extension-overview/ "File extension list \| The most important file types - IONOS"))。                                                        |
| `.exe`          | 可执行文件  | Windows 可执行程序文件，双击即可运行([it.nmu.edu](https://it.nmu.edu/docs/common-windows-file-extensions?utm_source=chatgpt.com "Common Windows file extensions \| Technology Support Services"))。                                             |
| `.msi`          | 可执行安装包 | Microsoft Installer 安装程序包，用于软件安装([nce.fd.org](https://nce.fd.org/sites/nce/files/seminar-docs//Common%20file%20name%20extensions%20in%20Windows.pdf?utm_source=chatgpt.com "[PDF] Common file name extensions in Windows.pdf"))。 |
| `.dll`          | 系统/库   | Dynamic Link Library，动态链接库文件，供多个程序共享([IONOS](https://www.ionos.com/digitalguide/server/know-how/file-extension-overview/ "File extension list \| The most important file types - IONOS"))。                                       |
| `.ini`          | 系统/配置  | Initialization 文件，用于存储程序或系统配置参数([IONOS](https://www.ionos.com/digitalguide/server/know-how/file-extension-overview/ "File extension list \| The most important file types - IONOS"))。                                            |
| `.bat`          | 脚本     | 批处理脚本文件，包含一系列 DOS 命令([IONOS](https://www.ionos.com/digitalguide/server/know-how/file-extension-overview/ "File extension list \| The most important file types - IONOS"))。                                                       |
| `.ps1`          | 脚本     | PowerShell 脚本文件，用于执行系统管理脚本([nce.fd.org](https://nce.fd.org/sites/nce/files/seminar-docs//Common%20file%20name%20extensions%20in%20Windows.pdf?utm_source=chatgpt.com "[PDF] Common file name extensions in Windows.pdf"))。       |
| `.iso`          | 光盘镜像   | 光盘镜像文件，可用于挂载或刻录到光盘([IONOS](https://www.ionos.com/digitalguide/server/know-how/file-extension-overview/ "File extension list \| The most important file types - IONOS"))。                                                         |
<center><b>
表：系统文件常见的扩展名后缀</b></center>

### 1.3.2. 安装软件

安装软件主要分为3个步骤：找资源-->下资源-->安到电脑上，基本上任何形式的安装都离不开这三部，所以从这一节开始会逐步锻炼你的信息检索能力——这一大学生因为手机应用市场的存在几乎丧失了的能力。

#### （1）以EXE方式安装

1. **在你的 Edge 中检索 360压缩**：
	![image.png](https://i0.hdslb.com/bfs/openplatform/03591ac1fbafd3166199666b7c4052ea8bcf4f05.png)
2. **打开网页点击立即下载**（不要点到 压缩+卫士极速版，要不然过一会电脑就360全家桶了）
	![image.png](https://i0.hdslb.com/bfs/openplatform/8c43f7259d9417e7cecef3b12f1b0dbdb621c25c.png)
	> **注意**：一定要辨别假冒、广告网页，别犯下载 STEAM 却下到盗版 STEAM 的笑话
	
3. 点击安装文件：
	![image.png](https://i0.hdslb.com/bfs/openplatform/1797cda642480252bd60e06e740f25f6c0be89be.png)
4. 点击自定义安装：
	![360压缩：安装、加密、多图压缩技巧及特色全知道](https://xaizai-fd.zol-img.com.cn/t_s800x2000/g7/M00/03/00/ChMkLGdtBsKIfggFAABmvqpLj8gAAnMDQPbZtQAAGbW526.jpg "360压缩：安装、加密、多图压缩技巧及特色全知道")
5. 点击更换目录

>	**注意**：千万不要点立即安装，所有类似“立即安装”、“一键安装”字样的选项，都是直接装 C 盘 Promgram 目录下的，时间久了 C 盘很容易满！！

6. 选中 C 盘以外的其他盘

7. 在该盘下新建一个目录：新建一个软件目录，要求是最好软件英文/或中译英，不要用中文，有些软件会因为中文文件夹报错

- # 小试牛刀
- 
	
	- 安装 360 驱动 （如果安装的版本说明搞不懂请问 AI ）
		![image.png](https://i0.hdslb.com/bfs/openplatform/5f2e90eb5d7ed51f0d95b64449e0e76e4055cc13.png)
	- 安装 WPS 
		![image.png](https://i0.hdslb.com/bfs/openplatform/fb137df12c560cc4cfe8f050f1a3e29a2acaca73.png)
	- 安装火绒安全（看不懂版本选择问AI，别瞎选）
		![image.png](https://i0.hdslb.com/bfs/openplatform/74d11503bffd64b71e0c93e4a160123c9f724ca0.png)
	- 安装360驱动：（不放图了，自己找正确的官网，以此锻炼你的信息分辨能力，我不可能每次都替你找软件并判断它是不是对的）
	

<center><b>表：AI 生成的前三个软件的简介
</b></center>

| **360压缩** | 360安全中心      | 支持42种压缩格式解压，承诺永久免费；内置360云安全引擎，可检测压缩包内木马；以快速、轻巧、兼容性好为特点                                        |
| --------- | ------------ | --------------------------------------------------------------------------------------------- |
| **WPS**   | 金山软件股份有限公司   | 主要用于文字处理、演示文稿和电子表格等办公场景                                                                       |
| **火绒安全**  | 北京火绒网络科技有限公司 | 提供病毒查杀、防护中心、访问控制等功能；自主研发新一代反病毒引擎，支持本地查杀和EDR运营体系，具备低误报率、小体积、低资源占用等特点，支持多维度防御（如U盘保护、浏览器保护等）<br> |
|           |              |                                                                                               |

#### （2）以MSI方式安装

1. **获取MSI文件​**​：从正规渠道获取软件的MSI安装文件，此处以 Blender 的安装做介绍（你看到了很多你根本不认识的名词，我这里不解释和指引，为了锻炼你的信息分析能力，你认为你应该怎么做？）
	![image.png](https://i0.hdslb.com/bfs/openplatform/3bd5ede3303021dfb6582787a898add163a5e741.png)
	如果你下载的东西是正确的话，下载的包应该是.msi后缀的，可能版本不一定对的上（教程具有时空限制）
	![image.png](https://i0.hdslb.com/bfs/openplatform/45c35cf8b8b37cb8a5822b5075686c31dda2568e.png)

>**提示**：我就知道有人会第一眼就进入到下图一所示的网站中，放心，这个网站你如果没有开梯子是下不动的，你得到国内的下载镜像站去下载对应的软件包。有些比较有名的国外软件，他在国内是有专门的网站下的。==还是那句话，如果你的操作得到了与你预期不符合的结果，或者遇到了你不知道的名词，请多问AI，不要随便问人，因为大家时间都很宝贵，只有当你确定用AI解决不了问题的时候再来问人==。

![image.png](https://i0.hdslb.com/bfs/openplatform/d279466f8eef90d4387b093f1422865c5af34a7c.png)


2. ​**​运行MSI文件​**​：双击MSI文件，Windows Installer会自动启动安装过程。
	
	点击Next（如果你看不懂，截图问AI）
	![image.png](https://i0.hdslb.com/bfs/openplatform/930168767da062f1baf50b071ea89215530d0947.png)


3. ​**​安装过程​**​：与EXE安装类似，会依次显示许可协议、安装路径选择、组件选择等界面，用户按照提示进行操作。MSI安装过程相对更加自动化和标准化，在一些企业环境中，管理员可以通过组策略等方式批量部署MSI软件。

4. ​**​完成安装​**​：安装结束后，同样可能会有启动软件的提示和快捷方式创建选项。

- # 小试牛刀
	
	- 安装 Calibre 
		![image.png](https://i0.hdslb.com/bfs/openplatform/71f0abb17c0e0a00e626c97349eadf74e68a474b.png)
	- 安装 ScreenToGif


>**提示**：如果你装错地方了，请参考卸载篇目进行卸载，或者自行学习处理这个问题，发挥自己刚学的信息检索能力、问题分析能力、AI学习能力。

#### （3）以压缩包方式安装

1. **下载和解压​**​：从指定来源下载软件的压缩包文件，使用解压软件（如WinRAR、7 - Zip等）将其解压到指定文件夹。如果是RAR格式压缩包，需要安装WinRAR等支持RAR格式的软件；如果是ZIP格式，Windows系统自带的压缩功能或7 - Zip等软件均可解压。




2. ​**​查找安装文件​**​：解压后，在解压得到的文件夹中查找安装程序（通常是EXE或MSI文件），双击运行该安装程序，后续操作与上述以EXE或MSI方式安装的步骤相同。

比如：
![](https://img.picui.cn/free/2025/05/13/6823333c34e29.png)

#### （4）以ISO镜像安装

1. 使用虚拟光驱软件（如 Daemon Tools、UltraISO 等）加载 ISO 镜像文件。

2. 加载后，虚拟光驱会模拟出一个光盘驱动器，打开该驱动器，查看是否有安装程序，运行安装程序进行安装。


#### （5）其他安装方式


### 1.3.3. 卸载软件

#### （1）用控制面板卸载

- 在 Windows 系统中，打开控制面板，找到 “程序和功能”（在不同版本的 Windows 中可能名称略有不同）。

![](https://img.picui.cn/free/2025/05/13/682333c531466.png)

- 在程序列表中找到要卸载的软件，右键点击选择 “卸载”，然后按照卸载向导提示进行操作。

![](https://img.picui.cn/free/2025/05/13/6823341fc561f.png)

#### （2）用第三方工具卸载

我们用Geek来卸载，打开后如图

![](https://img.picui.cn/free/2025/05/13/682334c2a0e7a.png)


然后右键卸载即可

![](https://img.picui.cn/free/2025/05/13/682335686e46b.png)

### 1.3.4. 创建快捷方式

>**引言**：有些时候特别是压缩包方式安装的东西，你会发现，有些解压完成后桌面不会出现图标（快捷方式），这个时候需要我们手动去创建快捷方式并且发送到桌面上，以便

- 在软件安装目录下找到软件的可执行文件（通常是 EXE 文件），右键点击该文件-->显示更多-->选择 “创建快捷方式”，这样就可以在桌面上创建软件的快捷方式。

![](https://img.picui.cn/free/2025/05/13/682335e062dc3.png)


### 1.3.5. 添加到开始菜单

>**引言**：之所以要介绍这个是因为随着电脑使用时间的变长，你们用到的软件越来越多，==**桌面会产生一半甚至整个屏幕都是文件夹快捷方式的情况**==。为了解决这个问题，下面我向大家介绍如何把软件的快捷方式固定到开始菜单上，一半添加到开始菜单的快捷方式的来源主要有以下介绍的三种。

![ed1da1ce6c8c76023e211c97581ffac.png](https://i0.hdslb.com/bfs/openplatform/21c47ee3950ceac5b8bf03c30bf7040e1d52b7bb.png)

<center><b>
图：全屏爆满的桌面</b></center>

- **在软件安装过程中添加到开始菜单**：一般安装向导会有选项询问是否创建开始菜单快捷方式，用户勾选相应选项即可。（但是不是所有的软件设计者都会放一个这样的勾选）


- **从快捷方式中添加到开始菜单**：如果在安装时没有创建，可以**右键软件快捷方式/软件可执行程序本体**-->显示更多选项-->点击固定到“开始”

	![image.png](https://i0.hdslb.com/bfs/openplatform/8d9303cd0eacc9ce3b84a57b4a35cfa0fc2fd092.png)
	![image.png](https://i0.hdslb.com/bfs/openplatform/4c3a7fe3d43cedbb14c28a73fef6aa319718cc19.png)

- **从最近添加项中固定到开始菜单**：右键推荐的项目-->固定到开始屏幕
	![image.png](https://i0.hdslb.com/bfs/openplatform/1ab19002923ef7ff3c5edd8522b0b13dcf1c189b.png)
	
	![image.png](https://i0.hdslb.com/bfs/openplatform/339c0bbb6c1b9831c16852350c86377b51c6ed8e.png)


### 1.3.6. 识别流氓下载器

**软件下载去官网，流氓软件不敢狂**  
不收费的软件求求各位，一定一定去软件官网下载。识别软件官网三步走：  
- 搜索“软件名”官网下载  
- 识别网址：官网网址一般是http：www.➕软件英文名.com  
- 官网标识：部分软件的右上角会有“官网”标识，但不是所有，主要还是看识别网址
	![](https://picx.zhimg.com/v2-069d1ddde16b6ad799169d14a069c2e7_1440w.jpg)
	![](https://pic2.zhimg.com/v2-ef5a4f9dd79914d68a322e96bd79f961_1440w.jpg)


**破解软件下载有技巧，流氓软件休想[薅羊毛](https://zhida.zhihu.com/search?content_id=224567234&content_type=Article&match_order=1&q=%E8%96%85%E7%BE%8A%E6%AF%9B&zd_token=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJ6aGlkYV9zZXJ2ZXIiLCJleHAiOjE3NDc1NDgzMzAsInEiOiLoloXnvormr5siLCJ6aGlkYV9zb3VyY2UiOiJlbnRpdHkiLCJjb250ZW50X2lkIjoyMjQ1NjcyMzQsImNvbnRlbnRfdHlwZSI6IkFydGljbGUiLCJtYXRjaF9vcmRlciI6MSwiemRfdG9rZW4iOm51bGx9.HirSrA1KWyy-3-rNpBqRlAfMmDYZWSvbUx_DinXaBDI&zhida_source=entity)**  ：部分需要破解的软件确实只有去下载“非官方”的破解版，但这也是流氓软件泛滥的地方。做到以下几点，纵向“纯净版”丝滑安装体验  

- ==“安全下载”不安全，“高速下载”不要选==：这类“诱导性”极强的按钮背后往往就是为了迎合大众心理需求所挖的“大坑”，反正记住一个选择，别人给的好处别去点！！！
  
- ==软件大小、文件看仔细，一不小心遇到“下崽器==：正常的软件后缀名一般是以RAR、zip等压缩文件格式或者其他特殊格式呈现，且文件的大小一般比较大，如果你发现即将下载的软件是EXE的后缀名，就得好好注意了，很少有软件能只靠一个EXE运行的，正规的文件大小也不可能才几百KB，这类安装包一般就是隐藏的下载器，一旦安装，那真的就安装了一窝垃圾软件了。
	![](https://pic3.zhimg.com/v2-096708e99968d65e1520ff5c19d54146_1440w.jpg)
	![](https://picx.zhimg.com/v2-39fac9eadf429c92235e53d12674a747_1440w.jpg)

如果你已经不幸中招，普通的卸载真的很难把这些垃圾软件斩草除根。下面这教你两招教你阻止所有垃圾软件自动安装。

第1步：打开设置，选择应用，找到应用和功能，将选择获取应用位置的选项更改为这个。

第2步，右键垃圾软件，打开文件所在的位置，再返回一级，将这个文件夹全部删除。
- #  小试牛刀

下载正版Steam，并完成账号注册

# 2. 进阶阶段
## 2.1. 系统使用进阶

### 2.1.1. 桌面操作进阶

*   **使用虚拟桌面**：
    *   创建和管理多个虚拟桌面，以便在不同桌面组织不同的工作内容。
    *   使用快捷键 `Win + Ctrl + D` 创建新桌面，`Win + Ctrl + ←/→` 切换桌面，`Win + Ctrl + F4` 关闭当前桌面。
    *   将不同应用程序窗口移动到不同桌面，提高工作效率。
*   **高级窗口管理**：
    *   使用 `Win + Shift + ←/→` 将当前窗口移动到其他显示器。
    *   利用窗口吸附功能，快速调整窗口大小和位置。
    *   学习使用第三方窗口管理工具，如 FancyZones，实现更灵活的窗口布局。
- **自定义桌面环境**：
    - **更换动态壁纸**：使用 Wallpaper Engine 等软件，让桌面更生动。
    - **使用 Rainmeter**：自定义桌面小工具，显示系统信息、天气、日历等。
    - **创建自定义快捷方式**：将常用文件、文件夹、网址等添加到桌面，方便快速访问。
    - **使用启动器**：例如 Listary、Wox 等，通过键盘快速启动应用程序和搜索文件。
- **优化桌面性能**：
    - **减少桌面图标数量**：避免桌面图标过多，影响系统性能。
    - **关闭不必要的视觉效果**：在“系统属性”中调整视觉效果，提高桌面响应速度。
    - **定期清理桌面文件**：将不常用的文件移动到其他文件夹，保持桌面整洁。

### 2.1.2. 资源管理器进阶

*   **使用磁盘清理工具**
    *   打开磁盘清理工具，选择要清理的驱动器。
    *   勾选要清理的文件类型，如临时文件、回收站等。
    *   清理系统文件，删除旧的 Windows 更新文件。
*   **清理临时文件**
    *   手动删除 `C:\Windows\Temp` 目录下的文件。
    *   使用 `%temp%` 快捷方式打开用户临时文件夹，删除其中的文件。
*   **高级搜索技巧**：
    *   使用通配符 `*` 和 `?` 进行模糊搜索。
    *   使用 `size:`、`date:` 等关键词进行高级搜索，例如 `size:>100MB` 搜索大于 100MB 的文件。
    *   保存常用搜索条件，方便以后快速查找。
*   **自定义文件夹选项**：
    *   修改文件夹视图，例如显示详细信息、图标大小等。
    *   更改默认打开方式，例如将图片默认使用 IrfanView 打开。
    *   设置文件夹权限，保护重要文件。

### 2.1.3. 终端使用入门
*   **基本命令**：
    *   `cd`：切换目录。
    *   `dir`（或 `ls`）：列出目录内容。
    *   `mkdir`：创建目录。
    *   `rmdir`：删除目录。
    *   `copy`：复制文件。
    *   `move`：移动文件。
    *   `del`：删除文件。
*   **常用命令**（如ipconfig, ping, tracert）：
    *   `ipconfig`：查看网络配置信息。
    *   `ping`：测试网络连接。
    *   `tracert`：跟踪路由。
*   **管道和重定向**：
    *   使用 `|` 将一个命令的输出作为另一个命令的输入。
    *   使用 `>` 将命令输出重定向到文件。
    *   使用 `<` 将文件内容作为命令输入。
*   **批处理脚本**：
    *   编写简单的 `.bat` 批处理脚本，自动化常用任务。
    *   学习使用 `for`、`if` 等控制结构，实现更复杂的逻辑。

请注意，这只是对进阶阶段的补充，每个小节的具体内容还需要进一步完善。



## 2.2. 浏览器使用进阶

### 2.2.1. 插件功能

>**引言**：我发现很多人用浏览器都只用了一点，很多人都不知道有插件这个东西，事实上，插件这个功能基本上每一个大一点的国外软件都有，插件是为了对原来软件的功能进行补充而存在的。下面我简单介绍 Edge 的插件功能。
>
>插件的使用主要步骤：安装插件-->配置插件。插件的安装主要有两种方法：在线安装法以及离线安装法则，下面来依次进行介绍。而配置插件的方法因插件而异，因为STA能力要求中有一条自学能力在这里我就提一提一笔带过，仅给你们展示有这个信息就可以了。

- 在线安装法
	1. 打开edge浏览器，点击右上角头像右侧的【更多 – 扩展】进入添加插件页面。
	![](https://pica.zhimg.com/v2-f3d6ea617afdc85ef175e695c560e18e_1440w.jpg)
	2. 进入扩展页面后，如果我们已经下载好了插件到电脑中，开启左下角的【开发人员模式】，然后点击【加载解压缩的扩展】，然后选择并打开下载好的插件即可。
	![](https://picx.zhimg.com/v2-d91ccbb27ac4ee53aeef3382f0f2895b_1440w.jpg)
	3. 我们还可以进入[Microsoft商店](https://zhida.zhihu.com/search?content_id=213119845&content_type=Article&match_order=1&q=Microsoft%E5%95%86%E5%BA%97&zd_token=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJ6aGlkYV9zZXJ2ZXIiLCJleHAiOjE3NDc1NDg4MDAsInEiOiJNaWNyb3NvZnTllYblupciLCJ6aGlkYV9zb3VyY2UiOiJlbnRpdHkiLCJjb250ZW50X2lkIjoyMTMxMTk4NDUsImNvbnRlbnRfdHlwZSI6IkFydGljbGUiLCJtYXRjaF9vcmRlciI6MSwiemRfdG9rZW4iOm51bGx9.B-TFS7mmKJUHzXC-PbptqsB7fwG7khuKQurf0KNvzbM&zhida_source=entity)中搜索下载插件，点击【获取Microsoft edge扩展程序】进入Microsoft edge外接程序。
	![](https://pic4.zhimg.com/v2-eaa328e52d0f8d86d37ed2176232c23b_1440w.jpg)
	4. 点击左上角的搜索框，搜索插件名称或者需要实现的功能，搜索之后在右侧找到需要下载的扩展程序，点击【获取】。
	![](https://picx.zhimg.com/v2-b5dec33aa94d713f7f87f0c0eebaf1a5_1440w.jpg)
	5. 之后会在上方的地址栏下弹出提示窗口，提示我们是否“将XXX添加到Microsoft edge”，点击【添加扩展】。
	![](https://pic3.zhimg.com/v2-32d73fe669c78fdf80851a6e211028c4_1440w.jpg)
	6. 最后，该插件下载并安装之后，会自动开启该插件，并在上方地址栏的右侧显示该插件的图标，点击即可使用。
	![](https://pic3.zhimg.com/v2-ce8a872a22fdb26de2ad90b2882d418c_1440w.jpg)
	



- 离线安装法
	　1. 我们首先要打开edge浏览器，然后在浏览器的界面中点击右上角的【…】省略号，点击进入菜单界面。
		![](https://pic2.zhimg.com/v2-d709bd86b64edd63585ca5249001bd1b_1440w.jpg)
	2. 在菜单界面可以看到最下面有【扩展】的功能选择，点击扩展进入到扩展界面。
		![image.png](https://i0.hdslb.com/bfs/openplatform/b8a0dba8f3d6452a217b77ff2bfa91b7dfc1d530.png)
	3. 在扩展界面我们可以看到有一个选项【从应用商店获取扩展】，点击进入，（注：Edge浏览器的扩展不能从别的地方下载，只能来源于官方的应用商店，但是也有方法可以安装，请接续向下看）。
		![](https://pic4.zhimg.com/v2-684722a4bd774e25890dd7a6adfb0f61_1440w.jpg)
	4. 而我们需要通过加载解压缩文件的方式，来安装三方扩展，方法就是将下载好的crx扩展文件，进行压缩再解压，或者使用压缩软件「[7-Zip](https://zhida.zhihu.com/search?content_id=213119845&content_type=Article&match_order=1&q=7-Zip&zd_token=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJ6aGlkYV9zZXJ2ZXIiLCJleHAiOjE3NDc1NDg4MDAsInEiOiI3LVppcCIsInpoaWRhX3NvdXJjZSI6ImVudGl0eSIsImNvbnRlbnRfaWQiOjIxMzExOTg0NSwiY29udGVudF90eXBlIjoiQXJ0aWNsZSIsIm1hdGNoX29yZGVyIjoxLCJ6ZF90b2tlbiI6bnVsbH0.HhnN-u1NNxAqRMgBrRilYKW-iHkBQiJ7Bu8CeUiiEYg&zhida_source=entity)」，直接提取文件，才能安装成功。
	![动图封面](https://picx.zhimg.com/v2-c416810150e9376d6b337dc25fca5b9f_b.jpg)
	5. 将「Goole翻译」的CRX的文件，转移到Edge拓展应用文件夹内，然后将文件的后缀名改为ZIP压缩文件，然后再解压。如果你电脑有安装有7ZIP的话，就不用这么麻烦，直接右键提取该文件即可。
	![](https://pica.zhimg.com/v2-1686cddd9aae1f5d70cb6b8b263bd5f2_1440w.jpg)
　　6. 在拓展页面我们需要打开「开发人员模式」和「允许来自**拓展」，才能安装外来的拓展应用，一切准备工作就绪，最后只需加载上面解压的文件，即可完成最后的程序安装。

	![image.png](https://i0.hdslb.com/bfs/openplatform/d77b996dca9ea0a6e9c7658f8e60b2fd6755ef49.png)
	![image.png](https://i0.hdslb.com/bfs/openplatform/fcfceed500c1b76c26d4cfec96581abfa6c79d16.png)
	
	![动图封面](https://picx.zhimg.com/v2-3efd8828b8bfe5c7e5f48a711eab7e87_b.jpg)
	
	
- 让插件显示到顶部栏上：如图，依次点击插件图标和相应的置顶按钮就能把插件显式的凸显出来方便点击和查看（说实话，我发现大部分都没有到处点点点的好奇心，这些都是我瞎点发现的，我希望你们去培养自己的这种好奇心，因为这就是创新能力的来源）

![image.png](https://i0.hdslb.com/bfs/openplatform/c481403e184c310800ffbde38ee80f01c3905ccb.png)


- 对插件进行详细设置：点击每个安装的插件，你发现他都是有一定选项的（如下图），那些选项怎么调整会产生什么样的功能，还请你们自己动动手去满足下自己的好奇心，此处我就不多说了

![image.png](https://i0.hdslb.com/bfs/openplatform/d034239e06e409641683dd3b2b30e8529324ab07.png)

如果你学会了上面两种方法的话可以依次安装以下插件，然后我们再来介绍每一个插件是拿来做什么用的，以及怎么用。（事实上这些东西都可以自己找到，只要有关键词，我就可以把这个关键词背后涉及到的所有东西全部找到，这就是信息检索分析能力到一定程度才能做到的。）

- #  小试牛刀

你已经学会如何安装扩展了，下面把这些扩展都安装好吧！这些扩展的作用和说明都在下面了

![image.png](https://i0.hdslb.com/bfs/openplatform/4763f0895d30f96351e9490d9a9b025b0854c0f1.png)
![image.png](https://i0.hdslb.com/bfs/openplatform/f40d6b5079d7c7eb2f9c405f0bc45c1468552053.png)
![image.png](https://i0.hdslb.com/bfs/openplatform/cd1f4011ee6c15f37a14d2c715aee4954f5e817d.png)
![image.png](https://i0.hdslb.com/bfs/openplatform/a619dc2dbae0855769478fca6d9630255f9db935.png)
![image.png](https://i0.hdslb.com/bfs/openplatform/f21e4f345c1952e30e8a56465c20dbdf8f262a40.png)

| 插件名称                               | 功能描述                                                                                                    | 使用                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| ---------------------------------- | ------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| iTab New Tab                       | 提供个性化新标签页，包含日历、天气、新闻、壁纸等小部件                                                                             | [Edge浏览器之主页布局神器——iTab： - 知乎](https://zhuanlan.zhihu.com/p/565032836)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| 万能复制                               | 解除网页限制，允许复制、选择、粘贴被禁止的内容                                                                                 | [万能复制神器，在不能复制文字的网页照常复制：Simple Allow Copy - 知乎](https://zhuanlan.zhihu.com/p/301091959)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| 大学搜题酱插件                            | 大学搜题酱插件是由作业帮官方开发的一款支持电脑端框选截屏的搜题工具，无论是网课答案还是教材习题，截选题目后答案解析即刻展现！搜题服务完全免费，答案精准全面，快来体验吧~~~                  | 无网友教程，自己摸索使用                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| AdBlock — block ads across the web | 免费拦截YouTube和常用网站广告                                                                                      | 入门的话安装完就行，不需要教程                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| AdGuard AdBlocker                  | 强力广告拦截器，支持Facebook、YouTube等平台                                                                           | 入门的话安装完就行，不需要教程                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| Dark Reader                        | 为所有网站启用暗黑模式，保护眼睛                                                                                        | [说明 – Dark Reader](https://darkreader.org/help/zh-CN/)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| 网页图片批量下载器-图片助手(ImageAssistant)     | 批量下载网页图片的图像提取工具                                                                                         | [网页图片批量下载器-图片助手(ImageAssistant)扩展插件 - 知乎](https://zhuanlan.zhihu.com/p/351628654)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| 沉浸式翻译                              | 支持网页、PDF、电子书翻译及视频字幕双语显示                                                                                 | [快速开始 \| 沉浸式翻译](https://immersivetranslate.com/zh-Hans/docs/usage/)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| 五彩 - 网页划线高亮工具                      | 在可任意网页划线、高亮和批注，支持无限层级标签，支持网页剪藏。非常方便的效率工具，能有效提升学习和工作效率，节约更多时间。                                           | [在任意网页划重点做笔记，功能强大！ - 知乎](https://zhuanlan.zhihu.com/p/666160253)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| Tampermonkey                       | 用户脚本管理器，可自定义网页行为                                                                                        | [Tampermonkey篡改猴官网，油猴脚本插件使用教程 - 知乎](https://zhuanlan.zhihu.com/p/28221024353#:~:text=Tampermonkey%E7%AF%A1%E6%94%B9%E7%8C%B4%E4%BD%BF%E7%94%A8%E6%AD%A5%E9%AA%A4%201%20%E5%AE%89%E8%A3%85%E6%89%A9%E5%B1%95%EF%BC%9A%E5%9C%A8Chrome%E3%80%81Firefox%E3%80%81Edge%E7%AD%89%E6%B5%8F%E8%A7%88%E5%99%A8%E7%9A%84%E6%89%A9%E5%B1%95%E5%95%86%E5%BA%97%E6%90%9C%E7%B4%A2%E2%80%9CTampermonkey%E2%80%9D%EF%BC%8C%E7%82%B9%E5%87%BB%E5%AE%89%E8%A3%85%E6%8C%89%E9%92%AE%E5%8D%B3%E5%8F%AF%E5%AE%8C%E6%88%90%E3%80%82%20%E5%AE%89%E8%A3%85%E5%90%8E%E6%B5%8F%E8%A7%88%E5%99%A8%E5%B7%A5%E5%85%B7%E6%A0%8F%E4%BC%9A%E6%98%BE%E7%A4%BA%E7%8C%B4%E5%AD%90%E5%9B%BE%E3%80%82%202%20%E6%B7%BB%E5%8A%A0%E8%84%9A%E6%9C%AC%EF%BC%9A%E5%9C%A8%E7%BA%BF%E5%AE%89%E8%A3%85%EF%BC%9A%E8%AE%BF%E9%97%AEGreasy%20Fork%E7%AD%89%E8%84%9A%E6%9C%AC%E5%BA%93%EF%BC%8C%E7%82%B9%E5%87%BB%E2%80%9C%E5%AE%89%E8%A3%85%E2%80%9D%E6%8C%89%E9%92%AE%E5%8D%B3%E5%8F%AF%E8%87%AA%E5%8A%A8%E8%BD%BD%E5%85%A5%E3%80%82%20%E4%BE%8B%E5%A6%82%E2%80%9C%E6%9F%90%E7%93%A3%E8%B5%84%E6%BA%90%E4%B8%8B%E8%BD%BD%E5%A4%A7%E5%B8%88%E2%80%9D%E8%84%9A%E6%9C%AC%E5%8F%AF%E5%AE%9E%E7%8E%B0%E4%B8%80%E9%94%AE%E8%A7%A3%E6%9E%90%E4%B8%8B%E8%BD%BD%E9%93%BE%E6%8E%A5%E3%80%82,%E6%9C%AC%E5%9C%B0%E5%AF%BC%E5%85%A5%EF%BC%9A%E9%80%9A%E8%BF%87Tampermonkey%E4%BB%AA%E8%A1%A8%E7%9B%98%E7%9A%84%E2%80%9C%E5%AE%9E%E7%94%A8%E5%B7%A5%E5%85%B7%E2%86%92%E6%96%87%E4%BB%B6%E2%86%92%E5%AE%89%E8%A3%85%E2%80%9D%E4%B8%8A%E4%BC%A0%E6%9C%AC%E5%9C%B0%E8%84%9A%E6%9C%AC%E6%96%87%E4%BB%B6%E3%80%82%203%20%E7%AE%A1%E7%90%86%E4%B8%8E%E8%B0%83%E8%AF%95%EF%BC%9A%E7%82%B9%E5%87%BB%E6%89%A9%E5%B1%95%E5%9B%BE%E6%A0%87%E5%8F%AF%E6%9F%A5%E7%9C%8B%E5%BD%93%E5%89%8D%E9%A1%B5%E9%9D%A2%E7%94%9F%E6%95%88%E7%9A%84%E8%84%9A%E6%9C%AC%EF%BC%8C%E8%BF%9B%E5%85%A5%E4%BB%AA%E8%A1%A8%E7%9B%98%E5%8F%AF%E6%89%B9%E9%87%8F%E5%90%AF%E7%94%A8%2F%E7%A6%81%E7%94%A8%E6%88%96%E7%BC%96%E8%BE%91%E8%84%9A%E6%9C%AC%E3%80%82%20%E8%8B%A5%E9%81%87%E8%84%9A%E6%9C%AC%E5%86%B2%E7%AA%81%EF%BC%8C%E5%8F%AF%E9%80%9A%E8%BF%87%E2%80%9C%E8%84%9A%E6%9C%AC%E6%A3%80%E6%9F%A5%E5%99%A8%E2%80%9D%E5%AE%9A%E4%BD%8D%E9%97%AE%E9%A2%98%E4%BB%A3%E7%A0%81%E3%80%82%20%E5%BC%80%E5%8F%91%E8%80%85%E5%8F%AF%E5%88%A9%E7%94%A8%40match%E5%8F%82%E6%95%B0%E9%99%90%E5%AE%9A%E8%84%9A%E6%9C%AC%E4%BD%9C%E7%94%A8%E5%9F%9F%E5%90%8D%EF%BC%8C%E4%BD%BF%E7%94%A8%20GM_%2A%20API%20%E5%AE%89%E5%85%A8%E8%B0%83%E7%94%A8%E6%B5%8F%E8%A7%88%E5%99%A8%E5%8A%9F%E8%83%BD%E3%80%82) |
| 极客侧边栏                              | 免费好用的AI侧边栏,有着DeepSeek-R1满血联网版、Qwen3以及众多顶尖模型加持,支持书签云端同步管理、AI智能分类、网页总结、文档分析、AI绘图、网页截图、书签查重、书签有效性检测等众多实用功能 | [极客侧边栏 - 入门教程 - 飞书云文档](https://icnz60awc799.feishu.cn/wiki/HNXYwCMENiqN2DkncH9clwLAnBh)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |

**说明**：  
- 表格汇总了各插件的核心功能与版本信息，部分插件ID因长度过长未完全展示。  
- 操作按钮（如`Details`/`Remove`）在实际使用中可通过浏览器扩展管理页面访问。


>**注意**：上述插件都是能在插件市场被直接搜到的，下面布置一个不能直接搜到需要用离线法安装的插件，至于如何安装，自己找信息和教程。


![image.png](https://i0.hdslb.com/bfs/openplatform/a264d6a2943650b17a593d2cfe925d14041cef6a.png)

如下图所示，其最主要的作用就是改变网页版 B 站的显示效果，这样的话网页版 B 站的使用体验会上升一大截，详情见[因为B站网页端太拉，有人做了一款插件吊打官方 - 知乎](https://zhuanlan.zhihu.com/p/690166592)

![image.png](https://i0.hdslb.com/bfs/openplatform/d32d21e49179f66989233c5038c06abe0e4b0b80.png)

![image.png](https://i0.hdslb.com/bfs/openplatform/05679e94b7d44c4cfe70ad4aa94c76e49c0c0d8b.png)

如果你安装好了的话，在我的扩展页面你能看到如下图所示的条目

![image.png](https://i0.hdslb.com/bfs/openplatform/8020b567af5346b93a7195795d68c4edb65d4c57.png)


### 2.2.2. 调整设置

#### （1）调整边栏


#### （2）调整外观


#### （3）启用 IE 浏览

1. 打开设置-->切换到默认浏览器选项卡

![image.png](https://i0.hdslb.com/bfs/openplatform/2fad68f6bec818c9ba957f5ac39a2791f06fb882.png)

2. “允许在 Internet Explorer 模式下重新加载网站”开关。随后重启浏览器，IE 模式即可开启

![image.png](https://i0.hdslb.com/bfs/openplatform/dc60bd1f49bce39feb8023afd77c077c24725894.png)

3. 点击浏览器设置-->点击外观-->找到 Internet Explorer 模式按钮-->开启按钮

![image.png](https://i0.hdslb.com/bfs/openplatform/b2cc0101fcf40bd6a88db524c279071acaeba748.png)

4. 看到浏览器右上角出现了一个灰色的 IE 图标按钮

![image.png](https://i0.hdslb.com/bfs/openplatform/c2f08938a0dbd7111a28260ebec39ace856d7f46.png)

5. 打开 [4399小游戏](https://www.4399.com/) 网站，验证 IE 选项是否工作正常

![image.png](https://i0.hdslb.com/bfs/openplatform/1b761435b59ac7cc60bb505ccfdd48c5065692e9.png)

6. 点击右上角变色的 IE 图标，切换成 IE 内核模式进行加载

![image.png](https://i0.hdslb.com/bfs/openplatform/7535e9c9b693170c59a0b1b669c3754528a3b84b.png)

7. 如果你的界面变成如下效果，那么说明 IE 模式起作用了

![image.png](https://i0.hdslb.com/bfs/openplatform/2b44f06a4ef0581259a215eca74f25d00590139b.png)

### 2.2.3. 垂直标签页

>**引言**：或许有人会觉得下图一所示的标签页显示方式占用的屏幕面积比较多，有没有其他的标签页显示方式？答案是下图二所示的垂直标签页显示方式

![image.png](https://i0.hdslb.com/bfs/openplatform/435d6683bea06062984d2656e0a6e5bda19fed47.png)

![image.png](https://i0.hdslb.com/bfs/openplatform/a25338d57d1f6605ccf17e9ec1defcfcb2a27e4b.png)


1. 右键顶部标签栏-->点击打开垂直标签页

![image.png](https://i0.hdslb.com/bfs/openplatform/6c791647c4d6436e130aa9b4f4d252d0481d22d5.png)

2. 然后预览标签页预览效果如下

![image.png](https://i0.hdslb.com/bfs/openplatform/4d487fcea141e1c8f47fdfe8706b28b916fe4981.png)

3. 如果你觉得不喜欢垂直标签页，点击如下图所示的按钮关闭垂直标签页

![image.png](https://i0.hdslb.com/bfs/openplatform/0ea9db4269d7b97ac80516189df10937260c5e16.png)

### 2.2.4. 标签工作组

>**引言**：假设你打开了如下图一这么多关于 ESIM 的文章的网页，这个时候在开启垂直标签页的时候一旦鼠标脱离了标签栏就变成了下图二的样子。你发现你没办法通过图标一眼看出来哪些标签是关于 ESIM 介绍的，这个时候标签工作组的作用就体现了——将描述同类事务的网页归纳成一个可被管理的组。

![image.png](https://i0.hdslb.com/bfs/openplatform/78c91aae473625dd6b54923eef98c8b8dddd92ad.png)

![image.png](https://i0.hdslb.com/bfs/openplatform/cff383e026fc591accdc0af7bdef5882a62e46ae.png)


1. 将其中一个标签页往下拖，使其慢慢靠近下方标签页

![image.png](https://i0.hdslb.com/bfs/openplatform/8ab5d5828f11a1b9148a37f2742ed13067064fc4.png)

2. 待到两个标签页变色时松手，发现就会变成下图所示样

![image.png](https://i0.hdslb.com/bfs/openplatform/d23ef8b5e87f44b1f5c19720e2f75eacf46c030e.png)

3. 这个时候我们再把其他的标签页往里面拖

![image.png](https://i0.hdslb.com/bfs/openplatform/57ea765f2ae67d0663c919551383bc5f6399b486.png)

4. 发现其也加入到名为 Sim Cards 的标签组中了，其他标签同理

![image.png](https://i0.hdslb.com/bfs/openplatform/2420175d22178f93085b344bd48a8b8a246c2cb6.png)


5. 点击图中所示处，可以折叠该标签组

![image.png](https://i0.hdslb.com/bfs/openplatform/e60a06ef3d1f4082a10b363e61f501e22672a08b.png)

![image.png](https://i0.hdslb.com/bfs/openplatform/015d8de4e7ea8f42a812c9c6b6cd3636e8bc43df.png)

6. 然后可以按住该标签组，自由的拖动其位置

![image.png](https://i0.hdslb.com/bfs/openplatform/83d98d335de6085a8aafe9d8ba7e3766698210b4.png)

这样当你的标签页多的和下图一样发麻的时候，你就能用这个方法把你的标签页给他压缩起来以求整洁

![image.png](https://i0.hdslb.com/bfs/openplatform/e54b27caddd40882d39a56b8434b04d1bb8717b4.png)

![image.png](https://i0.hdslb.com/bfs/openplatform/d7fbe84c3807790c9ebffd1693356e4fcc2f9565.png)

当然，一般垂直标签页的时候用的比较少，因为垂直标签页一个标签的宽就那么些。

### 2.2.5. 页任务管理器

>**引言**：网页也是有任务管理器的，不过它的作用是监控每一个页面的资源消耗情况，有些时候某些3A网页比较吃性能，但是当你开了几个同类型的时候你判断不了哪个更吃性能，所以就需要借助页面任务管理器来进行判断了。

1. 右键顶部标签页空白处-->点击浏览器任务管理器

![image.png](https://i0.hdslb.com/bfs/openplatform/73255dd0822920a5022a9ba81fc4dafab98095ed.png)

2. 查看目前打开的浏览器任务以及资源开销情况

![image.png](https://i0.hdslb.com/bfs/openplatform/9c0415d628d87ce5d2b9a5811b33dc81122d3354.png)

3. 结束高占用的浏览器页面进程（可选）

![image.png](https://i0.hdslb.com/bfs/openplatform/b24f5cf0e73f63e86be34235d0d22b23ef029ab4.png)

### 2.2.6. 浏览器工作区

>**引言**：[^6]借助边缘工作区，可以轻松地将团队放在同一页上。 已加入工作区的任何人都可以查看同一组选项卡、收藏夹和历史记录并与之交互。   

邀请其他人加入你的工作区：

1. 在 Microsoft Edge 中，通过选择浏览器窗口左上角的 **“工作区”菜单** 并选择要打开的工作区，转到要共享的工作区。 你的 Edge 工作区将在新的浏览器窗口中打开。 
    
2. 选择工作区浏览器窗口右上角的**“邀请**”，然后选择“ **复制链接**”。  
      
    ![邀请其他人加入你的 Edge 工作区。](https://support.microsoft.com/images/zh-cn/d71d4295-d2d1-4e9f-a930-ec1e9259937c)
    
3. 将此链接发送给要邀请的人员。
    


- ### Edge 工作区共享的内容：

- 实时显示其选项卡、收藏夹和历史记录。
    
- 组成员的个人资料图片，指示他们在使用 Edge 工作区时所在的选项卡。
    

- ### Edge 工作区不共享的内容：

- 你的登录名、密码、下载、集合、扩展或 Cookie。
    
- 个人浏览器设置，例如外观或搜索引擎。
    
- 来自边缘工作区外部的任何选项卡或数据。
    
- 只有你有权访问的网站内容-例如，如果你在共享工作区中登录到电子邮件，则只有你会看到你的电子邮件内容。
    
- 你的屏幕 - 共享边缘工作区的组成员将看不到你如何与打开的网页交互。 
    

除了这些功能，Edge 工作区的行为类似于标准 Microsoft Edge 浏览器窗口。  若要了解详细信息，请访问



1. 选择 Microsoft Edge 浏览器窗口左上角的 **“工作区”菜单** ，然后选择“**新建** ”以开始使用第一个 Edge 工作区。  
      
      
      
    ![在 Microsoft Edge 上创建 Edge 工作区。](https://support.microsoft.com/images/zh-cn/491db792-e45d-4356-b873-c084f97306a9) 若要创建其他工作区，请选择**工作区**右侧的 加号。   
      
    ![在 Microsoft Edge 工作区中创建更多工作区。](https://support.microsoft.com/images/zh-cn/0c3136fb-6333-4344-9696-ab487c8056e3)
    
2. 为其指定名称，选择颜色，然后选择“ **完成**”，新工作区将在新的浏览器窗口中打开。    
      
    ![在 Microsoft Edge 工作区中自定义工作区的名称和颜色。](https://support.microsoft.com/images/zh-cn/a2757bb5-bd15-493e-8004-bc13855e9207)
    
3. 开始打开要包含在工作区中的选项卡。
    
    **提示:** 以后始终可以通过选择 **“工作区”菜单** > **“编辑工作区**”来更改颜色或名称，输入名称并选择工作区所需的颜色，然后选择“ **完成**”。

## 2.3. 系统设置进阶
### 2.3.1. 调整任务栏

#### （1）任务栏居中
第一次启动 Windows 11 操作系统时，你可能已经注意到一个最明显的变化，即：桌面底部任务栏图标已经默认不再居左显示，而是位于**中间位置**。

![windows 11 开始菜单](https://img.sysgeek.cn/img/2023/02/windows-11-taskbar-customize-2.jpg)

Windows 11 任务栏默认居中显示

在 Windows 11 中任务栏图标有如下两种对齐方式：

- 靠左
- 居中

因为时间、日期和系统图标位于任务栏最右侧，所以无法靠右。

你是否希望将「开始」菜单和应用程序图标还原到像 Windows 10 那样的靠左位置？这个操作很简单：

1右击任务栏空白处——在弹出窗口中点击「任务栏设置」按钮

![windows 11 任务栏](https://img.sysgeek.cn/img/2023/02/windows-11-taskbar-customize-3.jpg)

选择「任务栏设置」

2在任务栏设置窗口中，向下滚动到「任务栏行为」部分，将「任务栏对齐方式」更改为「靠左」

![Windows 11 任务栏行为](https://img.sysgeek.cn/img/2023/02/windows-11-taskbar-customize-4.jpg)

设置「任务栏对齐方式」

3更改设置后，可以看到「开始」菜单和所有任务栏图标现在都对齐在任务栏的左侧。

![Windows 11 任务栏左侧对齐](https://img.sysgeek.cn/img/2023/02/windows-11-taskbar-customize-5.jpg)

「开始」菜单和图标左侧对齐

#### （2）自动隐藏任务栏

与之前的 Windows 版本一样，Windows 11 的任务栏也可以设置为自动隐藏：

1右击任务栏空白处——在弹出窗口中点击「任务栏设置」按钮

![windows 11 任务栏](https://img.sysgeek.cn/img/2023/02/windows-11-taskbar-customize-3.jpg)

选择「任务栏设置」

2在任务栏设置窗口中，向下滚动到「任务栏行为」部分，勾选「自动隐藏任务栏」即可。

![Windows 11 任务栏对齐方式](https://img.sysgeek.cn/img/2023/02/windows-11-taskbar-customize-6.jpg)

自动隐藏任务栏

#### （3）自定义任务栏图标

##### 1）移除任务栏默认图标

默认情况下，任务栏上有一些固定的功能图标是无法通过「右击」——「从任务栏取消固定」来移除的，需要通过：

1右击任务栏空白处——在弹出窗口中点击「任务栏设置」按钮

![windows 11 任务栏](https://img.sysgeek.cn/img/2023/02/windows-11-taskbar-customize-3.jpg)

选择「任务栏设置」

2在「任务栏项」区域中你可以选择「搜索」「任务视图」「小组件」和「聊天」这些项目是否出现在任务栏中。

![Windows 11 任务栏项](https://img.sysgeek.cn/img/2023/02/windows-11-taskbar-customize-7.jpg)

Windows 11 任务栏项

##### 2）将应用图标固定到任务栏

1我们可以在开始菜单中搜索任意应用程序，再通过「右击」——「固定到任务栏」的方式将任意应用程序图标固定到任务栏；

![将图标固定到 Windows 11 任务栏](https://img.sysgeek.cn/img/2023/02/windows-11-taskbar-customize-8.jpg)

固定到任务栏

2也可以直接将应用程序图标拖到任务栏图标位置达到相同目的，Windows 11 version 21H2可能无效。

##### 2）隐藏/显示系统托盘图标

1右击任务栏空白处——在弹出窗口中点击「任务栏设置」按钮

![windows 11 任务栏](https://img.sysgeek.cn/img/2023/02/windows-11-taskbar-customize-3.jpg)

选择「任务栏设置」

2在「系统托盘图标」区域中你可以选择，是否是要在系统托盘中要显示「笔菜单」「触摸键盘」「小组件」和「虚拟触摸板」图标

![控制 Windows 11 系统托盘图标](https://img.sysgeek.cn/img/2023/02/windows-11-taskbar-customize-9.jpg)

控制 Windows 11 系统托盘图标

3「其它系统托盘图标」部分，还可以对「Windows 更新状态」「安全删除软件硬件并弹出媒体」「Windows 安全通知图标」等 Windows 功能，及「VMware Tools」等第三方功能的图标进行控制

![Windows 11 其它系统托盘图标](https://img.sysgeek.cn/img/2023/02/windows-11-taskbar-customize-10.jpg)

控制其它系统托盘图标

4向下滚动到「任务栏行为」还可以对更多任务栏的行为和操作方式进行人性化微调和控制。

#### （4）自定义任务栏颜色和透明度

任务栏的颜色取决于用户选择的 Windows 主题，即「深色」或「浅色」模式。我们也可以手动将任务栏指定为几乎任何颜色：

使用Windows + I快捷键打开「设置」——「个性化」——「颜色」选项

![Windows 11 个性化](https://img.sysgeek.cn/img/2023/02/windows-11-taskbar-customize-11.jpg)

任务栏颜色和透明效果控制

在这里我们可以：

- 通过下拉列表选择 Windows 系统使用「浅色」「深色」甚至「自定义」外观模式
- 通过「透明效果」开关来控制窗口或表面的半透明显示
- 选择或指定开始菜单和任务栏上的重点颜色，以及标题和窗口边框上显示的强调色


### 2.3.2. 调整开始菜单

Windows 11 带来了全新设计的「开始」菜单，不仅抛弃了之前的动态磁贴，转向更加简洁的图标，还新增了一个「推荐的项目」区域，占据了「开始」菜单一半的版面空间。

这个「推荐的项目」区域主要展示两个方面的内容：

- 新安装的应用程序
- 最近使用或下载的文件

虽然它能帮助你快速访问这些内容，但也占据了过多的「开始」菜单空间，甚至可能无意中暴露个人隐私。如果你不想要这个推荐内容，可以通过以下方法来调整「推荐的项目」区域。



在 Windows 11 的「设置」中，你可以选择「推荐的项目」显示哪些内容。操作步骤如下：

1使用`Windows + I`快捷键打开「设置」。

2依次打开「个性化」>「开始」。

3在这里，你会看到以下 3 个选项，请根据需要开启或关闭：

- **显示最近添加的应用**：默认开启，控制显示新安装的应用程序。
- **显示最常用的应用**：默认关闭，控制显示经常访问的应用程序。
- **在开始、跳转列表和文件资源管理器中显示最近打开的项目**：默认开启，控制显示最近访问的文件和文件夹。

关闭所有选项后，「推荐」区域仍会显示，但所占比例会缩小。

![Windows 设置：个性化](https://img.sysgeek.cn/img/2024/03/windows-11-start-recommended-p2.jpg)

通过「设置」开关控制「推荐的项目」要显示的内容

4（可选）在页面顶部的「布局」方式下，可以选择「更多固定项」来压缩「推荐」区域的大小。


### 2.3.3. 调整播放设备

#### （1）调整应用音频

>**引言**：相信大家都会遇到想要调整某个应用的音频，比如说你在打微信电话时同时想要小声的听音乐，这个时候就需要对音乐应用进行独立的音频增益调整了。

1. 首先搜索并点击进入“设置”功能
    ![win11如何调节不同应用的声音大小？](https://exp-picture.cdn.bcebos.com/def3c219ce2c5b1b26ffba6b2b39131fcfec0eb8.jpg?x-bce-process=image%2Fresize%2Cm_lfit%2Cw_500%2Climit_1%2Fformat%2Cf_auto%2Fquality%2Cq_80)
    
2. 之后点击进入左侧列表的“系统”
    ![win11如何调节不同应用的声音大小？](https://exp-picture.cdn.bcebos.com/92dd32f7dfb2dc19f80d15ac95def4dca13910b8.jpg?x-bce-process=image%2Fresize%2Cm_lfit%2Cw_500%2Climit_1%2Fformat%2Cf_auto%2Fquality%2Cq_80)
    
3. 其次点击进入箭头所指的“声音”
    ![win11如何调节不同应用的声音大小？](https://exp-picture.cdn.bcebos.com/2db6c1b2dc19ce2c6c3a50697fdca039121f11b8.jpg?x-bce-process=image%2Fresize%2Cm_lfit%2Cw_500%2Climit_1%2Fformat%2Cf_auto%2Fquality%2Cq_80)
    
4. 然后点击进入“声音合成器”
    ![win11如何调节不同应用的声音大小？](https://exp-picture.cdn.bcebos.com/dd58d02c5b1b1edecdfdee8e981fceecd2d90fb8.jpg?x-bce-process=image%2Fresize%2Cm_lfit%2Cw_500%2Climit_1%2Fformat%2Cf_auto%2Fquality%2Cq_80)
    
5. 最后调节不同应用的声音即可
    ![win11如何调节不同应用的声音大小？](https://exp-picture.cdn.bcebos.com/cf6d451b1edef4dc9a185da845ecd3d968750cb8.jpg?x-bce-process=image%2Fresize%2Cm_lfit%2Cw_500%2Climit_1%2Fformat%2Cf_auto%2Fquality%2Cq_80)

#### （2）切换录放音设备

　**方法一：通过快捷设置面板**

　　单击由 Wi-Fi 图标、扬声器图标和电池图标组成的快速设置面板图标。

　　在快速设置面板中，单击与音量滑块关联的向右箭头图标。

![Win11更改声音输出设备的四种方法](https://img3.xitongzhijia.net/allimg/220407/132-22040G55AK43.png)

　　现在在弹出的窗口中，您将能够看到连接到计算机的所有输出设备。只需单击您喜欢的输出设备即可。而已。

![Win11更改声音输出设备的四种方法](https://img3.xitongzhijia.net/allimg/220407/132-22040G55F4I8.png)

　　**方法二：通过系统声音设置**

同时按下Win + I键以启动设置应用程序。在左侧窗格中，单击“系统”选项卡，在右侧窗格中，单击“声音”选项卡。

![Win11更改声音输出设备的四种方法](https://img3.xitongzhijia.net/allimg/220407/132-22040G55G4341.png)

在“声音设置”窗口中，通过单击与其关联的箭头展开“选择播放声音的位置”部分。

在此部分下，您可以看到连接到计算机的所有输出设备。如果有多个输出设备，您可以选择您喜欢的输出设备，只需单击对应的单选按钮即可。而已。

注意：在下面的屏幕截图中，没有单选按钮，因为只有一个输出设备连接到我的电脑。

或者，如果您想将某个特定设备设为默认输出设备，请单击与该输出设备关联的右箭头图标以展开其属性。

![Win11更改声音输出设备的四种方法](https://img3.xitongzhijia.net/allimg/220407/132-22040G55H2554.png)

在随后的“属性”窗口中，在“常规”部分下，为“设置为默认声音设备”下拉菜单中的“音频”选项选择“默认”。而已。

![Win11更改声音输出设备的四种方法](https://img3.xitongzhijia.net/allimg/220407/132-22040G55I0G8.png)

　　**方法三：通过音量混合器设置**

　　右键单击[任务栏](https://www.xitongzhijia.net/zt/rwlsz/)右上角的扬声器图标。从展开的菜单中，单击打开音量混合器选项。

![Win11更改声音输出设备的四种方法](https://img3.xitongzhijia.net/allimg/220407/132-22040G55J3C0.png)

　　现在在音量混合器窗口中，您可以从与输出设备选项关联的下拉列表中选择您喜欢的输出设备。

![Win11更改声音输出设备的四种方法](https://img3.xitongzhijia.net/allimg/220407/132-22040G55K0929.png)

#### （3）管理音频设备

1. [^7]我们先打开Windows11系统设置应用，在设置界面中，我们点击“系统”---然后点击右侧的“声音”选项。
    
    ![Win11系统如何对声音设备进行设置？](https://exp-picture.cdn.bcebos.com/9b2098254193cee8c1a42fac5a0ff2260c9aa83b.jpg?x-bce-process=image%2Fresize%2Cm_lfit%2Cw_500%2Climit_1%2Fformat%2Cf_auto%2Fquality%2Cq_80)
    
2. 进入“声音”页面后，我们往下翻页，在高级设置中，点击“所有声音设备”选项，可以查看所有声音设备的状态，可以开启关闭设备，可以排除设备故障等。
    
    ![Win11系统如何对声音设备进行设置？](https://exp-picture.cdn.bcebos.com/87645f93cee8b00426bbaab879260d9a300ea93b.jpg?x-bce-process=image%2Fresize%2Cm_lfit%2Cw_500%2Climit_1%2Fformat%2Cf_auto%2Fquality%2Cq_80)
    
3. 进入“所有声音设备”页面后，我们可以看到我们当前系统中所有的声音设备，选择我们要设置的声音设备，点击该设备。
    
    ![Win11系统如何对声音设备进行设置？](https://exp-picture.cdn.bcebos.com/40d2d0e8b004541ba2af8991869a310e1699a63b.jpg?x-bce-process=image%2Fresize%2Cm_lfit%2Cw_500%2Climit_1%2Fformat%2Cf_auto%2Fquality%2Cq_80)
    
4. 进入该声音设备的属性页面，这里我们就可以设备该声音设备了。可以设置该设备是否可用，输出的声音格式，声音大小，声道等。
    
    ![Win11系统如何对声音设备进行设置？](https://exp-picture.cdn.bcebos.com/b1454a1bd10ff226783a4ab99c99e92abbb8a43b.jpg?x-bce-process=image%2Fresize%2Cm_lfit%2Cw_500%2Climit_1%2Fformat%2Cf_auto%2Fquality%2Cq_80)

### 2.3.4. 调整自启动任务

 1、[^8]首先，按键盘上的 Win 键，或点击任务栏上的开始图标；

![](https://pic2.zhimg.com/v2-d6d10d0106b37e7043256f6079990bb9_1440w.jpg)

2、然后，找到并点击所有应用下的设置；

![](https://pica.zhimg.com/v2-c6ac5144be641f14d1a57f17cb2f922c_1440w.jpg)

3、设置窗口，左侧边栏，点击应用；

![](https://pic4.zhimg.com/v2-96c265bd49cc2a997652ea5f28abc391_1440w.jpg)

4、再找到并点击启动（登录时自动启动的应用程序）；

![](https://pic4.zhimg.com/v2-a7f9f51b1d6cb82864cee6c0d5c11abd_1440w.jpg)

5、启动应用下，可以将应用配置为登录时启动。在大多数情况下应用启动后会最小化，或者可能只启动后台任务；

![](https://pic1.zhimg.com/v2-f0939699b9e6951249e570da259767ee_1440w.jpg)

### 2.3.5. 关闭自动更新

>**引言**：不知道你们看没看过电脑显示下面这个图标，每次更新时间久还不说，而且更新后还容易出现 Bug。有人会问，不更新会不会不安全，我认为更新反而使小白的电脑不安全——我问两个问题：1. 你知道每次更新更新了什么么？ 2. 你觉得这更新带来的东西对你有用么？ 如果两个答案都是不知道的话，跟着我来关闭更新功能吧~

![](https://www.pe8.com/ueditor/php/upload/image/20190322/1553225431693986.png)

【步骤】
	1 .打开设置，搜索组策略  
	![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/c27596c61b96a1537edb0a6fbab8c7f9.png)
	2.依次打开 计算机配置 -> 管理模板 -> Windows组件 -> Windows更新  
	![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/4a7ba6c00af9a44fbbfea67be887ed6b.png)  
	![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/c8611249514b2646b079775646c076d8.png)  
	3.配置自动更新设置为 已禁用，然后点击 应用、确定  
	![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/25e1b39f7a2b633ccdb1ced167a0e3dc.png)  
	4.之后还需要再找到“删除使用所有Windows更新功能的访问权限”，选择已启用，完成设置后，点击“应用”、“确定”。  
	![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/daeadeff9510eea02718622e98a95276.png)

如果正常的话，你打开你的设置，查看更新这个页面的时候你会发现有一个更新策略

### 2.3.6. 存储感知使用

#### （1）开启存储感知

1[^9]打开「设置」——「系统」——「存储」

2在「存储管理」区域中打开「存储感知」功能的开关

![开启「存储感知」](https://img.sysgeek.cn/img/2022/07/windows-11-storage-sense-2.jpg)

开启「存储感知」

完成这些步骤后，该功能将使用默认设置自动运行。

> 推荐阅读：[如何在 Windows 10 中启用「存储感知」功能](https://www.sysgeek.cn/windows-10-creators-update-storage-sense/)

#### （2）管理存储感知

要配置「 存储感知 」以自动释放计算机上的空间，请使用以下步骤：

1打开「设置」——「系统」——「存储」

2在「存储管理」区域中点击「存储感知」选项——勾选「清理临时文件」下的「通过自动清理临时系统和应用程序文件来保持 Windows 顺畅运行」选项

3打开「自动用户内容清除」开关

![配置「存储感知」](https://img.sysgeek.cn/img/2022/07/windows-11-storage-sense-3.jpg)

配置「存储感知」

4按自己的需要，对「配置清理计划」中「运行存储感知」的条件进行设置：

- 每天
- 每周
- 每月
- 当磁盘空间不足时（默认）

5（可选）按需要对回收站中超过 N 天的文件进行删除：

- 从不
- 1 天
- 14 天
- 30 天（默认）
- 60 天

6（可选）按需要将「下载」文件夹中 N 天未打开的文件进行删除：

- 从不（默认）
- 1 天
- 14 天
- 30 天
- 60 天

> 「下载」文件夹可能包含您之前从 Internet 下载的重要文件，开启此选项要慎重。

7（可选）如果你在使用微软的 OneDrive，这里会多出一个下拉列表，我们可以控制将 N 天未打开的文件仅联机保存：

- 从不（默认）
- 1 天
- 14 天
- 30 天
- 60 天

![配置清理计划](https://img.sysgeek.cn/img/2022/07/windows-11-storage-sense-4.jpg)

配置清理计划

> 开启此功能时，文件将继续罗列在 OneDrive 文件夹中，但可能需要连接互联网才能再次打开它们。

# 3. 高级阶段

## 3.1. 高级系统使用


## 3.2. 高级浏览器使用


## 3.3. 终端控制台基础


## 3.4. 策略组管理器



## 3.5. 网络基础知识


## 3.6. 科学上网基础


# 4. 后续学习


## 4.1. 学习 Markdown 

## 4.2. 学习 Obsidian
### 4.2.1. 界面认识

### 4.2.2. 快捷功能


### 4.2.3. 扩展功能


# 附录：推荐网站

- [系统极客 - 掌握软件技能](https://www.sysgeek.cn/)


# 附录：引用链接

[^1]:[Win10/Win11学院：玩转 Windows 文件资源管理器 - IT之家 (ithome.com)](https://www.ithome.com/0/589/240.htm#:~:text=%E9%A6%96%E5%85%88%EF%BC%8C%E6%88%91%E4%BB%AC%E4%BB%8E%E7%9B%B4%E8%A7%82%E4%B8%8A%E5%AF%B9%E6%AF%94%E4%B8%80%E4%B8%8B%20Win10%20%E5%92%8C%20Win11%20%E7%9A%84%E6%96%87%E4%BB%B6%E8%B5%84%E6%BA%90%E7%AE%A1%E7%90%86%E5%99%A8%E7%9A%84%20%E4%B8%BB%E7%95%8C%E9%9D%A2%E3%80%82%20%E5%A6%82%E4%B8%8B%E5%9B%BE%E6%89%80%E7%A4%BA%EF%BC%8C%E4%B8%8A%E4%BE%A7%E5%92%8C%E4%B8%8B%E4%BE%A7%E5%88%86%E5%88%AB%E4%B8%BA%20Win10,%E6%8E%92%E5%BA%8F%20%E4%BB%A5%E5%8F%8A%20%E6%9F%A5%E7%9C%8B%209%20%E4%B8%AA%E5%B8%B8%E7%94%A8%E9%80%89%E9%A1%B9%EF%BC%8C%E8%80%8C%E5%AF%B9%E5%85%B6%E4%BB%96%E9%80%89%E9%A1%B9%E5%88%99%E4%BD%9C%E4%BA%86%E9%9A%90%E8%97%8F%EF%BC%8C%E7%9B%B8%E6%AF%94%20Win10%EF%BC%8C%E5%8F%98%E7%9A%84%20%E7%AE%80%E6%B4%81%E9%AB%98%E6%95%88%20%E4%BA%86%E8%AE%B8%E5%A4%9A%E3%80%82)
[^2]:[这些是我的 19 个技巧，可帮助您从 Windows 11 上的任务管理器中获得更多收益 (windows-office.net)](https://cn.windows-office.net/?p=39479)
[^3]:[Win11怎么设置双屏或多屏显示？Win11设置多屏/显示操作方法-攀升知识库 (ipason.com)](https://knowledge.ipason.com/ipKnowledge/knowledgedetail.html/828)
[^4]: [[Windows 11/10] - 如何更改显示大小、屏幕分辨率和刷新率？ | 官方支持 | ROG 中国 (asus.com.cn)](https://rog.asus.com.cn/support/faq/1013049/)
[^5]: [涨知识丨一文看懂笔记本电脑HDMI接口 - 知乎](https://zhuanlan.zhihu.com/p/268136918)
[^6]: [Microsoft Edge 工作区入门 - Microsoft 支持](https://support.microsoft.com/zh-cn/topic/microsoft-edge-%E5%B7%A5%E4%BD%9C%E5%8C%BA%E5%85%A5%E9%97%A8-63a5a6d7-3db4-468f-aba8-fdd00dce4c35)

[^7]: [Win11系统如何对声音设备进行设置-百度经验](https://jingyan.baidu.com/article/e4d08ffd9d401f4ed3f60d5a.html)

[^8]: [Win11电脑怎么管理/设置开机启动项？ - 知乎](https://zhuanlan.zhihu.com/p/477089385)

[^9]: [如何在 Windows 11 中使用「存储感知」自动释放磁盘空间 - 系统极客](https://www.sysgeek.cn/windows-11-storage-sense/)


# 附录：修改历史

- 防火墙操作事项
