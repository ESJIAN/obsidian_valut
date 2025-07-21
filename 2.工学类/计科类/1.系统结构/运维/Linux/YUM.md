
### RPM

**RPM包主要用于在Linux操作系统中管理软件包的安装、‌升级、‌卸载和查询等操作。‌**

RPM（‌[Red Hat](https://so.csdn.net/so/search?q=Red%20Hat&spm=1001.2101.3001.7020) Package Manager）‌是一种用于Linux系统的软件包管理工具，‌它允许用户对软件包进行安装、‌升级、‌卸载和查询等操作。‌

### YUM

Yum（全称为 Yellow dog Updater, Modified）是一个在[Fedora](https://baike.baidu.com/item/Fedora/3293972?fromModule=lemma_inlink)和RedHat以及[CentOS](https://baike.baidu.com/item/CentOS/498948?fromModule=lemma_inlink)中的Shell前端[软件包](https://baike.baidu.com/item/%E8%BD%AF%E4%BB%B6%E5%8C%85/10508451?fromModule=lemma_inlink)管理器。基于[RPM](https://baike.baidu.com/item/RPM/3794648?fromModule=lemma_inlink)包管理，能够从指定的服务器自动下载RPM包并且安装，可以自动处理[依赖性](https://baike.baidu.com/item/%E4%BE%9D%E8%B5%96%E6%80%A7/3927846?fromModule=lemma_inlink)关系，并且一次安装所有依赖的软件包，无须繁琐地一次次下载、安装。**YUM相当于在PRM基础上进行了封装，使用YUM后底层还是调用PRM进行包安装**


>所以YUM相当于Ubuntu的APT管理器

### YUM的好处

1. 用RPM安装需要手动下载包后在安装而yum是一种自动化的软件包管理工具，可以自动下载并安装软件包。
2. RPM只能安装指定的软件包，如果软件包依赖其他软件包，需要手动下载并安装所有依赖的软件包，yum自动解决软件包依赖关系，自动下载并安装所有依赖的软件包。
3. yum因为可以自动下载包所以更新包版本方便
4. yum操作命令简单

### YUM源配置

什么是yum源？yum安装rpm包的时候可以先把rpm包下载，然后再使用yum loaclinstall安装，但是要每次安装下载都需要手动找rpm包及依赖下载。**所以需要一个yum的仓库，可以直接通过 yum 进行访问完成 （下载/更新）动作**，配置好这个仓库后，就可以直接使用 install，upgrade，update，yum就会自己去这个仓库获取相应的rpm包进行操作。**配置仓库可以使用远程仓库，也可以使用本地仓库**。YUM源本质就是一个下载路径，通过这个路径可以获取RPM包，不管是远端源还是本地源。

#### YUM源格式

再 /etc/yum.reps.d下所有.repo后缀的文件都是用于配置YUM源的，打开其中**一个文件可以包含很多个源仓库的配置**，**下面为一个源仓库的基础结构**。

```
# 源标识 唯一自定义配置 
[base]
# 源名称 唯一自定义配置
name=CentOS-$releasever - Base - mirrors.aliyun.com
# 源的参数配置 priority为baseurl顺序尝试失败了获取下一关链接， roundrobin随机尝试
failovermethod=priority
# 源的位置
baseurl=http://mirrors.aliyun.com/centos/$releasever/os/$basearch/
        http://mirrors.aliyuncs.com/centos/$releasever/os/$basearch/
        http://mirrors.cloud.aliyuncs.com/centos/$releasever/os/$basearch/
#是否启用此源 1启用，0不启用 默认为启用
enabled=1
# 是否校验源 1校验 0不校验 防止源被篡改
gpgcheck=1
# 校验地址 如果gpgcheck为0 则不校验
gpgkey=http://mirrors.aliyun.com/centos/RPM-GPG-KEY-CentOS-7

配置完成后清理缓存
yum clean all
```

```
#查看已启用的源仓库配置 （enabled为1）
yum repolist enabled

下面截图为查询出的源名称 CentOS-7 - Base - mirrors.aliyun.com就是上面配置好的
```

![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/12736cf8dc204670b10e3afd5cd19d00.png)

#### YUM远程源

##### 远程源位置及内容

```
# 进入yum源位置
cd /etc/yum.reps.d
下面会有很多.repo文件，其中CentOs-Base.repo就是配置远程源的，配置远程源修改这一个文件即可
默认这个文件配置的应该是centos自带的源地址，所以只需要更换里面的地址即可,建议直接替换已经配置好的CentOs-Base.repo文件。
```

![外链图片转存失败,源站可能有防盗链机制,建议将图片保存下来直接上传](https://i-blog.csdnimg.cn/direct/1e05af2cda1a4d40860a038fadc75d96.png)

**CentOS-Base.repo（截图是已经替换后的）**

---

![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/5c9df677417f477f943089b5728542d9.png)

##### 更换远程源

```
# 阿里镜像里面包含了镜像源
http://mirrors.aliyun.com/repo/

看个人需要，再替换源前如果有需要可以把CentOS-Base.repo做个备份 

# 再linux下可以使用wget进行下载，下载Centos-7.repo 到/etc/yum.reps.d目录下，文件命名为CentOS-Base.repo
wget -O /etc/yum.reps.d/CentOS-Base.repo http://mirrors.aliyun.com/repo/Centos-7.repo
（也可以再windows下载好，然后使用远程链接工具拖到服务器上配置）

# yum缓存清理,把之前的索引删掉
yum clean all

# 创建缓存，用刚配置好的源下载软件包的元数据和索引信息，并将它们存储在本地缓存中，加快操作速度减少网络访问
yum makecache
```

![ea5b9fc2afe8.png)](https://i-blog.csdnimg.cn/direct/43bc27d491cc407ea9733bef1088bb61.png)

#### YUM本地源

##### yum源本地搭建（暂空）

**后续自己搭建本地源后会进行更新**

##### 本地源配置

**使用本地源大概率是因为服务器由于限制无法链接公网，所以内网一般都会自己搭建源。**

实质就是把baseurl路径换成了你本地存储rpm包的路径位置，这样再执行yum命令的时候baserurl就会去系统路径里面寻找rpm包了。如果把存储了rpm包的这个服务器当成yum源服务器开放访问权限，那么其实就相当于你把远端源迁移到了内网里面，**对别的机器来说，你搭建了yum源的服务器就是他们的远端源。**

```
# 进入源位置目录
cd /etc/yum.repos.d

# 备份下里面的文件 (觉得没用可以不备份)
tar -zcvf /备份路径/repos.bak.tar.gz *

# 删除配置
rm -rf *.repo

# 创建配置
vim /etc/yum.repos.d/ldsx.repo

[ldsxLocal] 自定义但是必须唯一
name=Centos 7.9 自定义
# 本地源路径,本地源存放路径，或者内网源访问路径
baseurl=file://本地源路径   本地位置（file:///home/ldsx/xxxx）  内网访问位置 http://源所在服务器ip/所在路径
# 是否启用 1启用，0不用
enabled=1
# 是否验证 0不验证
gpgcheck=0

# yum缓存清理,把之前的索引删掉
yum clean all

# 创建缓存，用刚配置好的源下载软件包的元数据和索引信息，并将它们存储在本地缓存中，加快操作速度减少网络访问
yum makecache
```

### YUM基本命令

#### 查看源仓库

```
# 展示所有源仓库
yum repolist all

# 展示启用的源仓库
yum repolist enabled

# 展示禁用的源仓库
yum repolist disabled
```

**展示所有**

![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/a85ea872c2b84e7da346a942e7635f4c.png)

#### 查看

```
# 列出可用rpm包列表，包括已装跟未装
yum list 
# 使用过滤条件
yum list | grep xxxx*
yum list xxxx*

# 查看已经安装的包
yum list installed

# 查找包，模糊查找
yum search 关键字

# 查找包，通过命令 如果你知道一个特定的文件 `xxx` 在你的系统中，但是你不知道是哪个软件包包含它可以使用
yum provides 要查询的可执行文件
如：yum provides ifconfig

# 查看包详情
yum info 包名称
```

![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/db0417baf2104a3489d9d9c106760e3a.png)

#### 下载带依赖的rpm包

**需要下载离线包**

```
#安装 Yumdownloader 工具
yum install yum-utils

#下载包并且把找个包所需要的依赖一起下载
yumdownloader --resolve  包名 （默认下载到当前目录）

# 下载到指定目录
yumdownloader --resolve --destdir <directory> <package-name>
yumdownloader --resolve --destdir 下载到本地目录 下载的包名
```

#### 安装

**一般情况配置源，使用源安装即可**

```
# yum源安装，会自动处理依赖 ， -y参数自动回答yes  ， --nogpgcheck 跳过gpgcheck环节
yum install 要安装的包名

# 已经按准过的包重新安装
yum reinstall 要安装的包名

# yum本地安装rpm包，无依赖
yum localinstall /xxxx/路径要安装的包

# yum本地安装rpm包，有依赖（前提本地已经下载好了所有依赖（下载方式见上节），rpm包放入同一目录 ）
yum localinstall /xxx/路径/*.rpm -y

# rpm安装方式，再下载完成rpm包的基础上，如果确认不需要依赖可以使用。（不推荐，可以了解）
rpm -ivh  /xxx/路径/要安装的包
```

#### 更新

```
# 查看可更新包
yum check-update
```

**upgrade**

更新包后删除旧包，当全部更新时不会对系统内核升级

```
#更新所有可以升级的包，只更新包
yum upgrade

#指定包更新
yum upgrade 指定包名
```

**update**

更新包后对旧包操作可控制（可删除可不删），还同时升级软件和系统内核确保系统的稳定性和安全性

```
#配置是否保留旧包
vi /etc/yum.conf 
其中obsoletes 1删除，0保留修改此参数控制是否保留包

#更新系统中已安装的软件包到最新版本，还同时升级软件和系统内核确保系统的稳定性和安全性
yum update

#指定包更新
yum upgrade 指定包名
```

#### 卸载

```
#卸载包名
yum remove 包名
```

#### 清理缓存

```
# yum缓存清理,把之前的索引删掉
yum clean all
```

#### 生成缓存

```
# 创建缓存，用刚配置好的源下载软件包的元数据和索引信息，并将它们存储在本地缓存中，加快操作速度减少网络访问
yum makecache
```