win11这些系统真的很爽啊，WSL本地跑liunx，WSA本地跑安卓，虚拟的还挺完整的，美滋滋的有木有。  

不过微软win11的这个安卓子系统（WSA）没有 [root](https://www.tjsky.net/tutorial/384#)，也没有谷歌框架，应用市场是那个奇葩的亚马逊市场，没有Google Play，用起来相当让人不爽。  

直接给win11的安卓子系统（WSA）安装magisk，获取系统root权限非常麻烦。

经过一番查找发现LSPosed早就解决这个问题了。可以通过构建安卓子系统安装包，直接把magisk提前整合进WSA安装包就可以了。

**主要提示：微软发通知， Windows Subsystem for  [Android](https://www.tjsky.net/tutorial/384#) 在2025 年 3 月 5 日停更，之后还会再提供1年的技术支持，也就是说除非有严重bug或漏洞，不然微软不会更新升级了，大版本会停留在 2311 了 （微软大刀部名不虚传）**

文章目录

- [1 win11 安卓子系统（WSA）ROOT安装面具（Magisk）与谷歌框架（Google Apps）](https://www.tjsky.net/tutorial/384#win11_WSAROOTMagiskGoogle_Apps)
    - [1.1 前提](https://www.tjsky.net/tutorial/384#i)
    - [1.2 构建WSA安装包](https://www.tjsky.net/tutorial/384#WSA)
    - [1.3 构建选项](https://www.tjsky.net/tutorial/384#i-2)
    - [1.4 本地安装](https://www.tjsky.net/tutorial/384#i-3)
    - [1.5 后续更新WSA](https://www.tjsky.net/tutorial/384#WSA-2)
    - [1.6 卸载WSA](https://www.tjsky.net/tutorial/384#WSA-3)
    - [1.7 几种常见的问题](https://www.tjsky.net/tutorial/384#i-4)

---

win11安卓子系统系列文章之一：[win11 安卓子系统（WSA）ROOT安装面具（Magisk）与谷歌框架（Google Apps）](https://www.tjsky.net/?p=384 "win11 安卓子系统（WSA）ROOT安装面具（Magisk）与谷歌框架（Google Apps）")  
win11安卓子系统系列文章之二：[Windows Android 子系统 WSA 代理设置方法教程](https://www.tjsky.net/?p=391 "Windows Android 子系统 WSA 代理设置方法教程")  
win11安卓子系统系列文章之三：[解决Win11安卓子系统烦人的提示“VirtWifi的连接受限”](https://www.tjsky.net/?p=397 "解决Win11安卓子系统烦人的提示“VirtWifi的连接受限”")  
win11安卓子系统系列文章之四：[Windows 11 Android 子系统 WSA 安装APP软件APK文件方式教程](https://www.tjsky.net/?p=401 "Windows 11 Android 子系统 WSA 安装APP软件APK文件方式教程")  
win11安卓子系统系列文章之五：[为 win11 安卓子系统（WSA）内 APP 设置桌面快捷方式](https://www.tjsky.net/?p=630 "为 win11 安卓子系统（WSA）内 APP 设置桌面快捷方式")

---

## 前提

1. 首先也是最主要的，你的电脑的配置要能安装安卓子系统（WSA），不然这文章对你完全没用
    - 确定系统版本
    - windows11 系统需确保Windows 11版本为22000.526或更高版本。
    - windows10 系统需要先**依次安装**这两个补丁 [KB5014032](https://www.tjsky.net/goto/?url=https://www.catalog.update.microsoft.com/Search.aspx?q=KB5014032 "KB5014032") [KB5022834](https://www.tjsky.net/goto/?url=https://www.catalog.update.microsoft.com/Search.aspx?q=KB5022834 "KB5022834")
    - WSA 按说和 win11 一样有 CPU 型号限制，需要 CPU 大于等于 core i3 8XXX 、Ryzen 3000。不过实际可能再早一点的 CPU 也能运行起来，具体就自己测试吧。
    - 硬件必须支持并启用BIOS/UEFI虚拟化（打开任务管理器，切换到性能，CPU页面，如果你看到`虚拟化：已启用`说明就启用了）
    - 微软商店版本为22110.1402.6.0或更高版本
    - 安卓子系统默认会分配2G（最大16G）以上内存，建议16G内存以上的 [电脑](https://www.tjsky.net/tutorial/384#)使用。
2. 然后你的电脑里需要先卸载WSA（如果你已经安装过安卓子系统的话），当然你可以备份你的数据，不过我还是建议彻底卸载重装算了，免得出奇怪的问题，如果你安装过并卸载了，那你可以忽略下边的第3步
    
3. 在电脑的设置 → 应用 → 可选功能 → 更多 Windows 功能，找到并勾选开启「Hyper-V」和「虚拟机平台」，确定后系统会自动安装组件，安装完成后会提示重启系统，并且伴随一次系统更新。  
    ![](https://www.tjsky.net/wp-content/uploads/2022/08/20220819203821.png)
    
4. 你是否有一台运行 Ubuntu20.04 LTS 或 OpenSUSE Leap 15.4 或 Debian 11.3以上版本系统，且磁盘可用空间大于10GB的机器（其他linux 系统无法保证开箱即用，比如 CentOS ， FreeBSD 等系统）
    

- 没有

请直接跳到【[本地安装](https://www.tjsky.net/?p=384#i-3 "本地安装")】开始看，直接提供了适用于最普遍情况的安装包。

- 有

且你希望进行更多自定义设置或者希望自己编译安装包，请继续往下看（否则推荐直接下载[预构建安装包](https://www.tjsky.net/?p=384#i-3 "预构建安装包")），你可以用WSL2在win11里跑一个Ubuntu系统，这个是完全没问题的。关于怎么在win10或者win11里安装基于WSL2的Ubuntu网上教程一搜一大把，就不再赘述了（运行Ubuntu的服务器/电脑需要有至少10G的空闲可用磁盘空间，以及目前/tmp在WSL上是会被直接写入内存，构建脚本利用了这个特性来加速构建，所以请确保你 [电脑](https://www.tjsky.net/tutorial/384#)内存也足够大，以及**确保机器能自由访问网络**）

## 构建WSA安装包

**2023-07-21更新 目前已知升级到WSA 2306 及以上版本，可能会出现WSA启动后自动退出的问题，需要卸载原有WSA再重新安装），这个问题不是每个人都存在，不过升级前最好做好准备。**

1. 打开[MagiskOnWSALocal](https://www.tjsky.net/goto/?url=https://github.com/LSPosed/MagiskOnWSALocal "MagiskOnWSALocal")项目地址
    
2. 右上角有个星标【Star☆】点一下（非必须）
    
3. 把项目的文件放到你的Ubuntu系统里，你是用git啊，还是SVN啊，还是下载项目ZIP到电脑里，再用FTP上传到Ubuntu系统都行，方法很多的。(以下假设你放在了/usr/MagiskOnWSALocal/目录下)  
    比如  
    登录你的你的Ubuntu系统 SSH里输入
    

```shell
cd /usr/
git clone https://github.com/LSPosed/MagiskOnWSALocal.git
```

4. SSH里执行

```shell
cd /usr/MagiskOnWSALocal
```


5. SSH里输入

```shell
scripts/run.sh
```

运行构建脚本，耐心等待脚本拉取构建环境，然后脚本会询问你**构建选项**  
方向键移动选择项目，空格选择，回车确认。

- 临时措施（20230721）  
    目前项目代码上有个bug可能导致保留亚马逊商店的用户更新到2306及2307后，WSA崩溃退出，所以目前更新 2306 与 2307 的代码没合并到主线。直接获取到的代码只能构建到 2305。  
    我们可以手动修改 `scripts/build.sh` 文件，来构建更高的版本  
    下边以构建 2306 为例，（构建 2307 就把 2306 改成 2307 ）

```shell
#651行
if [[ "WSA_MAJOR_VER" -ge 2304 && "WSA_MAJOR_VER" -lt 2306 ]]; then
#675行
if [[ "WSA_MAJOR_VER" -lt 2304 || "WSA_MAJOR_VER" -ge 2306 ]]; then
#909行
if [[ "WSA_MAJOR_VER" -ge 2304 && "WSA_MAJOR_VER" -lt 2306 ]]; then
```

Bash

Copy

然后再执行上边的第5步.

## 构建选项

方向键移动光标，空格键选中，回车箭确认选项。

1. 【Build arch】选择安卓子系统（WSA）的运行硬件架构  
    咱们 [电脑](https://www.tjsky.net/tutorial/384#)一般都是X64的架构吧，你电脑要真是是ARM架构那就选arm64，不然就选默认的X64
    
2. 【WSA release type】选择安卓子系统（WSA）的版本，  
    这个一般选默认的retail，除非你需要预览版
    
3. 【Magisk version】选择 面具（Magisk）的版本  
    这个一般选默认的retail，除非你需要预览版的面具
    
4. 【Install G [app](https://www.tjsky.net/tutorial/384#)s】选择 是否安装谷歌框架  
    根据需求，需要就选Yes，不需要就选No
    
5. 【Which GApps do you want to install】选择安装的谷歌框架类型  
    目前基于MagiskOnWSA项目的安装有两个google框架体系，一个是**OpenGApps**（稳定性比较好，但是最近更新慢，完全没适配安卓13，导致wsa版本只能支持到2210.400000.7.0），一个是**MindTheGapps**（有适配安卓13的版本，但遇到兼容性问题几率提升）没如果强烈的使用安卓13或最新版wsa的需求，推荐使用**OpenGApps**
    
6. 【Variants of gapps】选择你装多少谷歌APP  
    （2022-08-27的更新：WSA内安卓更新至安卓12后，Gapps只有pico实际可用,而MindTheGapps公开编译只有一个包,所以目前这一个选项是会被跳过的）
    

一般默认的pico就行，如果你使用的某些 [APP](https://www.tjsky.net/tutorial/384#)，需要更加完整的谷歌环境，再尝试用nano

- Super就是谷歌全家桶我全要了（1G多空间需求），
- stock类似于 Google Pixel手机的状态
- mini类似于谷歌比较常用APP都装进来，
- micro是把常用谷歌APP装进来
- nano是完整谷歌框架，
- pico就是只有必须的谷歌框架
    
- 具体各种选项的区别看：[这里](https://www.tjsky.net/goto/?url=https://github.com/opengapps/opengapps/wiki#variants "这里")
    

7. 【remove 亚马逊市场】选择是否安装没啥卵用的亚马逊应用市场  
    选no就行，因为确实没啥用，里面应用少的可怜，咱上一步都装了GooglePlay了是不。
    
8. 【 [Root](https://www.tjsky.net/tutorial/384#) Solution】选择是否root  
    这里当然是选magisk获取root啊，你要是不需要root，只需要安装google框架的话可以选none
    
9. 【Compress output】选择是否压缩output  
    如果选NO，安装文件就是一个文件夹，你需要下载这个文件夹  
    如果选Yes，安装文件打包成一个压缩包，方便下载（也不容易出错）。  
    注意如果你的机器性能欠佳，有可能压缩所需要的时间，会长到让你怀疑人生。
    
10. 【Compress format】选择压缩格式  
    7z压缩率最高，但压缩时最吃CPU资源，zip压缩率稍低，相对不太吃资源，而且支持性好，tar.xz性能和压缩率都不错，但在win解压需要解压软件的支持。
    
11. 等待构建完成
    

```shell
Everything is Ok
done
Cleanup Work Directory
done
```

等待SSH显示如上内容时说明安装包已经构建完毕了

## 本地安装

- WSA 安装包1号（安卓12）【[下载地址1](https://www.tjsky.net/goto/?url=https://mypikpak.com/s/VNI59j5McsDFdt_m1NIJOTBto1)】，【[下载地址2](https://www.tjsky.net/goto/?url=https://url71.ctfile.com/f/21226171-738765619-be4206?p=acgmoe "下载地址2")】（访问密码：acgmoe）  
    `X64 系统使用，正式版 WSA（2210.400000.7.0）下载，Magisk25.2，OpenGApps 谷歌框架 pico，ROOT，移除亚马逊应用市场`**2022-11-30更新**
- WSA 安装包2号（安卓13）【[下载地址1](https://www.tjsky.net/goto/?url=https://mypikpak.com/s/VNjQDLzmswsd6dqRYoftpL4Bo1%22%E4%B8%8B%E8%BD%BD%E5%9C%B0%E5%9D%801%22)】,【[下载地址2](https://www.tjsky.net/goto/?url=https://url71.ctfile.com/f/21226171-976091083-81ed91?p=acgmoe "下载地址2")】（访问密码：acgmoe）  
    `X64 系统使用，正式版 WSA（2310.40000.2.0）下载，Magisk26.4，MindTheGapps 谷歌框架 pico，ROOT，移除亚马逊应用市场`**2023-11-17更新**
- WSA 安装包3号（安卓13）【[下载地址1](https://www.tjsky.net/goto/?url=https://mypikpak.com/s/VNlIC4FgqHxD_y_C13BCkOpzo1%22%E4%B8%8B%E8%BD%BD%E5%9C%B0%E5%9D%801%22)】,【[下载地址2](https://www.tjsky.net/goto/?url=https://url71.ctfile.com/f/21226171-987259696-c4fc2f?p=acgmoe%22%E4%B8%8B%E8%BD%BD%E5%9C%B0%E5%9D%802%22)】（访问密码：acgmoe）  
    `X64 系统使用，正式版 WSA（2311.40000.3.0）下载，Magisk26.4，MindTheGapps 谷歌框架 pico，ROOT，移除亚马逊应用市场`**2023-12-10更新**
    
- 历史安装包下载【[下载地址](https://pic.tjsky.net/Share/Windows/WSA "下载地址")】
    

**2023-11-01提醒 直接安装版本大于2309的安装包可能会出现 LSPosed 模块消失，无法弹出VPN授权弹窗等问题，可以通过到【[历史安装包下载](https://pic.tjsky.net/Share/Windows/WSA "历史安装包下载")】先安装旧版WSA，等待安装好VPN类软件和LSPosed后，再升级到最新版WSA即可解决问题**

**2023-12-19提醒 最新的7z格式引入了针对ARM64文件的新压缩算法2308版本后的安装包，需要你将压缩软件升级到最新，才可正确解压**

**上述两种安装包因为使用了不同的google框架体系，所以不能直接切换安装，装了一种后，想装另一种就要彻底卸载原有的WSA**  
**安装包3号是我自己正在使用的安装包**

1. 构建结束后，你会在/usr/MagiskOnWSALocal/目录下看到一个新出现的output文件夹，把他里面的文件全部下载/复制到你的win11系统里（SFTP，FTP，webdav，WSL的直接复制，随便你发挥），如果你是用的上边的“WSA 安装包X号”直接在对应地址的网盘里下载即可。

- 请一定保留最后可用的压缩包以备出现奇怪问题时可以通过重新覆盖安装解决
- **解压出的安装文件夹是不可被删除的，这会是WSA的工作目录。**

2. 在复制并解压（如果你得到的是一个压缩包的话就解压）到本机你喜欢的文件夹内（比如C:/output），找到`run.bat`文件,双击运行。（如果这是你第一次安装，可能会显示一个要求同意诊断信息的窗口，也有可能会显示两个相同的窗口，这都是正常的）
    
3. 没了，等安装完毕就好了，这俩窗口或其中一个弹出来，就说明你已经安装好了带 [root](https://www.tjsky.net/tutorial/384#)，带面具的安卓子系统了。  
    ![](https://www.tjsky.net/wp-content/uploads/2022/08/20220819212926.png)  
    截图里可以看到，初始的Magisk的页面里“Zygisk”是“否”，想要正式开用你还需要自己装[LSPosed-zygisk](https://www.tjsky.net/goto/?url=https://hub.fastgit.xyz/LSPosed/LSPosed/releases/ "LSPosed-zygisk")。  
    这个和手机上装没**几乎**区别，唯一需要注意的是，你可能在Magisk模块里安装后，还需要手动从LSPosed-zygisk.zip的压缩包里找到LSPosed的APK文件（manager.apk），安装到安卓子系统里。（未来LSPosed-zygisk会直接内置进去，当你看到本文的时候可能就不需要自行安装LSPosed-zygisk了）
    
4. WSA 从 2304 版本开始微软会默认使用 Windows Defender 来扫描新装的 [APP](https://www.tjsky.net/tutorial/384#)，而 Magisk 是被认为是恶意应用而被自动阻止安装的。所以如果你是从之前版本 WSA 升级上来的，大概率什么都不会发生，而如果你是新装的 WSA 请进入`适用于Android™ 的 windows子系统设置`，将阻止安装恶意应用的开关关闭，然后重新再运行一次 `run.bat` 文件，才能让Magisk被正确安装。
    
5. 注意目前基于MagiskOnWSA项目的安装有两个google框架体系，一个是**OpenGApps**（也就是本文所提供的，也是目前网上使用范围最广的），一个是**MindTheGapps**，这两个谷歌框架体系之间是不能相互无损切换的，你只能彻底卸载你的WSA再重装。
    
6. WSA 从 2305 版本开始增加了`共享用户文件夹`选项，可将`C:\Users\用户名`目录内，非隐藏文件与文件夹全部映射到安卓系统下（.exe文件出于安全考虑无法映射进去），可以在WSA内对目录下文件直接进行修改和删改操作，而且删除文件是不进回收站的，而且这可能会绕过系统内安全软件的实时监控，因为文件的操作都是以 WSA 的权限执行的，一旦开启请在WSA系统内小心操作。
    

## 后续更新WSA

目前代码还在频繁迭代中，建议注意项目的commits，如果发现重大修改，请及时更新。

**不要在Microsoft Store更新Windows Subsystem for  [Android](https://www.tjsky.net/tutorial/384#)™ with Amazon Appstore**  
重新去[MagiskOnWSALocal](https://www.tjsky.net/goto/?url=https://github.com/LSPosed/MagiskOnWSALocal "MagiskOnWSALocal")拉取最新代码，重新构建，得到新的output文件，再重新用`run.bat`安装一次就行了，脚本会自动为你保留之前的数据，为你更新Magisk，不用担心你的应用数据。  
自己构建时最好工作目录下之前生成的download和output文件夹删了，让脚本重新拉去最新的组件。  
你要是不放心，直接删掉整个/usr/MagiskOnWSALocal/文件夹，一切从头来也行。

1. SSH里执行（切换到工作目录）

```shell
cd /usr/MagiskOnWSALocal
```

Bash

Copy

2. SSH里输入（**非必须** 删除下载和打包缓存）

```shell
rm -r download output
```

Bash

Copy

3. SSH里输入（拉取最新代码）

```shell
git pull
```

Bash

Copy

4. SSH里输入（重新执行构建）

```shell
scripts/run.sh
```

Bash

Copy

5. 下载output文件夹内的文件并解压（如果需要解压的话）

- 打开你的开始菜单
- 点击`适用于Android™ 的 windows子系统设置`
- 切换到系统窗口，找到`关闭适用于Android™ 的 windows子系统`，点击【关闭】按钮
- 用新内容覆盖原有文件夹的内容。
- 找到`run.bat`文件,双击运行。

我也会不定期更新【[本地安装](https://www.tjsky.net/?p=384#i-3 "本地安装")】部分的预制安装包。不过更新时间就不太保证了。

## 卸载WSA

1. 打开你的开始菜单
2. 点击`适用于Android™ 的 windows子系统设置`
3. 切换到系统窗口，找到`关闭适用于Android™ 的 windows子系统`，点击【关闭】按钮
4. 点击`重置为默认值`的【重置】按钮
5. 关闭这个字窗口，重新打开开始菜单
6. 找到`适用于Android™ 的 windows子系统设置`在上边右键，选择【卸载】
7. 如果你要备份应用数据，可以备份`%LOCALAPPDATA%\Packages\MicrosoftCorporationII.WindowsSubsystemForAndroid_8wekyb3d8bbwe\LocalCache\userdata.vhdx`  
    安装[WSAHelper](https://www.tjsky.net/goto/?url=https://github.com/LSPosed/WSAHelper/releases/latest "WSAHelper")，重新恢复开始菜单里的 [APP](https://www.tjsky.net/tutorial/384#)图标。

## 几种常见的问题

1. 报错提示类似`"[SocketCore.cc:507] errorCode=1 Failed to connect to the host 2402:6800:764:a000::1, cause: Network is unreachable"`  
    【微软服务器的问题,解析出的IPv6你无法使用，最快速的解决办法就是，关闭你网络的IPv6】
    
2. 报错中最后几行有类似 `TLS handshake timeout`  
    / `ConnectionResetError: connection reset by peer` / `dns lookup failed` / `ConnectionRefusedError: connection refused` /`Client.Timeout exceeded while awaiting headers`/`ConnectionError：Connection aborted`/`ConnectionError: HTTPSConnectionPool`的日志  
    【诸如此类报错，统统都是网络问题，有些文件无法被下载，只能通过代理解决，要么开TUN模式，要么在WSL2里面设置全局代理，要么路由器上开全局模式】
    
3. Magisk 模块内安装 LSPosed 完重启 Magisk 后 LSPosed 模块消失：
    
    - 最无脑的解决方法：适用于刚新装就出问题的人或者狠得下新重装 WSA 的  
        完全卸载你装的 2309 之后版本的 WSA ，然后去【历史安装包】里下载旧版 WSA（比如2301、2304等）安装，并把最新的 LSPosed 模块安装好。  
        然后再升级到 2309 之后的版本，从旧版升级是不会触发这个问题的。  
        注意一下如果从 2304、2305 等几个版本来新装。  
        需要安装后进入适用于 [Android](https://www.tjsky.net/tutorial/384#)™ 的 windows子系统设置，  
        将“阻止安装恶意应用”的开关关闭，然后重新再运行一次 run.bat 文件。  
        不然 Magisk 是会被系统杀软认为是恶意应用而被自动阻止安装。
    - 稍微复杂点的方式：适合已经装了一部分APP，用了一段时间，不想彻底重装的  
        详见github上的这个[issues](https://www.tjsky.net/goto/?url=https://github.com/MustardChef/WSABuilds/issues/154#issuecomment-1729105000)操作不难，看不懂英文，可以直接浏览器机器翻译一下。  
        ![](https://img.tjsky.net/2023/11/61a9981deec51c7ac768f21154203a44.png)
4. WSA突然只有支持X86_64框架的 [APP](https://www.tjsky.net/tutorial/384#)可以运行，  
    本质上是配置的问题，需要干净重装一下，步骤如下
    
    - 打开你的开始菜单
    - 点击`适用于Android™ 的 windows子系统设置`
    - 切换到系统窗口，找到`关闭适用于Android™ 的 windows子系统`，点击【关闭】按钮
    - 在系统任务管理器里结束残留的 WSA 进程(比如`WSACrashUploader.exe`)
    - 删掉原有WSA安装文件夹内的一切内容，如果有删不掉的，说明有残留WSA相关进程没删干净
    - 用新内容覆盖原有文件夹的内容。
    - 找到`run.bat`文件,双击运行。