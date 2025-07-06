延时摄影（Time-lapse photography）是一种通过延长摄影时间间隔来观察缓慢变化的摄影技术。 与 Adobe 官方网站 《[How to create time-lapse videos](https://www.adobe.com/creativecloud/video/discover/time-lapse-video.html)》 讲解延时摄影的文章略有不同，本篇文章更多地是讲解如何使用类似 OBS Studio 这样的软件来录制延时视频。 具体案例是：我是一个长期在电脑前学习和工作的人，因此大部分有关活动可以用电脑屏幕来展示。 希望用每 1 分钟的最终视频长度来对应现实生活中 1 小时实际流逝时间，也就是 60 倍速的延时视频。 这样我只需要 10 分钟左右的时间就能够快速回顾我在镜头下的一天。

其它类似场景：板绘、3D 建模、动画、特效等制作过程的记录。

虽然 60 倍速的画面看起来很鬼畜，但是效果还是很不错的，是不错的信息压缩手段。

## 原始方法[​](https://blog.chai.ac.cn/posts/how-to-make-time-lapse-video-with-obs#%E5%8E%9F%E5%A7%8B%E6%96%B9%E6%B3%95)

前期录制一切照常，后期用如 FFMPEG 对视频进行倍速处理，但这样会导致：

- 前期录制需要更高的机器性能，有较高的 CPU 占用率
- 前期录制的视频文件体积过大，直接导致后期处理的时间过长
- 如果你设置不正确或做了多余的改动，甚至会导致视频重新渲染编码

问题在于，很多人并不知道 OBS 上面更正确、也是更轻松的延时视频的录制方法。

## 更轻松的方法[​](https://blog.chai.ac.cn/posts/how-to-make-time-lapse-video-with-obs#%E6%9B%B4%E8%BD%BB%E6%9D%BE%E7%9A%84%E6%96%B9%E6%B3%95)

在录制时就降低视频的帧率，大幅减少视频文件的体积、后期处理的时间、机器资源的占用。

![](https://blog.chai.ac.cn/assets/19a757015d5ba21e5d871bfc241efc92.s4gmGNr5.png)

以 OBS 为例子，跑到 “设置-视频” 面板，将帧率调整为 1 FPS（每秒只录制 1 张图片）。 后期想得到 60 倍速的延时视频，只需要将视频加速 60 倍，帧率调整为 60 FPS 即可。 这样最终输出的视频每秒钟有 60 张图片，代表着在对应一分钟内的 60 次采样。 [

[1]

](https://blog.chai.ac.cn/posts/how-to-make-time-lapse-video-with-obs#fn1)

OBS 还支持分数帧率，这意味着你可以以更低的帧率录制，比如 0.5 FPS、0.128 FPS 等等， 分别对应每 2 秒、每 8 秒录制一张图片（那么 `setpts` 和 `r` 值需要你重新换算）。 [↩︎](https://blog.chai.ac.cn/posts/how-to-make-time-lapse-video-with-obs#fnref1)

### 视频后期如何进行加速[​](https://blog.chai.ac.cn/posts/how-to-make-time-lapse-video-with-obs#%E8%A7%86%E9%A2%91%E5%90%8E%E6%9C%9F%E5%A6%82%E4%BD%95%E8%BF%9B%E8%A1%8C%E5%8A%A0%E9%80%9F)

以 FFMPEG 为例子，使用如下命令：

powershell

```
ffmpeg -i input.mkv -filter:v "setpts=PTS/60" -an -r 60 output.mkv
```

参数解释：

- `-i input.mkv`：输入文件
- `-filter:v "setpts=PTS/60"`：将视频的时间戳除以 60，即加速 60 倍
- `-an`：去掉音频
- `-r 60`：设置输出视频的帧率为 60 FPS
- `output.mkv`：输出文件

为了方便，我直接在 Windows 下写了个批处理文件，把源文件拖上去即可：

powershell

```
@echo off

set "input_file=%~1"
if "%input_file%"=="" goto NoFile

set "output_file=%~dpn1_60fps.mkv"

ffmpeg -i "%input_file%" -filter:v "setpts=PTS/60" -an -r 60 "%output_file%"

echo Output saved to "%output_file%"
goto End

:NoFile
echo No file provided.
echo Please drag and drop a file onto the script.
goto End

:End
pause
```

新建一个 `convert-to-60fps.bat` 文件，将上面的代码复制进去，保存即可。

### 可能有用的脚本[​](https://blog.chai.ac.cn/posts/how-to-make-time-lapse-video-with-obs#%E5%8F%AF%E8%83%BD%E6%9C%89%E7%94%A8%E7%9A%84%E8%84%9A%E6%9C%AC)

如果你录制中途突然中断，可以使用下面的代码来快速合并多个文件：

如果你想要裁剪视频，可以使用下面的 Python 代码：

关于 OBS 其它地方的设置，视频封装格式采用了默认的 MKV 格式，可按需修改。 录像设置，我使用的是 x264 编码器，VBR 1000 Kbps 速率，1080p 分辨率，CRF 23. 差不多平均每天录制的视频文件大小在 300 MB 左右，加速后的视频文件大小在 150 MB 左右。 而且最终视频的每一帧都是清晰的，没有丢帧的情况。