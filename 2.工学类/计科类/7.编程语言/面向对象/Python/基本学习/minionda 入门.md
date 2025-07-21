#### 为什么选择MiniConda而不是Anaconda？

MiniConda是Anaconda的轻量级版本，只包含conda包管理器和Python解释器，

Anaconda包含更多的科学计算和数据分析库。

> 我知道很多人想问conda这玩意到底是干什么的？作用就是 **环境隔离** (Environment Management)当你开发多个 Python 项目时，不同的项目可能需要不同版本的 Python 解释器或者不同的软件包版本。MiniConda 和 Anaconda 允许你创建独立的 “虚拟环境”，每个环境都有自己独立的 Python 解释器和软件包，避免不同项目之间的依赖冲突。你可以为每个项目创建一个单独的环境，确保项目的稳定性和可移植性。然后是 **软件包管理** (Package Management): 它们都自带一个强大的软件包管理器 conda (或 mamba，它是 conda 的一个更快替代品，Anaconda 也支持)。conda 能够方便地安装、卸载、更新各种 Python 软件包（例如 NumPy, Pandas, Scikit-learn 等），以及非 Python 的依赖库。 conda 还能处理软件包之间的依赖关系，确保安装的软件包能够正常运行。

> 简单来说就是，用来管理Python环境和包的工具。你也不希望自己电脑里面几十个不同版本的OpenCV冲突吧。

> 这个时候又有人问了，为什么不用docker或者虚拟机，因为docker复杂和资源占用多，当然如果你要跨平台就只能选择docker了。

### 1. MiniConda 快速入门

#### 安装 MiniConda

首先，需要从 [Miniconda 官方网站](https://docs.conda.io/en/latest/miniconda.html) 下载并安装 Miniconda。 （注意看别找错了，虽然下载成Anaconda也不是不行。）

#### 配置镜像源

为了加快下载速度，建议配置国内镜像源，清华源好用的。

```bash
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/free/
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/main/
```

#### 创建虚拟环境

创建一个新的 Python 环境，可以指定 Python 版本：

```bash
conda create -n myenv python=3.9
```

#### 激活环境

切换到刚创建的环境：

```bash
conda activate myenv
```

#### 安装包

在当前环境中安装需要的包：

```bash
conda install numpy pandas matplotlib
```

#### 查看已安装的包

列出当前环境中所有已安装的包：

```bash
conda list
```

#### 查看所有环境

显示系统中所有的 conda 环境：

```bash
conda env list
```

#### 导出环境配置

将当前环境的配置导出到文件：

```bash
conda env export > environment.yml
```

#### 从配置文件创建环境

使用配置文件创建新环境：

```bash
conda env create -f environment.yml
```

#### 删除环境

删除不再需要的环境：

```bash
conda env remove -n myenv
```

### 2. 环境管理最佳实践

#### 创建项目专属环境

为每个项目创建独立的环境，避免包冲突：

```bash
conda create -n projectname python=3.9 numpy pandas
```

#### 环境清理

定期清理不需要的缓存文件：

```bash
conda clean --all
```

#### 更新 conda

保持 conda 本身为最新版本：

```bash
conda update conda
```

### 3. 常用命令速查

#### 基础命令（Mini）

日常使用最常用的命令：

```bash
conda create -n myenv python=3.9    # 创建环境
conda activate myenv/.conda         # 激活环境:既可以是环境名也可以是环境路径
conda install package_name          # 安装包
conda list                         # 查看已安装包
conda env list                     # 查看所有环境
```

#### 完整命令（More）

更多高级命令：

```bash
# 环境管理
conda create -n myenv python=3.9    # 创建环境
conda activate myenv                # 激活环境
conda deactivate                    # 退出环境
conda env list                      # 列出环境
conda env remove -n myenv           # 删除环境

# 包管理
conda install package_name          # 安装包
conda update package_name           # 更新包
conda remove package_name           # 删除包
conda list                         # 列出已安装包
conda search package_name          # 搜索包

# 系统维护
conda update conda                 # 更新conda
conda clean --all                  # 清理缓存
```

