[toc]

---

## git的概述

#### 1，git的特点

1.1，直接记录快照，而非差异比较。

1.2，近乎所有操作都是本地执行。

1.3，时刻保持数据完整性。

1.4，多数操作仅添加数据。

1.5，git管理的文件有三种状态：

- 已修改（modified）

- 已暂存（staged）

- 已提交（committed）

- 由此说明：git管理项目时，文件流转的三个工作区域为：git的`工作目录`，`暂存区域`，`本地仓库`。

#### 2，git是分布式版本控制系统

2.1，所谓版本控制系统，就是一种记录一个或若干文件内容变化，以便将来查阅特定版本修订情况的系统。

2.2，git无中央服务器，每个人的电脑就是一个完整的版本库，即工作的时候不需要联网，因为版本都在自己的电脑上。

#### 3，git工作流程

![image](https://ss1.bdstatic.com/70cFvXSh_Q1YnxGkpoWK1HF6hhy/it/u=3456711285,762623164&fm=26&gp=0.jpg)

#### 4，使用版本控制系统的好处

4.1，版本控制系统，可以将某个文件回溯到之前的状态，甚至将整个项目都回退到过去某个时间点的状态。

## 集中式版本控制系统

#### 1，集中式版本控制系统概述

- 集中式的版本控制系统诸如：`CVS、Subversion、Perforce`等，都有一个单一的集中管理的服务器，用来保存所有文件的修订版本，而协同工作的人们都通过客户端连接这台服务器，取出最新的文件或者提交更新。

#### 2，集中式版本控制系统的特点及优缺点

2.1，集中式版本控制系统`具有中央服务器`。

2.2，集中式管理方式在一定程度上可以看到其它开发人员在干什么，而管理员也能轻松掌握每个人的开发权限。

2.3，集中式管理的`优点`在于：

- 代码存放在单一的服务器上，便于项目的管理。

2.4，集中式管理的`缺点`在于：

- 中央服务器单点故障。
    
- 如果中央服务器宕机了，那么谁都无法提交更新，也就无法协同工作了。
    
- 如果中央服务器磁盘发生故障，碰巧有没有备份，就会有丢失数据的风险。
    
- 总之就是集中式版本控制系统容错性较差。

## 分布式版本控制系统

#### 1，分布式版本控制系统概述

1.1，客户端并不只提取最新版本的文件快照，而是把`代码仓库完整地镜像下来`。也就是说，任何一处协同工作的服务器发生故障，事后都可以用任何一个镜像出来的本地仓库恢复。

1.2，分布式版本控制系统都可以指定和若干不同的远端代码仓库进行交互。可以在同一个项目中分别和不同工作小组的人相互协作。

1.3，分布式的版本控制系统在管理项目时，存放的不是项目版本与版本之间的差异，它存的是`索引`（所需磁盘空间很少，所以每个客户端都可以放下整个项目的历史记录）。

## git的安装及配置

#### 1，快速下载网址

1.1，git快速下载地址：[link](https://npm.taobao.org/mirrors/git-for-windows/)。

#### 2，git初始配置

2.1，一般在新系统上都要配置自己的git工作环境。配置工作只需要一次，以升级时还会沿用现在的配置。但是如果先修改现有的配置，可随时使用相同的命令修改已有配置。

2.1，git提供了一个叫做`git config`的命令来配置或读取相应的工作环境变量。这些环境变量决定了git在各个环节的具体工作方式和行为。这些变量可以存放在以下三个不同的地方：

- `/etc/gitconfig`文件：系统中对所有用户都普遍使用的配置。若使用`git config`时用`--system`选项，读写的就是/etc/gitconfig这个文件。
    
- `-/.gitconfig`文件：用户目录下的配置文件只适用于该用户。若使用`git config`时用`--global`选项，读写的就是-/.gitconfig这个文件。一般使用--global选项。
    
-  `.git/config`文件：当前项目的git目录中的配置文件（也就是工作目录中的`.git/config`文件）这里的配置仅仅针对当前项目有效。
    
#### 3，如何检查是否安装成功

3.1，在windows电脑桌面单机鼠标右键，看是否有`Git Bush Here`及`Git GUI Here`两个选项，如果有则说明安装成功了。

#### 4，如何配置用户信息

4.1，可以用git config配置git。首先要做的事情就是设置你的`名字`和`邮件地址`：

- **git config --global user.name "your name"**
    
- **git config --global user.email your Email**

4.2，使用`git config --list`命令可检查已有的配置信息，检查用户名和邮箱等是否配置成功。

#### 5，删除用户配置信息

5.1，**git config --global --unset user.name**删除全局配置的用户名。

5.2，**git config --global --unset user.email**删除全局配置的邮箱。

## git底层命令

#### 1，基础Linux命令

1.1，clear：清屏。

1.2，echo "test content" ：往控制台输出信息。使用echo "test content" > xx文件夹：表示往xx文件中写入该test content内容。

1.3，`ll`：将当前目录下的子文件和子目录平铺在控制台。

1.4，`find 目录名`：将对应目录下的子孙文件及子孙目录平铺在控制台。

1.5，`find 目录名 -type f`：将对应目录下的文件平铺在控制台。

1.6，`rm 文件名`：删除文件。

1.7，`mv 源文件 文件新的名字`：从命名。

1.8，`cat 文件名`：查看对应文件的内容。

1.9，`vim 文件名`（在英文模式下）：
    
- 按`i`进入插入模式，进行文件的编辑。
    
- 编辑完成以后按`esc`键后按`:`键进行命令的执行。
    
    - 按冒号之后按`q!`强制退出（不保存）。
    
    - 按冒号之后按`wq`保存并退出编辑。
    
    - 按冒号之后按`set nu`设置行号。

## 初始化新仓库

#### 1，初始化新仓库命令

1.1，git init

#### 2，git init命令解析

2.1，要对现有的某个项目开始用git管理，只需要在此项目所在的目录，执行：git init即可。

#### 3，git init命令的作用

3.1，初始化后，在当前目录下会出现一个名为.git的目录，所有git需要的数据和资源都放在这个目录中。不过目前，仅仅是按照既有的结构框架初始化好了里面所有的文件和目录，还没有开始跟踪管理项目中的任一个文件。

- **注意**：.git文件在文件夹中是隐藏的，需要手动设置文件夹显示隐藏。

#### 4，.git文件中的内容

4.1，hooks文件夹：该目录包含客户端或服务端的钩子脚本。

4.2，info：该目录包含一个全局性排除文件。

4.3，logs：保存日志信息。

4.4，**objects**：该目录储存所有数据内容。

4.5，**refs**：该目录储存指向数据（分支）的提交对象的指针。

4.6，config：该文件包含项目特有的配置选项。

4.7，description：该文件用来显示对仓库的描述信息。

4.8，**HEAD**：该文件指示目前被检出的分支。

4.9，**index**：该文件用于保存暂存区信息。

## git对象

#### 1，git对象概述

1.1，git的核心部分是一个简单的键值对数据库。你可以向该数据库插入任意类型的内容，它会返回一个键值，通过该键值可以在任意时刻再次检索该内容。

1.2，git对象代表数据库中文件的一个个版本。

#### 2，向数据库写入内容，并返回对应键值

2.1，命令：`echo "test.txt v1" > test.txt（新建一个文件） |  git hash-object -w --stdin（将创建的文件生成git对象并保存进数据库中）`。

- `-w`选项指示 hash-object 命令储存数据对象：若不指定此选项。则该命令仅返回对应的键值。
    
- `--stdin`（standard input）选项则指示该命令从标准输入读取内容，若不指定选项，则须在命令尾部给出待存储文件的路径。
    
- **注意**：使用该命令存储的文件默认会保存在.git文件目录下的objects文件夹中。
    
2.2，命令：`git hash-object -w 文件路径`：该命令用于存文件进入数据库（版本库）。

2.3，命令：`git hash-object 文件路径`：不加`-w`就不会对内容进行存储，只返回对应文的件键值。

- 该命令返回对应文件的键值，如：d670460b4b4aece5915caf5c68d12f560a9fe3e4。该命令返回一个长度为40个字符串的校验和。这是一个SHA-1哈希值。

#### 3，如何查看git是如何存储数据的

3.1，命令：`find -git/objects -type f`该命令就是用来查看git是如何储存数据的。

- 该命令返回：./objects/d6/70460b4b4aece5915caf5c68d12f560a9fe3e4。这就是开始时git储存内容的方式：一个文件对应一条内容。校验和的前面两个字符用于命名子目录，余下的38个字符则用作文件名。

#### 4，根据键值拉取数据

4.1，命令：`git cat-file -p` d670460b4b4aece5915caf5c68d12f560a9fe3e4

- `-p`选项可指示该命令自动判断内容的类型，并为我们显示格式友好的内容。
    
- 该命令返回对应文件的内容。

#### 5，对一个文件进行简单的版本控制

5.1，`创建一个新文件并将其内容存入数据库`，使用命令：

- `echo "version 1" > test.txt`
    
- `git hash-object -w test.txt`
    
- 输入以上命令后返回：83baae618......

5.2，向文件里写入新内容，并再次将其存入数据库，使用命令：

- `echo "wersion 2" > test.txt`
    
- `git hash-object -w test.txt`
    
- 输入以上命令返回：1f7a7a472......
    
5.3，查看数据库内容，使用命令：

- find .git/objects -type f
    
- git cat-file -p 83baae618......
    
- git cat-file -p 1f7a7a472......
    
5.4，查看git保存的数据的类型，使用命令：

- `git cat-file -t`
    
- `git cat-file -t` 1f7a7a472......。该命令返回`bolb`
    
- **说明**：cat-file -t命令，可以让git告诉我们其内部存储的任何对象的类型，返回：`blob`类型。
    
5.5，**说明**：以上操作在git中，文件名并没有被保存，只是保存了文件的内容。而记住文件的每个版本所对应的SHA-1值，这并不现实。

5.6，**注意**：以上的操作都是在对本地数据库进行操作，不涉及暂存区。如果要解决以上问题，需要利用`树对象`。

## 树对象

#### 1，树对象概述

1.1，树对象（tree object），它能解决文件名保存的问题，也允许我们将多个文件组织到一起。git以一种类似于UNIX文件系统的方式储存内容。所有内容均以树对象和数据对象（git对象）的形式存储其中`树对象对应了UNIX中的目录项``数据对象（git对象）则大致上对应文件的内容`。`一个树对象包含了一条或多条记录`（每条记录含有一个指向git对象或者子树对象的`SHA-1指针`，以及相应的模式、类型、文件名信息）。`一个树对象也可包含另一个树对象`。

1.2，树对象代表数据库中项目的一个个版本（`每个树对象就是一次版本快照`）。只有将所有构成项目版本的git对象（创建的一个个文件）从数据库中提取出来加入到暂存区后，才能使用`git write-tree`生成项目的新版本。

#### 2，构建树对象

2.1，我们可以通过`update-index`、`write-tree`、`read-tree`等命令来**构建树对象并塞入到暂存区（update-index）及生成暂存区快照的同时将暂存区内容提交到版本库中（write-tree）**。

2.2，构建树对象实现步骤：

- 利用`updata-index`命令为test.txt文件的首个版本创建一个暂存区。并通过`write-tree`命令生成树对象，使用以下命令：
    
    - `git update-index --add --cacheinfo 100644  83base61804e65cc73a7201a7252750c76066a30 test.txt`。（创建暂存区的同时将数据加入创建的暂存区中）
    
    - `git write-tree`
        
- 可使用命令：`git ls-files -s`查看暂存区的内容。
        
- **注意**：
            
    - `update-index`并没有将数据存入数据库，只是加入了暂存区。使用命令`git hash-object -w test.txt`才将文件存入数据库（版本库）。
            
    - 使用命令`git write-tree`**为暂存区生成快照，并将暂存区内容生成树对象提交到版本库中。但是暂存区内容提交到版本库之后，并不会将暂存区的内容清除**。
        
- **说明** ：`git write-tree`命令可以等到暂存区文件达到构成一个项目版本的时候再执行。
    
    - **文件模式说明**：
    
        - 100644：表示一个普通文件。
    
        - 100755：表示一个可执行文件。
    
        - 120000：表示一个符号链接。
    
    - **--add选项说明**：
    
        - 因为此前该文件并不在暂存区中，首次需要使用--add。
    
    - **--cacheinfo选项说明**：
    
        - 由于将要添加的文件位于git数据库中，而不是位于当前目录下，即需使用--cacheinfo。
        
- 新增new.txt，将new.txt和test.txt文件的第二个版本塞入暂存区。并通过write-tree命令生成树对象。使用命令：
    
    - echo "new file" > new.txt （创建一个新的文件）
        
    - git update-index --cacheinfo 100644 1f7a7a472abf3dd9643fd615f6da379c4acb3e3a test.txt（创建该文件的暂存区）
        
    - git hash-object -w new.txt（生成git对象，将文件存入.git的objects数据库中）
        
    - git update-index --cacheinfo 100644 eae614245cc5faa121ed130b4eba7f9afbcc7cd9 new.txt（将该文件从数据库放到的暂存区）
        
    - git write-tree（将暂存区的内容生成快照加入数据库中，代表该项目的另一个版本）
        
    - **说明**：如果向暂存区加入与暂存区之前保存的相同名字的文件时，后面加入的厚覆盖前面加入的。当名字不一样时，则会在暂存区创建一个新的文件。
        
- 将第一个树对象加入第二个树对象，使其成为新的树对象。使用命令：
    
    - git read-tree --prefix=bak 06e21bb0105e2de6c846725a9a7172f57dd1af96（第一棵树的hash）
        
    - git write-tree
        
- 使用命令：`git cat-file -p master^{tree}(或者是树对象的hash)`查看树对象。
    
- 使用命令：`git ls-files -s`查看暂存区的内容。
    
## 提交对象

#### 1，提交对象概述

1.1，通过调用`commit-tree`命令创建一个提交对象，为此需要指定一个树对象的`SHA-1值（hash值）`，以及该提交的父提交对象（如果有的话）。注意，第一次将暂存区做快照就没有父对象。

1.2，创建提交对象，使用命令：

- echo "first commit" | git commit-tree 该提交树对象自身的hash值
    
- 该命令返回：生成的提交对象的hash值
    
1.3，查看提交对象：

- `git cat-file -p 生成的提交对象的hash值`

- 该命令会返回自己的前一个提交对象是哪个（创建的第一个提交对象除外），提交者是谁，邮箱是什么，以及提交时的时间戳。

1.4，提交对象的格式：

- 先指定一个顶层对象，代表当前项目快照，然后是作者、提交者信息（根据uxer.name和user.email配置来设定，外加一个时间戳），留空一行，最后提交注释。接着，将创建另外两个提交对象，它们分别引用各自的上一个提交（作为其父提交对象）：

    - `echo "second commit" | git commit-tree 该树对象自身hash -p 自身前一个提交对象hash值`
    
    - `echo "third commit" | git commit-tree 该树对象自身hash -p 自身前一个提交对象hash值`
    
1.5，`提交对象`是链式的（`项目的版本就是一个提交对象`），每个提交对象都知道自己的前一个提交对象是谁（除第一个提交对象外）。
    
**注意**：git commit-tree不但生成提交对象而且还会将对应的快照（树对象）提交到本地库中。

## git对象、树对象提交对象总结

#### 1，git对象

1.1，git对象就是使用`git hash-object -w 文件路径`命令将创建的文件添加到数据库中生成的。

- 每个文件都对应一个git对象，因此每个git对象就代表每个文件的一个个版本。

1.2，树对象就是使用`git write-tree`命令为版本库中提交到暂存区的git对象（使用`git update-index --add --cacheinfo 文件模式  该文件的hash值`
命令将git对象从版本库提交到暂存区）生成一次快照，并生成一个树对象提交到版本库（git数据库）中。

- 每个树对象其实就代表一个项目的一个个版本。

1.3，提交对象就是使用`echo "second commit" | git commit-tree 该树对象自身hash -p 自身前一个提交对象hash值`（如果是第一个提交将对象就不需要前一个提交对象的hash值）命令生成的。

- 每个提交对象中都包含有提交者的user.name以及email。还包括提交时的时间戳、注释以及自身前一个版本的提交对象。每个提交对象都代表项目的一个版本。

## git高层命令基本使用概述

#### 1，创建工作目录，对工作目录进行修改

1.1，echo "创建一个txt文件" > test.txt

#### 2，git add ./ 

2.1，在工作目录下使用该命令将文件添加到版本库中生成git对象，并且再从版本库中提交到暂存区。

2.2，git add ./相当于以下两个命令的结合：

- `git hash-object -w 要保存的文件名`（修改了多少个文件，该命令就要执行多少次。

- `git update-index --add --cacheinfo 文件模式 该文件的hash值`。

#### 3，git commit -m "注释内容"

3.1，为暂存区的git对象生成快照，并且生成树对象提交到版本库中，再从版本库中提取出来生成提交对象，之后再保存进入版本库。

3.2，`git commit -m "注释内容"`相当于以下两个命令的结合：

- `git write-tree`生成树对象。

- `git commit-tree`生成提交对象。

## git高层命令(CRUD)

#### 1，git init

1.1，要对现有的某个项目使用git管理，只需要在此项目所在的目录，执行git init命令。

1.2，`该命令的作用就是`：使用该命令进行初始化后，就会在当前目录下生成一个名为`.git`的目录所有git需要的数据和资源都存放在这个目录中。不过目前，仅仅是按照既有的结构框架初始化好了里面所有的文件和目录，但我们还没有开始跟踪管理项目中的任何一个文件。

#### 2，git add ./

2.1，`./`代表当前文件目录下所有的文件。而`git add "文件名"`就代表只提交当前文件到暂存区。

2.2，该命令用于将修改后的文件添加到暂存区。即可将未跟踪的文件设置为已跟踪的文件。而已跟踪文件有三种状态，分别是：`已修改`、`已提交`、`已暂存`。

2.3，修改了已暂存的文件需要再次使用`git add "文件名"`命令将修改后的文件
添加到暂存区。即只要文件修改了，就需要再次使用该命令将修改后的文件提交到暂存区。

#### 3，git commit -m "注释" 

3.1，该命令用于将暂存区的内容提交到版本库中。

3.2，`git commit`（不要加-m）能编写大量的注释。

- 如果有很多注释需要被写入提交对象，使用就能换行编写大量的注释。进入后使用英文模式下`i键`进入编辑模式，编辑好之后
使用`esc键`加`:键`输入`wq`将编辑内容保存并退出。

3.3，`git commit -a -m "注释"`：使用此命令能跳过暂存区直接将跟踪的内容提交到版本库中。但是**只有之前跟踪过的文件才可以使用该命令**。

#### 4，git status

4.1，该命令用于确定文件当前处于什么状态。

#### 5，git diff

5.1，该命令用于查看哪些文件修改了但还没暂存。

5.2，使用该命令后在Git Bash Here中颜色显示为`红色`的说明`修改了`但还`没有提交到暂存区`。

#### 6，git diff --staged

6.1，该命令用于查看哪些文件被暂存了但还没有被提交。

6.2，使用该命令后在Git Bash Here中颜色显示为白色的说明已经提交了，绿色表示暂存了但还没有提交。

#### 7，rm 要删除的文件

7.1，使用该命令可以删除工作目录中的文件。

7.2，**注意**：删除操作在git眼中就相当于修改文件，删除后的文件还是可以添加到暂存区。即在工作区做的是删除操作，但是在git中做的是添加操作，因为将此次删除后的文件提交到暂存区后进行git commit提交到版本库中还是会生成一个树对象及提交对象，只是这次的树对象和提交对象中不包含删除的git对象了。

#### 8，git rm 要删除的文件

8.1，使用该命令可以删除工作目录中的文件并且将修改添加到暂存区。

8.2，执行该命令相当于使用了`rm命令`加上`git add ./`命令。

#### 9，mv 原文件 新文件名

9.1，使用此命令可修改文件名

#### 10，git mv 原文件 新文件名

10.1，将工作目录中的文件进行重命名，再将修改添加到暂存区。

#### 11，git log 

11.1，使用该命令可以查看历史记录

**11.2，git log 参数**

- `git log --pretty=oneline`使用该命令可以使每条历史记录在一行显示。

- `git log --oneline`使用该命令可以缩短hash值位数使每条历史记录在一行显示。

#### 12，git reflog

12.1，使用该命令**git reflog**可以查看完整的历史记录。

## git高层命令（分支）

#### 1，git分支概述

1.1，几乎所有的版本控制系统都以某种形式支持分支。使用分支意为着可以把工作从开发主线上分离开来，以免影响开发主线。在很多版本控制系统中，这是一个略微低效的过程，常常需要完全创建一个源代码目录的副本。这对于大型项目来说，这样的过程会花费很多时间。

1.2，但对于git来说，git的分支模型是极其高效轻量的。是git的必杀技特性。也正是因为这一特性，是的git从众多版本控制系统中脱颖而出。

1.3，**分支**：即为指向最新提交对象的指针，`本质上就是一个提交对象`。

1.4，**HEAD**：是一个`指针`，默认指向master分支，切换分支其实就是让HEAD指向不同的分支。当每次有新的提交时，HEAD都会带着当前指向的分支一起往前移动。

#### 2，git branch 分支名

2.1，使用命令：`git branch 分支名`创建git分支。

- 该命令的作用就是为我们`创建一个可以移动的新的指针`。比如，创建一个testing分支：`git branch testing`。这会在当前所在的提交对象上创建一个指针。

- **注意**：`git branch 分支名`创建的一个新分支，并不会自动切换到新分支中去。在不手动更改的情况下，HEAD默认指向`master`分支。

2.4，如图所示：

![image](https://img2018.cnblogs.com/blog/1133560/201903/1133560-20190325203719744-1657731907.png)

#### 3，git branch

3.1，使用该命令`git branch`显示分支列表。

#### 4，git checkout 分支名

4.1，使用该命令`git checkout 分支名`切换分支。 

- 当分支创建完成以后，git不会自动指向创建的分支，而需要手动切换到新创建的分支。

![image](https://img2018.cnblogs.com/blog/1133560/201903/1133560-20190325204624109-1036114359.png)

- 一但分支切换完成，HEAD指针就会带着新创建的分支向前移动，而master分支则会留在原地。

![image](https://img2018.cnblogs.com/blog/1133560/201903/1133560-20190325205631549-188439943.png)

#### 5，git checkout -b 分支名

5.1，使用该命令`git checkout -b 分支名`可以创建一个分支，并且切换到新创建的这个分支。

#### 6，git branch -d name

6.1，使用该命令`git branch -d name`删除分支。但是必须先切回主分支（master）上再删除创建的分支。

#### 7，git branch -D name

6.2，使用命令`git branch -D name`强制删除分支。删除时需要先回到主分支（master）上。
尽管当前分支上有为提交的修改，但还是需要删除时，可以使用此命令。

#### 8，git branch -v

8.1，使用该命令`git branch -v`可以查看每一个分支的最后一次提交。

#### 9，git branch name commitHash

9.1，使用该命令`git branch name(创建的分支名) commitHash(需要查询提交对象的hash值)`
可以新建一个分支并且使分支指向对应的提交对象。

#### 10，git branch --merged

10.1，使用该命令`git branch --merged`查看哪些分支已经合并到当前分支上了。

- 在这个列表中分支名字前面没有`*`号的分支通常可以使用`git branch -d branchName`命令进行删除。

#### 11，git branch --no-merged

11.1，使用该命令`git branch --no-merged`查看所有包含未合并工作的分支。

- 尝试使用`git branch -d`命令删除在这个列表中的分支时会失败。如果真的需要删除分支并丢掉那些工作，可以使用`git branch -D`选项强制删除它。

#### 12，git log --oneline --decorate --graph --all

12.1，该命令用于查看这个项目的分支图。

## 配置命令别名

#### 1，配置git命令别名

1.1，可以通过git config文件来为每一个命令设置一个别名。

- **git config --global alias.别名 需要配置别名的git命令**

    - git config --global alias.loga "log --oneline --decorate --graph --all"
    
- **注意**：当需要配置的git命令是多单词的命令时，需要加引号，当是单个单词的命令时，可不加引号。

## 切换分支涉及问题说明

#### 1，该分支未处理干净就切换到别的分支

1.1，当在切换分支时，如果当前分支上有未暂存的修改（修改的文件从未使用add提交到暂存区）或者有未提交的暂存（该暂存文件从未使用commit提交），此时分支可以切换成功，但是这种操作可能会污染其他分支。即在切换完分支后，git会自动将之前切换分支时为处理的文件带到目前HEAD指向的分支上，污染当前工作目录。

1.2，当在切换分支时，如果当前分支上有未暂存的修改（该修改使用add提交过）或者有未提交的暂存（该暂存文件使用commit提交过），那么此次分支切换将会失败。需要先处理未处理干净的文件才能完成切换。

1.3，**提示**：每次切换分支时，当前分支需要处理干净（所有文件处于已提交的状态）。

#### 2，切换分支影响的三个区域

2.1，`HEAD`，当切换分支后，HEAD就会指向新切换过来的分支。

2.2，`暂存区`，当前换分支后，暂存区将不是原来分支上的内容了，而是当前HEAD指向的分支上暂存区的内容了。

2.3，`工作目录`，切换分支后，工作目录的内容不再是之前分支上的内容，而是当前HEAD指向的分支最后一次提交时的内容了。

## 合并分支

#### 1，git merge 需要被合并的分支

1.1，使用`git merge 需要被合并的分支`命令可以用来合并分支。

1.2，**注意**：需要先切回主分支，再进行分支合并。还需要注意的是，使用这种方式合并分支属于`快进合并`。这种合并方式不会产生冲突，因为这两个分支处于同一条线上。

1.3，如下图所示情况：

- 首先创建了一个分支iss53，遇到紧急情况将这个分支的工作先停下，并将其提交了。之后又创建了一个新的分支hotfix，在这个新创建的分支上进行工作。

![image](F6769C0A41DA48F6AFE4AAF4965880E1)

- 当hotfix分支上的工作完成后，就需要将该分支与master分支进行合并。而这个合并过程就是**快速合并**，由于这两个合并的分支`处于同一条线上`，所以就`不会产生冲突`。

![image](DB3E246130F247C7976064155C70E08A)

- 当hotfix分支与master分支合并完成以后，将hotfix分支进行删除，并切回iss53分支上进行工作。

![image](C9BB6E05BB2742C795586ED28A94844A)

- 当iss53分支上的工作完成以后，需要与主分支进行合并时，主分支master并不是iss53的直接祖先（iss53的直接祖先应该在C2位置）。但现在master主分支已经处于iss53分支直接祖先的前面了，这种情况合并分支时，git会使用两个分支的末端所指的快照（如图C4与C5）以及这两个分支的公共祖先（C2），做一个简单的三方合并。

![image](F508B9DE6D4B4D81A2B2AB897CCF508D)

- 这种三方合并也称为**典型合并**，这种合并可能导致iss53分支上修改了之前hotfix分支上修改的文件，即这两个不同的分支修改了同一个文件的同一个部分的内容。在这中情况下合并分支就会`产生冲突`。**而当不同的分支没有修改同一个文件内容时，就不会出现产生冲突的情况**。

- 当产生冲突时，合并分支过后，会给出产生冲突的提示（会提示哪个文件产生冲突），并且在冲突的文件内部git会加入冲突的解决标记，如下：

``` js
<<<<<<< HEAD:index.html
<div id="footer">contact : email.support@github.com</div>
=======
<div id="footer">
 please contact us at support@github.com
</div>
>>>>>>> iss53:index.html
```
- 遇到这种情况时，我们只需要将文件中的这些提示进行处理（直接将标记删除或其他操作），之后使用命令**git add ./**就可说明冲突已经解决了。之后将解决好冲突的文件进行`commit`提交后，也就完成一次成功的典型合并了。

![image](9E12F1ACE4514FAC80C4A78468E35AF4)

## 分支模式

#### 1，分支的模式概述

1.1，分支模式有两种情况，分别为：**长期分支**与**特性分支**。

- 长期分支：就是`master`及`自己从master一开始创建出来的分`就可称为长期分支。

- 特性分支：特性分支就是为了完成项目某个功能而开辟的分支，当这个功能所涉及的工作完成后，就将该分支与自己的开辟的长期分支进行合并。之后在开启下一个特性分支。

## git存储

#### 1，git存储概述

1.1，当不希望切换到别的分支时将当前分支上的内容进行提交时，就需要使用git存储将数据先存储下来。

#### 2，git stash

2.1，使用该命令`git stash`可将未完成的修改保存到一个栈上，之后可以在任何时候重新应用这些改动（**git stash apply**）。

2.2，**注意**：需要保存的修改需要先使用`git add`命令进行追踪，之后才能使用命令`git stash`进行储存。否无法储存。

#### 3，git stash list

3.1，使用该命令`git stash list`可以查看储存。

#### 4，git stash apply stash@(2) 

4.1，使用该命令`git stash apply stash@(2)`可以应用储存。

- **注意**：如果不指定一个储藏，git会默认指定最新的储存。

#### 5，git stash pop

5.1，使用该命令`git stash pop`可以应用储存，然后立即从栈上扔掉它。

#### 6，git stash drop

6.1，使用该命令`git stash drop`可以用来加上将要移除储存的名字来移除它。

## git撤销(覆盖)命令解析

#### 1，git commit -amend

1.1，使用该命令`git commit --amend`可修改提交的注释信息，
并且将上一次commit提交的内容覆盖。也就相当于撤回了上一次commit。

1.2，如果上次提交以来还未做任何修改（例如：在上一次提交后马上执行了此命令），那么快照会保持不变，而修改的只是提交信息。

1.3，如果在提交后发现忘了暂存某些需要的修改（未暂存其他需要的文件），可进行如下操作：

```
git commit -m "initial commit"

git add forgotten_file

git commit --amend
```

- **说明**：进行以上操作后，最终只会有一个提交，第二次提交将代替第一次提交的结果。

#### 2，git reset HEAD 文件名

2.1，使用该命令`git reset HEAD 文件名`可将文件从暂存区中撤回到工作目录中。

- 该命令完整形式是git reset --mixed HEAD 文件名。

#### 3，git checkout --文件名

3.1，使用该命令`git checkout -- 文件名`可在工作目录中对文件的修改进行撤销。

- **提示**：该文件需要被git管理（add过后）了，使用`git checkout -- 文件名`命令才有效，否则无效
。而且`--`与文件名之间需要有一个空格，否则会报错。

3.2，**注意**：`git checkout -- 文件名`
是个很危险的命令。你对这个需要删除的文件所做的任何修改都会消失。该命令本质上只是拷贝了另一个文件来覆盖删除的文件。

## git reset原理解析

#### 1，reset的本质

1.1，reset的本质其实就是**移动HEAD以及它所指向的branch（分支）**。

1.2，实质上，reset这个命令虽然可以用来撤销commit，但它的实质行为并不是撤销，而是移动HEAD，并且会捎带上HEAD所指向的branch。说白了reset这个指令就是用来重置HEAD以及它所指向的branch的位置的。

![image](C8719C4C514A4FA0B5F432164A43AF34)

#### 2，reset的三种模式图示

![image](EFFF5EA84FCA4413BBE9F32BB0FB864A)

#### 3，reset三种模式之reset --hard

3.1，使用命令**git reset --hard HEAD~**
会将工作目录、暂存区、版本库都重置成当前HEAD所指向的新位置（提交对象）的内容。其效果相当于清空了暂存区和工作区。即工作目录里的新改动和已经add到暂存区的新改动也一起消失了。

- `HEAD~`代表当前HEAD的前一个提交对象（commithash)。

- **说明**：reset三种模式所用到的**HEAD~**都可以使用**commitHash**进行代替。

3.2，`reset --hard HEAD~`之所以起到了撤销commit的效果，是因为它把`HEAD`和`HEAD所指向的分支`一起移动到了当前commit的父commit上，从而起到了撤销的效果。

![image](B8224A64A4B34C4C90B11846CD48DE7A)

3.3，由于git的历史只能往回看，不能往前看，所以把HEAD和分支往回移动，就起到了撤回commit的效果。而reset --hard不仅可以撤销提交，还可以用来把HEAD和分支移动到其它任何地方。

- 使用命令**git reset --hard 分支名**可以将`HRAD`及`当前HEAD所处的分支`移动到指定的其它分支上。

![image](BA21A40A5AE94EE09A20AB8638E18AA3)

#### 4，reset三种模式之reset --soft

4.1，使用命令**git reset --soft HEAD~**
可以保留工作目录和暂存区的内容，并把重置HEAD所带来的新的差异放进暂存区。而这种效果看起来就是**工作目录**和**暂存区原有的内容**都不变，只是原节点和当前节点之间的所有差异都会放入暂存区。

![image](6D1E3A37BD3C4133924D0D0681FED9AC)

- 所谓的新的差异就是HEAD从图中4移动到3时，4中的工作目录内容及暂存区的内容都没有被清除，因此就会与3处的工作目录及暂存区存在差异。而这个新的差异就会放入到当前HEAD所处的暂存区中。

#### 5，reset三种模式之reset --mixed

5.1，reset如果不加参数，默认使用--mixed参数。

5.2，使用命令**git reset --mixed HEAD~**可以保留工作目录，并且清空暂存区。

- 该命令会将工作目录的修改、暂存区的内容以及由reset所导致的新的文件差异，都放进工作目录。

- 简单说，该命令就是将所有的差异都混合（mixed）起来放在工作目录中。

#### 6，reset三种模式之间的差异

6.1，**--mixed和--soft**的区别在于：--mixed会保留工作目录，但会把暂存区清空，并把原节点和reset节点的差异文件放进工作目录。而--soft则不会将暂存区清空，也不会清空工作目录，并且把reset节点的差异放进暂存区。

6.2，**--soft**和**--hard**的区别在于：--hard会清空工作目录和暂存区的改动，而--soft会保留工作目录及暂存区的内容，并把由于保留工作目录内容所带来的新的文件差异放入暂存区。

#### 7，reset --hard与checkout的共同点

7.1，这两者都需要重置HEAD、暂存区、工作目录。

#### 8，reset --hard与checkout的区别

8.1，checkout只动HEAD。而--hard在动HEAD的同时还会带着分支一起动。

8.2，checkout对工作目录是安全的。而--hard是强制覆盖工作目录，当工作目录没有add时，将会有丢失数据的危险。

#### 9，reset三种模式的本质（除路径reset）

9.1，其本质就是使用**当前HEAD的前一个提交对象的内容**`重置`**当前HEAD的内容**。

- reset --hard就类似于`git checkout --filename(文件名)`。
    
    - 将HEAD移到上一次提交对象处，并且直接用上一次HEAD所指向的提交对象覆盖当前HEAD所指向的提交对象，其效果看起来就像是将暂存区及工作目录全部删除了，实际是被上一次的内容覆盖了。

- reset --soft就类似于`git commit amend`。

    - 将HEAD移到上一次提交对象处，用上一次的提交对象覆盖当前提交对象，但是会保留当前暂存区及工作目录的内容，再将重置出现的差异存入重置后的暂存区，再次提交就实现了覆盖前一次commit。

- reset --mixed就类似于`git reset HEAD 文件名`。

    - 将HEAD移到上一次提交对象处，用上一次的提交对象覆盖当前提交对象，但会保留当前工作目录的内容，同时删除当前暂存区的内容，并将重置后文件差异存入工作目录。这就实现了将暂存区文件撤回到工作目录中。

9.2，reset --soft的本质就是使用

## 路径reset

#### 1，路径reset概述

1.1，所谓的路径reset就是在HEAD后面可以跟文件名。

1.2，**注意**:只有--mixed才能跟路径，其余`--soft`和`--hard`都无法跟路径。

- **git reset --mixed HEAD filename**：该命令可用来将暂存区文件撤回到工作目录中。

- 该命令的本质就是用`上一次的提交对象的内容`去重置当前暂存区，将重置后产生的差异存入工作目录，这就实现了撤回暂存区内容。

1.3，所有的路径reset都不会改变HEAD的内容（即不会改变HEAD的指向）。

- 其原理在于HEAD本质指向一个分支，分支的本质是一个提交对象，提交对象又指向一个树对象，树对象很有可能指向多个git对象，而一个git对象就代表一个文件。由此可见：HEAD可以代表一系列文件的状态。因此只有一个文件需要改变时，不可能改变整个HEAD的内容。

## git数据恢复

#### 1，硬重置

1.1，使用命令**git reset --hard 目标hsah值**就可以实现用重置到指定的节点上。

#### 2，创建分支进行恢复

2.1，使用命令**git branch 分支名 需要恢复的提交对象hash值**
创建一个新分支指向需要恢复的提交，进而可对该恢复的提交进行操作，完成后进行commit提交，即可与master分支进行合并。达到了数据恢复的效果。

2.2，**提示**：尽量使用创建分支进行数据恢复，少用硬重置。

## 打tag

#### 1，打tag概述

1.1，git可以给历史中某一个提交打上标签，以示该提交较为重要。比较有代表性的是人们会使用这个功能来标记发布节点（v1.0等）。

#### 2，列出标签

2.1，使用**git tag**命令列出创建的标签。

#### 3，创建标签

3.1，使用命令**git tag 版本号**即可创建标签。

- 使用`git tag 版本号 commitHash`命令可以为指定的提交对象创建版本号。

3.2，git使用两种主要类型的标签：**轻量标签**和**附注标签**。

- **轻量标签**：很像一个不会改变的分支，它只是一个特定提交的引用。

- **附注标签**：附注标签是储存在git数据库中的一个完整对象。它们是可以被校验的，其中包含`打标签者的名字`、`电子邮件地址`、`日期时间`、`还有一个标签信息`。通常建议创建附注标签，这样可以拥有以上所有信息，但是如果只想用一个临时的标签，或者因为某些原因不想要保存那些信息，轻量标签也是可用的。

- 使用**git tag -a 版本号**命令可以创建附注标签。

- 使用**git tag -a 版本号 commitHash**命令为指定提交对象创建附注标签。

- 使用**git tag -a 版本号 commitHash -m "注释"**命令为指定提交对象创建附注标签即编写注释信息。

#### 4，查看特定标签

4.1，**git show**命令可以显示任意类型的对象（git对象、树对象、提交对象、tag对象）。

- 使用**git show tagname**命令可以查看tag标签对象。

#### 5，远程标签

5.1，默认情况下，`git push`命令
并不会传送标签到远程仓库服务器上。在创建完标签后，必须显示地推送标签到共享服务器上。

- 使用命令**git push origin [tagname]**命令推送标签至远程仓库服务器上。

- 如果想一次性推送很多标签，也可以使用带有`--tags`选型的`git push`命令。
这将会把所有不在远程仓库的服务器上的标签全部传送到那里。命令如下：

- **git push origin --tags**命令将所有不在远程仓库中的标签全部传送到远程仓库。

#### 6，删除标签

6.1，想要删除本地仓库上的标签可使用如下命令：

- **git tag -d <tagname>**

- `git tag -d v1.0`即表示删除本地仓库上版本为1.0的标签。

- **注意**：上述命令并不会从远程仓库中移除这个标签，必须使用
`git push <remote> :refs/tags/<tagname>`命令来更新远程仓库。

- **git push origin :refs/tags/v1.0**

#### 7，检出标签

7.1，如果想查看某个标签所指向的文件版本，可以使用`git checkout`命令：

- **git checkout tagname**

- 这个命令会使仓库处于`分离头指针（detacthed HEAD）`状态。

- 在`分离头指针`状态下，如果做了某些更改然后提交它们，标签不会发生任何变化，但是新提交将不属于任何分支，并且将无法访问，除非访问确切的提交hash（**HEAD目前并未指向任何分支**）。因此，如果需要进行更改，比如修复旧版本的错误，这通常需要创建一个新的分支：`git checkout -b version2`。

- 总之当你处于分离头指针状态时，只需在该检出标签所处的节点上创建一个新的分支即可解决以上问题。

## 使用远程仓库

#### 1，远程仓库概述

1.1，远程仓库是指托管在因特网或其他网络中的你的项目的版本库。你可以有好几个远程仓库，通常有些仓库对你是只读的，有些则可以读写。**与他人协作涉及管理远程仓库以及根据需要推送或拉取数据**。

#### 2，管理远程仓库

1.2，管理远程仓库包括了解如何添加远程仓库、移除无效的远程仓库、管理不同的远程分支并定义它们是否被跟踪等等。

#### 3，忽略某些文件

3.1，当不希望`无需纳入git管理的文件`出现在未跟踪文件列表中时，可以创建一个名为.gitignore的文件，在该文件中列出要忽略的文件模式。

- `*.[oa]`

- `*~`

- 上述第一行告诉git忽略所有以.o或.a结尾的文件。一般这类对象文件和存档文件都是编译过程中出现的，不需要跟踪它们的版本。第二行告诉git忽略所有以波浪符（~）结尾的文件，许多文本编辑软件（比如Emacs）都用这样的文件名保存副本。此外，可能还需要忽略log、tmp或者pid目录，以及自动生成的文档等等。最好养成一开始就设置好`.gitignore文件`的习惯，以免将来误提交这类无用的文件。

#### 4，**.gitignore**的格式规范

4.1，所有`空行`或者`以注释符号#开头的行`都会被git忽略。

4.2，可以使用标准的glob模式匹配。

- `*`代表匹配任意个字符。

- `?`代表匹配任意一个字符。

- `**`代表匹配多级目录。

- 匹配模式前跟反斜杠（`/`)，这个斜杠代表项目根目录。

- 匹配模式最后跟反斜杠（`/`），说明要忽略的是目录。

- 要忽略指定模式以外的文件或目录，可以在模式前加上感叹号（`!`）取反。

#### 5，忽略文件.gitignore配置

```
.DS_Store

node_modules/

/dist/

npm-debug.log*

yarn-debug.log*

yarn-error.log*

# Editor directories and files

.idea

.vscode

*.suo

*.ntvs*

*.njsproj

*.sln
```

#### 6，在gitHub中创建远程仓库

6.1，登录github，点击页面右上角`+`号位置，再点击出现的`New repository`创建一个远程仓库。

6.2，**注意**：初始化这个远程仓库一定要是空的，该操作在gitHub上操作。

#### 7，创建本地仓库

7.1，使用`git init`命令初始化一个本地仓库。

#### 8，为远程仓库配置别名&用户信息

8.1，使用命令**git remote add shortname(要设置的别名) url(远程仓库url地址)**
添加一个新的远程git仓库，同时指定一个你可以轻松引用的简写。

8.2，使用命令**git remote -v**显示远程仓库使用的git别名与其对应的URL。

8.3，使用命令**git remote show [remote-name]（[]代表该参数可以不写）**
查看某个远程仓库的更多信息。

8.4，使用命令**git remote rename pb paul**进行重命名。

8.5，如果因为一些原因想要移除一个远程仓库（已从服务器上搬走了或者不想使用某个特定的镜像了，又或者某个贡献者不再贡献了），即可使用命令**git remote rm [remote-name]**移除某个远程仓库。

#### 9，推送本地仓库到远程仓库

9.1，使用命令**git push [remote-name] [branch-name]**将本地仓库文件推送到远程仓库。

- `git push 远程仓库别名 分支名`

#### 10，如何邀请他人进入项目。

10.1，如果想要与他人合作，并想给他们提交的权限，此时你需要他们添加为`Collaborators（伙伴）`。

- 在登录状态下，点击需要与他人合作的项目，选择**settings**项，之后点击`Collaborators`

## 团队协作

#### 1，项目经理初始化远程仓库。

1.1，登录github，点击页面右上角`+`号位置，再点击出现的`New repository`创建一个远程仓库。
需要注意的是，一定要初始化一个空的仓库。

#### 2，项目经理创建本地仓库

2.1，使用命令**git remote 别名 远程仓库地址（https，远程仓库创建成功后会有显示）**给项目设置别名。

2.2，使用命令**git init**初始化仓库，之后将源码复制进做git init初始化的文件中。

2.3，将源码准备好准备好之后，项目经理修改自己的用户名和邮箱地址。

2.4，一切处理完毕后使用命令**git add ./**将文件推送到暂存区，在使用**git commit**命令进行提交。

#### 3，项目经理推送本地仓库到远程仓库。

3.1，清理windows凭据。

- 当在一台电脑上同时操作两个github账号进行推送时，需要清理凭据。

- 凭据在电脑`控制面板>用户账户>管理您的凭据`处可以找到。

3.2，使用命令**git push 项目别名 当前项目所处分支名**进行推送。

#### 4，项目经理邀请成员

4.1，项目经理邀请成员后，需要得到成员的答复。

- 在github登录状态下，点击需要与他人合作的项目，选择项目的**settings**选项，之后点击左侧**Manage access**选项之后，即可邀请指定的成员。

- 成员只有在项目经理授权之后，才能对该项目进行修改，并提交修改到该远程仓库。即成员需要被授权成为
`Collaborators`之后才能将修改推送到该远程仓库。

#### 5，成员克隆远程仓库

5.1，使用命令**git clone 远程仓库地址**

- 克隆之后在本地生成.git文件，默认为远程仓库配置一个别名**origin**。而且默认主分支有对应的远程跟踪分支。

- 成员将代码从远程仓库clone下来时，会默认为远程仓库配置一个`origin的别名`。

#### 6，成员作出贡献

6.1，成员修改代码后进行add与commit提交到本地仓库。

6.2，在使用命令**git push 项目别名 分支名**。

- 需输入用户名，密码，将本地分支推送到远程仓库之后会附带生成`远程跟踪分支`。

#### 7，项目经理更新成员提交的修改

7.1，使用命令**git fetch 项目别名**访问远程仓库，从中拉取所有你还没有的数据。

- 执行该命令之后，你将会拥有那个远程仓库中所有分支的引用，可以随时合并查看。

- **注意**：`git fetch命令`会将数据拉取到你的本地仓库，它并不会自动合并或修改你当前的工作。当准备好时，你必须手动将其合并入你的工作。

- git fetch拉取数据时，会先将数据拉取到**远程跟踪分支**上，之后再将远程跟踪分支与master分支进行合并才能在本地仓库将远程仓库拉取的修改进行合并。

- 如果不小心将创建的项目别名忘了，可以使用命令**git remote -v**进行查看项目设置的别名。

7.2，使用命令**git merge 远程跟踪分支**将分支进行合并。

- 当将本地仓库推送到远程仓库时，会默认生成一个分支**(项目别名/master)分支**，该分支称为`远程跟踪分支`，也可简称为`跟踪分支`。

- **注意**：本地仓库有master分支，远程仓库也有一个master分支，而当将本地仓库提交到远程仓库时会生成一个远程跟踪分支`项目别名/master`。

- **远程跟踪分支**就是`本地分支`与`远程分支`之间的**媒介**。当需要获取到远程仓库的修改，就需要先从本地分支上切到远程跟踪分支上，从远程跟踪分支上获取到修改后，再切回本地分支master上将远程跟踪分支进行合并，就完成了数据的跟新。

7.3，**提示**：本地分支需要与远程分支进行交互，就需要远程跟踪分支作为媒介。

## 深入理解远程仓库

#### 1，远程跟踪分支概述

1.1，远程跟踪分支是`远程分支状态的引用`。它们是你不能移动的本地分支。当你做任何网络通信操作时，它们会自动移动。

1.2，远程分支与远程跟踪分支以（remote）/（branch）的形式命名，例如，当你想要看你最后一次与远程仓库origin通信时，master分支状态，就可以查看origin/master分支。

1.3，当克隆一个仓库时，它通常会自动的创建一个跟踪origin/master的master分支（本地分支）。

#### 2，远程跟踪分支与本地分支之间的关系

2.1，**注意**：在`clone`的时候会自动生成一个master本地分支，只有这种情况这个master本地分支才会与远程跟踪分支才会建立同步关系。除此以外`git push`与`git fetch`都是**生成远程跟踪分支**，
同时`建立远程跟踪分支与远程分支的同步状态`。

#### 3，如何建立已存在本地分支与远程跟踪分支的同步关系

3.1，使用命令**git branch -u origin/master**进行跟踪远程跟踪分支，与之建立同步关系。

- **说明**：该命令可以设置`已有的本地分支`跟踪一个刚刚拉取下来的远程分支，或者想要`修改`正在跟踪的运程跟踪分支。并且在任何时间都可以使用`-u选项`运行git branch来显示的设置。

- 已有的本地分支可以是除master分支之外的其他分支。

3.2，使用命令**git branch -vv**查看设置的所有跟踪分支。

#### 4，如何使远程跟踪分支被未存在的本地分支跟踪

4.1，使用命令**git checkout -b 要创建的分支名 远程跟踪分支**
在创建新分支的同时直接指向远程跟踪分支，与远程跟踪分支建立跟踪关系。

4.2，或者使用上述方式的快捷命令**git checkout --track 远程跟踪分支**同样能达到上述命令的效果。

#### 5，建立本地分支与跟踪分支同步关系的好处

5.1，本地分支就可以直接使用**git push**命令将当前分支所处的本地仓库推送到远程仓库。

5.2，本地仓库可以直接使用**git pull**命令将远程仓库中的数据拉取到本地。

#### 6，数据推送与拉取总结

6.1，确保本地分支（包含master在内的任意分支）已经跟踪了远程跟踪分支。

6.2，确保跟踪后，直接使用命令**git pull拉取数据**。

6.3，确保跟踪后，直接使用命令**git push推送数据**。

## git冲突

#### 1，产生冲突的情况

1.1，git本地合并分支处于`典型合并`时，可能会产生冲突。

1.2，git远程协作`push及pull时`都可能产生冲突。

- 当两者修改了同一个文件的相同地方时，进行`push推送`到远程仓库时，就会提示产生冲突。

- 当你在本地修改的文件处与他人已推送到远程仓库的文件处相同时，这时你再`pull拉取`远程仓库中的文件就会产生冲突。此时会提示你`先对你的修改使用add及commit进行提交`，`再push文件`进行冲突处理，当你push时，就会提示哪个文件产生了冲突。根据提示解决冲突即可。

## 删除远程分支

#### 1，如何删除远程分支

1.1，使用命令**git push origin(项目别名) --delete 需删除的远程分支**将远程分支删除。

1.2，使用命令**git remote prune 项目别名** --dry-run列出任在远程跟踪但是远程已被删除的无用分支。

1.3，使用命令**git remote prune origin**清除上面命令列出来的正在跟踪的无用远程跟踪分支。

## pull request（合并请求）流程

#### 1，pull request流程概述

1.1，如果想要参与某个项目，但是并没有推送权限，这时可以对这个项目进行“派生”（Fork）。派生的意思是指，github将你在空间中创建一个完全属于你的项目副本，且你对其具有推送权限。通过这种方式，项目管理者不再需要忙着把用户添加到贡献者列表并给于他们推送权限。人们可以派生这个项目，将修改推送到派生出的项目副本中，并通过创建合并请求（Pull request）来让他们的改动进入源版本库中。

#### 2，pull request基本操作流程

2.1，在github中选中需要Fork的项目后，选择页面右上角的Fork选项，将该项目派生到自己的远程仓库中。

2.1，从master分支中创建一个新分支（自己Fork的项目）。

2.2，提交一些修改来改进项目（自己Fork的项目）。

2.3，将这个分支推送到github上（自己Fork的项目）。

2.4，创建一个合并请求。

2.5，讨论，根据实际情况继续修改。    

2.6，项目的拥有者合并或关闭你的合并请求。

#### 3，pull request注意点

3.1，每次在发起新的`Pull request`时,
要去拉取最新的源仓库的代码，而不是自己Fork的那个仓库。自己Fork的仓库始终是
你Fork时的状态。不会随着源仓库代码的改变而改变。

3.2，在`github中使用Fork选项`将远程仓库派生下来后，
在不是使用`git clone 远程仓库url`命令将代码克隆下来时，都需要手动使用
**git fetch 远程仓库别名**先拉取远程仓库中你没有的修改。
再使用**git merge 对应的远程跟踪分支名**合并拉取的远程跟踪分支得到需要的修改。

- **说明**：使用初次将代码在master主分支上将代码clone下来时，会自动为master主分支与远程跟踪分支建立跟踪关系。

## SSH

#### 1，SSH概述

1.1，github提供了两种URL，分别为https与SSH。

- SSH是github自身提供的URL。该协议只有git用。当你在push时，不需要用户填写密码/用户名等信息。但需要作一些配置。

- https是公开的协议，因此在push时需要填写用户名与密码。

#### 2，SSH创建公私钥

2.1，使用**ssh-keygen -t rsa -C 你的邮箱**可以生成公私钥。

- 公钥需要交给github。在用户的settings中设置。

- 私钥就保存在自己电脑上即可。

2.2，.ssh文件位置：`C:\Users\Administrator\.ssh`路径中。

2.3，使用ssh-T git@github.com可以测试公私钥是否配对成功。

2.4，**说明**：github中可以配置多个公钥。

- 即可将多个成员的公钥配置在github中，这样即使成员不是该项目的合作者，也可以对该项目进行读写操作。

#### 3，使用SSH推送本地仓库到远程仓库

3.1，首先需要选择sshURL进行推送。

3.2，为远程仓库设置别名：`git remote add 别名 SSH地址`。

3.3，推送本地仓库至远程仓库：`git push -u 别名 项目所在分支名（master）`

## 关于远程仓库总结

#### 1，关于远程仓库三个必懂的概念

1.1，本地分支

- 使用命令**git checkout -b 需创建的分支名**
进行创建分支的同时将HEAD指向该创建好的分支。

1.2，远程跟踪分支（remote/分支名）

- 初次将本地仓库push到远程仓库时就会生成一个远程跟踪分支。

- 初次使用git clone将远程仓库克隆下时，也将产生一个远程跟踪分支。

- 只有初次在`master主分支`上使用`git clone`命令将远程仓库克隆下来时，
才会`自动`与远程跟踪分支建立`跟踪`。其余情况都需要使用`git fetch`命令
将远程仓库中的数据拉去下来，在使用`本地分支`与拉去到的`远程跟踪分支`进行合并，最终获取到远程仓库中你没有的修改数据。

1.3，远程跟踪分支。

- 当创建好一个远程仓库时，会自动生成一个远程分支。

- 将本地仓库push到远程仓库时产生的远程跟踪分支会自动与远程分支建立跟踪。即远程分支与远程跟踪分支都可以代表远程仓库中的项目。

#### 2，远程协作基本流程

2.1，项目经理在github中创建一个空的远程仓库。

2.2，项目经理创建一个待推送的本地仓库。

2.3，为远程仓库配置别名，以及项目经理推送时的用户名/邮箱。

2.4，在本地仓库中初始化代码，之后提交代码到本地仓库。

2.5，将本地仓库推送到远程仓库。

2.6，邀请成员成为项目的collaborators合作者。

2.7，成员同意成为合作者之后，克隆远程仓库。

2.8，成员对克隆下来的数据进行修改。

2.9，成员推送自己的修改到远程仓库。

2.10，项目经理拉取成员的修改。

#### 3，建立跟踪

3.1，当克隆仓库时，会自动为master与远程跟踪分支建立跟踪。

3.2，当本地没有分支时：

- 需使用命令**git checkout --track 远程跟踪分支(remote/分支名)**建立跟踪。

3.3，本地已经创建了分支时：

- 需使用命令**git branch -u 远程跟踪分支(remote/分支名)**建立跟踪。

#### 4，建立跟踪情况下推送与拉取。

- 直接使用**git push**进行推送。

- 直接使用**git pull**进行拉取。
