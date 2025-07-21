## 什么是Gitea

> `Gitea` 是一个开源社区驱动的轻量级代码托管解决方案，后端采用 Go 编写，采用 MIT 许可证.  
> **官网**：[https://gitea.io/zh-cn/](https://gitea.io/zh-cn/)  
> ![img](https://i-blog.csdnimg.cn/blog_migrate/6e6f3fe153ec4dadd6a642d02823e312.png)

## 一、源代码安装方式

> 实验环境为MacOS系统，Windows系统以下操作大同小异
> 
> **官方文档**：[https://docs.gitea.io/zh-cn/install-from-source/](https://docs.gitea.io/zh-cn/install-from-source/)

### 1. 前置环境要求

- Go环境安装（版本要求大于1.16，一定要设置`$GOPATH` 环境变量，并将其bin目录添加到$PATH中）
    - [Go语言环境搭建(Windows+Linux)_欢迎来到 Baret~H 的博客-CSDN博客](https://bareth.blog.csdn.net/article/details/117433613)
- Node.JS环境安装（版本要求大于等于12.17，用于构建js和css文件，建议安装最新版本）
    - [Node.JS安装教程_欢迎来到 Baret~H 的博客-CSDN博客](https://bareth.blog.csdn.net/article/details/106947546)
- 数据库环境安装，建议MySQL
    - [MySQL最新版8.0.21安装配置教程_欢迎来到 Baret~H 的博客-CSDN博客](https://bareth.blog.csdn.net/article/details/107369405)

```shell
# 我的环境
zhongsiru@zhongsirudeMacBook-Air ~ % go version
go version go1.17.1 darwin/arm64
zhongsiru@zhongsirudeMacBook-Air ~ % node -v   
v14.17.6
zhongsiru@zhongsirudeMacBook-Air ~ % npm -v    
8.1.3
zhongsiru@zhongsirudeMacBook-Air ~ % mysql -V
mysql  Ver 8.0.27 for macos11 on x86_64 (MySQL Community Server - GPL)
```

### 2. 下载gitea

- Github：[https://github.com/go-gitea/gitea](https://github.com/go-gitea/gitea)
- Gitee镜像：[https://gitee.com/mirrors/gitea](https://gitee.com/mirrors/gitea)

通过git将项目下载到`$GOPATH/src`目录下

```shell
git clone https://github.com/go-gitea/gitea
```

### 3. 构建运行

下载完成后用Goland打开，在项目根目录下使用以下命令安装各种前端依赖，下载好的依赖在项目根目录下生的`node_modules`目录中

```shell
npm install
```

然后通过以下目录构建后端代码

```shell
TAGS="bindata" make backend
```

![image-20211230150012039](https://i-blog.csdnimg.cn/blog_migrate/dd9969a73ff7323f5b41bb5e10fc4b8d.png)

构建完成后，会在项目根目录下生成`gitea`可执行文件，我们使用以下命令来启动项目

```shell
./gitea web
```

![image-20211230150148194](https://i-blog.csdnimg.cn/blog_migrate/9fd3caa5830f47b6b10a4ee9dc08ed01.png)

启动成功后我们访问本机的3000端口，可以看到如下界面：

![image-20211230151654530](https://i-blog.csdnimg.cn/blog_migrate/cb1f033ef4ad1587e06b338b2cb03158.png)

这里我们配置我们所安装的mysql数据库和密码即可，这里的数据库名称需要我们提前创建一个数据库，这里创建的名称为`gitea`，此外还可以更改站点名称为自己想要的名称。

设置更新完后，点击安装即可，然后就进入到gitea的控制台，到此即安装配置成功。

![image-20211230152309941](https://i-blog.csdnimg.cn/blog_migrate/ee2862cc687b92be9451cf47d5f688a9.png)

---

  

## 二、[Docker安装](https://so.csdn.net/so/search?q=Docker%E5%AE%89%E8%A3%85&spm=1001.2101.3001.7020)方式

> 实验环境为CentOS7.6服务器，可以使用任意云厂商或者centos虚拟机
> 
> **官方文档**：https://docs.gitea.io/zh-cn/install-with-docker/

### 1. Docker安装

**官方文档**：[Install Docker Engine on CentOS | Docker Documentation](https://docs.docker.com/engine/install/centos/)

```shell
# 1.移除以前docker相关包
sudo yum remove docker \
                  docker-client \
                  docker-client-latest \
                  docker-common \
                  docker-latest \
                  docker-latest-logrotate \
                  docker-logrotate \
                  docker-engine

# 2. 配置yum源
sudo yum install -y yum-utils
sudo yum-config-manager \
--add-repo \
http://mirrors.aliyun.com/docker-ce/linux/centos/docker-ce.repo

# 3. 安装docker
sudo yum install -y docker-ce docker-ce-cli containerd.io

# 4. 启动docker
systemctl enable docker --now

# 5. 配置阿里云加速
sudo mkdir -p /etc/docker
sudo tee /etc/docker/daemon.json <<-'EOF'
{
  "registry-mirrors": ["https://82m9ar63.mirror.aliyuncs.com"],
  "exec-opts": ["native.cgroupdriver=systemd"],
  "log-driver": "json-file",
  "log-opts": {
    "max-size": "100m"
  },
  "storage-driver": "overlay2"
}
EOF
sudo systemctl daemon-reload
sudo systemctl restart docker
```

以上操作完成后，我们可以使用 `systemctl status docker`来查看 Docker 服务是否启动

![docker](https://i-blog.csdnimg.cn/blog_migrate/ce15834533227e7f7bd0791fbde06853.png)

### 2. Dokcer Compose安装

**官方文档**：[Install Docker Compose | Docker Documentation](https://docs.docker.com/compose/install/)

```shell
# 1.安装docker compose
sudo curl -L "https://github.com/docker/compose/releases/download/1.29.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose

# 2.赋予下载的docker-compose执行权限
sudo chmod +x /usr/local/bin/docker-compose
```

**注意**：[Docker Compose](https://docs.docker.com/compose/install/) 存放在GitHub不太稳定，可以通过镜像网址高速安装。

- 镜像网站：http://get.daocloud.io/

```shell
curl -L https://get.daocloud.io/docker/compose/releases/download/v2.2.2/docker-compose-`uname -s`-`uname -m` > /usr/local/bin/docker-compose
chmod +x /usr/local/bin/docker-compose
```

下载完成后可以输入`docker-compose --version`来查看是否安装成功

![image-20220101230824252](https://i-blog.csdnimg.cn/blog_migrate/0962b6ca1f4a306c6ef9dc868dadb448.png)

### 3. 安装启动gitea

我们通过docker compose的yaml配置文件来安装gitea，其中选用数据库mysql来存储gitea的数据文件。

创建`docker-compose.yml`文件，内容如下：

```yaml
version: "3"

networks:
  gitea:
    external: false

services:
  server:
    image: gitea/gitea:1.15.9
    container_name: gitea
    environment:
      - USER_UID=1000
      - USER_GID=1000
      - DB_TYPE=mysql
      - DB_HOST=db:3306
      - DB_NAME=gitea
      - DB_USER=gitea
      - DB_PASSWD=gitea
    restart: always
    networks:
      - gitea
    volumes:
      - ./gitea:/data
      - /etc/timezone:/etc/timezone:ro
      - /etc/localtime:/etc/localtime:ro
    ports:
       - "3000:3000"
       - "222:22"
    depends_on:
       - db
 
  db:
     image: mysql:8
     restart: always
     environment:
       - MYSQL_ROOT_PASSWORD=gitea
       - MYSQL_USER=gitea
       - MYSQL_PASSWORD=gitea
       - MYSQL_DATABASE=gitea
     networks:
       - gitea
     volumes:
       - ./mysql:/var/lib/mysql
```

编写完成后，我们通过以下命令再启动 Gitea

```shell
# 后台启动gitea
docker-compose up -d server
```

![image-20220102150832312](https://i-blog.csdnimg.cn/blog_migrate/287637390c252c98350072ada7d3feac.png)

![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/ec18aec7ba416e1ae1dd974c3c68a416.png#pic_center)

待启动成功，可以看到它启动在3000端口，然后我们通过服务器`公网IP:3000`即可访问到其web界面，注意服务器安全组规则要放行3000端口

![image-20220102143252724](https://i-blog.csdnimg.cn/blog_migrate/9042f340d3a911c8dd4bc57c4b70abd3.png)

其中数据库设置我们不需要更改，因为是根据上述docker-compose.yml文件中的数据库配置来读取的，我们需要更改ssh服务的域名为服务器的公网ip，通知基础url的前缀也更改为服务器的公网ip

![image-20220102145544295](https://i-blog.csdnimg.cn/blog_migrate/b77bc67117f944d2a3f1cfe1dc4f862e.png)

然后创建一个管理员用户(zsr/123456)即可，然后点击安装

![image-20220102145608014](https://i-blog.csdnimg.cn/blog_migrate/0dc89a71601ecb798624fa9337ac60cb.png)

设置完成后，点击立即安装，然后即可进入如下界面

![image-20220102145704870](https://i-blog.csdnimg.cn/blog_migrate/6dcba3315effd0a4b432357aaad01e0e.png)

到此gitea的已经安装部署完成

### 4. 基本操作实例

我们来新建一个仓库：

![image-20220102151847036](https://i-blog.csdnimg.cn/blog_migrate/d13d5cf2c5cf7237d49f46697820ec8a.png)

然后我们将仓库克隆下来新增一个文件然后再推送回去：

```shell
# 克隆仓库
zhongsiru@zhongsirudeMacBook-Air Desktop % git clone http://139.198.40.248:3000/zsr/hello.git
Cloning into 'hello'...
warning: You appear to have cloned an empty repository.

# 进入本地仓库目录
zhongsiru@zhongsirudeMacBook-Air Desktop % cd hello 

# 新增hello.txt文件
zhongsiru@zhongsirudeMacBook-Air hello % vim hello.txt
zhongsiru@zhongsirudeMacBook-Air hello % ls
hello.txt

# 将变更添加到暂存区
zhongsiru@zhongsirudeMacBook-Air hello % git add .

# 将暂存区的内容添加到本地仓库
zhongsiru@zhongsirudeMacBook-Air hello % git commit -m "添加hello.txt"
[master (root-commit) 1f46f0e] 添加hello.txt
 1 file changed, 1 insertion(+)
 create mode 100644 hello.txt

# 推送到远程仓库(要输入用户名和密码)
zhongsiru@zhongsirudeMacBook-Air hello % git push origin master
Username for 'http://139.198.40.248:3000': zsr
Password for 'http://zsr@139.198.40.248:3000': 
Enumerating objects: 3, done.
Counting objects: 100% (3/3), done.
Writing objects: 100% (3/3), 230 bytes | 230.00 KiB/s, done.
Total 3 (delta 0), reused 0 (delta 0), pack-reused 0
remote: . Processing 1 references
remote: Processed 1 references in total
To http://139.198.40.248:3000/zsr/hello.git
 * [new branch]      master -> master
```

上述命令操作完成后，我们回到gitea web页面，即可看到变更

![image-20220102152425323](https://i-blog.csdnimg.cn/blog_migrate/b6bd1ecdde0a92b8ea554ecaed20ba7e.png)

### 5. [ssh配置](https://so.csdn.net/so/search?q=ssh%E9%85%8D%E7%BD%AE&spm=1001.2101.3001.7020)

上述我们推送到远程仓库要输入用户名和密码进行校验，这是十分麻烦的，我们可以配置ssh实现免密登陆：

1️⃣ **首先在本机生成公钥**：

```shell
# 进入到.ssh目录
cd ~/.ssh

# 生成密钥对
ssh-keygen -t rsa -C "邮箱"

# 查看公钥内容
cat id_rsa.pub
```

![image-20220102153648897](https://i-blog.csdnimg.cn/blog_migrate/b767c25fa626be9d4544affd235eb4a7.png)

2️⃣ **gitea中添加公钥**

在gitea web界面的ssh配置页面新增一个ssh密钥，复制上面生成的公钥粘贴进去即可

![image-20220102153831643](https://i-blog.csdnimg.cn/blog_migrate/c4a6403057f4b2531222ce1218dc519d.png)

添加完成后如下所示

![image-20220102153924527](https://i-blog.csdnimg.cn/blog_migrate/042a1d2efaa648aa7244ed7ebb6bb7a8.png)

此时如果我们修改hello.txt的内容再重新推送到gitea仓库，就不需要输入密码了

![image-20220102154216729](https://i-blog.csdnimg.cn/blog_migrate/270fea3a547902049e291d122b88fbfb.png)

如果我们采用ssh的方式克隆下来呢？

![image-20220102155224545](https://i-blog.csdnimg.cn/blog_migrate/5f134573b4917d4d0b97de74ecaa465a.png)

我们复制这个ssh地址来看看：

![image-20220102155339973](https://i-blog.csdnimg.cn/blog_migrate/88e163bb2e4f7579c46c6d86ca9eef86.png)

发现还让我们输密码，我们不是刚刚配置的ssh吗？我们仔细看这个ssh地址：

```shell
git@139.198.40.248:zsr/hello.git
```

在服务器公网ip后面直接接了`zsr`用户名，没有接任何端口，也就是想当于走了默认端口`22`，等价于`服务器公网ip:22`也就是要登陆服务器的操作，这当然是需要密码的，我们应该是登陆服务器内部gitea容器的操作，因此我们需要修改gitea的一些配置：

![image-20220102160627103](https://i-blog.csdnimg.cn/blog_migrate/ae6e4b517c6ec798cfd818e59a394d0e.png)

在docker-compose.yml文件中，由于我们将gitea的data目录挂在到本季的gitea目录中，因此我们需要进入该目录中来修改相关配置，需要修改`/gitea/gitea/conf/app.ini`文件

![image-20220102160854239](https://i-blog.csdnimg.cn/blog_migrate/6f66e5e53fffaaacda7d167008c9e909.png)

由于我们将主机的222端口映射到gitea容器中的22端口，因此我们将app.ini中的`ssh_port`和`ssh_listen_port`修改为222端口

![image-20220102160008026](https://i-blog.csdnimg.cn/blog_migrate/3633c96491f715fe13640b809f7d9e0b.png)

修改完成后我们通过`docker-compose restart`命令重启一下gitea容器

![image-20220102161111503](https://i-blog.csdnimg.cn/blog_migrate/1bff354c3c528fc711d6f23478e53ce6.png)

然后再次访问web界面，可以看到ssh地址已经变更，在服务器的公网ip后接了222端口（注意服务器安全组要放行222端口），也就相当于访问服务器内部gitea容器的22端口

![image-20220102161221084](https://i-blog.csdnimg.cn/blog_migrate/5e8de768d43978cd4da8d06f529811d8.png)

此时我们再通过ssh进行克隆，然后修改文件再推送回去

![image-20220102161602175](https://i-blog.csdnimg.cn/blog_migrate/b7a63ee4adc713bc35351db2371344fa.png)

这次期间任何流程无需再需要输入密码进行验证，到此ssh配置已经完毕。