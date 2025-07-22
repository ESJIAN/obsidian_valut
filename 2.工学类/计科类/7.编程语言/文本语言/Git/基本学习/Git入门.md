
# 1. 为什么需要用 Git 管理代码

每次代码写完，`Ctrl + Z` 按多了导致回退过度？亦或者是不小心删掉了某一行但是记不起来？又或者是这个版本代码出问题了想要回退？在没有 `Git` 时想做到上述实现会非常难受。但是一旦有了 `Git` ，上面的问题都解决了

![改变了世界的软件！程序员的基本功，Git 应该如何使用？_哔哩哔哩_bilibili](https://www.bilibili.com/video/BV1u94y1n73L/?spm_id_from=333.337.search-card.all.click&vd_source=4c095a1bfb5e2a56290ec68b55b5d467)



# 2. 安装 Git 

>**说明**：如果你是 Windows 系统这一章节看 2.1. 就可以了， macOS 和 Linux 不用看。

## 2.1 Windows篇：别再用绿色版了！

1. 访问官网下载：直接点击[Git for Windows/x64 Setup (github.com)](https://github.com/git-for-windows/git/releases/download/v2.49.0.windows.1/Git-2.49.0-64-bit.exe)下载。==如果你的下载速度太慢，请自己尝试分析原因（自己分析不出来把你的情况复述给AI让他分析）==
    
2. 一路点击Next（注意：安装路径得仔细确认，别安装错路径了）：
	
3. 验证安装是否成功：
    
    ```bash
    git --version
    ```
    
    看到类似`git version 2.41.0`的输出就对了！
    

## 2.2 macOS篇：两种姿势任你选

👉 **Homebrew大法**（推荐给技术控）：

```bash
brew install git
```

👉 **官方安装包**（适合小白）：  
直接下载`.dmg`文件双击安装，全程下一步就行（记得允许系统权限）

## 2.3 Linux篇：一行命令搞定

```bash
sudo apt-get install git  # Ubuntu/Debian
sudo yum install git      # CentOS/RedHat
```

# 3. 配置 Git

- # 4. 本章犯错

- ## 4.1. 未意识到全局代理优先局部代理

- 【问题描述】Git 拉取发生报错如下，尝试执行命令 `git config --global --get http.proxy ` ` git config --global --get https.proxy` 后依然有这个报错（此处本想不开梯子提交，但是由于设置了默认代理导致去用为开启服务的端口上传代码导致报错）

```bash
2025-06-26 18:33:25.659 [info] fatal: unable to access 'https://github.com/ESJIAN/Canteen_Statisic.git/': Failed to connect to 127.0.0.1 port 7890 after 2072 ms: Couldn't connect to server
```

- 【问题分析】终端输入 `git config --global --list` 发现设置了局部代理，即使取消了全局代理，局部代理也会生效。

```bash
PS C:\Users\Administrator\Documents\CODE\VsCode\python\Canteen_Statisic> git config --global --list
safe.directory=%(prefix)///192.168.1.106/temp/alipaymini_SDk
safe.directory=%(prefix)///192.168.1.106/xie/工程文件/pycharm
safe.directory=%(prefix)///192.168.1.106/xie/工程文件/pycharm/homework/ESP_Program
safe.directory=%(prefix)///192.168.31.193/hhd/1类-共享知识/谢承旭
user.name=ESJIAN
user.email=3340580252@qq.com
http.sslverify=false
http.sslbackend=openssl
credential.https://gitee.com.provider=generic
http.https://github.com.proxy=http://127.0.0.1:7890
https.https://github.com.proxy=https://127.0.0.1:7890
```

- 【方案尝试】取消局部代理，重新配置全局代理即可。下面是操作步骤

## 3.1 全局用户配置

>**说明**：配置全局用户主要会用到类似如下的命令模板（==粘贴此模板命令到终端回车没用，往下看！==）

```bash
git config --global user.name "xxx"
git config --global user.email "xxx"
```

1. 确保你有 GitHub 账号，如下图一所示，我的账号页面显示用户名为 ESJIAN，邮箱为 3340580252@qq.com 。


2. 然后根据命令模板修改好对应的内容，修改好后命令如下


3. 把这些命令粘贴到终端进行回车


4. 输入如下命令，验证刚刚的设置是否成功


5. 如果你的终端显示类似如下，那么你的全局用户配置就成功了

## 3.2 项目级配置（可选）

进入项目目录后执行：

```bash
git config user.name "项目专用马甲"
git config user.email "project@example.com"
```


## 3.3 让命令行更友好（可选）

```bash
git config --global color.ui auto  # 彩色输出
git config --global core.autocrlf input  # 智能换行符处理
git config --global alias.lg "log --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)  %Cres  # 超强日志别名
```

## 3.4  让命令行学会代理

>**引言**：如果你不做这么一步，那么往往在克隆 GitHub 上的项目时候总会遇上奇怪的 443 错误，有人可能会说我开了梯子但是为什么还是 443 这是因为，Git 命令自己的代理配置权限级别是要高于全局代理配置的，他会优先使用自己的代理，但是自己的代理往往都是直连。所以就会出现开梯克隆 GitHub 上的项目仍然会发生 443 的报错。

### 3.4.1. 设置全局代理

#### 1. 设置 HTTP 代理

>**说明**：设置Https的模板命令如下（==粘贴此模板命令到终端回车没用，往下看！==）

```bash
git config --global http.proxy http://<proxy-server>:<port>
```

查看系统代理设置好的默认端口，发现是 7897 ，那么配置本地代理命令如下

```
git config --global http.proxy http://127.0.0.1:7897
```

#### 2. 设置 HTTPS 代理

```bash
git config --global https.proxy https://<proxy-server>:<port>
```

查看系统代理设置好的默认端口，发现是 7897 ，那么配置本地代理命令如下

```
git config --global https.proxy http://127.0.0.1:7897
```

将 `<proxy-server>` 替换为你的代理服务器地址，`<port>` 替换为对应的端口号。

#### 3. 取消代理（可选）

因为当你配置好了 Git 代理的时候，如果你把代理工具关了会发生无法访问的报错，所以如果此时你想取消代理设置，可以使用以下命令：

```bash
git config --global --unset http.proxy 
git config --global --unset https.proxy
```

#### 4. 查看代理（可选）

你可以通过以下命令查看当前的代理设置：

```bash
git config --global --get http.proxy 
git config --global --get https.proxy
```

以上命令会修改 Git 的全局配置文件，通常位于 `~/.gitconfig`。

>**Ps**：如果你想要查看 Git 的全局配置，输入命令 `git config --global --list` 即可，终端会输出类似如下信息

```bash
PS C:\Users\Administrator\Documents\CODE\VsCode\python\Canteen_Statisic> git config --global --list
safe.directory=%(prefix)///192.168.1.106/temp/alipaymini_SDk
safe.directory=%(prefix)///192.168.1.106/xie/工程文件/pycharm
safe.directory=%(prefix)///192.168.1.106/xie/工程文件/pycharm/homework/ESP_Program
safe.directory=%(prefix)///192.168.31.193/hhd/1类-共享知识/谢承旭
user.name=ESJIAN
user.email=3340580252@qq.com
http.sslverify=false
http.sslbackend=openssl
credential.https://gitee.com.provider=generic
http.https://github.com.proxy=http://127.0.0.1:7890
https.https://github.com.proxy=https://127.0.0.1:7890
```

### 3.4.2. 设置局部代理

>**引言**：有些时候使用 Git 技术的网站有些在国外（Gitlab）有些在国内（Gitee），如果全局给设置死了的话很可能出现一方访问不了的情况，这个时候就有必要设置局部代理了。

#### 1. 设置 HTTP 代理

```shell
git config --global http.https://github.com.proxy http://<proxy-server>:<port>
```

#### 2. 设置 HTTPS 代理

```shell
git config --global https.https://github.com.proxy https://<proxy-server>:<port>
```

由于我们实验室的 IStore OS 服务器设置了 VPN 服务器功能，所以只需要

#### 3. 取消代理（可选）

若你为 GitHub 手动配置了如下代理

```bash
http.https://github.com.proxy=http://127.0.0.1:7890
https.https://github.com.proxy=https://127.0.0.1:7890
```

可以使用如下命令去取消对于这个网站设置的局部代理

```bash
git config --global --unset http.https://github.com.proxy 
git config --global --unset https.https://github.com.proxy 
```

#### 4. 查看代理（可选）


# 4. 命令行使用 Git 

## 4.1. 从本地创建新项目并推送到远程仓库

>**背景**：

### 4.1.1. 初始化项目
完成所有步骤后，在命令行依次执行：

```bash
mkdir test-project # 初始化项目文件夹
cd test-project    # 进入项目文件夹
git init           # git 初始化
echo "Hello Git" > README.md #  
git add .          # 将所有文件添加到暂存区
git commit -m "初始提交" # 将暂存区内的文件提交
```

如果顺利看到类似`[main (root-commit) 5f4b5c6] 初始提交`的提示，恭喜你正式加入Git玩家行列！

### 4.1.2. 关联远程仓库

### 4.1.3. 添加至暂存区

### 4.1.4. 初始化本地提交

### 4.1.5. 拉取远程更改

### 4.1.6. 同步本地更改到云端

## 4.2. 从远程拉取项目并推送到远程仓库

>**背景**：

### 4.2.1. 克隆项目

### 4.2.2. 修改代码

### 4.2.3. 添加至暂存区

### 4.2.4. 提交到本地提交

### 4.2.5. 同步本地更改到云端

# 5. Vscode 中使用 Git 

## 5.1. 检查 Git 

1. 打开 Vscode[^1] （假设你以及安装好 Vscode了）

2. 配置 Vscode 语言为简体中文（假设你已经配置好了）

3. 启动完成后检查侧边面板是否出现如图所示图标
	![](https://i-blog.csdnimg.cn/direct/ef98ff69cc7a41c487236636f9df3c2d.png)

## 5.2. 安装插件

安装这三个插件，这三个插件可以帮助你查看历史提交记录和分支管理

![](https://i-blog.csdnimg.cn/direct/ae4cd3472cda4d1cad9d8dd6b9346bea.png)


## 5.3. 使用插件





### 5.3.1. 克隆仓库

1. 打开一个 Github 的仓库网址，以 [STA Git 教学仓库]() 作练习，打开后界面如下

![image.png](https://i0.hdslb.com/bfs/openplatform/91fe6f92cfb0fd53fafb110d650d5f4f066806aa.png)


2. 点击 Code 按钮 --> 点击 HTTPS --> 点击复制按钮

![image.png](https://i0.hdslb.com/bfs/openplatform/e14c28563eceef5cc16d5eef4df4a79fe54ac12e.png)

3. 切回 Vscode --> 点击文件 --> 新建窗口 


4. 点击克隆仓库

![](https://i-blog.csdnimg.cn/direct/977122dd41e5495db03b164258151745.png)

5. 在弹窗中粘贴刚刚复制的URL

![](https://i-blog.csdnimg.cn/direct/942c6a32b1204cbe9d7c20070d91a490.png)

5. 在弹出的文件选择器中选择一个文件夹用来保存你的项目

![](https://i-blog.csdnimg.cn/direct/b1cfbe5bd8174858960f88f73cafeab0.png)

6. 克隆完后会弹窗提示，我们打开刚刚克隆的仓库

![](https://i-blog.csdnimg.cn/direct/60817faa2a7d40e191ee517ddd5e7648.png)

 7. 这样我们就能看到仓库的工程目录了，到这里克隆仓库完成

![](https://i-blog.csdnimg.cn/direct/67a6a22e5294409094da56f1803b6ba0.png)

### 5.3.2. 提交代码

1. 在克隆


2. 修改保存的文件都在这个框会显示，暂存更改就是相当于命令行的 git add，我们先点击暂存更改

![](https://i-blog.csdnimg.cn/direct/4dd44d30db78485ea4f0439661e92bd5.png)

 填写完后点击提交就提交到本地仓库，再同步提交到远程。这里相当于命令行的 git push

![](https://i-blog.csdnimg.cn/direct/86216e9a809940f599fb90a4aaf975a5.png)

![](https://i-blog.csdnimg.cn/direct/6bea9375b5d14a2fb7a2b3f4df94b28a.png)

如果想撤回暂存的提交也可以点击 撤销上次提交就可以退回未提交前的状态了

![](https://i-blog.csdnimg.cn/direct/9fd794249bc748adbf6d1dd6a2408152.png)

### 5.3.3. 分支管理

#### （1）创建分支

![](https://i-blog.csdnimg.cn/direct/401babdf5e9d479ebfad7ca197d1b23a.png)

 输入你新分支的名字，我这里就设置为feature-led-name，后面的name就是你的名字，关于分支的命名规范，你们的可以搜下git命名规范照着命名就可以了

![](https://i-blog.csdnimg.cn/direct/c3efe8bbab554511b9fca81960c0b08f.png)

创建分支成功会自动切换程新建的分支，然后就可以开始写代码了，如下图所示：

![](https://i-blog.csdnimg.cn/direct/07416947b22d4fd5b56dc832bca69d04.png)

#### （2）切换分支

这里分本地分支和远程分支，本地分支就是你新建的分支还没推到远程仓库上面的，其他仓库组成员是看不到的，远程分支则是已经推送到了远程仓库的分支，其他组成员是能拉到本地进行开发的分支，点击你想切换的分支进行切换即可

![](https://i-blog.csdnimg.cn/direct/93ffd8df325d47ceafd131e21157aeea.png)

这里有个容易忽略的地方，就是切换分支之前，一定要把修改的东西先提交或者撤销，否则会切换不成功

![](https://i-blog.csdnimg.cn/direct/a1f92dd90f4c4bdb9bd433caf4904ce2.png)

#### （3）合并分支

合并分支就可以用到我们刚刚安装的那三个插件的其中之一git graph了，打开git graph，可以看到仓库分支代码提交的作者、日期、分支创建、合并等等信息，非常方便

![](https://i-blog.csdnimg.cn/direct/01f1a6f4a2f34aeda0e7654e2d49680c.png)

提交完代码后，先切换到你要合并的分支，例如release分支，然后右击要合并的分支

![](https://i-blog.csdnimg.cn/direct/349770f1be9b471a9b79da038057620b.png)

![](https://i-blog.csdnimg.cn/direct/dd9f2e29d1bc4cc18cc868dbb58f179e.png)

合并完再同步提交到远程仓库就大功告成了

![](https://i-blog.csdnimg.cn/direct/d0e7a67928b34092b02d23490bf20732.png)

### 5.3.4. 创建标签和推送标签

![](https://i-blog.csdnimg.cn/direct/7ebbee82db804be8a9bc4ddc77cad57d.png)

![](https://i-blog.csdnimg.cn/direct/e582abda3d3441748fc389727e4af1e0.png)

### 5.3.5. 解决冲突

这时候又用到刚刚安装的三个插件之一GitLens了，解决完冲突重新提交即可

![](https://i-blog.csdnimg.cn/direct/8b87cd6bb50d434db812f911dec641dc.png)

### 5.3.6. 仓库同步

![](https://i-blog.csdnimg.cn/direct/ca52db69cc614dc4aa10a9d3aa521eae.png)

### 5.3.7. 评审代码

点击你要reivew的分支就可以看到别人提交的代码和信息了，点击文件就可以开始查看了

![](https://i-blog.csdnimg.cn/direct/9e71518329374d5083b0eacff492131a.png)

左边是提交前的代码，右边是提交后的代码，一目了然知道他修改了什么

![](https://i-blog.csdnimg.cn/direct/11997a3603eb480ab5e33b31c4ba3522.png) ![](https://i-blog.csdnimg.cn/direct/8124f8e6f9434cbc98d6a37cdb4a8bfd.png)



# 6. SSH密钥配置（选做）

## 6.1 生成密钥对

```bash
ssh-keygen -t ed25519 -C "your_email@example.com"
```

连按三次回车（不要设密码！后面会教你怎么安全保存）

## 6.2 添加密钥到Git服务

- 查看公钥：
    
    ```bash
    cat ~/.ssh/id_ed25519.pub
    ```
    
- 复制到GitHub/GitLab的SSH Keys设置页面

## 6.3 测试连接

```bash
ssh -T git@github.com
```

看到`You've successfully authenticated`就是成功啦！

# 7. 报错集锦

## 7.1 报错：git不是内部命令

说明环境变量没配置好！重新安装时务必勾选`Add to PATH`，或者手动添加安装目录到系统Path

## 7.2 中文乱码问题

在git bash里执行：

```bash
git config --global core.quotepath false
```

## 7.3 记住密码的正确姿势

别再用明文存储密码了！推荐使用官方的Git Credential Manager：

```bash
git config --global credential.helper manager
```

[^1]: [如何在VsCode中使用git（免敲命令版本！保姆级！建议收藏！）_vscode git-CSDN博客](https://blog.csdn.net/lijiemeiyyds/article/details/148380409)
