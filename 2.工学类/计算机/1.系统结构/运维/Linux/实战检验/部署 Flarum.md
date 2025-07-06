[仓库地址](https://github.com/0xffff-one/flarum-0x)

原文：[https://www.itnt.xyz/it/11/](https://www.itnt.xyz/it/11/)  


Flarum 是一款非常棒的开源论坛程序，在这里记录下非常详细的适用于宝塔+linux 的搭建步骤，供环境相同的同志们参考参考。

---

## 一、服务器环境说明

1. 宝塔 7.0.3 或更新版本
2. Linux Server（本文用的是 ==CentOs 7.4.6 64位==）
3. Apache 或者 Nginx（本文用的是 Nginx 1.16.0）
4. MySQL 5.6+（本文使用 MySQL 5.7，原因请看下方引用）
5. PHP 7.1+（本文 PHP-7.3）
6. phpMyAdmin 4.7

> MySQL 自 5.7 开始支持 FULLTEXT 中文搜索，后续方便我们优化 Flarum 论坛的中文关键词搜索。

---

## 二、安装宝塔 Linux 面板

使用 SSH 工具（[查看使用方法](https://www.bt.cn/bbs/thread-1971-1-1.html)），执行命令开始安装（大约2分钟完成面板安装）。

**Centos安装宝塔面板命令：**

`yum install -y wget && wget -O install.sh http://download.bt.cn/install/install_6.0.sh && sh install.sh`

执行安装命令，询问是否安装，回答 “ y ”

```ad-note
title:问题集
- Ubuntu没有yum组件
[Linux(Ubuntu系统)安装yum及源的更新(详细操作+文字描述！！！)_ubuntu 安装yum源-CSDN博客](https://blog.csdn.net/qq_45261963/article/details/117520995)
- yum：There are no enabled repos
[Ubuntu配置yum仓库](https://kimi.moonshot.cn/share/css7149mqu00462kh4u0)
```



[](https://s1.ax1x.com/2020/10/15/0ThQjU.png)![](https://s1.ax1x.com/2020/10/15/0ThQjU.png)

安装完成会打印这些东西（面板 ip 地址、用户名、密码）：

[](https://s1.ax1x.com/2020/10/15/0Th4KS.png)![](https://s1.ax1x.com/2020/10/15/0Th4KS.png)

图源：宝塔面板

---

## 三、安装 LNMP 环境

浏览器输入宝塔面板的 ip 地址。登陆账号，进入面板。

> 首次进入面板，在弹出的“推荐安装套件”窗口中选择左侧的**「LNMP 极速安装」**

选择好 PHP 等环境的版本号，点击一键安装后，会弹出消息盒子，等待任务执行完毕即可。

[](https://s1.ax1x.com/2020/10/15/0T4uad.png)![](https://s1.ax1x.com/2020/10/15/0T4uad.png)

> 需要注意的是，在 LNMP 安装完成之后，我们还需要安装一些 PHP 的扩展（exif / fileinfo），其中 fileinfo 是必须的，否则下面 Flarum 会安装失败。exif 是图片上传所需的扩展。

进入宝塔面板 – 【软件商店】 – 【已安装】，点击 PHP 设置。

[](https://s1.ax1x.com/2020/10/15/0T4NZQ.png)![](https://s1.ax1x.com/2020/10/15/0T4NZQ.png)

选择【安装扩展】，安装 fileinfo（opcache、exif 非必选）。

等待安装完毕。

[](https://s1.ax1x.com/2020/10/15/0T40Gq.png)![](https://s1.ax1x.com/2020/10/15/0T40Gq.png)  
　

---

## 四、安装 Composer

### 4.1 更新服务器软件包

使用 SSH 执行下方命令：

`yum update -y`

更新完左下角会提示 “ Complete! ”

[](https://s1.ax1x.com/2020/10/15/0T42dJ.png)![](https://s1.ax1x.com/2020/10/15/0T42dJ.png)

### 4.2 解除 PHP 函数禁用

_此步骤仅适用于宝塔面板用户，如您直接使用 OneinStack 一键安装服务器环境，请**跳过此步**。_

> 宝塔面板默认禁用一些安装 Composer 要用到的 3 个函数 `putenv()` 、 `pcntl_signal()` 、 `proc_open()`，我们需要**解除禁用**，否则导致步骤 4.3 Composer 变更源地址时报错、步骤 5.3 Composer 安装 Flarum 时报错。

如下图所示，进入宝塔面板，打开 PHP 设置，在【禁用函数】中，删除 `putenv` 、 `pcntl_signal` 以及 `proc_open`

[](https://s1.ax1x.com/2020/10/15/0T5SQf.png)![](https://s1.ax1x.com/2020/10/15/0T5SQf.png)

若您不取消这三个函数的禁用，则会出现以下问题：

1.   
    [](https://s1.ax1x.com/2020/10/15/0T5dmD.png)![](https://s1.ax1x.com/2020/10/15/0T5dmD.png)
2.   
    [](https://s1.ax1x.com/2020/10/15/0T5sfI.png)![](https://s1.ax1x.com/2020/10/15/0T5sfI.png)
3.   
    [](https://s1.ax1x.com/2020/10/15/0T5g6f.png)![](https://s1.ax1x.com/2020/10/15/0T5g6f.png)

### 4.3 安装 Composer

使用 SSH 依次执行以下命令：

　　　# （此步骤可省略）进入当前用户家目录

1. `cd`
    

　　　# 将安装脚本下载到当前目录

2. `php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');"`
    

　　　# 运行安装脚本

3. `php composer-setup.php --install-dir=bin --filename=composer`
    

　　　# 删除安装脚本

4. `php -r "unlink('composer-setup.php');"`
    

> 由于 Composer 的服务器在国外，可能导致下载 Flarum 已经依赖包会很慢，所以我们需要更换一下源地址。至于 Composer 是啥，其实就是 PHP 的一个包管理，类似 Java 的 Maven 和 Gradle 工具。  
> [——引用自 ryanc.cc](https://ryanc.cc/archives/flarum-install-and-config)

　　　# 变更全局范围内的 Composer 服务器地址：（如果您禁用了  
putenv() 函数，会导致此命令执行失败）。将 composer 源改成[阿里云的镜像](https://developer.aliyun.com/composer)

5. `composer config -g repo.packagist composer https://mirrors.aliyun.com/composer/`
    

---

## 五、安装 Flarum

### 5.0 设置设置PHP配置文件：

最大脚本运行时间（max_execution_time）：600  
脚本内存限制（memory_limit）：512M 或 1024M

### 5.1 新建存放 Flarum 的网站

前往宝塔面板 – 【网站】 – 【添加站点】，同时创建用于 Flarum 的数据库。最后提交。

> 务必注意！数据库字符集一定要是 utf8mb4，至于为什么是 utf8mb4，参考：  
> [https://www.jianshu.com/p/6967ce16a202](https://www.jianshu.com/p/6967ce16a202)

### 5.2 配置 SSL 证书

打开站点设置，进入 SSL 选项卡页面，挑选您想要配置的安全证书方式：

- [宝塔一键 SSL](https://www.bt.cn/ssl)（一年证书免费申请，需要登录宝塔账号并实名认证）
- [Let’s Encrypt 三个月免费证书](https://blog.csdn.net/msllws/article/details/82255078)
- [已有证书文件，上传至宝塔](https://yq.aliyun.com/articles/705391)

配置完成后，请注意开启 “ 强制 HTTPS ”！否则在 6.2 步骤中无法正常访问网站

### 5.3 下载 Flarum

> 因为 Flarum 要求安装目录必须是空目录，因此我们还需要删除刚刚新建的网站目录里的所有文件。

在 SSH 中执行：

　　　# 进入网站目录。注意网站目录每个人都不一样！记得替换！

1. `cd /www/wwwroot/example.com`
    

　　　# 解除 .user.ini 的文件锁定，否则该文件无法被删除

2. `chattr -i .user.ini`
    

> 然后在宝塔面板中（或者在 FTP 中）删除网站目录下的所有文件。

　　　# 确保进入网站目录执行（[前面也提到了](https://discuss.flarum.org.cn/d/2195#title-4.2)，若您禁用了`pcntl_signal()` 函数和 `proc_open()` 函数，此步执行会出错）

3. `composer create-project flarum/flarum .`
    

执行成功后会下载 Flarum 并更新依赖包。更新依赖包会根据服务器地理位置花费 十几秒 至 三十分钟 不等的时间，请耐心等待。

Flarum 以及对应的依赖安装完成应该是这个样子的：

[](https://s1.ax1x.com/2020/10/16/0HJsts.png)![](https://s1.ax1x.com/2020/10/16/0HJsts.png)  
　

---

## 六、配置运行

> 上面其实就已经安装好了 Flarum，但是还需要进一步配置才能正确运行。

### 6.1 修改 Nginx 配置

进入宝塔面板，打开站点设置，修改网站配置文件：(可对照下图修改)

1. **root**：需要在路径后面加上 `public`，比如原本是 `root /www/wwwroot/example.com;`，需要修改为 `root /www/wwwroot/example.com/public;`。
    
2. 引入 Flarum 提供的伪静态配置，在 `server name` 下方加上 `include /www/wwwroot/example.com/.nginx.conf;`，网站目录不要忘记更换成自己的。
    

[](https://s1.ax1x.com/2020/10/29/BG8Nzd.png)![](https://s1.ax1x.com/2020/10/29/BG8Nzd.png)

修改站点配置，别忘记保存

### 6.2 检查 Nginx 配置

修改完上一步的配置，在点击保存时，宝塔会自动检查，如有错误，会保存失败并弹窗提示。  
　

---

## 七、Flarum 安装引导

在浏览器中访问安装 Flarum 的站点网址。

可以看到出现下面的情况：

[](https://s1.ax1x.com/2020/10/15/0T7BKP.png)![](https://s1.ax1x.com/2020/10/15/0T7BKP.png)

> 这是因为没有给予网站目录写入的权限，我们加一下权限即可：

前往宝塔面板，点击左侧【文件】，（或者使用 SSH 工具）进入 `/www/wwwroot` 目录。

右击您的站点目录，选择【权限】，权限修改为 755 权限并保存。不要忘记勾选 “ 应用到子目录 ”。

接着刷新一下论坛网页就好了，根据图片提示填写好论坛信息。`数据库名`、`数据库用户名`、`数据库密码`都可以在宝塔面板查看。

[](https://s1.ax1x.com/2020/10/15/0THoQI.png)![](https://s1.ax1x.com/2020/10/15/0THoQI.png)

填写完数据库信息、管理员信息，点击安装即可。  
安装部署部分到此结束。  
　

---

## 八、常用插件安装

> 安装完成后会发现不支持中文，所以我们需要安装中文语言包。还有一些常用的插件。更多插件，请前往[插件标签](https://iflarum.cn/exts)查看。

　　　# xxx 为网站目录名称，因为安装插件需在 Flarum 根目录执行。

`cd /data/wwwroot/xxx`

　　　# [简体中文语言包](https://discuss.flarum.org.cn/d/1211)

　　　# [编辑器 Emoji 表情选择框](https://discuss.flarum.org.cn/d/1213)

　　　# 导[航栏菜单插件](https://discuss.flarum.org.cn/d/1350)

　　　# [显示帖子阅读次数](https://discuss.flarum.org.cn/d/1283)

　　　# [论坛用户名录](https://discuss.flarum.org.cn/d/1256)

　　　# [上传文件](https://discuss.flarum.org.cn/d/1292/28)

　　　# [Sitemap （网站地图）生成器](https://discuss.flarum.org.cn/d/1563)

　　　# [Fancybox 图片灯箱（放大）插件](https://discuss.flarum.org.cn/d/1526)

安装完成后去后台启用即可（后台地址：网址/admin）。

[](https://s1.ax1x.com/2020/10/15/0TbINF.png)![](https://s1.ax1x.com/2020/10/15/0TbINF.png)


以下是以 **Markdown 表格形式** 对 Flarum 插件的分类整理，涵盖核心功能、第三方集成、主题美化等维度：

---

### 🔧 核心功能插件

| 插件名称 | 功能描述 | 原生支持 |
|---------|----------|----------|
| Approval | 审核机制，设置用户组无需审核直接发布 | ✅ |
| BBCode | 基础 BBCode 标记语言支持 | ✅ |
| Emoji | 原生 Emoji 选择器（其他插件依赖项） | ✅ |
| Flags | 帖子举报功能（敏感词过滤前提） | ✅ |
| Likes | 点赞功能 | ✅ |
| Lock | 主题锁定，禁止回复 | ✅ |
| Markdown | Markdown 基础语法支持 | ✅ |
| Mentions | @提及功能 | ✅ |
| Pusher | 实时推送新主题/回复（实时聊天前提） | ✅ |
| Statistics | 仪表盘统计图表（无需额外下载） | ✅ |
| Sticky | 置顶帖子 | ✅ |
| Subscriptions | 订阅主题并接收通知 | ✅ |
| Suspend | 关闭讨论（禁止回复） | ✅ |
| Tags | 节点/标签管理 | ✅ |

---

### 🌐 第三方集成插件

| 插件名称 | 功能描述 | 原生支持 |
|---------|----------|----------|
| ACG Embed | 嵌入 Bilibili/AcFun 视频 | ❌ |
| Analytics | 集成 Google Analytics 和 Piwik | ❌ |
| Author Change | 管理员修改帖子作者 | ❌ |
| Bazaar | 插件市场（无需 Composer 安装） | ❌ |
| Doorman | 邀请码注册机制 | ❌ |
| Flagrow Direct Links | 通过 URL 打开登录/注册/编辑界面 | ❌ |
| Flagrow Sitemap | 生成站点地图 | ❌ |
| FoF Default User Preferences | 新用户默认开启邮件通知 | ❌ |
| FoF Filter | 敏感词过滤（审核后公开） | ❌ |
| FoF Formatting | 自动识别链接并嵌入媒体 | ❌ |
| FoF Linguist | 自定义多语言翻译 | ❌ |
| FoF Pages | 自定义 HTML 页面 | ❌ |
| FoF Pretty Mail | 自定义邮件模板样式 | ❌ |
| FoF Prevent Necrobumping | 防止挖坟（超时主题提醒） | ❌ |
| FoF Spamblock | 标记垃圾用户 | ❌ |
| FoF Subscribed | 管理员接收新主题/新用户通知 | ❌ |
| PWA | 渐进式 Web 应用支持 | ❌ |
| SEO | 搜索引擎优化 | ❌ |
| Web Push Notification | OneSignal 推送通知 | ❌ |

---

### 💬 用户互动插件

| 插件名称                        | 功能描述             | 原生支持 |
| --------------------------- | ---------------- | ---- |
| Announce                    | 顶部公告栏通知          | ❌    |
| Back to Top                 | 返回顶部按钮           | ❌    |
| Color Circles               | 用户组头像描边          | ❌    |
| Rainbow Comic Sans          | 动态彩虹文字特效         | ❌    |
| Diff                        | 帖子编辑记录追踪         | ❌    |
| Discussion Views            | 主题浏览次数统计         | ❌    |
| Emoji Picker                | 增强型 Emoji 选择器    | ❌    |
| FancyBox                    | 图片放大与排版优化        | ❌    |
| Flagrow Ads                 | 广告位管理（首页/楼层间）    | ❌    |
| FoF Best Answer             | 最佳答案功能（类似百度知道）   | ❌    |
| FoF Byōbu                   | 私密主题（指定用户可见）     | ❌    |
| FoF Drafts                  | 草稿箱功能            | ❌    |
| FoF Follow Tags             | 订阅标签更新通知         | ❌    |
| FoF Forum Statistics Widget | 首页统计信息展示         | ❌    |
| FoF Gamification            | 替代点赞按钮（支持踩）      | ❌    |
| FoF GeoIP                   | 记录发帖 IP 地址       | ❌    |
| FoF Links                   | 自定义导航栏链接         | ❌    |
| FoF Merge Discussions       | 合并主题功能           | ❌    |
| FoF Night Mode              | 夜间/日间模式切换        | ❌    |
| FoF Polls                   | 帖子内投票功能          | ❌    |
| FoF Profile Image Crop      | 头像裁剪功能           | ❌    |
| FoF Reactions               | 表情戳功能（非点赞）       | ❌    |
| FoF Share Social            | 社交分享按钮           | ❌    |
| FoF Social Profile          | 用户资料页添加社交媒体链接    | ❌    |
| FoF Split                   | 拆分主题为新讨论         | ❌    |
| FoF Terms                   | 注册时用户条款确认        | ❌    |
| FoF Upload                  | 允许上传图片/视频/文件     | ❌    |
| FoF User Bio                | 个性签名功能           | ❌    |
| FoF User Directory          | 用户名单展示           | ❌    |
| FoF Username Request        | 用户名修改申请          | ❌    |
| FoF reCAPTCHA               | 谷歌验证码防恶意注册       | ❌    |
| Link Decisions              | 外链打开方式选择         | ❌    |
| Mailing                     | 邮件群发功能           | ❌    |
| Money                       | 用户资产系统（发帖奖励）     | ❌    |
| Online Users                | 在线用户展示           | ❌    |
| Password Strength Indicator | 密码强度检测           | ❌    |
| Post Date                   | 修改帖子发布时间         | ❌    |
| Profile Views               | 用户最近访客记录         | ❌    |
| ReFlar Cookie Consent       | Cookie 同意横幅      | ❌    |
| ReFlar Level Ranks          | 经验等级系统           | ❌    |
| NeonChat                    | 在线聊天室（依赖 Pusher） | ❌    |
| Show Last Posts             | 显示最新回复内容         | ❌    |
| Show Password               | 注册/登录时显示密码       | ❌    |
| Sign Up Button              | 未登录时替换发布按钮为注册    | ❌    |
| Status                      | 用户心情状态           | ❌    |

---

### 🧩 内容格式化插件

| 插件名称 | 功能描述 | 原生支持 |
|---------|----------|----------|
| BBCode Alerts & Notifications | 插入提示框/警告框 | ❌ |
| BBCode FA | 插入 FontAwesome 图标 | ❌ |
| FoF BBCode Tabs | 插入标签选项卡内容 | ❌ |
| BBBBcode | 扩展 BBCode 样式 | ❌ |
| Login 2 See | 登录后可见内容 | ❌ |
| Reply 2 See | 回复后可见内容 | ❌ |

---

### 🔐 登录认证插件

| 插件名称 | 功能描述 | 原生支持 |
|---------|----------|----------|
| FoF Discord Login | Discord 账号登录 | ❌ |
| GitHub Login | GitHub 账号登录 | ✅ |
| Google Login | Google 账号登录 | ❌ |
| WeChat Login | 微信账号登录 | ❌ |
| Steam Login | Steam 账号登录 | ❌ |

---

### 🎨 主题美化插件

| 插件名称 | 功能描述 | 原生支持 |
|---------|----------|----------|
| Stargazing Theme | 观星主题（暗色系） | ❌ |

---

### 📌 使用建议

1. **必装核心插件**：  
   - `Approval`（审核）、`Flags`（举报）、`FoF Filter`（敏感词）、`FoF Upload`（上传）、`FoF Linguist`（多语言）。

2. **社区运营推荐**：  
   - `FoF Best Answer`（最佳答案）、`FoF Gamification`（积分系统）、`FoF Night Mode`（夜间模式）。

3. **性能优化**：  
   - `PWA`（渐进式应用）、`SEO`（搜索引擎优化）、`Statistics`（统计）。

4. **安全性**：  
   - `FoF reCAPTCHA`（验证码）、`FoF Spamblock`（垃圾用户标记）。

5. **第三方集成**：  
   - `Bazaar`（插件市场）、`Analytics`（统计）、`Web Push Notification`（推送）。

---

## 问题集锦

**问题描述**
```bash
    ERROR: failed to solve failed to do request: Head “https://registry-1.docker.io/v2/library/nginx/manifests/1.19.7”: EOF
```

**出现原因**

    更换了镜像仓库为国内镜像源；
    修改docker engine的配置；

这里贴一下我改后的配置，两处改动，增加了国内镜像源地址registry-mirrors，buildkit 改为false。配置文件路径为～.docker/daemon.json
```json
{
 "registry-mirrors": [ 
    "http://hub-mirror.c.163.com",
    "https://docker.mirrors.ustc.edu.cn/"
  ],
  "builder": {
    "gc": {
      "defaultKeepStorage": "20GB",
      "enabled": true
    }
  },
  "experimental": false,
  "features": {
    "buildkit": false
  }
}
```



**解决办法**

使用 docker system 的系列命令来清理镜像缓存。一般情况下，运维清理镜像是通过命令 docker rm i 删除镜像的。但是这条命令不会删除docker build命令产生的缓存文件。

先查看一下docker占用的存储空间情况，执行docker system df 。如图，Build Cache 为本地缓存，大小为15.11MB：
查看docker占用

执行命令docker builder prune，一键清除Build Cache缓存:
```bash
docker builder prune
```


执行命令后，会提示此操作将移除所有悬空镜像缓存，输入y确认，
清楚build cache
再次查看docker占用情况，Build Cache已清空，
在这里插入图片描述

深度清理
如果还是不行🙅，可以尝试使用docker system prune深度清理，此操作会删除所有未使用的容器、网络、镜像（包括悬空的和未引用的）以及卷（可选），务必谨慎操作！！！
docker system prune

对应可使用的参数：

    -a, --all：删除未被任何容器引用的所有镜像，而不仅仅是悬空镜像
    –force, -f：跳过确认步骤，直接执行删除；如果不用在执行步骤时需要手动确认，建议不用
    –volumes, -v：删除所有未被至少一个容器引用的卷
    –filter：根据提供的条件过滤要删除的内容
————————————————













**问题描述**


``` 
=> ERROR [internal] load metadata for docker.io/library/composer:latest                                                                                                30.3s
 => ERROR [internal] load metadata for docker.io/library/php:8.2-fpm-bookworm        
```

**问题分析**
1. Docker国内国外镜像源全部关站



Docker 镜像加速列表（2024年11月已更新）

    请注意！有些镜像站仅提供基础镜像或白名单镜像，如果某个加速地址无法拉取到所需的镜像，可以尝试切换到其他地址。有些站点是热心网友自费搭建的，请务必合理使用。如果侵犯了您的权益，请随时联系我，我会及时删除相关信息。感谢您的理解与支持！

DockerHub 镜像仓库	是否正常
hub.xdark.top	正常
hub.littlediary.cn	正常
dockerpull.org	新增
hub.crdz.gq	正常
docker.1panel.live	正常
docker.unsee.tech	新增
docker.m.daocloud.io	正常
docker.kejilion.pro	正常
registry.dockermirror.com	正常
hub.rat.dev	正常
dhub.kubesre.xyz	正常
docker.nastool.de	正常
docker.hpcloud.cloud	失效
docker.hlyun.org	失效
doublezonline.cloud	失效
docker.chenby.cn	失效
ginger20240704.asia	失效
lynn520.xyz	失效
hub.docker-ttc.xyz	失效
noohub.ru	失效
docker.nat.tf	失效
dockerproxy.cn	失效
freeno.xyz	失效
docker.registry.cyou	失效
hub.yuzuha.cc	失效
docker-cf.registry.cyou	失效
docker.mrxn.net	失效
dockerproxy.github.io	失效
docker.wget.at	失效
atomhub.openatom.cn	失效
ccr.ccs.tencentyun.com	失效
dockerproxy.com	失效
dislabaiot.xyz	失效
dockerpull.com	失效
hub.firefly.store	失效
配置方式1：临时使用

直接使用，直接拿镜像域名拼接上官方镜像名，例如要拉去镜像istio/distroless，可以用下面写法（不要带 https://）

docker pull docker.unsee.tech/istio/distroless


配置方式2：长久有效

    Ubuntu 16.04+、Debian 8+、CentOS 7+

修改文件 /etc/docker/daemon.json（如果不存在则需要创建创建，注意不要写入中文，要带https://），并重启服务。


```
sudo mkdir -p /etc/docker # 创建目录
```

``` bash
sudo tee /etc/docker/daemon.json <<-'EOF'  # 写入配置文件
{
    "registry-mirrors": [
    	"https://docker.unsee.tech",
        "https://dockerpull.org",
        "docker.1panel.live",
        "https://dockerhub.icu"
    ]
}
EOF
```

```bash
sudo systemctl daemon-reload && sudo systemctl restart docker #重启docker服务
```


可直接使用docker pull拉去镜像进行测试：

或用以下命令检查是否生效：

ping -c 3 docker.unsee.tech


————————————————






1. 问题详情

```bash
正在拉取 Trantor 基础环境镜像....
Pulling consul    ... 
Pulling redis     ... 
Pulling mysql     ... 
Pulling datastore ... 
Pulling console   ... 
Pulling workspace ... 
Pulling gateway   ... 
Pulling metastore ... 

ERROR: for workspace  docker-credential-desktop not installed or not available in PATH

ERROR: for redis  docker-credential-desktop not installed or not available in PATH

ERROR: for gateway  docker-credential-desktop not installed or not available in PATH
```


2. 原因：

大多为重新安装了docker-compose之后，~/.docker/config.json文件中配置不对

3. 解决办法：

删除rm -rf ~/.docker/config.json文件
————————————————










**问题描述**：
```
unable to access 'https://github.com/nvm-sh/nvm/': Failed to connect to github.com port 443 after 135941 ms:
```

**问题分析**：
```
这是由于node已不支持nvm，所以你会去查看nvm官方的解决方案，会给你提供最新的安装或者更新方法，还有各种问题的排查思路
```

**问题解决**
```
开VPN访问https://github.com/devcontainers/features/tree/main/src/node
```

```
手动安装
wegt https://github.com/devcontainers/features/blob/main/src/node/install.sh

. install.sh
```


nvm 常用操作命令：

    nvm ls 查看已经安装了的node版本
    nvm use vxx.xx.x 应用某个版本
    nvm alias default vxx.xx.x 设置默认当前电脑的默认版本，每次打开VScode等编辑器已版本为主；
————————————————



