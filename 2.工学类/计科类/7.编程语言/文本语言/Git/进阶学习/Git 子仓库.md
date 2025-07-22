在前端日常开发中,我们经常git来当做代码[版本管理工具](https://zhida.zhihu.com/search?content_id=110400536&content_type=Article&match_order=1&q=%E7%89%88%E6%9C%AC%E7%AE%A1%E7%90%86%E5%B7%A5%E5%85%B7&zhida_source=entity),使用中基本都是一个项目一个Git仓库的形式,那么当我们的代码中碰到了业务级别的需要复用的代码,我们一般怎么做呢?

  
我们大致的考虑一下,一般有两种方案:

- 抽象成[NPM包](https://zhida.zhihu.com/search?content_id=110400536&content_type=Article&match_order=1&q=NPM%E5%8C%85&zhida_source=entity)进行复用
- 使用Git的子仓库对代码进行复用

在涂鸦的小程序业务场景开发中,两个程序中有部分页面是重叠的,开发过程中重叠部分如果开发两套代码会浪费不少的人力,考量之后决定使用Git子模块的方式进行开发,父级仓库依赖两个公共的子模块,子模块本身和父级仓库一同进行开发,避免了版本问题和重复开发的问题。

我们在下面介绍的子仓库的使用场景基本都是如下的开发方式:

多个父级仓库都依赖同一个子仓库,但是子仓库自身不单独进行修改,而是跟随父级项目进行更新发布,其他依赖子仓库的项目只负责拉取更新即可。

**那么什么是Git的子仓库呢?**

通俗上的理解, 一个Git仓库下面放了多个其他的Git仓库,其他的Git仓库就是我们父级仓库的子仓库。

在正式开始介绍git的子仓库之前,我们要提前认识到一点,在刚开始使用[Git子仓库](https://zhida.zhihu.com/search?content_id=110400536&content_type=Article&match_order=1&q=Git%E5%AD%90%E4%BB%93%E5%BA%93&zhida_source=entity)的时候,如果不是很了解底层原理,很可能会导致使用子仓库出现云里雾里的现象,搞不清楚是父级仓库先提交,还是子仓库先提交,所以在本教程中,我们会先介绍子仓库的两种使用方式,然后携带一些子仓库的Git底层的分析,让大家对子仓库有一个更加全面的认识。

**Git两种子仓库使用方案**

1. [git submodule](https://zhida.zhihu.com/search?content_id=110400536&content_type=Article&match_order=1&q=git+submodule&zhida_source=entity)

2. [git subtree](https://zhida.zhihu.com/search?content_id=110400536&content_type=Article&match_order=1&q=git+subtree&zhida_source=entity)

我们按照顺序分别演示这两种子仓库的使用方式,方便大家深入理解两种子仓库的使用方式:

## `1. git submodule(子模块)`

Git子模块允许我们将一个或者多个Git仓库作为另一个Git仓库的子目录,它能让你将另一个仓库克隆到自己的项目中,同时还保持提交的独立。

我们演示一下`git submodule`的使用方法:

_为了方便后续对两种子仓库的原理进行讲解,我们会详细的描述git的相关操作步骤_

**1.1 开始使用子模块**

使用`git init --bare`在本地创建两个裸仓库,分别表示主仓库和依赖的子仓库,我们将主仓库命名为`main`,依赖的子仓库命名为`lib`, `git subtree`使用同样的初始化方法,下文不再赘述。

```bash
# 为了方便演示,我们使用/path/to/repos代表你当前开发的绝对路径
# 比如笔者的/path/to/repos代表/Users/userName/Documents/work
git --git-dir=/path/to/repos/main.git init --bare # 初始化主仓库
git --git-dir=/path/to/repos/lib.git init --bare # 初始化子仓库

# 本地拉取到这两个仓库
git clone /path/to/repos/main.git
git clone /path/to/repos/lib.git

# 我们分别对这两个仓库进行一次提交
cd main
echo "console.log('main');" > index.js
git add .
git commit -m "feat: 父级仓库创建index.js"
git push

cd ../lib
echo "console.log('utils');" > util.js
git add .
git commit -m "feat: 子仓库创建util.js"
git push
```

初始化结束两个子仓库后,我们想让`main`主仓库能够使用`lib`仓库的代码进行后续的开发,使用`git submodule add`的命令后面加上想要跟踪项目URL来添加新的子模块(本文中的`lib`仓库)。

```bash
# 首先进入到main的工作目录下
cd main

# 添加lib模块到main仓库下的lib同名目录
git submodule add /path/to/repos/lib.git
```

默认情况下,子模块会被添加到项目的子模块同名的目录下,如果想放到其他目录. 在`add`命令的结尾跟上放置目录的相对路径即可。

执行完上述命令后,我们查看`main`仓库下当前的目录结构:

```bash
tree
.
├── index.js
├── .gitmodules
└── lib
    └── util.js
```

我们发现`lib`仓库已经被放到`main`仓库下的`lib`目录下面了,同时还要注意的是,Git为我们创建了一个`.gitmodules`文件,这个配置文件中保存了子仓库项目的URL和在主仓库目录下的映射关系:

```bash
cat .gitsubmodules

[submodule "lib"]
    path = lib
    url = /path/to/repos/lib.git
```

执行`git status`发现有了新的文件

```bash
git status

On branch master
Your branch is up to date with 'origin/master'.

Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)

        new file:   .gitmodules
        new file:   lib
```

我们对`main`仓库进行一次提交:

```bash
git add .
git commit -m "feat: 增加子仓库依赖"
git push
```

操作结束后,我们的`main`仓库就依赖了`lib`仓库的代码并且已经上传到了云端的仓库当中,那么别人应该怎么去克隆包含子模块的项目呢?

**1.2 克隆含有子项目的仓库**

当我们正常克隆`main`项目的时候,我们会发现,`main`仓库中虽然包含`lib`文件夹,但是里面并不包含任何内容,仿佛就是一个空文件夹:

```bash
git clone /path/to/repos/main.git
Cloning into 'main1'...
done.

cd main
tree # 使用tree命令查看当前目录,省略隐藏文件

.
├── index.js
└── lib
```

此时你需要运行`git submodule`的另外两个命令,不需要担心,`submodule`的命令不会太多。

首先执行`git submodule init`用来初始化本地配置文件,也就是向`.git/config`文件中写入了子模块的信息。

`git submodule update`则是从子仓库中抓取所有的数据找到父级仓库对应的那次子仓库的提交id并且检出到父项目的目录中。

```bash
git submodule init 

Submodule 'lib' (/path/to/repos/lib.git) registered for path 'lib'

git submodule update

done.
Submodule path 'lib': checked out '40f8536319ede421cfd9ca9f9904b5106946e8ec'
```

现在我们查看`main`仓库下的目录结构,会发现和我们之前的提交的结构保持一致了,我们成功的拉取到了父级仓库和相关依赖子仓库的代码。

```text
tree

.
├── index.js
└── lib
    └── util.js
```

上述命令着实有些麻烦,有没有简单一些的命令能够直接拉取整个仓库的代码的方式呢? 答案是有的,我们使用`git clone --recursive`,Git会自动帮我们递归去拉取我们所有的父仓库和子仓库的相关内容。

```bash
git clone --recursive /path/to/repos/main.git

Cloning into 'main'...
done.
Submodule 'lib' (/path/to/repos/lib.git) registered for path 'lib'
Cloning into '/path/to/repos/main/lib'...
done.
Submodule path 'lib': checked out '40f8536319ede421cfd9ca9f9904b5106946e8ec'
```

**1.3 在主仓库上进行协同开发**

我们在`main`仓库下对`lib`文件夹做了一些修改,然后我们想提交父仓库(`main`)和子仓库(`lib`)的修改,此时首先我们应该先提交子仓库的修改。

```text
cd lib
```

当我们执行完上述命令后发现,`lib`目录竟然包含了一整个完整的git仓库,甚至包含了`.git`目录。

但是我们也发现当前不在`lib`的`master`分支上,而是在一个游离分支上面,这个游离分支的hash正式`lib`仓库的`master`分支的hash值,这正是`git submodule`为我们所做的, Git不关心我们开发的分支,而只是去拉取子仓库对应的`commit`提交。

所以我们需要先切换到正常分支, 然后正常操作git仓库一样去进行子仓库的提交。

```bash
git add .
git commit -m "子仓库进行修改"
git push
```

子仓库提交结束后,我们回到`main`仓库的主目录下,执行`git status`:

```bash
git status

On branch master
Your branch is up to date with 'origin/master'.

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

        modified:   lib (new commits)

no changes added to commit (use "git add" and/or "git commit -a")
```

我们发现本次的Git的status和以往有些不一样的地方,Git并没有告诉我们当前到底修改了什么文件,而是说`lib`下有一次新的提交,我们记住这个点,正常将主仓库进行提交并且push到云端仓库即可。

对`git submodule`使用下来发现, submodule本身就是一个大的Git仓库下包含了多个子的Git仓库,我们修改之后,首先对每个子仓库进行了提交,然后父级仓库就会记录下每个子仓库的提交,然后正常提交父级仓库即可,拉取也是同样的过程,如果是在子仓库的分支上开发,也是先拉取子仓库,随后拉取父级仓库的更新,此处不再赘述。

如果觉得对每个子仓库进行提交繁琐的话,`git sumodule foreach`就可以解决你这个烦恼:

```bash
# main目录下
git submodule foreach git pull
```

我们对所有的子仓库拉取了一次最新的代码, `foreach`后面使用的就是你要对子模块使用的git命令。

那么还有一个问题,我们在修改了子仓库提交后,回到父级仓库执行`git status`后为什么git不像以前一样告诉我们具体的文件更新信息呢,而是给出了`modified: lib (new commits)`这样一串奇怪的信息,而这正式`git submodule`的底层实现原理。

**1.4 `git submodule`原理分析**

我们知道Git底层大致依赖了四种对象,构成了Git对于文件内容追踪的基础:

```bash
blob: 二进制大文件,可以通俗理解为对文件的修改
tree: 记录了blob对象和其他tree对象的修改,通俗理解为目录
commit: 提交对象,记录了本次提交的tree对象和父类的commit对象以及我们的提交信息
tag: 我们对当前提交记录版本的对象
```

更加详细的内容请参考[深入理解Git](https://zhuanlan.zhihu.com/p/71577255),阅读后更容易理解后续知识点哦~

我们此处需要依赖一个`print_all_object`的工具函数,它会帮助我们将git仓库下的这四种对象按照反向提交历史的排序展现出来,可以将它放在环境变量下方便全局使用:

```bash
#!/bin/bash

print_all_object() {
  for object in `git rev-list --objects --all | cut -d ' ' -f 1`; do
    echo 'SHA1: ' $object
    git cat-file -p $object
    echo '-------------------------------'
  done
}

print_all_object
```

我们在`main`仓库下执行`print_all_object`:

```bash
# 此时处于我们刚对子模块提交的那个时间点
# 对部分长的hash进行了截取处理,不影响阅读观感
print_all_object

SHA1:  a1cfd26e
tree c77ba9c2
parent ab118b8

feat: 增加子仓库依赖
-------------------------------
SHA1:  ab118b8
tree f5771cd

feat: 父级仓库创建index.js
-------------------------------
SHA1:  c77ba9c2
100644 blob d8c9fb4    .gitmodules
100644 blob ddd81ae    index.js
160000 commit 40f8536  lib
-------------------------------
SHA1:  d8c9fb4
[submodule "lib"]
        path = lib
        url = /path/to/repos/lib.git
-------------------------------
SHA1:  ddd81ae
console.log('main');-------------------------------
SHA1:  f5771cd
100644 blob ddd81ae    index.js
-------------------------------
```

我们查看`feat: 增加子仓库依赖`此次`commit`对象的`tree`对象,发现内容如下:

```text
SHA1:  c77ba9c
100644 blob d8c9fb456  .gitmodules
100644 blob ddd81aef    index.js
160000 commit 40f85363  lib
```

`index.js`文件是`blob`对象,对应的file mode是100644,但是对于`lib`子仓库的确是一个`commit`对象, file mode为160000,这是Git中一种特殊的模式,表明我们是将一次提交的`commit`记录在Git当中,而非将它记录成一个子目录或者文件。

而这正式`git submodule`的核心原理,Git在处理`submodule`引用的时候,并不会去扫描子仓库下的文件的变化,而是取子仓库当前的`HEAD`指向的`commit`的hash值,当我们对子仓库进行了更改后,Git获取到子模块的`commit`值发生变化,从而记录了这个Git指针的变化。

在暂存区所以我们才发现了`new commits`这种提示语,Git并不关心子模块的文件如何变化,我只需要在当前提交中记录子模块的commit的hash值即可,之后我们从父级仓库拉取子仓库的时候,Git拉取了本次提交记录中的子模块的hash值对应的提交,就还原了我们的整个仓库的代码。

**1.5 `git submodule`注意点**

虽然使用`git submodule`为我们的开发带来了很多便利,但是随之而来也会导致一些比较容易犯的错误,整理出来,防止大家采坑:

1. 当子模块有提交的时候,没有push到远程仓库, 父级引用子模块的commit更新,并提交到远程仓库, 当别人拉取代码的时候就会报出子模块的commit不存在 `fatal: reference isn’t a tree`。  
    
2. 如果你仅仅引用了别人的子模块的游离分支,然后在主仓库修改了子仓库的代码,之后使用`git submodule update`拉取了最新代码,那么你在子仓库游离分支做出的修改会被覆盖掉。  
    
3. 我们假设你一开始在主仓库并没有采用子模块的开发方式,而是在另外的开发分支使用了子仓库,那么当你从开发分支切回到没有采用子模块的分支的时候,子模块的目录并不会被Git自动删除,而是需要你手动的删除了 。  
    

## `2. git subtree(子树合并)`

上面介绍的`git submodule`是Git自带的原生功能,我们接下来将要介绍的`git subtree`则是由第三方开发者贡献的`contrib script`,Git本身并不提供`git subtree`命令,contrib中包含一些实验性的第三方工具,由各自的作者进行维护。

同时这也让我们认识到`git subtree`不是Git原生支持的命令,而是第三方开发者通过Git的底层命令写出的一个高层次脚本,所以它是可以由基础的Git命令来实现的,我们稍后会介绍`git subtree`的实现原理,在此之前,还是先来介绍一下`git subtree`的基础使用吧!

**2.1 开始使用子树合并**

我们按照子模块时讲的,首先在本地创建`main`和`lib`的子仓库,然后对两个仓库各自进行一次提交,代码此处不再重复展示。

初始化结束两个子仓库后,我们想让`main`主仓库能够使用`lib`仓库的代码进行后续的开发,使用`git subtree add`的命令后面加上想要跟踪项目URL来添加新的子模块(本文中的`lib`仓库),这段和之前的步骤基本一致,但是命令使用方式不同。

```bash
cd main

git subtree add --prefix=lib /path/to/repos/lib.git master

git fetch /path/to/repos/lib.git master

warning: no common commits
remote: Enumerating objects: 3, done.
remote: Counting objects: 100% (3/3), done.
remote: Total 3 (delta 0), reused 0 (delta 0)
Unpacking objects: 100% (3/3), done.
From /path/to/repos/lib
 * branch            master     -> FETCH_HEAD
Added dir 'lib'
```

我们首先分析一下加入子仓库的命令的参数部分: - `--prefix=lib`: 指定我们要把子仓库放到哪个文件夹下面 - `/path/to/repos/lib.git`: 指定我们子仓库的地址 - `master`: 指定我们子仓库需要拉取回代码的分支

执行完上述命令后,我们查看`main`仓库下当前的目录结构:

```bash
tree

.
├── index.js
└── lib
    └── util.js
```

我们发现`lib`仓库已经被放到`main`仓库下的lib目录下面了,除了一个`lib`文件夹外,`git subtree`并没有额外的标记信息去记录我们子仓库的地址,这也正是`git subtree`命令繁琐的地方,`add`命令和其他的命令每次都要指定我们子仓库的远程地址,如果你觉得复杂,可以使用`git remote add lib /path/to/repos/lib.git`去给远程服务器取一个别名,以后就可以使用 `git subtree add --prefix=lib lib master`进行其他类似命令的操作了。

我们进入到`lib`文件夹下面,查看文件夹下面的文件,我们发现`git subtree`并没有包含`.git`文件夹,这也是和`git submodule`不一致的地方,`lib`在主仓库下就像是一堆子仓库的文件,我们并不能从`lib`下进行子仓库的提交,而是要使用`git subtree`其他的命令进行提交和拉取操作,`subtree`表现的就像是所有的代码都在我们的主仓库下,并不存在什么其他的子仓库一样。

**2.2 克隆含有子项目的仓库**

对包含`subtree`的主仓库进行拉取非常简单,就像我们拉取普通仓库一样支持克隆即可。

```bash
git clone /path/to/repos/main.git
```

并不掺杂什么额外的操作,我们进入到仓库下发现,主仓库和子仓库的代码都已经包含在当前目录下面了。

**2.3 在主仓库上进行协同开发**

当我们在主仓库对`lib`进行修改后,我们执行`git status`查看一下:

```bash
git status

On branch master
Your branch is up to date with 'origin/master'.

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

        modified:   lib/util.js

no changes added to commit (use "git add" and/or "git commit -a")
```

我们发现了`subtree`和`submodule`不一样的另外一点,子仓库的更改是会反映在主仓库的更改上面的,我们刚才也提到`lib`就是代码目录,没办法像`submodule`一样直接在子仓库中提交,所以`subtree`提供了另外两个命令来对代码进行拉取和推送的操作 - `git subtree pull` - `git subtree push`

如果当前情况下我们只在主仓库下对子仓库的代码进行了修改,无论如何我们都需要对主仓库进行一次提交(_针对本文开始讲的大前提的条件下_),这就是`subtree`的提交模式,从我们的主仓库的提交历史下拆分部分`commit`出去给子仓库进行提交,现在不理解也没有关系,我们等会在讲述`subtree`原理的时候会提到这个地方。

我们首先提交主仓库:

```bash
# 省略部分输出信息
git add .
git commit -m "修改了lib的代码"
```

然后我们尝试去推送子包代码的更新:

```bash
# 首先要拉取一下子仓库是否存在更新
# 如果拉取子仓库的过程中存在冲突,我们需要在主仓库解决冲突后重新提交一次commit
git subtree pull --prefix /path/to/repos/lib.git master

From /path/to/repos/lib
 * branch            master     -> FETCH_HEAD
Subtree is already at commit a5f21e31a721920ba7007949f3db59df4b543436.

# push代码到子仓库,我们不难发现 subtree的命令格式基本都是一致的
git subtree push --prefix /path/to/repos/lib.git master

git push using:  /path/to/repos/lib.git master
Enumerating objects: 8, done.
Counting objects: 100% (8/8), done.
Delta compression using up to 4 threads
Compressing objects: 100% (2/2), done.
Writing objects: 100% (4/4), 511 bytes | 511.00 KiB/s, done.
Total 4 (delta 0), reused 0 (delta 0)
To /path/to/repos/lib.git
   a5f21e3..67387da  67387da30c87c97bb4e0020be18e8da7a720dbab -> master
```

这样子我们就在主仓库完成了对子仓库的拉取和推送,`subtree`使用起来我们发现并没有什么奇怪的地方,但是它确实帮我们管理了子仓库的代码,那么`subtree`是怎么做到的呢?

**2.4 `git subtree`原理分析**

我们主要对`subtree`新增子仓库和合并子仓库更新的原理进行讲解, `push`的操作我们稍后会简单的提一下。

首先`subtree`是如何将子仓库的代码加入到我们的子仓库的呢? `git subtree`我们中文一般翻译成_"子树合并"_,那么正如我们理解的,`subtree`正是利用了Git的的底层的`tree`对象和一些相关对象完成了增加子仓库的操作,我们简短的总结为下面这么一句话:

> 在主仓库中我们通过Git拉取到子仓库下的分支代码到主仓库的另外一根分支中, 通过类似`merge`的操作,将代码合并到我们主仓库的某个目录下,此时会生成的一次提交对象, 这个提交对象parent引用了我们主仓库的当前commit对象和子仓库的当前commit对象, 就完成了子仓库的新增,主仓库也顺便记录了子仓库的所有文件。  

这句话有点绕? 没关系,我们用Git的代码来演示一下这个过程,当然首先我们还是要初始化`main`和`lib`两个仓库,并且对各自进行一次初始化的提交。

### `git subtree add原理解析`

然后我们对`git subtree add`的过程进行拆解,使用了部分Git的底层命令,我们首先对它们进行一个简单介绍:

- `git read-tree`: 将某次commit的提交读取到当前的暂存区,工作区不变
- `git write-tree`: 将暂存区保存的文件生成一个顶级的tree对象,返回tree-hash
- `git commit-tree`: 生成一个commit对象,可以指定引用的`tree`对象,`parent`对象和提交信息
- `git cat-file`: 查看git底层四种对象信息

`git`可以设置不同的remote的远程服务器地址,我们之前使用`git fetch`都是获取同一个项目的文件,但是`git fetch`也可以获取其他项目(比如子仓库)的内容,放到另外一根分支上,然后通过合并的策略来完成子仓库的代码拉取。

在`main`仓库进行初始化子仓库的操作

为了方便之后对远程仓库做跟踪,我们在remote上面对仓库做一个别名:

```bash
cd main
git remote add lib /path/to/repos/lib.git # git添加服务器别名
```

首先, 我们需要将子仓库的代码拉取到主仓库里面来:

```bash
git fetch lib

warning: no common commits
remote: Enumerating objects: 3, done.
remote: Counting objects: 100% (3/3), done.
remote: Total 3 (delta 0), reused 0 (delta 0)
Unpacking objects: 100% (3/3), done.
From /path/to/repos/lib
 * [new branch]      master     -> lib/master
```

查看一下当前的所有分支:

```bash
git branch -a

* master
  remotes/lib/master
  remotes/origin/master
```

将远程的`lib`分支代码首先合并到main仓库的`lib`分支上面来方便后续操作。

```bash
# 创建lib的本地分支
git checkout -b lib lib/master

Branch 'lib' set up to track remote branch 'master' from 'lib'.
Switched to a new branch 'lib'

# 然后切换回master分支
git checkout master
```

当前子模块(`lib`)的代码已经到了我们本地的一根分支上面了,我们和`submodule`的使用方式一样,也要将`lib`文件夹放到`main`文件夹下面使用,所以需要将子仓库的代码合并到主仓库的一根分支上面来:

查看当前`lib`分支的最新提交的`commit-id`,然后获取到相对应的`tree-id`:

```bash
# 查看lib对应的tree-id
git cat-file -p lib 

tree 309cc0d
author userName <email> 1577349863 +0800
committer userName <email> 1577349863 +0800

feat: 创建lib文件

# 查看当前tree对象下面的文件:
# 当前tree对象下面包含我们在lib创建的index.js文件
git cat-file -p 309cc0d

100644 blob 043a685d4c9b48a74bdde1181ab22b53f8a8e363    index.js
```

我们回到`main`仓库下,调用`git read-tree`将`lib`分支下的代码读取到暂存区和工作目录下:

```text
# -u 指定在更新暂存区文件成功后,将文件一起写入到工作目录下
# --prefix 指定需要将文件放到哪个子目录下
git read-tree -u --prefix=lib lib
```

执行`git status`查看当前仓库状态:

```bash
git status

On branch master
Your branch is up to date with 'origin/master'.

Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)

        new file:   lib/index.js
```

我们发现`lib`仓库的代码以子目录的形式存在于`main`上面了,现在还不能够提交,因为现在没有体现出两个分支的合并关系,之后主仓库下修改了子仓库代码就会导致不方便拆分子仓库代码,如果现在直接提交,仅仅只是我们将`lib`的代码类似拷贝的操作放到了主仓库下,所以我们还需要调用`git write-tree`和`git commit-tree`生成一次新的commit对象建立起来分支间的联系:

```bash
# 因为read-tree已经将子仓库的文件添加到了暂存区
# 我们可以调用write-tree对当前的暂存区文件生成一个tree对象
git write-tree
e0551170da5e913efe6a97c1137f4da890688243
```

之后我们手动创建一次合并提交,也就是`commit`对象,这个提交要有两个父对象,分别是`main`的提交对象和`lib`的提交对象,用`git rev-parse`首先获取到两次提交的ID:

```bash
git rev-parse master
57d55a545a24a10df7b4be4e3eb79dc3c3c195e6

git rev-parse lib
b8bcfe5c2ec04c7c028bbab8dfd3dbea53dcb745
```

执行`commit-tree`命令手动创建提交,提交需要的`tree`对象来自于我们`write-tree`生成的`tree`对象,父级的提交用上面两个ID, 我们需要输出一些提交消息到`commit`对象中来显示当前这次提交做了些什么事情,`commit-tree`支持从输入流中获取提交消息:

```bash
echo "初次合并子模块" | git commit-tree e0551170da5e913efe6a97c1137f4da890688243 \
-p 57d55a545a24a10df7b4be4e3eb79dc3c3c195e6 \
-p b8bcfe5c2ec04c7c028bbab8dfd3dbea53dcb745

# 此处显示的是commit对象的ID;
e54dc295322387a460130f33ed571f724c700fe8
```

然后此时`master`分支并没有指向到我们新生成的这次`commit`对象上面,我们使用`git reset`将分支强指到本次提交对象上面来:

```bash
git reset e54dc295322387a460130f33ed571f724c700fe8
```

查看一下当前的提交历史,可以看到我们将父仓库和子仓库的提交合并到了一起:

```text
git log --graph --pretty=oneline

*   e54dc295322387a460130f33ed571f724c700fe8 (HEAD -> master) 初次合并子模块
|\  
| * b8bcfe5c2ec04c7c028bbab8dfd3dbea53dcb745 (lib/master, lib) feat: 创建lib文件
* 57d55a545a24a10df7b4be4e3eb79dc3c3c195e6 (origin/master) feat: main创建
```

这样我们就完成了对子树的初次合并的操作,整个过程还是比较繁琐的,需要对Git的`Plumbing(底层命令)`有较为清楚的认知,不过我们可以使用`git subtree add`就可以完成上述的操作;

### `git subtree pull原理解析`

如果`lib`的上游代码提交了新的代码,我们就需要将新代码合并到`main`仓库下面来,之前讲解了`git subtree pull`的用法,我们现在简单分析下`pull`这个行为的原理:

首先我们在`main`仓库下切换到`lib`分支,将最新代码通过`git pull`拉取回来,case比较简单, 此处不再进行赘述,切换回到`master`分支,我们利用`git merge`子树合并策略将代码合并到`lib`文件夹下,如果直接merge的话,代码就不会合并到子文件夹下面。

```text
# -X指定merge的合并策略为subtree
git merge -Xsubtree=lib lib
```

这样子我们就将子仓库的上游更新合并到了主仓库下,此处涉及到的合并策略我们不再进行详细分析,冲突解决都是提升到主仓库级别进行处理的和`submodule`的形式不太一致,有兴趣的读者可以对`git subtree`的源码进行扩展阅读。

### `git subtree push原理解析`

`push`的操作在`subtree`的底层涉及到了`split`的方式对代码进行拆分,我们讲解一下`git subtree split`的使用。

```bash
# 在main仓库下的master分支进行操作
git subtree split --prefix=lib -b lib-split

Created branch 'lib-split'
8e8086648ff4956062a7239beebef7494d47c137
```

`split`操作指定`main`下面需要分割的目录, 按照上次的子仓库的提交ID进行拆分到指定的分支上面去, 我们的`git subtree push`底层也依赖了这个操作。

我们假设`main`仓库下我们新增了三次提交,其中一次提交包含了对`lib`文件夹的修改,`split`会找到上次包含`lib`的commit的ID然后进行查找当前这三次提交有没有针对子仓库的修改。

此时`split`会找出三次修改中哪次`commit`对象修改了子仓库,然后将它的`tree`对象找出,然后将此次`commit`对象的commit-message合并创建一次新的针对`lib`的`commit`对象, 重新设置本次提交的父类对象。

之后这些修改拆分后拷贝到另外一根分支上,这根分支仅包含`lib`子仓库的修改,然后使用`git push`指定提交的远程仓库提交到`lib`下面。

`subtree`提交的原理我们只进行了简单的分析,有兴趣的读者可以对`git subtree`的源码进行扩展阅读。

## 总结

我们对`submodule`和`subtree`的用法以及原理都进行了比较详细的阐述,因为涉及内容比较多,而且原理部分大多是Git的底层机制,阅读起来可能有些难度,我们大多用了Git的演示来对这些内容进行了分析,但因为笔者能力一般水平有限,可能存在部分不正确的地方,大家可以对内容进行纠正 。