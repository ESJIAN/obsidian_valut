## 一、什么是Git Submodule

`Git Submodule` 是Git版本控制系统中的一种机制，用于在一个Git仓库中包含另一个Git仓库。它允许将一个Git仓库作为另一个Git仓库的子目录，并且可以独立地管理这个子仓库的版本，同时还保持提交的独立。  
![image.png](https://segmentfault.com/img/remote/1460000044639290 "image.png")  
Submodule的作用在于，它允许你在一个项目中使用其他项目的特定版本，而无需将整个子项目的代码复制到主项目中。这对于依赖管理和代码复用非常有用。

## 二、使用 Git Submodule

### 1 创建和初始化仓库

- 初始化主库和子模块库

我采用的是 Gitee 来进行本次实操，首先在 Gitee 中创建一个主库 `GitSubmoduleDemo`，两个子模块库 `ModuleA`和 `ModuleB`:  
![image.png](https://segmentfault.com/img/remote/1460000044639292 "image.png")  
先将主库 clone 到本地：

```shell
$ git clone https://gitee.com/haohuin/git-submodule-demo.git
```

- 在主库中，使用 `git submodule add` 命令添加 `Submodule`子模块。

其命令为：`git submodule add <remote repo url> <local repo url>`

- remote repo url 指远程仓库的 url
- local repo url 指本地仓库的路径 url

```shell
//在主库中添加ModuleA
$ git submodule add ../module-a.git ModuleA

//在主库中添加ModuleB
$ git submodule add ../module-b.git ModuleB
```

查看当前主库的状态：

```shell
$ git status
On branch master
Your branch is up to date with 'origin/master'.

Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        new file:   .gitmodules
        new file:   ModuleA
        new file:   ModuleB
```

发现有新的文件在主库中，分别是 `.gitmodules`文件，`ModuleA`和 `ModuleB`目录

#### 1.1 `.gitmodules`文件

首先看一下 `.gitmodules`配置文件，它保存了远程仓库 url 与本地仓库 url 路径的映射：

```shell
[submodule "ModuleA"]
    path = ModuleA
    url = ../module-a.git
[submodule "ModuleB"]
    path = ModuleB
    url = ../module-b.git
```

每条记录对应一个子模块信息，path 和 url 对应远程仓库 url 和本地仓库路径

#### 1.2 主库中的子模块

接着提交当前主库中出现的文件和目录：

```shell
//暂存
$ git add .
//提交
$ git commit -m "ModuleA and ModuleB submodule commit"
[master 2dcfefd] ModuleA and ModuleB submodule commit
 3 files changed, 8 insertions(+)
 create mode 100644 .gitmodules
 create mode 160000 ModuleA
 create mode 160000 ModuleB
```

发现`ModuleA`和 `ModuleB`目录的模式编码为 `160000`。  
在之前讲解 `index`文件提到过，模式 `160000`是引用其他 Git 仓库的特殊文件类型，它允许将一个 Git 仓库作为另一个仓库的子目录进行管理。具体可以看这篇文章[Git暂存区机制详解](https://segmentfault.com/a/1190000044573067)  
所以此时主库中只是存储了子模块的引用，也就是一次的提交记录。而不是其他的文件或者目录。最后将主库中的修改进行推送：

```shell
$ git push origin master
```

![image.png](https://segmentfault.com/img/remote/1460000044639293 "image.png")  
发现在主库中`ModuleA`和 `ModuleB`确实是以引用的形式存储的。

### 2 更新和同步子模块

那么如何将子模块的修改更新到主仓库中呢？这又分两种情况：

- 在子模块所在的仓库中修改代码后提交，然后在主仓库中拉取更新
- 在主仓库中修改子模块代码后提交远程仓库，然后在子模块仓库中拉取更新

#### 2.1 主仓库更新子模块仓库中的修改

首先在子模块仓库 ModuleA 中新增一个文件，并提交到 ModuleA 的远程仓库中：

```shell
$ echo "updateModuleA-1">updateModuleA-1.txt
$ git add .
$ git commit -m "update ModuleA"
$ git push
```

![image.png](https://segmentfault.com/img/remote/1460000044639294 "image.png")  
此时子模块仓库中的 commit ID 值为 `6026b48`，再来看一下主仓库中的子模块的 Commit ID 值  
![image.png](https://segmentfault.com/img/remote/1460000044639295 "image.png")  
发现此时主仓库的 Commit ID 值为 `3474554`，和子模块仓库中的 ID 值并不同步，所以需要在主仓库的子模块代码中同步子模块远程仓库的更新：

```shell
$ cd ModuleA
$ git checkout master
$ git pull origin master
```

然后在主仓库根目录中提交子模块仓库推送和更新：

```shell
$ cd ..
$ git add .
$ git commit -m "update ModuleA"
$ git push
```

此时发现远程主仓库已经同步子模块的更新内容，而且 Commit ID 值也同步成`6026b48` ，和子模块仓库中最新的 Commit ID 保持一致：

![image.png](https://segmentfault.com/img/remote/1460000044639296 "image.png")

#### 2.2 子模块仓库更新主仓库中子模块代码的修改提交

首先在主仓库的子模块目录下修改代码：

```shell
//在主仓库中进入子模块ModuleA目录
$ cd ModuleA
//修改文件和提交和普通Git仓库提交流程一致：
//1.创建文件并提交
$ echo "ModuleA">updateModuleA.txt
$ git add .
$ git commit -m "update ModuleA"
//2.推送到远程ModuleA仓库
$ git push
```

发现远程子模块仓库也同步完成：

![image.png](https://segmentfault.com/img/remote/1460000044639297 "image.png")

接着需要将主仓库中的子模块 ModuleA 的变化同步到远程主仓库中具体的操作和上一节主仓库更新子模块仓库中的修改类似，用 add 和 commit 方式提交主仓库的更新，这个时候就完成了子模块和主仓库代码一致。

```shell
$ cd ..
$ git add .
$ git commit -m "update ModuleA"
$ git push
```

在实际的 IDE 环境中，只需要在子模块目录下进行代码修改：

![image.png](https://segmentfault.com/img/remote/1460000044639298 "image.png")  
然后在提交时先更新子模块 ModuleB 的远程仓库：  
![image.png](https://segmentfault.com/img/remote/1460000044639299 "image.png")  
然后再同步远程主仓库中的 ModuleB 目录变化，这一步需要用命令行，直接在主目录提交没法更新远程主目录，但是本地主仓库的 ModuleB 目录确实发生了变化：

```shell
$ git status
On branch master
Your branch is up to date with 'origin/master'.

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   ModuleB (new commits)

no changes added to commit (use "git add" and/or "git commit -a")
```

需要命令行切换到主仓库目录执行 `git add` 后再用 IDE 集成的 Git 提交操作：

```shell
$ git add .
```

再点击提交发现 IDE 中出现了 ModuleB 的更新变化：  
![image.png](https://segmentfault.com/img/remote/1460000044639300 "image.png")  
接着推送到远程主仓库即可完成主仓库和子模块仓库的更新

## 三、总结

本文通过实践介绍子模块：

- 包括子模块的初始化，如何使用 git submodule add 命令在主仓库添加子模块
- 如何在子模块和主仓库之间的更新和同步

子模块主要有以下应用场景

- 不同项目间需要共享同一个公共代码,如基础类库或工具包;
- 较大的项目需要拆分成多个子项目进行开发,通过子模块控制依赖关系;
- 第三方开源库或组件的本地开发与项目进行绑定;
- 需要隔离成组和组件版本的同时利用依赖关系,如微服务架构下的服务与组件;
- 子项目有较强的独立性同时也存在一定的耦合关系,通过子模块进行管理。

同时从上面的时间可以看到，子模块和主仓库之间的同步比较复杂，维护成本高，子模块与主项目需要进行紧密的协调管理，否则很容易导致不同步的情况出现。在使用中要结合实际情况下操作，简单的项目就不要用子模块，采用分支管理可能更合适。