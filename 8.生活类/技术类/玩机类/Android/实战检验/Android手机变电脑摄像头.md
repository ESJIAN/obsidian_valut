## 一、方式一：使用 DroidCam

使用 DroidCam，你可以将手机作为电脑摄像头和[麦克风](https://so.csdn.net/so/search?q=%E9%BA%A6%E5%85%8B%E9%A3%8E&spm=1001.2101.3001.7020)。一则省钱，二则可以在紧急情况下使用，比如要在电脑端参加一个紧急会议，但电脑却没有摄像头和麦克风。

DroidCam 的安卓端分为免费的 DroidCam 版和收费的 DroidCamX版（支持高清），都需要去谷歌商店下载，且需要绑定手机。另外 ，需要PC[客户端](https://so.csdn.net/so/search?q=%E5%AE%A2%E6%88%B7%E7%AB%AF&spm=1001.2101.3001.7020)（Windows 和 Linux 客户端均可用）配合使用，[DroidCam PC 客户端官网下载](https://www.dev47apps.com/)

可以参考这篇文章进行使用：[**用手机作为电脑摄像头和麦克风，DroidCamX使用详解附下载**](https://blog.51cto.com/u_9843231/5903518)

## 二、方式二：使用 RemoteCam

RemoteCam 是一款简单的开源手机软件，手机安装 RemoteCam 后，可以实时将手机录像画面，传输到PC端。

RemoteCam 官网及手机安装包下载：[RemoteCam github地址](https://github.com/Ruddle/RemoteCam)

安装并打开软件后，开启Stream ，点击下面 ips 后面的网址将其复制到电脑浏览器打开测试下，你会发现发现手机录像已经同步到电脑浏览器中了。

**注意：手机和电脑要位于同一网络下（即同一WiFi下）**

你可以使用 ffmpeg 将手机传来的视频画面保存到 PC 端 为 mp4 格式，或者在PC 端安装 OBS 来接收手机端的视频画面。

### 1. 使用 ffmpeg 来接收手机端传输来的画面

需要先在PC端安装ffmpeg ，可参考：[ffmpeg的下载及安装](https://blog.csdn.net/qq_33697094/article/details/112718101)

然后使用下面的 ffmpeg 命令将 RemoteCam 实时拍摄传输到电脑的画面保存为 output.mp4  
（命令中的 http 网址是从 RemoteCam 的 ips 复制的网址）

```bash
ffmpeg -f mjpeg -i http://192.168.1.2:8080/cam.mjpeg -c:v libx264 -crf 23 output.mp4
```

### 2. 使用 OBS 来接收手机端传输来的画面

你可以 PC 端在 [OBS官网下载](https://obsproject.com/zh-cn/) OBS 并安装

然后如下配置便可接收手机端拍摄传输来的画面，下面的操作 OBS 录制的只是手机传来的视频画面，声音是通过电脑来录制的，因为 RemoteCam 只传递视频画面到电脑。

**(1) 点击控制按钮里点击设置**

![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/7c99751bad258b73c80832fc6bce1aa0.png)

在输出里可以调整最终保存的录像路径

![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/9f017eac5d5fc6f3826381c14150168e.png)

**(2) 点击来源下面的加号，选择媒体源，点击确定**

![请添加图片描述](https://i-blog.csdnimg.cn/blog_migrate/885ddcd68eb49eb090f81e2b04e65099.jpeg)

![请添加图片描述](https://i-blog.csdnimg.cn/blog_migrate/920b2bc832027eea8ad89ac31b6ed65e.jpeg)

取消掉本地文件选项前面的勾选，然后输入填入你手机 RemoteCam 软件中 ips 后面的网址，输入格式填 mjpeg

![请添加图片描述](https://i-blog.csdnimg.cn/blog_migrate/cf939bd5ad50bc9c93843ccc26e9a343.jpeg)

**(3) 点击 开始录制 就可以把手机的画面传到 obs 软件里并开始录制了，点击结束录制，然后去上面的 录像路径  
文件夹下就可以找到录制的视频文件啦。**

![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/d481ade6c2f1b405e71b75aa5bec2db8.png)

当然，如果想直播并且有其他直播平台的直播连接和推流码，可以点开始直播填入直播相关信息，这样就可以把画面传到其他直播平台直播了，比如：YouTube、Twitter 等

**（4）使用虚拟摄像头**  
你可以把手机 RemoteCam 拍摄到的画面推流到电脑的软件。比如要用腾讯会议开会，电脑摄像头坏了，你就可以点击启动虚拟摄像机，然后腾讯会议里选择 OBS 虚拟摄像头就行，这个时候手机就相当于你电脑的摄像头了。

![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/56f714f09f904525cae554e825a06ff0.png)  
**（6）直播提前录好的视频**  
如果你电脑有一段已经录好的视频文件，想把这个视频作为直播的内容（也就是常说的录播。），可以很方便的用 OBS 做到。

点击来源下面的加号，选择媒体源，点击确定。然后勾选本地文件，选择视频文件，如果要循环直播，可以勾选循环。  
![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/c07278159f91ed76abd34de1c3f73353.png)

然后就可以直播那个视频了。

当然也可以点启动虚拟摄像头，把那个视频作为你摄像头的输出，这样你可以提前录好一段视频，等开会的时候如果你有事不在，可以用提前录好的视频作为你摄像头的视频。