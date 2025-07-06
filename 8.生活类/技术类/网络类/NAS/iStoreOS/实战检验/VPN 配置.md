# 基础： 安装 OpenClash 

iStoreOS 是一个经过修改的 Openwrt 版本，目标是提供一个人人会用的路由兼轻 NAS 系统，不管是作为路由还是 轻NAS ，你都能拥有较为轻松的操作体验。但总所周知，买软路由就是为了科学上网的，所以安装一个 OpenClash 之类的插件是有必要的。

![](https://topstip.com/wp-content/uploads/2024/05/iStore-OS-%E6%A6%82%E8%A7%88.png)

iStore OS 默认搭载了 Argon 主题，界面非常清晰易懂

OpenClash 是一个可运行在 OpenWrt 上的  [Clash](https://github.com/Dreamacro/clash)  客户端，兼容 Shadowsocks、ShadowsocksR、Vmess、Trojan、Snell 等协议，根据灵活的规则配置实现策略代理，虽然之前有 Clash 删库风波，但旧版本的 Clash 核心任然可以继续使用，并且还有一些作者进行维护，所以继续使用 Clash 问题不大。

安装 OpenClash 首先需要下载 IPK 包，访问 OpenClash 的 [Github](https://github.com/vernesong/OpenClash) 界面，找到 [IPK下载链接](https://github.com/vernesong/OpenClash/releases)，新版本默认的包已经和以前的版本不同，不需要根据自己软路由的 CPU 架构 进行选择，能自动部署在任意架构的软路由上，也可以下载 [Source code](https://github.com/vernesong/OpenClash/archive/refs/tags/v0.46.003-beta.tar.gz) 自己进行编译安装。（如果你下载不下来或是速度太慢，我们也提供了网页下载，请到文末自取）

## 安装注意事项

- 请先安装好这两个依赖:

## iptables



```
opkg updateopkg install coreutils-nohup bash iptables dnsmasq-full curl ca-certificates ipset ip-full iptables-mod-tproxy iptables-mod-extra libcap libcap-bin ruby ruby-yaml kmod-tun kmod-inet-diag unzip luci-compat luci luci-base
```

## nftables



```
opkg updateopkg install coreutils-nohup bash dnsmasq-full curl ca-certificates ipset ip-full libcap libcap-bin ruby ruby-yaml kmod-tun kmod-inet-diag unzip kmod-nft-tproxy luci-compat luci luci-base
```

安装好依赖之后，进行如下操作：

![](https://topstip.com/wp-content/uploads/2024/05/%E5%AE%89%E8%A3%85-OpenClash.png)

- 系统-软件包
- 更新列表
- 上传 软件包 （即你刚才下载的 ipk 文件）

系统会自动安装软件包，但安装完成后还不能使用代理，因为安装这个软件包只是有了一个软件前端，还需要导入内核文件才能正常使用，方法非常简单：

![](https://topstip.com/wp-content/uploads/2024/05/%E5%AF%BC%E5%85%A5%E5%86%85%E6%A0%B8.png)

首先来到 iStore OS 首页，点击文件管理

![](https://topstip.com/wp-content/uploads/2024/05/%E5%86%85%E6%A0%B8%E8%B7%AF%E5%BE%84.png)

点开路径 root/etc/openclash/core/ ，不要关闭这个窗口，因为随后要将下载的内核文件放到这个路径

## 下载内核文件

- 重新开一个浏览器标签页，点开 服务- OpenClash -插件设置-软件更新
- 这时候你会注意到界面上提示您文件不存在，点击右边的下载到本地，分别下载 Clash 内核，Tun模式内核 ；Meta 内核 （如果无法下载可以到文末下载）
- 解压压缩包后将三个内核文件放到上述的路径中即可
- 重启 Clash 控制台 

![](https://topstip.com/wp-content/uploads/2024/05/%E5%AE%8C%E6%88%90%E4%B8%8B%E8%BD%BD.png)

如果操作正确，你就会看到界面变成这样，没变也不用着急，可以试试重启软路由

之后就和其他平台的各类 Clash 使用方法相同，导入您的订阅链接即可。

文件下载：

[IPK](https://topstip.com/wp-content/uploads/2024/05/IPK.zip)[下载](https://topstip.com/wp-content/uploads/2024/05/IPK.zip)

[内核文件](https://topstip.com/wp-content/uploads/2024/05/%E5%86%85%E6%A0%B8%E6%96%87%E4%BB%B6.zip)[下载](https://topstip.com/wp-content/uploads/2024/05/%E5%86%85%E6%A0%B8%E6%96%87%E4%BB%B6.zip)


# 进阶：配置旁路由 VPN 服务器

### 配置旁路由地址

>**引言**：由于传统一个电脑一个 Clash 客户端的方案存在着一个致命缺陷，就是

![image.png](https://i0.hdslb.com/bfs/openplatform/1f6dc0800220746e2250fc807c6c4eab4171fff1.png)



配置旁路由登录OpenWrt后台之后，进入【网络向导】中有傻瓜式引导功能【配置为旁路由】，当然也可以使用【高级模式】，自己来配置[^1]

![群晖安装OpenWrt（iStoreOS）构建旁路由配置](https://www.moluyao.wang/wp-content/uploads/2023/08/unnamed-file-1109.png "群晖安装OpenWrt（iStoreOS）构建旁路由配置插图18")

小白一般选择自动配置就行

![image.png](https://i0.hdslb.com/bfs/openplatform/f52d809727e8d944368379adefc9b54326556490.png)

关闭 “提供DHCPv4服务” 按钮，然后点击保存配置。 

![image.png](https://i0.hdslb.com/bfs/openplatform/786790bba2a1fec5f3e02255299e58f0503ef675.png)



### 旁路路由测试

测试旁路由可以用电脑配置一个IP地址测试一下，只要能上网就表示成功了，主要是把网关和DNS指向旁路由的固定IP：192.168.31.2。

![群晖安装OpenWrt（iStoreOS）构建旁路由配置](https://www.moluyao.wang/wp-content/uploads/2023/08/unnamed-file-1111.png "群晖安装OpenWrt（iStoreOS）构建旁路由配置插图20")





安装OpenClash插件iStoreOS提供的OpenWrt【服务】中已经自带几个插件，如果不需要可以手动关掉。

推荐使用iStore固件，便捷菜单下可以安装一些常见的插件，比较方便。

**注意**：安装插件有一定风险，虚拟机可以先拍个快照，万一系统崩溃可以快速回退

下载OpenClash目前要安装OpenClash，最好升级下内核，不然可能会报错，安装好依赖

```
#iptables opkg update opkg install coreutils-nohup bash iptables dnsmasq-full curl ca-certificates ipset ip-full iptables-mod-tproxy iptables-mod-extra libcap libcap-bin ruby ruby-yaml kmod-tun kmod-inet-diag unzip luci-compat luci luci-base
```

```
#nftables opkg update opkg install coreutils-nohup bash dnsmasq-full curl ca-certificates ipset ip-full libcap libcap-bin ruby ruby-yaml kmod-tun kmod-inet-diag unzip kmod-nft-tproxy luci-compat luci luci-base
```

### 安装 OpenClash

**下载地址1：** https://downloads.openwrt.org/snapshots/targets/x86/64/packages/kernel_**************.ipk

**下载地址2：**

https://github.com/vernesong/OpenClash/releases

**下载地址3：**

https://ghproxy.com/https://github.com/vernesong/OpenClash/releases/download/v0.45.78-beta/luci-app-openclash_************.ipk

上传并安装先上传到OpenWrt中，在【系统】-【文件传输】中把下载的两个文件都上传到/tmp/upload目录下：

![群晖安装OpenWrt（iStoreOS）构建旁路由配置](https://www.moluyao.wang/wp-content/uploads/2023/08/unnamed-file-1113.png "群晖安装OpenWrt（iStoreOS）构建旁路由配置插图22")

kernel的ipk可以在界面点安装，不过OpenClash要在安装好依赖之后才能点击安装，可以都在终端用命令安装。

进入终端（默认账号是root/password，如果修改过密码，使用自己修改后的密码），按照OpenClash的文档安装依赖

![群晖安装OpenWrt（iStoreOS）构建旁路由配置](https://www.moluyao.wang/wp-content/uploads/2023/08/unnamed-file-1114.png "群晖安装OpenWrt（iStoreOS）构建旁路由配置插图23")

**# 升级核心，不升级可能会提示 pkg_hash_check_unresolved: cannot find dependency kernel**

```
opkg install /tmp/upload/kernel_5.15.86-1-9f9e11a5e946333b83ba37f6864e5c49_x86_64.ipk
```

**# 升级 opkg update**

**# 安装依赖**

```
opkg install coreutils-nohup bash dnsmasq-full curl ca-certificates ipset ip-full libcap libcap-bin ruby ruby-yaml kmod-tun kmod-inet-diag unzip kmod-nft-tproxy luci-compat luci luci-base
```

 安装OpenClash opkg install /tmp/upload/luci-app-openclash_********.ipk安装成功之后，在【服务】中就有【OpenClash】了。** （有些固件已经自动安装就不需要再次安装了，必须下面推荐的高大上）


### 配置 OpenClash

配置OpenClash在配置文件订阅中，新增自己的订阅地址。

![群晖安装OpenWrt（iStoreOS）构建旁路由配置](https://www.moluyao.wang/wp-content/uploads/2023/08/unnamed-file-1115.png "群晖安装OpenWrt（iStoreOS）构建旁路由配置插图24")

启动OpenClash之后，可以看到网站访问性检查已经正常了，说明路由器已经能够访问外网了。

![群晖安装OpenWrt（iStoreOS）构建旁路由配置](https://www.moluyao.wang/wp-content/uploads/2023/08/unnamed-file-1116.png "群晖安装OpenWrt（iStoreOS）构建旁路由配置插图25")

接下来关闭 SOCKS5/HTTP(S) VPN代理验证，防止连接代理旁路由服务器时，浏览器蹦出一个账号密码验证弹窗[^1]

点击 Openclash 设置面板的覆写设置

![image.png](https://i0.hdslb.com/bfs/openplatform/1ed6fb1dc32d3b0d9ed2e55fb8e2846a993cc7d5.png)

向下滑动找到  SOCKS5/HTTP(S)  认证信息这一栏，然后点击删除

![image.png](https://i0.hdslb.com/bfs/openplatform/00eab9eb546655031247605e37fdc581de9274c5.png)

然后依次点击保存和应用配置信息

![image.png](https://i0.hdslb.com/bfs/openplatform/d9df38865a1b8b1802b5ec88c8090a1d08d6c0b1.png)

回到运行状态点击 Dashboard 控制面板

![image.png](https://i0.hdslb.com/bfs/openplatform/c5bd8ec61114ddefe30e1f706170fb125d92770e.png)

在 Dashboard 控制面板中点击设置条目

![image.png](https://i0.hdslb.com/bfs/openplatform/d2ea4718fe603c1928a470ce56f2067274414443.png)

打开你电脑设置搜索代理设置，然后对照下表填写代理地址和代理端口

![image.png](https://i0.hdslb.com/bfs/openplatform/813da4fa0cdee9b34014a7ac27d04e2ed26a5bbb.png)

点击保存，然后点击开启代理

![image.png](https://i0.hdslb.com/bfs/openplatform/06d8cfaa4ee4ecd9896c1a7da2ab486fcd49c4f9.png)

打开油管随便看一段视频，发现流量已被成功代理

![image.png](https://i0.hdslb.com/bfs/openplatform/826439f62ea774ad1706ddaf2db3df93ce6615a9.png)

如果你因为开了 VPN 导致某些国内网站访问较慢，在系统设置-->代理-->手动代理-->关闭 使用代理服务即可解决国内网站访问慢或者不给访问的问题，等到需要用的时候再重复前面说的步骤给他开起来即可。

![image.png](https://i0.hdslb.com/bfs/openplatform/1c7e8382c0bf50fc656cbb7d3b3fb310cd2d1a06.png)


## 管理 OpenClash



## 问题集锦

- 【】


[^1]: [开启openclash后，局域网其他设备代理时需要输入账号密码 · vernesong/OpenClash · Discussion #4198](https://github.com/vernesong/OpenClash/discussions/4198)
