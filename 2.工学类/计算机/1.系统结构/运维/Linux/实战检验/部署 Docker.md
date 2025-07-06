> Docker Linux 桌面版
> 
> Docker Desktop 可帮助您在 Mac 和 Windows 上轻松构建、共享和运行容器，就像在 Linux 上一样。我们很高兴地告诉大家，适用于 Linux 的 Docker 桌面现已上市。有关详细信息，请参阅 [Docker Desktop for Linux](https://docs.docker.com/desktop/linux/install/) 。

要开始在 Ubuntu 上使用 Docker 引擎，请确保您是 [meet the prerequisites](https://runebook.dev/cn/docs/docker/engine/install/ubuntu/index#prerequisites) ，然后是 [install Docker](https://runebook.dev/cn/docs/docker/engine/install/ubuntu/index#installation-methods) 。


- # 4. 本节犯错

- ## 4.1. Docker 所在目录文件系统错用 exFat

- 【问题描述】尝试在 Docker 中安装 KVM 虚拟机时发生如下报错

```bash
failed to register layer: symlink ... operation not permitted
```

- 【问题分析】你挂载的是 `/mnt/sata1-4`，这个目录很可能是 **挂载在 ext4/xfs 以外格式的硬盘分区（比如 NTFS、exFAT）**。这类文件系统不支持某些 Linux 特性，如符号链接、文件权限、overlay 文件系统操作。

	```bash
	symlink ... operation not permitted
	```

  这说明 Docker 在用 `fuse-overlayfs` 尝试创建符号链接时被拒绝。

- 【方案尝试】


## Prerequisites

### OS requirements

要安装 Docker 引擎，您需要以下 Ubuntu 版本之一的 64 位版本：

- Ubuntu Jammy 22.04 (LTS)
- Ubuntu 小鬼 21.10
- Ubuntu Focal 20.04 (LTS)
- Ubuntu 仿生 18.04 (LTS)

Docker 引擎受 `x86_64` （或 `amd64` ）、 `armhf` 、 `arm64` 和 `s390x` 架构支持。

### 卸载旧版本

Docker 的旧版本称为 `docker` 、 `docker.io` 或 `docker-engine` 。如果安装了这些，请卸载它们：

$ sudo apt-get remove docker docker-engine docker.io containerd runc

如果 `apt-get` 报告已安装这些软件包的 none ，则没关系。

`/var/lib/docker/` 的内容（包括映像、容器、卷和网络）将被保留。如果您不需要保存现有数据，并希望开始全新安装，请参阅本页底部的 [uninstall Docker Engine](https://runebook.dev/cn/docs/docker/engine/install/ubuntu/index#uninstall-docker-engine) 部分。

## Installation methods

您可以根据需要以不同的方式安装 Docker 引擎：

- 大多数用户使用 [set up Docker’s repositories](https://runebook.dev/cn/docs/docker/engine/install/ubuntu/index#install-using-the-repository) 并从其中安装，以方便安装和升级任务。这是推荐的方法。
    
- 一些用户下载DEB包和 [install it manually](https://runebook.dev/cn/docs/docker/engine/install/ubuntu/index#install-from-a-package) 并完全手动管理升级。这对于在无法访问互联网的气隙系统上安装 Docker 等情况非常有用。
    
- 在测试和开发环境中，部分用户选择使用自动化的 [convenience scripts](https://runebook.dev/cn/docs/docker/engine/install/ubuntu/index#install-using-the-convenience-script) 来安装Docker。
    

### 使用存储库安装

在新主机上首次安装 Docker 引擎之前，您需要设置 Docker 存储库。之后，您可以从存储库安装和更新 Docker 。

#### 设置存储库

1. 更新 `apt` 软件包索引并安装软件包以允许 `apt` 通过 HTTPS 使用存储库：
    
    $ sudo apt-get update
    
    $ sudo apt-get install \
        ca-certificates \
        curl \
        gnupg \
        lsb-release
    

添加Docker官方GPG密钥：

```bash
$ sudo mkdir -p /etc/apt/keyrings
$ curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
```

使用以下命令设置存储库：

```bash
$ echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu \
  $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```

#### 安装 Docker 引擎

1. 更新 `apt` 软件包索引，并安装最新版本的 Docker Engine、containerd 和 Docker Compose，或者转到下一步安装特定版本：
    
    ```bash
 $ sudo apt-get update
     $ sudo apt-get install docker-ce docker-ce-cli containerd.io docker-compose-plugin
```    

- > 运行 `apt-get update` 时收到 GPG 错误？
    > 
    > 您的默认 umask 可能设置不正确，导致无法检测到存储库的 public 密钥文件。运行以下命令，然后尝试再次更新您的存储库： `sudo chmod a+r /etc/apt/keyrings/docker.gpg` 。
    
- 要安装特定版本的 Docker Engine，请在存储库中列出可用版本，然后选择并安装：
    
    A。列出您的存储库中可用的版本：
    
```bash
    $ apt-cache madison docker-ce
    
    docker-ce | 5:20.10.16~3-0~ubuntu-jammy | https://download.docker.com/linux/ubuntu jammy/stable amd64 Packages
    docker-ce | 5:20.10.15~3-0~ubuntu-jammy | https://download.docker.com/linux/ubuntu jammy/stable amd64 Packages
    docker-ce | 5:20.10.14~3-0~ubuntu-jammy | https://download.docker.com/linux/ubuntu jammy/stable amd64 Packages
    docker-ce | 5:20.10.13~3-0~ubuntu-jammy | https://download.docker.com/linux/ubuntu jammy/stable amd64 Packages
```
    

b. 使用第二列中的版本字符串安装特定版本，例如 `5:20.10.16~3-0~ubuntu-jammy` 。

```bash
$ sudo apt-get install docker-ce=<VERSION_STRING> docker-ce-cli=<VERSION_STRING> containerd.io docker-compose-plugin
```

通过运行 `hello-world` 映像验证 Docker 引擎是否已正确安装。

```bash
$ sudo docker run hello-world
```

1. 此命令下载测试映像并在容器中运行它。当容器运行时，它会打印一条消息并退出。
    

Docker 发动机已安装并正在运行。 `docker` 组已创建，但未向其中添加用户。您需要使用 `sudo` 来运行 Docker 命令。继续 [Linux postinstall](https://runebook.dev/cn/docs/docker/engine/install/linux-postinstall/index) 以允许非特权用户运行 Docker 命令以及其他可选配置步骤。

#### 升级 Docker 引擎

要升级 Docker 引擎，请先运行 `sudo apt-get update` ，然后按照 [installation instructions](https://runebook.dev/cn/docs/docker/engine/install/ubuntu/index#install-using-the-repository) 操作，选择要安装的新版本。

### 从包安装

如果您无法使用 Docker 的存储库来安装 Docker 引擎，您可以下载适合您的版本的 `.deb` 文件并手动安装。每次升级 Docker 时都需要下载新文件。

1. 转到 [`https://download.docker.com/linux/ubuntu/dists/`](https://download.docker.com/linux/ubuntu/dists/) ，选择您的 Ubuntu 版本，然后浏览到 `pool/stable/` ，选择 `amd64` 、 `armhf` 、 `arm64` 或 `s390x` ，并下载您要安装的 Docker 引擎版本的 `.deb` 文件。
    
2. 安装 Docker 引擎，将下面的路径更改为您下载 Docker 软件包的路径。
    
    $ sudo dpkg -i /path/to/package.deb
    

- Docker 守护进程自动启动。
    
- 通过运行 `hello-world` 映像验证 Docker 引擎是否已正确安装。
    
    $ sudo docker run hello-world
    

1. 此命令下载测试映像并在容器中运行它。当容器运行时，它会打印一条消息并退出。
    

Docker 发动机已安装并正在运行。 `docker` 组已创建，但未向其中添加用户。您需要使用 `sudo` 来运行 Docker 命令。继续 [Post-installation steps for Linux](https://runebook.dev/cn/docs/docker/engine/install/linux-postinstall/index) 以允许非特权用户运行 Docker 命令以及其他可选配置步骤。

#### 升级 Docker 发动机

要升级 Docker 引擎，请下载较新的软件包文件并重复 [installation procedure](https://runebook.dev/cn/docs/docker/engine/install/ubuntu/index#install-from-a-package) ，指向新文件。

### 使用便捷脚本安装

Docker 在 [get.docker.com](https://get.docker.com/) 上提供了一个方便的脚本，可以快速且非交互地将 Docker 安装到开发环境中。不建议在生产环境中使用便利脚本，但可以将其用作示例来创建根据您的需求定制的配置脚本。另请参阅 [install using the repository](https://runebook.dev/cn/docs/docker/engine/install/ubuntu/index#install-using-the-repository) 步骤，了解使用软件包存储库进行安装的安装步骤。该脚本的源代码是开源的，可以在 [`docker-install` repository on GitHub](https://github.com/docker/docker-install) 中找到。

在本地运行脚本之前，请始终检查从互联网下载的脚本。安装之前，请熟悉便利脚本的潜在风险和限制：

- 该脚本需要 `root` 或 `sudo` 权限才能运行。
- 该脚本尝试检测您的 Linux 发行版和版本并为您配置包管理系统，并且不允许您自定义大多数安装参数。
- 该脚本会安装依赖项和建议，而不要求确认。这可能会安装大量软件包，具体取决于主机的当前配置。
- 默认情况下，该脚本会安装最新稳定版本的 Docker、containerd 和 runc。使用此脚本配置计算机时，可能会导致 Docker 主要版本意外升级。在部署到生产系统之前，始终在测试环境中测试（主要）升级。
- 该脚本并非旨在升级现有的 Docker 安装。使用脚本更新现有安装时，依赖项可能无法更新到预期版本，从而导致使用过时的版本。

> 提示：运行前预览脚本步骤
> 
> 您可以使用 `DRY_RUN=1` 选项运行该脚本，以了解该脚本在安装过程中将执行哪些步骤：
> 
> $ curl -fsSL https://get.docker.com -o get-docker.sh
> $ DRY_RUN=1 sh ./get-docker.sh

此示例从 [get.docker.com](https://get.docker.com/) 下载脚本并运行它以在 Linux 上安装 Docker 的最新稳定版本：

$ curl -fsSL https://get.docker.com -o get-docker.sh
$ sudo sh get-docker.sh
Executing docker install script, commit: 7cae5f8b0decc17d6571f9f52eb840fbc13b2737
<...>

Docker 已安装。 `docker` 服务在基于 Debian 的发行版上自动启动。在基于 `RPM` 的发行版（例如 CentOS、Fedora、RHEL 或 SLES）上，您需要使用适当的 `systemctl` 或 `service` 命令手动启动它。如消息所示，默认情况下非 root 用户无法运行 Docker 命令。

> 以非特权用户身份使用 Docker ，还是以无根模式安装？
> 
> 安装脚本需要 `root` 或 `sudo` 权限才能安装和使用 Docker 。如果您想授予非 root 用户访问 Docker 的权限，请参阅 [post-installation steps for Linux](https://runebook.dev/cn/docs/docker/engine/install/linux-postinstall/index#manage-docker-as-a-non-root-user) 。 Docker 也可以在没有 `root` 权限的情况下安装，或配置为在无根模式下运行。有关在无根模式下运行 Docker 的说明，请参阅 [run the Docker daemon as a non-root user (rootless mode)](https://runebook.dev/cn/docs/docker/engine/security/rootless/index) 。

#### Install pre-releases

Docker 还在 [test.docker.com](https://test.docker.com/) 上提供了一个方便的脚本，用于在 Linux 上安装 Docker 的预发行版。此脚本与 `get.docker.com` 中的脚本等效，但配置您的软件包管理器以启用我们的软件包存储库中的“测试”通道，其中包括 Docker 的稳定版和预发行版（测试版、候选版）。使用此脚本可以尽早访问新版本，并在稳定版本发布之前在测试环境中对其进行评估。

要从“测试”通道在 Linux 上安装最新版本的 Docker ，请运行：

```bash
$ curl -fsSL https://test.docker.com -o test-docker.sh
$ sudo sh test-docker.sh
<...>
```

#### 使用便捷脚本后升级 Docker

如果您使用便捷脚本安装了 Docker ，则应直接使用包管理器升级 Docker 。重新运行便利脚本没有任何好处，并且如果它尝试重新添加已添加到主机的存储库，则可能会导致问题。

## 卸载 Docker 引擎

1. 卸载 Docker Engine、CLI、Containerd 和 Docker Compose 软件包：
    
    $ sudo apt-get purge docker-ce docker-ce-cli containerd.io docker-compose-plugin
    

主机上的映像、容器、卷或自定义配置文件不会自动删除。要删除所有映像、容器和卷：

```bash
$ sudo rm -rf /var/lib/docker
$ sudo rm -rf /var/lib/containerd
```

您必须手动删除任何已编辑的配置文件。

## Next steps

- 继续 [Post-installation steps for Linux](https://runebook.dev/cn/docs/docker/engine/install/linux-postinstall/index) 。
- 查看 [Develop with Docker](https://docs.docker.com/develop/) 中的主题，了解如何使用 Docker 构建新应用程序。

[requirements](https://docs.docker.com/search/?q=requirements) 、 [apt](https://docs.docker.com/search/?q=apt) 、 [installation](https://docs.docker.com/search/?q=installation) 、 [ubuntu](https://docs.docker.com/search/?q=ubuntu) 、 [install](https://docs.docker.com/search/?q=install) 、 [uninstall](https://docs.docker.com/search/?q=uninstall) 、 [upgrade](https://docs.docker.com/search/?q=upgrade) 、 [update](https://docs.docker.com/search/?q=update)

© 2019 Docker, Inc.  
根据 Apache 许可证 2.0 版授权。  
Docker 和 Docker 徽标是 Docker , Inc. 在美国和/或其他国家/地区的商标或注册商标。  
Docker, Inc. 和其他方也可能拥有本文中使用的其他术语的商标权。  
[https://docs.docker.com/engine/install/ubuntu/](https://docs.docker.com/engine/install/ubuntu/)