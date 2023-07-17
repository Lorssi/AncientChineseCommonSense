# Git

常用速查表：

![image-20210603212958908](https://gitee.com/lishuaicong/note-image/raw/master/img/image-20210603212958908.png)

# Git概述

Git 是一个免费的、开源的分布式版本控制系统，可以快速高效地处理从小型到大型的各种

项目。

Git 易于学习，占地面积小，性能极快。 它具有廉价的本地库，方便的暂存区域和多个工作

流分支等特性。其性能优于 Subversion、CVS、Perforce 和 ClearCase 等版本控制工具。

## 什么是版本控制

版本控制（Revision control）是一种在开发的过程中用于管理我们对文件、目录或工程等内容的修改历史，==方便查看更改历史记录，备份以便恢复以前的版本的软件工程技术。==

* 实现跨区域多人协同开发

* 追踪和记载一个或者多个文件的历史记录

* 组织和保护你的源代码和文档

* 统计工作量

* 并行开发、提高开发效率

* 跟踪记录整个软件的开发过程

* 减轻开发人员的负担，节省时间，同时降低人为错误

简单说就是用于管理多人协同开发项目的技术。

没有进行版本控制或者版本控制本身缺乏正确的流程管理，在软件开发过程中将会引入很多问题，如软件代码的一致性、软件内容的冗余、软件过程的事物性、软件开发过程中的并发性、软件源代码的安全性，以及软件的整合等问题。

无论是工作还是学习，或者是自己做笔记，都经历过这样一个阶段！我们就迫切需要一个版本控制工具！

## 常见的版本控制工具

我们学习的东西，一定是当下最流行的！

主流的版本控制器有如下这些：

* **Git**

* **SVN**（Subversion）

* **CVS**（Concurrent Versions System）

* **VSS**（Micorosoft Visual SourceSafe）

* **TFS**（Team Foundation Server）

* **Visual Studio Online**

版本控制产品非常的多（Perforce、Rational ClearCase、RCS（GNU Revision Control System）、Serena Dimention、SVK、BitKeeper、Monotone、Bazaar、Mercurial、SourceGear Vault），现在影响力最大且使用最广泛的是Git与SVN /GitLab

### 集中式版本控制工具

CVS、SVN(Subversion)、VSS……

集中化的版本控制系统诸如 CVS、SVN 等，都有一个单一的集中管理的服务器，保存

所有文件的修订版本，而协同工作的人们都通过客户端连到这台服务器，取出最新的文件或

者提交更新。多年以来，这已成为版本控制系统的标准做法。这种做法带来了许多好处，每个人都可以在一定程度上看到项目中的其他人正在做些什么。而管理员也可以轻松掌控每个开发者的权限，并且管理一个集中化的版本控制系统，要远比在各个客户端上维护本地数据库来得轻松容易。

事分两面，有好有坏。这么做显而易见的缺点是中央服务器的单点故障。如果服务器宕

机一小时，那么在这一小时内，谁都无法提交更新，也就无法协同工作。

且所有的版本数据都存在服务器上，用户的本地只有自己以前所同步的版本，如果不连网的话，用户就看不到历史版本，也无法切换版本验证问题，或在不同分支工作。

![image-20210601222224984](https://gitee.com/lishuaicong/note-image/raw/master/img/image-20210601222224984.png)

### 分布式版本控制工具

Git、Mercurial、Bazaar、Darcs……像 Git 这种分布式版本控制工具，客户端提取的不是最新版本的文件快照，而是把代码仓库完整地镜像下来（本地库）。这样任何一处协同工作用的文件发生故障，事后都可以用其他客户端的本地仓库进行恢复。因为每个客户端的每一次文件提取操作，实际上都是一次对整个文件仓库的完整备份。分布式的版本控制系统出现之后,解决了集中式版本控制系统的缺陷:

1. 服务器断网的情况下也可以进行开发（因为版本控制是在本地进行的）

2. 每个客户端保存的也都是整个完整的项目（包含历史记录，更加安全）

![image-20210601222622466](https://gitee.com/lishuaicong/note-image/raw/master/img/image-20210601222622466.png)

对比图如下：

![image-20210601223037989](https://gitee.com/lishuaicong/note-image/raw/master/img/image-20210601223037989.png)

### Git与SVN的区别

SVN是集中式版本控制系统，版本库是集中放在中央服务器的，而工作的时候，用的都是自己的电脑，所以首先要从中央服务器得到最新的版本，然后工作，完成工作后，需要把自己做完的活推送到中央服务器。集中式版本控制系统是必须联网才能工作，对网络带宽要求较高。

Git是分布式版本控制系统，没有中央服务器，每个人的电脑就是一个完整的版本库，工作的时候不需要联网了，因为版本都在自己电脑上。协同的方法是这样的：比如说自己在电脑上改了文件A，其他人也在电脑上改了文件A，这时，你们两之间只需把各自的修改推送给对方，就可以互相看到对方的修改了。Git可以直接看到更新了哪些代码和文件！

**Git是目前世界上最先进的分布式版本控制系统。**

## Git简史

同生活中的许多伟大事物一样，Git 诞生于一个极富纷争大举创新的年代。

Linux 内核开源项目有着为数众广的参与者。绝大多数的 Linux 内核维护工作都花在了提交补丁和保存归档的繁琐事务上(1991－2002年间)。到 2002 年，整个项目组开始启用一个专有的分布式版本控制系统 BitKeeper 来管理和维护代码。

Linux社区中存在很多的大佬！破解研究 BitKeeper ！

到了 2005 年，开发 BitKeeper 的商业公司同 Linux 内核开源社区的合作关系结束，他们收回了 Linux 内核社区免费使用 BitKeeper 的权力。这就迫使 Linux 开源社区(特别是 Linux 的缔造者 Linus Torvalds)基于使用 BitKeeper 时的经验教训，开发出自己的版本系统。（2周左右！） 也就是后来的 Git！

**Git是目前世界上最先进的分布式版本控制系统。**

Git是免费、开源的，最初Git是为辅助 Linux 内核开发的，来替代 BitKeeper！Git的历史

![image-20210601223236775](https://gitee.com/lishuaicong/note-image/raw/master/img/image-20210601223236775.png)

# Git工作流程

## 三个区域

Git本地有三个工作区域：工作目录（Working Directory）、暂存区(Stage/Index)、资源库(Repository或Git Directory)。如果在加上远程的git仓库(Remote Directory)就可以分为四个工作区域。文件在这四个区域之间的转换关系如下：

![image-20210609213719522](https://gitee.com/lishuaicong/note-image/raw/master/elastic-search/image-20210609213719522.png)

* Workspace：工作区，就是你平时存放项目代码的地方,就是你在电脑里能看到的目录。

* Index / Stage：暂存区，用于临时存放你的改动，事实上它只是一个文件，保存即将提交到文件列表信息。一般存放在 **.git** 目录下的 index 文件（.git/index）中，所以我们把暂存区有时也叫作索引（index）。

* Repository：仓库区（或本地仓库），就是安全存放数据的位置，这里面有你提交到所有版本的数据。其中HEAD指向最新放入仓库的版本。工作区有一个隐藏目录 **.git**，这个不算工作区，而是 Git 的版本库。

* Remote：远程仓库，托管代码的服务器，可以简单的认为是你项目组中的一台电脑用于远程数据交换

下面这个图展示了工作区、版本库中的暂存区和版本库之间的关系：

![image-20210609214151774](https://gitee.com/lishuaicong/note-image/raw/master/elastic-search/image-20210609214151774.png)

- 图中左侧为工作区，右侧为版本库。在版本库中标记为 "index" 的区域是暂存区（stage/index），标记为 "master" 的是 master 分支所代表的目录树。
- 图中我们可以看出此时 "HEAD" 实际是指向 master 分支的一个"游标"。所以图示的命令中出现 HEAD 的地方可以用 master 来替换。
- 图中的 objects 标识的区域为 Git 的对象库，实际位于 ".git/objects" 目录下，里面包含了创建的各种对象及内容。
- 当对工作区修改（或新增）的文件执行 **git add** 命令时，暂存区的目录树被更新，同时工作区修改（或新增）的文件内容被写入到对象库中的一个新的对象中，而该对象的ID被记录在暂存区的文件索引中。
- 当执行提交操作（git commit）时，暂存区的目录树写到版本库（对象库）中，master 分支会做相应的更新。即 master 指向的目录树就是提交时暂存区的目录树。
- 当执行 **git reset HEAD** 命令时，暂存区的目录树会被重写，被 master 分支指向的目录树所替换，但是工作区不受影响。
- 当执行 **git rm --cached <file>** 命令时，会直接从暂存区删除文件，工作区则不做出改变。
- 当执行 **git checkout .** 或者 **git checkout -- <file>** 命令时，会用暂存区全部或指定的文件替换工作区的文件。这个操作很危险，会清除工作区中未添加到暂存区中的改动。
- 当执行 **git checkout HEAD .** 或者 **git checkout HEAD <file>** 命令时，会用 HEAD 指向的 master 分支中的全部或者部分文件替换暂存区和以及工作区中的文件。这个命令也是极具危险性的，因为不但会清除工作区中未提交的改动，也会清除暂存区中未提交的改动。

## 工作流程

git的工作流程一般是这样的：

1. 克隆Git资源作为工作目录；  git clone [url]   git checkout [branch]

2. 在工作目录中添加、修改文件；

3. 将需要进行版本管理的文件放入暂存区域； git add  git commit 

4. 将暂存区域的文件提交到git仓库。 git push(冲突)  git pull  

因此，git管理的文件有三种状态：已修改（modified）,已暂存（staged）,已提交(committed)

![image-20210609214444771](https://gitee.com/lishuaicong/note-image/raw/master/elastic-search/image-20210609214444771.png)

## 文件的四种状态

版本控制就是对文件的版本控制，要对文件进行修改、提交等操作，首先要知道文件当前在什么状态，不然可能会提交了现在还不想提交的文件，或者要提交的文件没提交上。

* **Untracked**: 未跟踪, 此文件在文件夹中, 但并没有加入到git库, 不参与版本控制. 通过git add 状态变为Staged.

* **Unmodify**: 文件已经入库, 未修改, 即版本库中的文件快照内容与文件夹中完全一致. 这种类型的文件有两种去处, 如果它被修改, 而变为Modified. 如果使用git rm移出版本库, 则成为Untracked文件

* **Modified**: 文件已修改, 仅仅是修改, 并没有进行其他的操作. 这个文件也有两个去处, 通过git add可进入暂存staged状态, 使用git checkout 则丢弃修改过, 返回到unmodify状态, 这个git checkout即从库中取出文件, 覆盖当前修改 !

* **Staged**: 暂存状态. 执行git commit则将修改同步到库中, 这时库中的文件和本地文件又变为一致, 文件为Unmodify状态. 执行git reset HEAD filename取消暂存, 文件状态为Modified

## 忽略文件

有些时候我们不想把某些文件纳入版本控制中，比如数据库文件，临时文件，设计文件等

在主目录下建立".gitignore"文件，此文件有如下规则：

1. 忽略文件中的空行或以井号（#）开始的行将会被忽略。

2. 可以使用Linux通配符。例如：星号（*）代表任意多个字符，问号（？）代表一个字符，方括号（[abc]）代表可选字符范围，大括号（{string1,string2,...}）代表可选的字符串等

3. 如果名称的最前面有一个感叹号（!），表示例外规则，将不被忽略。

4. 如果名称的最前面是一个路径分隔符（/），表示要忽略的文件在根目录下，而根目录的子目录中的文件不忽略。

5. 如果名称的最后面是一个路径分隔符（/），表示要忽略的是此目录下该名称的子目录，而非文件（默认文件或目录都忽略）。

```
#为注释
*.txt         #忽略所有 .txt结尾的文件,这样的话上传就不会被选中！
!lib.txt       #但lib.txt除外
/temp        #仅忽略项目根目录下的TODO文件,不包括其它目录
build/        #忽略build/目录下的所有文件
doc/*.txt     #会忽略 doc/notes.txt 但不包括 doc/server/arch.txt
```

# Git使用

## Git常用命令

| 命令                                                | 作用                               |
|:-------------------------------------------------:|:--------------------------------:|
| git config --global user.name 用户名                 | 设置用户签名                           |
| git config --global user.email 邮箱                 | 设置用户邮箱                           |
| <font color="red">git init</font>                 | <font color="red">初始化本地库</font>  |
| <font color="red">git status</font>               | <font color="red">查看本地库状态</font> |
| <font color="red">git add 文件名</font>              | <font color="red">添加到暂存区</font>  |
| <font color="red">git commit -m "日志信息" 文件名</font> | <font color="red">提交到本地库</font>  |
| <font color="red">git reflog</font>               | <font color="red">查看历史记录</font>  |
| <font color="red">git reset --hard 版本号</font>     | <font color="red">版本穿梭</font>    |

### 设置用户签名

当你安装Git后首先要做的事情是设置你的用户名称和e-mail地址。这是非常重要的，因为每次Git提交都会使用该信息。它被永远的嵌入到了你的提交中：

基本语法

​    git config --global user.name 用户名

​    git config --global user.email 邮箱

只需要做一次这个设置，如果你传递了--global 选项，因为Git将总是会使用该信息来处理你在系统中所做的一切操作。如果你希望在一个特定的项目中使用不同的名称或e-mail地址，你可以在该项目中运行该命令而不要--global选项。总之--global为全局配置，不加为某个项目的特定配置。

可以用 git config --global --list来查看：

<img src="https://gitee.com/lishuaicong/note-image/raw/master/img/image-20210602182311253.png" alt="image-20210602182311253"  />

又或者，可以在c盘用户下的.gitconfig文件中查看：

<img src="https://gitee.com/lishuaicong/note-image/raw/master/img/image-20210602182230570.png" alt="image-20210602182230570" style="zoom: 50%;" />

说明：

签名的作用是区分不同操作者身份。用户的签名信息在每一个版本的提交信息中能够看到，以此确认本次提交是谁做的。Git 首次安装必须设置一下用户签名，否则无法提交代码。

<font color="red">**※注意：**</font>这里设置用户签名和将来登录 GitHub（或其他代码托管中心）的账号没有任

何关系。

### 初始化本地库

基本语法

* git init

案例实操

<img src="https://gitee.com/lishuaicong/note-image/raw/master/img/image-20210602153151406.png" alt="image-20210602153151406"  />

结果查看

<img src="https://gitee.com/lishuaicong/note-image/raw/master/img/image-20210602153233873.png" alt="image-20210602153233873" style="zoom: 50%;" />

### 查看本地库状态

基本语法

* git status

案例实操

* 首次查看（工作区没有任何文件）
  
  <img src="https://gitee.com/lishuaicong/note-image/raw/master/img/image-20210602153614671.png" alt="image-20210602153614671" style="zoom: 80%;" />
  
  * 第一行
  
  ```
  on branch master
  ```
  
  是说明当前本地库是在master分支上
  
  * 第二行
  
  ```
  No commits yet
  ```
  
  说明当前没有提交过任何东西。
  
  * 第三行
  
  ```
  nothing to commit (create/copy files and use "git add" to track)
  ```
  
  说明当前没有东西需要提交。

* 新增文件
  
  <img src="https://gitee.com/lishuaicong/note-image/raw/master/img/image-20210602183503292.png" alt="image-20210602183503292" style="zoom:50%;" />
  
  这里我是直接手动创建的，也可以用linux命令vim hello.txt来创建。不过这都不是重点，创建这个文件只是为了验证操作
  
  怎么创建的并不重要，里面的内容也不重要。

* 查看
  
  <img src="https://gitee.com/lishuaicong/note-image/raw/master/img/image-20210602183605817.png" alt="image-20210602183605817"  />

### 添加到暂存区

**基本语法**

* git add 文件名

**案例实操**

<img src="https://gitee.com/lishuaicong/note-image/raw/master/img/image-20210602183919290.png" alt="image-20210602183919290"  />

* 因为是手动创建的，因此没有什么幺蛾子。如果是上面说的vim hello.txt创建的，可能换行会报一个warning，        不过问题应该不大。

<img src="https://gitee.com/lishuaicong/note-image/raw/master/img/image-20210602184018753.png" alt="image-20210602184018753" style="zoom:80%;" />

**查看状态**

<img src="https://gitee.com/lishuaicong/note-image/raw/master/img/image-20210602184142031.png" alt="image-20210602184142031"  />

### 提交到本地库

**将暂存区的文件提交到本地库**

基本语法

* git commit -m "日志信息" 文件名

案例实操

<img src="https://gitee.com/lishuaicong/note-image/raw/master/img/image-20210602184742526.png" alt="image-20210602184742526"  />

**查看状态（没有文件需要提交）**

<img src="https://gitee.com/lishuaicong/note-image/raw/master/img/image-20210602184947889.png" alt="image-20210602184947889"  />

**修改文件** <a id="txt"></a>

<img src="https://gitee.com/lishuaicong/note-image/raw/master/img/image-20210602185139694.png" alt="image-20210602185139694" style="zoom: 50%;" />

**查看状态（检测到工作区有文件被修改）**

<img src="https://gitee.com/lishuaicong/note-image/raw/master/img/image-20210602185242960.png" alt="image-20210602185242960"  />

**将修改过的文件再次添加到暂存区**

<img src="https://gitee.com/lishuaicong/note-image/raw/master/img/image-20210602185338900.png" alt="image-20210602185338900" style="zoom:80%;" />

**查看状态（工作区的修改添加到了暂存区）**

<img src="https://gitee.com/lishuaicong/note-image/raw/master/img/image-20210602185423023.png" alt="image-20210602185423023" style="zoom: 80%;" />

### 历史版本

#### 查看历史版本

* 基本语法
  
  ```
  git reflog 查看版本信息
  git log 查看版本详细信息
  ```

* 案例实操

<img src="https://gitee.com/lishuaicong/note-image/raw/master/img/image-20210602215443098.png" alt="image-20210602215443098"  />

这里git log下的是完整的版本号，而git reflog下的则是完整版本号的前七位。

* 基本语法
  
  ```
  git reset --hard
  ```

* 案例实操
  
  hello.txt当前内容在[这里--ctrl+左键前往](#txt)
  
  <img src="https://gitee.com/lishuaicong/note-image/raw/master/img/image-20210602220813329.png" alt="image-20210602220813329"  />
  
  结果如下，hello.txt的版本到了第一版：
  
  <img src="https://gitee.com/lishuaicong/note-image/raw/master/img/image-20210602220858434.png" alt="image-20210602220858434" style="zoom: 50%;" />

Git 切换版本，底层其实是移动的 HEAD 指针，具体原理如下图所示。

<img src="https://gitee.com/lishuaicong/note-image/raw/master/img/image-20210602221134100.png" alt="image-20210602221134100" style="zoom:67%;" />

### Git分支操作

<img src="https://gitee.com/lishuaicong/note-image/raw/master/img/image-20210602221300734.png" alt="image-20210602221300734" style="zoom:67%;" />

> 什么是分支

​    在版本控制过程中，同时推进多个任务，为每个任务，我们就可以创建每个任务的单独分支。使用分支意味着程序员可以把自己的工作从开发主线上分离开来，开发自己分支的时候，不会影响主线分支的运行。对于初学者而言，分支可以简单理解为副本，一个分支就是一个单独的副本。（分支底层其实也是指针的引用）

<img src="https://gitee.com/lishuaicong/note-image/raw/master/img/image-20210602221416209.png" alt="image-20210602221416209" style="zoom:80%;" />

> 分支的好处

同时并行推进多个功能开发，提高开发效率。各个分支在开发过程中，如果某一个分支开发失败，不会对其他分支有任何影响。失败

的分支删除重新开始即可。

> 分支操作

| 命令名称             | 作用          |
|:----------------:|:-----------:|
| git branch 分支名   | 创建分支        |
| git branch -v    | 查看分支        |
| git checkout 分支名 | 切换分支        |
| git merge 分支名    | 把分支合并到当前分支上 |

#### 查看分支

> 基本语法

```
git branch -v
```

> 案例实操

<img src="https://gitee.com/lishuaicong/note-image/raw/master/img/image-20210602221933928.png" alt="image-20210602221933928" style="zoom: 80%;" />

```
* 代表当前所在的分区
```

#### 创建分支

> 基本语法

```
git branch 分支名
```

> 案例实操

<img src="https://gitee.com/lishuaicong/note-image/raw/master/img/image-20210602222204317.png" alt="image-20210602222204317"  />

这里的

```
hot-fix 6ad4749 my first commit
```

就是刚创建的分支，并将主分支master的内容复制了一份

> 修改分支

先在master分支上修改<a id="switchBranch">*</a>

![image-20210602223257071](https://gitee.com/lishuaicong/note-image/raw/master/img/image-20210602223257071.png)

之后对master分支进行操作

![image-20210602223501536](https://gitee.com/lishuaicong/note-image/raw/master/img/image-20210602223501536.png)

首先查看状态，发现尚未添加到暂存区，于是添加到暂存区。之后提交到本地库中，信息为my third commit。最后查看分支，发现master分支上的版本号已经发生了变化，之前是6ad4749,而hot-fix分支则没有发生变化。

#### 切换分支

> 基本语法

```
git checkout 分支名
```

> 案例实操

![image-20210602224234144](https://gitee.com/lishuaicong/note-image/raw/master/img/image-20210602224234144.png)

可以看到，提示信息为：

```
Switched to branch 'hot-fix'
```

说明现在的分支已经转换到了hot-fix这分支上。

这时候我们再看一下我们的hello.txt，发现其中的内容果然变成了hot-fix分支上的内容：

![image-20210602224354074](https://gitee.com/lishuaicong/note-image/raw/master/img/image-20210602224354074.png)

之前master最后一次操作的时候，文件中的内容是[如图](#switchBranch)。

之后我们修改hot-fix分支上的文件：

![image-20210602224706669](https://gitee.com/lishuaicong/note-image/raw/master/img/image-20210602224706669.png)

之后提交到本地库中：

![image-20210602224832109](https://gitee.com/lishuaicong/note-image/raw/master/img/image-20210602224832109.png)

#### 合并分支

> 基本语法

```
git merge 分支名
```

> 案例实操

在master分支上合并hot-fix分支

![image-20210602225046791](https://gitee.com/lishuaicong/note-image/raw/master/img/image-20210602225046791.png)

> 产生冲突

如上图，master的后面跟了一个MERGING，这就是产生冲突的标志

![image-20210602225139511](https://gitee.com/lishuaicong/note-image/raw/master/img/image-20210602225139511.png)

打开hello.txt后发现文件中多了如图几行。

冲突产生的原因：

​    合并分支时，两个分支在==同一个文件的同一个位置有两套完全不同的修改==。Git 无法替我们决定使用哪一个。必须==人为决定==新代码内容。

查看状态（检测到有文件有两处修改）

![image-20210602225529428](https://gitee.com/lishuaicong/note-image/raw/master/img/image-20210602225529428.png)

##### 解决冲突

> 编辑有冲突的文件，删除特殊符号，决定要使用的内容

特殊符号：

<<<<<<< HEAD

​    当前分支的代码

\=\=\=\=\=\=\=

​    合并过来的代码

\>\>\>\>\>\>\> hot-fix

编辑冲突文件=>删除特殊符号=>决定要使用的内容

![image-20210603080957855](https://gitee.com/lishuaicong/note-image/raw/master/img/image-20210603080957855.png)

这里我们做的决定是：

小孩子才做选择，我全都要！

> 添加到暂存区

![image-20210603081151377](https://gitee.com/lishuaicong/note-image/raw/master/img/image-20210603081151377.png)

> 执行提交（注意：此时使用git commit命令时==不能带文件名==）

![image-20210603081303705](https://gitee.com/lishuaicong/note-image/raw/master/img/image-20210603081303705.png)

现在发现最下面一行的命令右边的(master)后没有了MERGING，代表没有了冲突。

> 创建分支和切换分支图解

![image-20210603081622149](https://gitee.com/lishuaicong/note-image/raw/master/img/image-20210603081622149.png)

master、hot-fix 其实都是指向具体版本记录的指针。当前所在的分支，其实是由 HEAD

决定的。所以创建分支的本质就是多创建一个指针。

HEAD 如果指向 master，那么我们现在就在 master 分支上。

HEAD 如果执行 hotfix，那么我们现在就在 hotfix 分支上。

### Git团队协作机制

> 团队内协作

![image-20210603081947582](https://gitee.com/lishuaicong/note-image/raw/master/img/image-20210603081947582.png)

> 跨团队协作

![image-20210603082152270](https://gitee.com/lishuaicong/note-image/raw/master/img/image-20210603082152270.png)

# GitHub操作

## 创建远程仓库

![image-20210603082445837](https://gitee.com/lishuaicong/note-image/raw/master/img/image-20210603082445837.png)

先点击New repository

![image-20210603082656805](https://gitee.com/lishuaicong/note-image/raw/master/img/image-20210603082656805.png)

之后点击Create repository即可，其他的按需设置。

## 远程仓库操作

| 命令名称                                            | 作用                                                    |
|:-----------------------------------------------:|:-----------------------------------------------------:|
| git remote add 别名 远程地址                          | 起别名                                                   |
| git remote -v                                   | 查看当前所有远程地址别名                                          |
| git remote rm 别名                                | 删除远程地址别名                                              |
| <font color="red">git push 别名 分支</font>         | <font color="red">推送本地分支上的内容到远程仓库</font>              |
| <font color="red">git clone 远程地址</font>         | <font color="red">将远程仓库的内容克隆到本地</font>                |
| <font color="red">git pull 远程库地址别名 远程分支名</font> | <font color="red">将远程仓库对于分支最新内容拉下来后与当前本地分支直接合并</font> |

## 创建远程仓库别名

> 基本语法

```
git remote -v 查看当前所有远程地址别名
git remote add 别名 远程地址
```

> 案例实操

![image-20210603084129832](https://gitee.com/lishuaicong/note-image/raw/master/img/image-20210603084129832.png)

如图，我们添加了一个叫ori的别名，上面的http地址可以在下图所示地方获得：

![image-20210603084237546](https://gitee.com/lishuaicong/note-image/raw/master/img/image-20210603084237546.png)

## 推送本地分支到远程仓库

> 基本语法

```
git push 别名 分支
```

将==[分支]==推送到==[别名]==中

> 案例实操

一开始推送master时，git报错了，查了查百度好像是什么代理问题，我看了看教程，他们的.gitconfig文件很干净只有user相关的属性，而我的还有

```
[filter "lfs"]
    clean = git-lfs clean -- %f
    smudge = git-lfs smudge -- %f
    process = git-lfs filter-process
    required = true
```

这个东西不应该在一开始出现的，一开始配置好的话.gitconfig里应该很干净，里面只有之前配置好的name和email，这里上面多出来的东西应该是我以前下载后不知道怎么配置的东西，删了之后就能成功push到github上了。

![image-20210603102117463](https://gitee.com/lishuaicong/note-image/raw/master/img/image-20210603102117463.png)

于是我把这些东西删了，成功出现了下图：

![image-20210603090126893](https://gitee.com/lishuaicong/note-image/raw/master/img/image-20210603090126893.png)

之后我点击了在浏览器登录

![image-20210603090150878](https://gitee.com/lishuaicong/note-image/raw/master/img/image-20210603090150878.png)

输入密码后push成功

![image-20210603090256375](https://gitee.com/lishuaicong/note-image/raw/master/img/image-20210603090256375.png)

可以在github上看到成功提交了hello.txt

![image-20210603101956112](https://gitee.com/lishuaicong/note-image/raw/master/img/image-20210603101956112.png)

## 拉取远程库到本地库

> 基本语法

```
git pull 远程库地址别名 远程分支名
```

> 案例实操

倘若远程库中的文件发生了改变：

![image-20210603103808315](https://gitee.com/lishuaicong/note-image/raw/master/img/image-20210603103808315.png)

之后通过命令将远程库拉取到本地：

![image-20210603104049707](https://gitee.com/lishuaicong/note-image/raw/master/img/image-20210603104049707.png)

可以看到最后两行的内容代表：

```
hello.txt被修改，修改了一行

一个文件被修改，一行新增，一行删除
```

再使用git status

![image-20210603104240290](https://gitee.com/lishuaicong/note-image/raw/master/img/image-20210603104240290.png)

可以看到，pull拉下来的远程库会被自动提交到本地库，因此无需再commit。

打开本地库的文件查看：

![image-20210603104319004](https://gitee.com/lishuaicong/note-image/raw/master/img/image-20210603104319004.png)

是远程库被修改过的内容了，说明本地库和远程库同步了。

## 克隆远程库到本地

> 基本语法

```
git clone 远程地址
```

> 案例实操

先在本地创建一个新目录，模拟需要克隆的环境：

![image-20210603104625368](https://gitee.com/lishuaicong/note-image/raw/master/img/image-20210603104625368.png)

之后去要克隆的远程库拿到远程地址：

![image-20210603104742035](https://gitee.com/lishuaicong/note-image/raw/master/img/image-20210603104742035.png)

执行命令：

![image-20210603105206762](https://gitee.com/lishuaicong/note-image/raw/master/img/image-20210603105206762.png)

打开本地后发现已经克隆下来了

![image-20210603105230815](https://gitee.com/lishuaicong/note-image/raw/master/img/image-20210603105230815.png)

点开后发现.git文件也有，这就说明clone执行后执行了以下操作

```
拉取代码=>初始化本地仓库=>创建别名
```

![image-20210603105451777](https://gitee.com/lishuaicong/note-image/raw/master/img/image-20210603105451777.png)

可以看到创建的别名默认是origin！

## 团队内协作

> 邀请加入团队

首先要选择邀请合作者

![image-20210603105717793](https://gitee.com/lishuaicong/note-image/raw/master/img/image-20210603105717793.png)

进入到库的settings中的Manage access下，点击Invite a collaborator，填入想要合作的人：

![image-20210603105848343](https://gitee.com/lishuaicong/note-image/raw/master/img/image-20210603105848343.png)

输入要邀请的人的用户名或邮箱：

![image-20210603121801552](https://gitee.com/lishuaicong/note-image/raw/master/img/image-20210603121801552.png)

复制地址并通过钉钉微信等方式发送给该用户，内容如下：

https://github.com/Lorssi/git--test/invitations

![image-20210603121920655](https://gitee.com/lishuaicong/note-image/raw/master/img/image-20210603121920655.png)

点击Pending Invite后面的复制符复制地址。

等到被邀请人接受邀请后，就可以看到该远程仓库并提交修改。而仓库的主人也能看到某个内容是谁提交的。

## 跨团队协作

将远程仓库的地址发送给邀请跨团队协作的人：

![image-20210603122444749](https://gitee.com/lishuaicong/note-image/raw/master/img/image-20210603122444749.png)

在被邀请人的地址栏复制收到的链接，然后点击右上角的Fork将项目Fork到自己的本地仓库。

![image-20210603122802836](https://gitee.com/lishuaicong/note-image/raw/master/img/image-20210603122802836.png)

Forking...

![image-20210603122848400](https://gitee.com/lishuaicong/note-image/raw/master/img/image-20210603122848400.png)

Fork成功后可以看到当前仓库信息：

![image-20210603122944833](https://gitee.com/lishuaicong/note-image/raw/master/img/image-20210603122944833.png)

可以看到当前仓库所有人由Yunai变成了Lorssi，而下面的的forked from则说明了Fork的来源。

之后被邀请的人就可以在线编辑Fork过来的文件，且编辑完成后可以点击Commit changes来提交修改。

接着点击仓库上方的pull request按钮，创建一个新的请求：

![image-20210603123343641](https://gitee.com/lishuaicong/note-image/raw/master/img/image-20210603123343641.png)

点击右侧绿色的New pull request按钮将request发送过去

![image-20210603123749587](https://gitee.com/lishuaicong/note-image/raw/master/img/image-20210603123749587.png)

再点击Create pull request按钮，可以创建一个聊天室

![image-20210603123822979](https://gitee.com/lishuaicong/note-image/raw/master/img/image-20210603123822979.png)

发送一个pull request请求。

之后原仓库所有人就能收到一个Pull request请求

![image-20210603124142618](https://gitee.com/lishuaicong/note-image/raw/master/img/image-20210603124142618.png)

并可以进入聊天室讨论代码相关内容

![image-20210603124654655](https://gitee.com/lishuaicong/note-image/raw/master/img/image-20210603124654655.png)

点击进去就是一个聊天室：

![image-20210603124721209](https://gitee.com/lishuaicong/note-image/raw/master/img/image-20210603124721209.png)

下面是聊天室的一些功能：

![image-20210603124819281](https://gitee.com/lishuaicong/note-image/raw/master/img/image-20210603124819281.png)

> 

![image-20210603124830686](https://gitee.com/lishuaicong/note-image/raw/master/img/image-20210603124830686.png)

> 

![image-20210603124846718](https://gitee.com/lishuaicong/note-image/raw/master/img/image-20210603124846718.png)

> 

![image-20210603124858060](https://gitee.com/lishuaicong/note-image/raw/master/img/image-20210603124858060.png)

## SSH免密登录

我们可以看到远程仓库中还有一个SSH的地址，因此我们也可以使用SSH进行访问。

![image-20210603125514030](https://gitee.com/lishuaicong/note-image/raw/master/img/image-20210603125514030.png)

**具体操作如下：**

先到C盘=>用户=>lishuaicong 将.ssh文件夹删除，因为要从头演示所以先把以前的删除。视频上是这么做的，但是我摸不准的是这东西敢不敢删。。保佑我吧。

之后在这个目录下打开git bash。

![image-20210603152412828](https://gitee.com/lishuaicong/note-image/raw/master/img/image-20210603152412828.png)

不过也可以直接执行cd命令进入这个目录：

![image-20210603152510441](https://gitee.com/lishuaicong/note-image/raw/master/img/image-20210603152510441.png)

之后输入如下命令：

```
ssh-keygen -t rsa -C 1477331829@qq.com
```

ssh-keygen:  生成私钥和公钥

-t：指定生成秘钥的加密算法

rsa： 著名非对称加密协议

-C： 描述

然后一直回车就好

![image-20210603153842334](https://gitee.com/lishuaicong/note-image/raw/master/img/image-20210603153842334.png)

之后会发现文件里就多了一个.ssh文件

![image-20210603153904310](https://gitee.com/lishuaicong/note-image/raw/master/img/image-20210603153904310.png)

进入到.ssh里面会发现里面多了一个公钥和一个私钥：

![image-20210603153951177](https://gitee.com/lishuaicong/note-image/raw/master/img/image-20210603153951177.png)

其中pub是公钥，另一个是私钥。~~之后打开公钥文件~~，不能用txt格式什么的打开，之后添加公钥的时候会出现格式错误，要用cat 文件名命令来打开。

将里面的内容复制，然后进入github=>settings=>SSH and GPG keys

![image-20210603154533151](https://gitee.com/lishuaicong/note-image/raw/master/img/image-20210603154533151.png)

点击New SSH key

![image-20210603155641863](https://gitee.com/lishuaicong/note-image/raw/master/img/image-20210603155641863.png)

然后输入title和key再点击Add SSH key即可。

![image-20210603155707460](https://gitee.com/lishuaicong/note-image/raw/master/img/image-20210603155707460.png)

**测试：**

我们先去git--test库里面在线修改一下hello.txt

![image-20210603160253006](https://gitee.com/lishuaicong/note-image/raw/master/img/image-20210603160253006.png)

之后拉取远程库，不过这时候就要注意了，==这时候使用的就不是http地址了，而是ssh。==

![image-20210603160905818](https://gitee.com/lishuaicong/note-image/raw/master/img/image-20210603160905818.png)

第一次的话他会提醒你问你确定要不要继续链接，输入yes即可。

打开本地库的hello.txt，确定是否拉取成功：

![image-20210603161005232](https://gitee.com/lishuaicong/note-image/raw/master/img/image-20210603161005232.png)

如图，拉取成功。

我们再测试一下push功能：

![image-20210603161043214](https://gitee.com/lishuaicong/note-image/raw/master/img/image-20210603161043214.png)

push成功

![image-20210603161221423](https://gitee.com/lishuaicong/note-image/raw/master/img/image-20210603161221423.png)

去网站确认一下：

![image-20210603161725806](https://gitee.com/lishuaicong/note-image/raw/master/img/image-20210603161725806.png)

emm，上传成功！不过其实也可以通过下图命令来测试，处于务实，还是手动测试一下功能比较安心。

![image-20210603161543650](https://gitee.com/lishuaicong/note-image/raw/master/img/image-20210603161543650.png)

# IDEA

## 集成Git

### 配置Git忽略文件

idea中使用的时候我们有些文件是不需要push上去的，比如idea的.idea文件等，这些文件与项目的实际功能无关，不参与服务器上部署运行。把它们忽略掉能够屏蔽IDE工具之间的差异。

那么怎么忽略呢？

> 创建xx.ignore(建议为git.ignore)

在c盘用户名的目录下，也就是和.gitconfig同级的目录下，创建一个git.ignore文件

![image-20210603163550361](https://gitee.com/lishuaicong/note-image/raw/master/img/image-20210603163550361.png)

之后修改.gitconfig文件

![image-20210603163742010](https://gitee.com/lishuaicong/note-image/raw/master/img/image-20210603163742010.png)

注意这里要使用==/==而不是==\\==

这就像是在全局配置的忽略文件。

### IDEA定位Git程序

![image-20210603163958095](https://gitee.com/lishuaicong/note-image/raw/master/img/image-20210603163958095.png)

### IDEA初始化本地库

![image-20210603164328393](https://gitee.com/lishuaicong/note-image/raw/master/img/image-20210603164328393.png)

按如上动作完成后，选择目录，之后到对应目录查看

![image-20210603164438605](https://gitee.com/lishuaicong/note-image/raw/master/img/image-20210603164438605.png)

多了一个.git文件，说明本地库初始化成功。

### 添加到暂存区

![image-20210603164557618](https://gitee.com/lishuaicong/note-image/raw/master/img/image-20210603164557618.png)

我们可以看到目前pom文件是红色的，说明还没有被添加到暂存区中，那么如何添加到暂存区呢

> 第一种方法

右键pom，按如下图选择

![image-20210603164721391](https://gitee.com/lishuaicong/note-image/raw/master/img/image-20210603164721391.png)

点击后，发现变绿了

![image-20210603164834605](https://gitee.com/lishuaicong/note-image/raw/master/img/image-20210603164834605.png)

说明pom被提交到了暂存区，但是还没有被提交到本地库。

> 第二种方法

![image-20210603165259050](https://gitee.com/lishuaicong/note-image/raw/master/img/image-20210603165259050.png)

直接提交整个项目文件，不过如果配置了ignore文件，会询问你是否要强制添加被忽略的文件，到时候选择cancel就行了。

### 提交到本地库

同样的，右键文件或者项目目录，按如下图选择：

![image-20210603165622004](https://gitee.com/lishuaicong/note-image/raw/master/img/image-20210603165622004.png)

点击后会出现这个窗口：

![image-20210603165635853](https://gitee.com/lishuaicong/note-image/raw/master/img/image-20210603165635853.png)

功能如下：

![image-20210603165728756](https://gitee.com/lishuaicong/note-image/raw/master/img/image-20210603165728756.png)

这里message实际上就是-m。

提交过后，可以看到文件又变成了原来的颜色，说明提交到了本地库了。

![image-20210603165918871](https://gitee.com/lishuaicong/note-image/raw/master/img/image-20210603165918871.png)

### 切换版本

我们先再多提交几次，修改文件后发现文件名变成了蓝色：

![image-20210603170216631](https://gitee.com/lishuaicong/note-image/raw/master/img/image-20210603170216631.png)

代表这个文件被git追踪过，但是被修改了。

这里再次提交到暂存区，然后commit。不过蓝色文件也可以不提交到暂存区，因为这个文件已经被追踪过了，可以直接commit。

在 IDEA 的左下角，点击 Version Control，然后点击 Log 查看版本

![image-20210603170529636](https://gitee.com/lishuaicong/note-image/raw/master/img/image-20210603170529636.png)

可以看到这里我们提交了两个版本，还可以看到当前版本处于哪个位置。

可以看到右侧有两个指针，一个黄的，一个绿的，其含义如下：

![image-20210603170717259](https://gitee.com/lishuaicong/note-image/raw/master/img/image-20210603170717259.png)

可以看到图片右下角，有说明黄色的是HEAD指针，绿色的是master分支的指针，还说明了什么时间，由谁提交的。

可以看到，HEAD指针指向了master，而master又指向了second commit。

> 切换版本就是右键想要切换的版本，选择checkout

![image-20210603170943364](https://gitee.com/lishuaicong/note-image/raw/master/img/image-20210603170943364.png)

点击后可以发现内容已经回溯到了first commit

![image-20210603171029168](https://gitee.com/lishuaicong/note-image/raw/master/img/image-20210603171029168.png)

### 创建分支

右键项目，选择如下：

![image-20210603171343994](https://gitee.com/lishuaicong/note-image/raw/master/img/image-20210603171343994.png)

点击你这New Branch

![image-20210603171429098](https://gitee.com/lishuaicong/note-image/raw/master/img/image-20210603171429098.png)

也可以点击idea右下角

![image-20210603171508231](https://gitee.com/lishuaicong/note-image/raw/master/img/image-20210603171508231.png)

选择New Branch

![image-20210603171604536](https://gitee.com/lishuaicong/note-image/raw/master/img/image-20210603171604536.png)

输入分支名称选择Create即可，而Checkout branch勾选就是创建分支之后会自动切换到创建的分支。如下，我们创建后就自动切换了过来。

![image-20210603171656081](https://gitee.com/lishuaicong/note-image/raw/master/img/image-20210603171656081.png)

那怎么切换回别的分支呢，一样的，点击右下角，选择master分支即可：

![image-20210603171834251](https://gitee.com/lishuaicong/note-image/raw/master/img/image-20210603171834251.png)

可以看到我们现在切换回了master分支

![image-20210603171909682](https://gitee.com/lishuaicong/note-image/raw/master/img/image-20210603171909682.png)

### 合并分支

#### 正常合并

修改hot-fix分支

![image-20210603172230262](https://gitee.com/lishuaicong/note-image/raw/master/img/image-20210603172230262.png)

之后提交到本地库：

![image-20210603172427667](https://gitee.com/lishuaicong/note-image/raw/master/img/image-20210603172427667.png)

现在是hot-fix有四行代码，而master有三行代码，那么如何合并分支呢？

我们现在切换回master分支，查看log

![image-20210603172629340](https://gitee.com/lishuaicong/note-image/raw/master/img/image-20210603172629340.png)

通过HEAD指针可以知道，我们目前是在master分支上，合并分支是如下操作：

![image-20210603172730908](https://gitee.com/lishuaicong/note-image/raw/master/img/image-20210603172730908.png)

这里可以看到，我们是在master分支上点击hot-fix，然后选择Merge into Current，翻译一下将hot-fix就是合并到当前(master)。

选择之后，可以看到我们现在是在master分支上：

![image-20210603172904988](https://gitee.com/lishuaicong/note-image/raw/master/img/image-20210603172904988.png)

但是我们的内容已经从三行变成了四行，也就是将hot-fix的内容合并过来了：

![image-20210603172931849](https://gitee.com/lishuaicong/note-image/raw/master/img/image-20210603172931849.png)

#### 冲突合并

我们先切换回hot-fix分支，现在经过合并，hot-fix分支和master分支的内容是一样的。

之后我们再修改hot-fix的内容:

![image-20210603173129411](https://gitee.com/lishuaicong/note-image/raw/master/img/image-20210603173129411.png)

然后提交到本地库

![image-20210603173205158](https://gitee.com/lishuaicong/note-image/raw/master/img/image-20210603173205158.png)

提交完后我们再回到master分支上

![image-20210603173236426](https://gitee.com/lishuaicong/note-image/raw/master/img/image-20210603173236426.png)

可以看到，现在的master分支上还是之前合并完以后的四行代码，这时候如果直接合并就是正常合并，但是我们再在下面一行增加一行代码，满足冲突条件：

合并分支时，两个分支在==同一个文件的同一个位置有两套完全不同的修改==。Git 无法替我们决定使用哪一个。必须==人为决定==新代码内容。

![image-20210603173423754](https://gitee.com/lishuaicong/note-image/raw/master/img/image-20210603173423754.png)

现在同一个地方master和hot-fix都做出了修改，发生了冲突，然后提交。

![image-20210603173601398](https://gitee.com/lishuaicong/note-image/raw/master/img/image-20210603173601398.png)

查看log

![image-20210603173706987](https://gitee.com/lishuaicong/note-image/raw/master/img/image-20210603173706987.png)

发现有一个分叉，分叉的两端分别是我们刚才提交的master和hot-fix。

不过现在还并没有报错，因为我们还没有开始合并，上面的分叉只是说明hot-fix和master都对hot-fix first commit做出了修改。

然后我们在master上合并hot-fix：

![image-20210603174205230](https://gitee.com/lishuaicong/note-image/raw/master/img/image-20210603174205230.png)

弹出了这么一个窗口，可以看到，窗口的title就是Conflis。还可以看到代码部分多出了几行代码：

![image-20210603174350897](https://gitee.com/lishuaicong/note-image/raw/master/img/image-20210603174350897.png)

是不是很熟悉？就是我们之前学的冲突的时候会出现的东西。现在我们就开始处理冲突啦！

点击窗口的Merge按钮：

![image-20210603174509990](https://gitee.com/lishuaicong/note-image/raw/master/img/image-20210603174509990.png)

蹦出来了一个大窗口，这个大窗口分为三块，左侧的是master分支，右侧的是hot-fix分支，而中间的则是没有冲突的代码，可以看到中间的窗口title是result。我们还可以看到中间的两个符号![image-20210603174642157](https://gitee.com/lishuaicong/note-image/raw/master/img/image-20210603174642157.png)

这个X就代表不要这个冲突的代码，而>>就是需要这行冲突的代码，给它合并的result里面。

我们现在需要master的代码，点击>>，可以看到冲突代码被合并到了result里面：

![image-20210603174827814](https://gitee.com/lishuaicong/note-image/raw/master/img/image-20210603174827814.png)

hot-fix侧的也是同样的处理：

![image-20210603174914901](https://gitee.com/lishuaicong/note-image/raw/master/img/image-20210603174914901.png)

可以看到中间弹出了一个弹框，==All changes have been processed. Save changes and finish merging==，翻译过来就是：

==所有更改都已处理。保存更改并完成合并==

点击apply：

可以看到冲突解决了，需要的代码都合并到了master里：

![image-20210603175131845](https://gitee.com/lishuaicong/note-image/raw/master/img/image-20210603175131845.png)

而且log里也显示了合并的过程：

![image-20210603175152205](https://gitee.com/lishuaicong/note-image/raw/master/img/image-20210603175152205.png)

## 集成GitHub

### 设置GitHub账户

![image-20210603175648794](https://gitee.com/lishuaicong/note-image/raw/master/img/image-20210603175648794.png)

然后点击右侧+

![image-20210603175704122](https://gitee.com/lishuaicong/note-image/raw/master/img/image-20210603175704122.png)

输入账户密码：

![image-20210603175849843](https://gitee.com/lishuaicong/note-image/raw/master/img/image-20210603175849843.png)

使用idea通过账户密码的方式登录github，因为网络问题，非常难以登录，我点击登录按钮登录几十次没登录上，艸！

这时候我们就要选择右上角的==User Token==来登录。

![image-20210603180048679](https://gitee.com/lishuaicong/note-image/raw/master/img/image-20210603180048679.png)

但这时候我们没有口令怎么办？

打开GitHub网站=>Settings=>Developer settings=>Psersonal access tokens=>Generate new token,进入如下页面：

![image-20210603180432839](https://gitee.com/lishuaicong/note-image/raw/master/img/image-20210603180432839.png)

Note是名字，而下面的Select scopes则是权限，要全部勾选。然后点击Generate token。

![image-20210603180606567](https://gitee.com/lishuaicong/note-image/raw/master/img/image-20210603180606567.png)

可以看到出现了一个token

![image-20210603181058904](https://gitee.com/lishuaicong/note-image/raw/master/img/image-20210603181058904.png)

需要注意的是，这个token只会出现这一次，之后就不会再出现了，因此一定要记得复制，不然就只能再重新生成一个口令了。

![image-20210603181157927](https://gitee.com/lishuaicong/note-image/raw/master/img/image-20210603181157927.png)

然后登录

![image-20210603181214543](https://gitee.com/lishuaicong/note-image/raw/master/img/image-20210603181214543.png)

可以看到这次就很轻松的就登录进来了。

### 分享项目到GitHub

![image-20210603181944563](https://gitee.com/lishuaicong/note-image/raw/master/img/image-20210603181944563.png)

这个就可以直接将项目分享到github上。点击后出现如下弹框：

![image-20210603182038063](https://gitee.com/lishuaicong/note-image/raw/master/img/image-20210603182038063.png)

**Repository name**输入的是远程库的名字，我们之前push文件还需要先在网站手动创建仓库，现在使用idea的话，idea能自动帮我们建库。一般来说，远程库的名字和项目名是一样的。

**Remote**就是别名，idea会给链接自动创建一个别名，默认为origin。

**Description**则是描述信息，不填也可以。

然后点击Share就能分享到GitHub上了。idea会先帮你创建远程库，再把代码push上去。其实就是先创建远程库，再push代码进远程库。

![image-20210603183220585](https://gitee.com/lishuaicong/note-image/raw/master/img/image-20210603183220585.png)

等到右下角出现这个弹窗就说明远程库创建成功且push成功，打开网站看看：

![image-20210603183658727](https://gitee.com/lishuaicong/note-image/raw/master/img/image-20210603183658727.png)

不过因为网络原因，可能会出现创建了库，但是没能把代码push上去。

### 推送代码到远程库

修改代码

![image-20210603183847777](https://gitee.com/lishuaicong/note-image/raw/master/img/image-20210603183847777.png)

增加了一行push test。然后就是提交到本地库。推送的话有好几种方法：

可以像下面这样：

![image-20210603184129849](https://gitee.com/lishuaicong/note-image/raw/master/img/image-20210603184129849.png)

还可以这样

![image-20210603192158779](https://gitee.com/lishuaicong/note-image/raw/master/img/image-20210603192158779.png)

点击push：

![image-20210603184304867](https://gitee.com/lishuaicong/note-image/raw/master/img/image-20210603184304867.png)

然后就能push了。不过这样默认是用https来push的，极受网络影响，很容易失败。上面share到github我就失败了，只创建了个库，push操作失败了，现在网站上是个空库，艸！

因此我们选择以ssh的方式来push，首先复制远程库的ssh

![image-20210603192117985](https://gitee.com/lishuaicong/note-image/raw/master/img/image-20210603192117985.png)

然后点击别名，选择Define Remote

![image-20210603192312131](https://gitee.com/lishuaicong/note-image/raw/master/img/image-20210603192312131.png)

自定义一个别名，将刚刚的ssh写进去

![image-20210603192626663](https://gitee.com/lishuaicong/note-image/raw/master/img/image-20210603192626663.png)

点击ok即可。

成功之后就可以选用刚刚定义的ssh

![image-20210603192549357](https://gitee.com/lishuaicong/note-image/raw/master/img/image-20210603192549357.png)

然后点击push就可以推送了

![image-20210603192704016](https://gitee.com/lishuaicong/note-image/raw/master/img/image-20210603192704016.png)

显示push成功

![image-20210603192733629](https://gitee.com/lishuaicong/note-image/raw/master/img/image-20210603192733629.png)

我们去远程库看看：

![image-20210603192749573](https://gitee.com/lishuaicong/note-image/raw/master/img/image-20210603192749573.png)

确实push上来了。

因此我们一般选用ssh链接最好，https链接对网络要求较高，容易推送失败。

注意：push 是将本地库代码推送到远程库，如果本地库代码跟远程库代码版本不一致，push 的操作是会被拒绝的。也就是说，要想 push 成功，一定要保证本地库的版本要比远程库的版本高！

<font color="red">因此一个成熟的程序员在动手改本地代码之前，一定会先检查下远程库跟本地代码的区别！如果本地的代码版本已经落后，切记要先 pull 拉取一下远程库的代码，将本地代码更新到最新以后，然后再修改，提交，推送！</font>

### 拉取远程库代码

![image-20210603193020635](Git.assets/image-20210603193020635.png)

假设我们远程库中的代码发生了改变，多了一行pull test。现在我们需要将远程库的代码pull到本地库。

现在我们本地的代码还是：

![image-20210603193717215](https://gitee.com/lishuaicong/note-image/raw/master/img/image-20210603193717215.png)

然后pull远程库

<img src="https://gitee.com/lishuaicong/note-image/raw/master/img/image-20210603193853963.png" alt="image-20210603193853963" style="zoom:67%;" />

出现如下界面：

![image-20210603193926996](https://gitee.com/lishuaicong/note-image/raw/master/img/image-20210603193926996.png)

可以看到可以通过两种链接来pull，一个是https，一个是ssh，自然我们要用ssh来拉取：

![image-20210603194014056](https://gitee.com/lishuaicong/note-image/raw/master/img/image-20210603194014056.png)

然后点击pull

![image-20210603194150866](https://gitee.com/lishuaicong/note-image/raw/master/img/image-20210603194150866.png)

如上，拉取成功，我们看看代码：

![image-20210603194209139](https://gitee.com/lishuaicong/note-image/raw/master/img/image-20210603194209139.png)

同样发生了改变，至此，拉取成功！

==注意：==

**pull 是拉取远端仓库代码到本地，如果远程库代码和本地库代码不一致，会自动合并，如果自动合并失败，还会涉及到手动解决冲突的问题。**

### 克隆远程库代码

我们先删除git-test这个项目，来模拟需要克隆远程库的情况。

之后点击IDEA的Get from Version Control

<img src="https://gitee.com/lishuaicong/note-image/raw/master/img/image-20210603194523805.png" alt="image-20210603194523805" style="zoom:67%;" />

进去后，我们先复制一下远程库的ssh，然后填入窗口中的URL中

<img src="https://gitee.com/lishuaicong/note-image/raw/master/img/image-20210603194734412.png" alt="image-20210603194734412" style="zoom:67%;" />

之后点击Clone即可，不过其实好像如果你登录过账户的话，直接点击下面的GitHub，Gitee就能直接clone，而不需要URL。

<img src="https://gitee.com/lishuaicong/note-image/raw/master/img/image-20210603194930950.png" alt="image-20210603194930950" style="zoom:67%;" />

点击clone后，就出现了下面的弹窗：

<img src="https://gitee.com/lishuaicong/note-image/raw/master/img/image-20210603195009945.png" alt="image-20210603195009945" style="zoom:67%;" />

点击yes即可，这样代码就Clone下来了：

![image-20210603205840788](https://gitee.com/lishuaicong/note-image/raw/master/img/image-20210603205840788.png)

# Gitee

> 简介

众所周知，GitHub 服务器在国外，使用 GitHub 作为项目托管网站，如果网速不好的话，

严重影响使用体验，甚至会出现登录不上的情况。针对这个情况，大家也可以使用国内的项

目托管网站码云。

码云是开源中国推出的基于 Git 的代码托管服务中心，网址是 https://gitee.com/ ，使用

方式跟 GitHub 一样，而且它还是一个中文网站，如果你英文不是很好它是最好的选择。

注册跟登录这里就不多说了，Gitee中绝大多数操作也跟GitHub差不多。

## 创建远程仓库

点击首页右上角的加号，选择下面的新建仓库

![image-20210603205512079](https://gitee.com/lishuaicong/note-image/raw/master/img/image-20210603205512079.png)

填写仓库名称，路径和选择是否开源（共开库或私有库）

![image-20210603195616728](https://gitee.com/lishuaicong/note-image/raw/master/img/image-20210603195616728.png)

最后根据需求选择分支模型，然后点击创建按钮。

![image-20210603195709925](https://gitee.com/lishuaicong/note-image/raw/master/img/image-20210603195709925.png)

远程库创建好以后，就可以看到 HTTPS 和 SSH 的链接。

![image-20210603195739720](https://gitee.com/lishuaicong/note-image/raw/master/img/image-20210603195739720.png)

## IDEA集成Gitee

Idea 默认不带码云插件，我们第一步要安装 Gitee 插件。如图所示，在 Idea 插件商店搜索 Gitee，然后点击右侧的 Install 按钮。

<img src="https://gitee.com/lishuaicong/note-image/raw/master/img/image-20210603195943897.png" alt="image-20210603195943897" style="zoom:67%;" />

Idea 链接码云和链接 GitHub 几乎一样，安装成功后，重启 Idea。

Idea 重启以后在 Version Control 设置里面看到 Gitee，说明码云插件安装成功。

然后在码云插件里面添加码云帐号，我们就可以用 Idea 连接码云了。

<img src="https://gitee.com/lishuaicong/note-image/raw/master/img/image-20210603200047088.png" alt="image-20210603200047088" style="zoom:67%;" />

## IDEA 链接Gitee

Idea 连接码云和连接 GitHub 几乎一样，首先在 Idea 里面创建一个工程，初始化 git 工程，然后将代码添加到暂存区，提交到本地库，这些步骤上面已经讲过，此处不再赘述。

Gitee操作基本和GitHub相同，只不过因为其服务器在国内，Gitee没必要用SSH而已。

## Gitee复制GitHbu项目

码云提供了直接复制 GitHub 项目的功能，方便我们做项目的迁移和下载。

具体操作如下：

<img src="https://gitee.com/lishuaicong/note-image/raw/master/img/image-20210603200449901.png" alt="image-20210603200449901" style="zoom:67%;" />

将 GitHub 的远程库 HTTPS 链接复制过来，点击创建按钮即可，当然也可以直接关联GitHub账户，然后点击导入GitHub仓库来复制。

<img src="https://gitee.com/lishuaicong/note-image/raw/master/img/image-20210603200523210.png" alt="image-20210603200523210" style="zoom:67%;" />

如果 GitHub 项目更新了以后，在码云项目端可以手动重新同步，进行更新！

<img src="https://gitee.com/lishuaicong/note-image/raw/master/img/image-20210603200731313.png" alt="image-20210603200731313" style="zoom:67%;" />

点击git--test右边的刷新按钮即可手动重新同步。
