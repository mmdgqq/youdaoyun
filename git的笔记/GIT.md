
- [一、安装及简单使用](#一-安装及简单使用)
    - [（一）安装](#一安装)
        - [1.在linux上安装](#1在linux上安装)
        - [2.在windows上安装](#2在windows上安装)
<br/>```$ git config --global user.name "Tinymonarch"```
<br/>```$ git config --global user.email "sap_wxy@163.com"```
    - [（二）创建版本库](#二创建版本库)
<br/>```$ git init ```
<br/>```$ git add <filename>```
<br/>```$ git commit -m "comment..."```
- [二、时光穿梭机](#二-时光穿梭机)
<br/>```$ git status```
<br/>```$ git diff```
    - [（一）版本回退](#一版本回退)
<br/>```$ git log ```
<br/>```$ git log --pretty=oneline ```
<br/>```$ git reset --hard HEAD^```
<br/>```$ git reset --hard <版本号>```
<br/>```$ git relog```
    - [（二）工作区和暂存区](#二工作区和暂存区) ★
    - [（三）管理修改](#三管理修改)
<br/>```$ git diff HEAD --<filename> ```
    - [（四）撤消修改](#四撤消修改)
<br/>```$ git checkout --<file> ```
<br/>```$ git reset HEAD <file> ```
    - [（五）删除文件](#五删除文件)
<br/>```$ rm <file> ```
<br/>```$ git rm/add <file> ```
<br/>```$ git commit -m "remove <file>" ```
- [三、远程仓库](#三-远程仓库)
<br/>```$ ssh-keygen -t rsa -C "youremail@example.com" ```
    - [（一）添加远程库](#一添加远程库)
<br/>```$ git remote add origin git@github.com:Tinymonarch/Gitfile.git ```
<br/>```$ git push origin master```
<br/>```$ git push -u origin master```
    - [（二）从远程库克隆](#二从远程库克隆)
<br/>```$ git clone git@github.com:Tinymonarch/remotegit.git ```
- [四、分支管理](#四-分支管理)
    - [（一）创建与合并分支](#一创建与合并分支)
<br/>```$ git checkout -b <name>```
<br/>```$ git branch <name>```
<br/>```$ git checkout <name>```
<br/>```$ git branch```
<br/>```$ git merge <name>```
<br/>```$ git branch -d <name>```
    - [（二）解决冲突：](#二解决冲突)
<br/>```$ git log --graph```
    - [（三）分支管理策略](#三分支管理策略)
<br/>```$ git merge --no-ff -m "comment..." <name>```
    - [（四）bug分支（保存现场）](#四bug分支保存现场)
<br/>```$ git stash```
<br/>```$ git stash list```
<br/>```$ git stash pop```
<br/>```$ git stash apply stash@{0}```
<br/>```$ git stash drop stash@{0}```
    - [（五）Feature分支](#五feature分支)
<br/>```$ git branch -D <name>```
    - [（六）多人协作](#六多人协作)
<br/>```$ git remote```
<br/>```$ git remote -v```
<br/>```$ git checkout -b dev origin/dev```
<br/>```$ git pull```
<br/>```$ git branch --set-upstream-to=origin/dev dev```
    - [（七）Rebase](#七rebase)
<br/>```$ git rebase```
<br/>```$ git log --graph --pretty=oneline --abbrev-commit```
- [五、标签管理](#五-标签管理)
    - [（一）创建标签](#一创建标签)
<br/>```$ git tag <name>```
<br/>```$ git tag```
<br/>```$ git tag <tagname> <commitid>```
<br/>```$ git tag -a <tagname> -m "comment..." <commitid>```
<br/>```$ git show <tagname>```
    - [（二）操作标签](#二操作标签)
<br/>```$ git push <origin> <tagname>```
<br/>```$ git push <origin> --tags```
<br/>```$ git tag -d <tagname>```
<br/>```$ git push <origin> :refs/tags/<tagname>```
- [六、使用Github](#六-使用github)
- [七、使用码云](#七-使用码云)
<br/>```$ git remote rm <origin>```
- [八、自定义Git](#八-自定义git)
<br/>```$ git config --global color.ui true```
    - [（一）忽略特殊文件](#一忽略特殊文件)
<br/>```.gitignore```
<br/>```$ git add .gitignore```
<br/>```$ git commit -m "git ignore"```
<br/>```$ git add -f <file>```
<br/>```$ git check-ignore -v <file>```
    - [（二）配置别名](#二配置别名)
<br/>```$ git config --global alias.st status```
<br/>```$ git config --global alias.co checkout```
<br/>```$ git config --global alias.ci commit```
<br/>```$ git config --global alias.br branch```
<br/>```$ git config --global alais.unstage 'reset HEAD'```
<br/>```$ git config --global alias.last 'log -1'```
<br/>```$ git config --global alias.lg "log --color --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit"```
        - [配置文件](#配置文件)
<br/>```.git/config```
    - [（三）搭建Git服务器](#三搭建git服务器)
<br/>```$ sudo apt-get install git```
<br/>```$ sudo adduser git```
<br/>```$ sudo git init --bare sample.git```
<br/>```$ sudo chown -R git:git sample.git```
<br/>```$ git clone git@server:/srv/sample.git```
        - [管理公匙](#管理公匙)
        - [管理权限](#管理权限)
- [期末总结](#期末总结)



## 一安装及简单使用



### （一）安装

#### 1.在linux上安装

Debian或Ubuntu Linux，通过一条 `sudo apt-getinstall git` 就可以直接完成Git的安装，老一点版本的可能是 `sudo apt-get install git-core`。

#### 2.在windows上安装

在官网直接下载[安装程序](https://git-scm.com/downloads)，然后默认选项安装。
</br></br>
安装完成后，需要在Git bash中运行一下代码来标识身份：
```
$ git config --global user.name "Tinymonarch"
$ git config --global user.email "sap_wxy@163.com"
```
注意`git config`命令的`--global`参数，用了这个参数，表示你这台机器上所有的Git仓库都会使用这个配置，当然也可以对某个仓库指定不同的用户名和Email地址。




### （二）创建版本库

版本库又名仓库，英文名repository，可以简单认为是给git使用的一个文件目录。
</br>创建版本库非常简单：</br>第一步找一个合适的地方创建一个目录，windows尽量避免使用中文路径。</br>第二步，cd到此目录下，或者在此目录中右键-Git bash进入git，通过`git init`命令就可以把这个目录变成仓库。
```
$ git init
Initialized empty Git repository in ~/Desktop/git file/.git
```

如果你没有看到`.git`目录，那是因为这个目录默认是隐藏的，用`ls -ah`命令就可以看见。

<html>
<h4 style="font-weight:normal">添加文件到版本库</h4>
</html>
明确一下，所有的版本控制系统，其实只能跟踪文本文件的改动，比如TXT文件，网页，所有的程序代码等等，Git也不例外。版本控制系统可以告诉你每次的改动，比如在第5行加了一个单词“Linux”，在第8行删了一个单词“Windows”。而图片、视频这些二进制文件，虽然也能由版本控制系统管理，但没法跟踪文件的变化，只能把二进制文件每次改动串起来，也就是只知道图片从100KB改成了120KB，但到底改了啥，版本控制系统不知道，也没法知道。
<br/>Microsoft的Word格式是二进制格式，因此，版本控制系统是没法跟踪Word文件的改动的。如果要真正使用版本控制系统，就要以纯文本方式编写文件。
<html><a style="color:red">注意：</a></html>
不要使用Windows自带的记事本编辑任何文本文件。原因是Microsoft开发记事本的团队使用了一个非常弱智的行为来保存UTF-8编码的文件，他们自作聪明地在每个文件开头添加了0xefbbbf（十六进制）的字符，你会遇到很多不可思议的问题，比如，网页第一行可能会显示一个“?”，明明正确的程序一编译就报语法错误，等等，都是由记事本的此行为带来的。下载Notepad++代替记事本，记得把Notepad++的默认编码设置为UTF-8 without BOM即可。
<br/>现在编写一个 `readme.txt` 文件：

```txt
Git is a version control system.
Git is free software.
```
一定要放到 `git file` 目录下（或子目录）。
<br/>把文件放到Git仓库只需要两步：
<br/>第一步，用`git add`告诉仓库，把文件添加到仓库。
```git
$ git add readme.txt
```
执行上面的命令，没有任何显示，这就对了，Unix的哲学是“没有消息就是好消息”，说明添加成功。
<br/>第二步，用命令 `git commit` 告诉Git，把文件提交到仓库。
```git
$ git commit -m "wrote a readme file"
[master (root-commit) eaadf4e] wrote a readme file
 1 file changed, 2 insertions(+)
 create mode 100644 readme.txt
```
`-m`后面是本次提交的说明，语法上可以任意输入，实际最好是描述本次提交，这样方便从历史记录中找到此次记录。
<br/>此命令成功后Git会显示，`1 file changed`：一个文件被改动（即刚添加的readme.txt）； `2 insertions(+)`：插入了两行内容（readme.txt有两行内容）。
<br/>为什么Git添加文件需要`add` `commit`两步呢，因为可以多次`add`不同文件，一次`commit`提交多个文件，比如：
```git
$ git add file1.txt
$ git add file2.txt file3.txt
$ git commit -m "add 3 files."
```
---






## 二、时光穿梭机

我们已经成功地添加并提交了一个readme.txt文件，现在，是时候继续工作了，于是，我们继续修改readme.txt文件，改成如下内容：
```txt
Git is a distributed version control system.
Git is free software.
```
运行 `git status`显示结果：
```
$ git status
On branch master
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

        modified:   readme.txt

no changes added to commit (use "git add" and/or "git commit -a")

```
`git status`命令可以让我们时刻掌握仓库当前的状态，上面的输出告诉我们`readme.txt`被修改过了，但还没有提交。
<br/>这时候就可以使用`git diff`命令来查看修改的内容：
```git
$ git diff
diff --git a/readme.txt b/readme.txt
index ba68144..66bbd58 100644
--- a/readme.txt
+++ b/readme.txt
@@ -1,2 +1,2 @@
- Git is a version control system.
+ Git is distributed a version control system.
  Git is free software.
\ No newline at end of file
```
结果是unix通用的diff格式，从上面的命令输出可以看到，在第一行添加了一个 `distributed`单词。
<br/>知道了对`readme.txt`做了什么修改之后，再提交到仓库就放心多了，提交修改和提交新文件是一样的两步，第一步是`git add`：
```
$ git add readme.txt
```
同样没有输出，在执行第二步之前，再运行一次`git status`看看当前仓库的状态：
```
$ git status
On branch master
Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)

        modified:   readme.txt

```
`git status`告诉我们将要被提交的修改包括`readme.txt`，下一步就可以放心的提交了。
```
$ git commit -m "add distributed"
[master a13932e] add distributed
 1 file changed, 1 insertion(+), 1 deletion(-)
```
提交之后再用 `git status`来查看仓库的当前状态：
```
$ git status
On branch master
nothing to commit, working tree clean
```
Git告诉我们当前没有需要提交的修改，而且工作树是干净的。



<br/>

### （一）版本回退

上面学会了修改文件，然后把修改提交到Git版本库，现在再做一次，修改`readme.txt`文件如下：
```txt
Git is a distributed version control system.
Git is free software distributed under the GPL.
```
然后提交：
```git
$ git add readme.txt
$ git commit -m "append GPL"
[master 82609ae] append GPL
 1 file changed, 1 insertion(+), 1 deletion(-)
```
像这样，你不断对文件进行修改，然后不断提交修改到版本库里，就好比玩RPG游戏时，每通过一关就会自动把游戏状态存盘，如果某一关没过去，你还可以选择读取前一关的状态。有些时候，在打Boss之前，你会手动存盘，以便万一打Boss失败了，可以从最近的地方重新开始。Git也是一样，每当你觉得文件修改到一定程度的时候，就可以“保存一个快照”，这个快照在Git中被称为`commit`。一旦你把文件改乱了，或者误删了文件，还可以从最近的一个`commit`恢复，然后继续工作，而不是把几个月的工作成果全部丢失。

现在回顾一下`readme.txt`文件有几个版本了：
<br/>版本一： wrote a readme file
```txt
Git is a version control system.
Git is free software.
```
版本二：add distributed
```txt
Git is a distributed version control system.
Git is free software.
```
版本三：append GPL
```
Git is a distributed version control system.
Git is free software distributed under the GPL.
```
在实际工作中，我们脑子里怎么可能记得一个几千行的文件每次都改了什么内容，不然要版本控制系统干什么。版本控制系统肯定有某个命令可以告诉我们历史记录，在Git中，我们用`git log`命令查看：
```
$ git log
commit 82609ae1d4a3ea533c583770c6238a2825337dec (HEAD -> master)
Author: Tintmonarch <sap_wxy@163.com>
Date:   Fri Mar 15 15:26:02 2019 +0800

    append GPL

commit a13932e1d90d946ad96ba132c28536c985c0a165
Author: Tintmonarch <sap_wxy@163.com>
Date:   Fri Mar 15 15:15:06 2019 +0800

    add distributed

commit 165fcf627904849a6accbbb1099652aaa57a2849
Author: Tintmonarch <sap_wxy@163.com>
Date:   Thu Mar 14 17:09:53 2019 +0800

    wrote a readme file

```
`git log`命令显示从最近到最远的提交日志，我们可以看到3次提交，最近的一次是`append GPL`，上一次是`add distributed`，最早的一次是`wrote a readme file`。
<br/>如果嫌输出信息太多，看得眼花缭乱的，可以试试加上`--pretty=oneline`参数：
```git
$ git log --pretty=oneline
82609ae1d4a3ea533c583770c6238a2825337dec (HEAD -> master) append GPL
a13932e1d90d946ad96ba132c28536c985c0a165 add distributed
165fcf627904849a6accbbb1099652aaa57a2849 wrote a readme file
```
每提交一个新版本，实际上Git就会把它们自动串成一条时间线。如果使用可视化工具查看Git历史，就可以更清楚地看到提交历史的时间线。

现在我们启动时光穿梭机，准备把`readme.txt`回退到上一个版本，也就是`add distributed`的那个版本，怎么做呢？
<br/>首先，Git必须知道当前版本是哪个版本，在Git中，用`HEAD`表示当前版本，也就是最新的提交`82609ae...`，上一个版本就是`HEAD^`，上上一个版本就是`HEAD^^`，当然往上100个版本写100个`^`比较容易数不过来，所以写成`HEAD~100`。
<br/>现在要把当前版本`append GPL`回退到上一个版本`add distributed`，就可以使用`git reset`命令：
```git
$ git reset --hard HEAD^
HEAD is now at a13932e add distributed
```
看一下`readme.txt`的内容被还原到`add distributed`：
```
$ cat readme.txt
 Git is distributed a version control system.
 Git is free software.
```
还可以继续回退到上一个版本`wrote a readme file`，不过我们先用`git log`再看看现在版本库的状态：
```
$ git log
commit a13932e1d90d946ad96ba132c28536c985c0a165 (HEAD -> master)
Author: Tintmonarch <sap_wxy@163.com>
Date:   Fri Mar 15 15:15:06 2019 +0800

    add distributed

commit 165fcf627904849a6accbbb1099652aaa57a2849
Author: Tintmonarch <sap_wxy@163.com>
Date:   Thu Mar 14 17:09:53 2019 +0800

    wrote a readme file
```
最新的那个版本`append GPL`已经看不到了！好比你从21世纪坐时光穿梭机来到了19世纪，想再回去已经回不去了，怎么办？
<br/>只要上面的命令行窗口还没有被关掉，你就可以顺着往上找啊找啊，找到那个`append GPL`的`commit id`是`82609ae...`，于是就可以指定回到未来的某个版本：
```git
$ git reset --hard 82609ae
HEAD is now at 82609ae append GPL

```
版本号没必要写全，前几位就可以了，Git会自动去找。当然也不能只写前一两位，因为Git可能会找到多个版本号，就无法确定是哪一个了。
<br/>再看一下文件内容：
```git
$ cat readme.txt
 Git is distributed a version control system.
 Git is free software distributed under the GPL.
```
果然又回到了`append GPL`版本。
<br/>Git的版本回退速度非常快，因为Git在内部有个指向当前版本的`HEAD`指针，当你回退版本的时候，Git仅仅是把`HEAD`从指向`append GPL`，改为指向`add distributed`,然后顺便把工作区的文件更新了。所以你让`HEAD`指向哪个版本号，你就把当前版本定位在哪。
<br/>万一找不到新版本的`commit id`怎么办？
<br/>当你用`$ git reset --hard HEAD^`回退到`add distributed`版本时，再想恢复到`append GPL`，就必须找到`append GPL`的`commit id`。Git中提供了命令`git reflog`来记录每一次命令：
```
$ git reflog
82609ae (HEAD -> master) HEAD@{0}: reset: moving to 82609ae
a13932e HEAD@{1}: reset: moving to HEAD^
82609ae (HEAD -> master) HEAD@{2}: commit: append GPL
a13932e HEAD@{3}: commit: add distributed
165fcf6 HEAD@{4}: commit (initial): wrote a readme file
```
从输出可知，`append GPL`的`commit id`是`82609ae`，现在，你又可以乘坐时光机回到未来了。
<br/>**小结**：
<br/>
- `HEAD`指向的版本就是当前版本，因此，Git允许我们在版本的历史之间穿梭，使用命令`git reset --hard commit_id`。
- 穿梭前，用`git log`可以查看提交历史，以便确定要回退到哪个版本。
- 要重返未来，用`git reflog`查看命令历史，以便确定要回到未来的哪个版本。


### （二）工作区和暂存区
Git和其他版本控制系统如SVN的一个不同之处就是有暂存区的概念。<html>
<h4 style="font-weight:normal">工作区（Working Directory）</h4>
</html>

比如我的 `git file` 文件夹就是一个工作区：
<html><h4 style="font-weight:normal">版本库（Repository）</h4></html>

工作区有一个隐藏目录`.git`，这个不算工作区，而是Git的版本库。
Git版本库中存了很多东西，其中最重要的是 称为stage（或index）的暂存区，还有Git为我们创建的第一个分支`master`，以及指向`master`的一个指针叫`HEAD`。

<html><img src="https://cdn.liaoxuefeng.com/cdn/files/attachments/001384907702917346729e9afbf4127b6dfbae9207af016000/0"/></html>

把文件添加到Git版本库是分两步进行的：
<br/>第一步`git add`把文件添加进去，实际上就是把文件添加到暂存区；
<br/>第二部`git commit`提交更改，实际上就是把暂存区的所有内容提交到当前分支。
<br/>因为创建版本库时，Git帮我们创建了唯一一个`master`分支，所以现在`git commit`就是往`master`分支上提交更改。
<br/>可以简单理解为，需要提交的文件通通放到暂存区，然后，一次性提交暂存区的所有更改。
<br/>实践一下：先对`readme.txt`修改一下，
```
Git is a distributed version control system.
Git is free software distributed under the GPL.
Git has a mutable index called stage.
```
再新建一个`LICENSE`文件。
<br>先用`git status`查看一下状态：
```git
$ git status
On branch master
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

        modified:   readme.txt

Untracked files:
  (use "git add <file>..." to include in what will be committed)

        LICENSE.txt

no changes added to commit (use "git add" and/or "git commit -a")
```
可以清楚的看到，Git告诉我们 `readme.txt`被修改了，而`LICENSE`从来没有添加过，所以状态是`untracked`。
<br/>现在使用两次`git add`命令把两个文件都添加，再`git status`查看状态：
```
$ git status
On branch master
Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)

        new file:   LICENSE.txt
        modified:   readme.txt
```
<html><img src="https://cdn.liaoxuefeng.com/cdn/files/attachments/001384907720458e56751df1c474485b697575073c40ae9000/0"/></html>

所以，`git add`命令实际上要把add的所有修改放到暂存区（stage），然后执行`git commit`就可以一次性把暂存区所有修改提交到分支。
```
$ git commit -m "understand how stage works"
[master 1f50969] understand how stage works
 2 files changed, 4 insertions(+), 1 deletion(-)
 create mode 100644 LICENSE.txt
```
一旦提交后，如果没有对工作区做任何修改，那么工作区就是`clean`的：
```
$ git status
On branch master
nothing to commit, working tree clean
```
<html><img src="https://cdn.liaoxuefeng.com/cdn/files/attachments/0013849077337835a877df2d26742b88dd7f56a6ace3ecf000/0"/></html>
















<br/>

### （三）管理修改
Git比其他版本控制系统做的优秀的地方是Git跟踪并管理的是修改而不是文件，什么是修改呢？新增一行，删除一行，更改了某些字符，删了一下新增一些，甚至新建一个文件这些都是修改。
<br>实践一下，第一步对`readme.txt`做一个修改，如新增一行：
```txt
Git is a distributed version control system.
Git is free software distributed under the GPL.
Git has a mutable index called stage.
Git tracks changes.
```
然后执行`git add`命令，
```
$ git add readme.txt
$ git status
On branch master
Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)

        modified:   readme.txt

```
然后再修改一下`readme.txt`，
```txt
Git is a distributed version control system.
Git is free software distributed under the GPL.
Git has a mutable index called stage.
Git tracks changes of files.
```
执行提交`git commit`，再查看状态`git status`：
```
$ git commit -m "git tracks changes"
[master 7d297b0] git tracks changes
 1 file changed, 2 insertions(+), 1 deletion(-)
```
```
$ git status
On branch master
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

        modified:   readme.txt

no changes added to commit (use "git add" and/or "git commit -a")

```
可以看到这次并没有像以前一样`clean`，第二次的修改并没有被提交。
<br/>我们回顾一下操作过程：
<br/> 第一次修改 -> `git add` -> 第二次修改 -> `git commit` 
<br/>前面讲了，Git管理的是修改，当你用`git add`命令后，工作区的第一次修改被放入暂存区，但是工作区的第二次修改并没有放入暂存区，所以再`git commit`只负责把暂存区的修改提交了，也就是第一次修改被提交了，第二次修改并不会被提交。
<br/> 这也证明了Git管理的是‘修改’，而不是文件。
<br/> 提交后可以用`git diff HEAD --readme.txt`命令来查看工作区和版本库里最新版的区别：
```git
$ git diff HEAD -- readme.txt
diff --git a/readme.txt b/readme.txt
index cd55b2d..d077a0d 100644
--- a/readme.txt
+++ b/readme.txt
@@ -1,4 +1,4 @@
  Git is distributed a version control system.
  Git is free software distributed under the GPL.
  Git has a mutable index called stage.
- Git tracks changes.
\ No newline at end of file
+ Git tracks changes of files.
\ No newline at end of file
```
可以清楚的看到第二次修改并没有被修改。
<br/>怎么提交第二次修改呢？ 可以再来一次两步走 `git add` `git commit`。也可以第一次修改之后先不要 `git add`， 两次修改之后在一起add一起commit。
<br/> 第一次修改 -> `git add` -> 第二次修改 -> `git add` -> `git commit` 
<br/>或
<br/> 第一次修改 -> 第二次修改 -> `git add` -> `git commit`





### （四）撤消修改
假如（万一）不小心在文件中添加了一行不应该有的内容：
```txt
$ cat readme.txt
 Git is distributed a version control system.
 Git is free software distributed under the GPL.
 Git has a mutable index called stage.
 Git tracks changes of files.
 My stupid girl still prefers SVN.

```
在提交之前，你发现了stupid girl 可能会让你跪键盘这个问题。
<br/> 既然发现的及时，那么很容易修改掉就好了。
<br/> 可以删掉最后一行，手动把文件恢复到原来的样子。但是如果用`git status`来查看一下状态：
```
$ git status
On branch master
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

        modified:   readme.txt

no changes added to commit (use "git add" and/or "git commit -a")

```
Git告诉我们， `git checkout -- <file>`丢弃工作区的修改。意思就是把工作区的修改全部撤消，那么会有两种情况：
<br/>一种是`<file>`自修改后没有`add`到暂存区，现在，撤消修改后就回到和版本库一样的状态；
<br/>一种是`<file>`已经`add`到暂存区，又做了修改，此时，撤消修改就回到了暂存区的状态。
<br/>所以就是让`<file>`回到最近一次`git add` 或 `git commit`的状态。
<br/>执行一下退回：看一下文件状态，和Git状态
```
$ git checkout -- readme.txt
```
```txt
$ cat readme.txt
 Git is distributed a version control system.
 Git is free software distributed under the GPL.
 Git has a mutable index called stage.
 Git tracks changes.
```
```
$ git status
On branch master
nothing to commit, working tree clean
```
文件内容还原了，而且工作区也`clean`了。

假设（万万一）不仅修改了，还`git add`到暂存区了，
```
$ cat readme.txt
 Git is distributed a version control system.
 Git is free software distributed under the GPL.
 Git has a mutable index called stage.
 Git tracks changes.
 My stupid girl still prefers SVN.
 
$ git add readme.txt
```
不过在commit之前，发现了这个问题，用`git status`查看一下，修改只是到了暂存区，还没有提交到版本库：
```
$ git status
On branch master
Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)

        modified:   readme.txt

```
Git又告诉我们，用命令 `git reset HEAD <file>`可以把暂存区的修改撤销掉（unstage），重新放回工作区：
```
$ git reset HEAD readme.txt
Unstaged changes after reset:
M       readme.txt
```
`git reset`既可以回退版本，又可以把暂存区的修改回退到工作区。 `HEAD`表示最新版本。
<br/>再用`git status`查看一下，现在暂存区是干净的，工作区有修改：
```
$ git status
On branch master
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

        modified:   readme.txt

no changes added to commit (use "git add" and/or "git commit -a")
```
再使用刚才的忽略工作区修改：
```
$ git checkout -- readme.txt
```
```
$ git status
On branch master
nothing to commit, working tree clean
```
啊，the world is clean.


<br/>假设（万万万万万一），不就修改错了东西，还从工作区添加到暂存区，还从暂存区提交到版本库了，这时候怎么办呢？ 可以坐时光穿梭机回到过去，回到上个版本。 但是！！这是有条件的，就是还没有把自己的本地版本库推送（push）到远程。一旦把错误的信息推送到远程版本库，就GG思密达了。

小结：
<br/>scene 1：当改乱了工作区某文件的内容时，想直接丢弃到此次修改，用命令 `git checkout -- <file>`。
<br/>scene 2：当不仅改乱了工作区某文件的内容，还添加到了暂存区，想丢弃修改，两步走：第一步`git reset HEAD <file>`，这样就回到了scene 1，第二步按scene 1的操作来。
<br/>scene 3：如果已经提交了不应该的修改到了本地版本库，还没有push到远程，可以用时光机回溯到旧版本。



### （五）删除文件
在Git中，删除文件也是一个修改操作，实践一下：先添加一新文件到版本库：
```
$ git add textdel.txt

$ git commit -m "add test.txt"
[master 46ebbc1] add test.txt
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 textdel.txt
```
一般情况下，通常直接在文件管理器中直接删掉文件，或者用`rm`命令把文件删掉：
```
$ rm textdel.txt
```
这个时候，Git知道我们删除了文件，因此版本库和工作区不一致了，用`git status`可以清楚的看到Git提示我们哪些文件被删除了：
```
$ git status
On branch master
Changes not staged for commit:
  (use "git add/rm <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

        deleted:    textdel.txt

no changes added to commit (use "git add" and/or "git commit -a")

```
现在有两个选择，一是确实要从版本库删掉次文件，那就`git rm <file>`删掉（此时用add效果一样），`git commit`提交：
```
$ git rm textdel.txt
rm 'textdel.txt'
```
```
$ git commit -m "remove textdel.txt"
[master 49a0c20] remove textdel.txt
 1 file changed, 0 insertions(+), 0 deletions(-)
 delete mode 100644 textdel.txt
```
这样就从版本库删除了。
<br/>另一种情况是删除错了，因为此时版本库中还有的，所以可以checkout一下：
```
$ git checkout -- textdel.txt
```
★`git checkout`的功能其实就是把版本库中的最新版本拿出来覆盖掉工作区的版本。



<hr/>

## 三、远程仓库
到目前为止，我们已经掌握了如何在Git仓库中对一个文件进行时光穿梭，再也不用担心文件备份与丢失的问题了。
<br>Git是分布式版本控制系统，同一个Git仓库，可以分布到不同的机器上。怎么分布呢？最早，肯定只有一台机器有一个原始版本库，此后，别的机器可以“克隆”这个原始版本库，而且每台机器的版本库其实都是一样的，并没有主次之分。
<br/>实际情况往往是这样，找一台电脑充当服务器的角色，每天24小时开机，其他每个人都从这个“服务器”仓库克隆一份到自己的电脑上，并且各自把各自的提交推送到服务器仓库里，也从服务器仓库中拉取别人的提交。
<br/>有个叫GitHub的神奇的网站，从名字就可以看出，这个网站就是提供Git仓库托管服务的，所以，只要注册一个GitHub账号，就可以免费获得Git远程仓库。
<br/>在继续学习之前，先自行申请一个[github](https://github.com/)的账号。由于本地Git仓库和github仓库之间的传输是通过SSH加密的，所以需要一个设置：
<br/>第一步：创建SSH Key，先在用户主目录（比如administrator）下，看看有没有.ssh目录，如果有，看看里面有没有`id_rsa`和`id_rsa.pub`这两个文件，如果已经有了，这一步跳过。如果没有打开Git bash，创建SSH Key：
```
$ ssh-keygen -t rsa -C "youremail@example.com"
```
把邮件地址换成自己的，然后一路回车，默认即可，这个key也不是机密，无需设置密码。
<br/>如果一切顺利，就可以在用户主目录找到.ssh目录，里面有`id_rsa`和`id_rsa.pub`这两个文件，这两个就是SSH Key的密匙对，`id_rsa`是私匙，不可以泄漏，`id_rsa.pub`是公匙，就是给别人用的。
<br/>第二步：登录github，点击头像下拉框打开“settings”，“SSH and GPG Keys”界面：
然后，点“new SSH Key”，填自定义title，在Key文本框中粘贴`id_rsa.pub`文件中所有内容。
<br/>为什么GitHub需要SSH Key呢？因为GitHub需要识别出你推送的提交确实是你推送的，而不是别人冒充的，而Git支持SSH协议，所以，GitHub只要知道了你的公钥，就可以确认只有你自己才能推送。
<br/>当然，GitHub允许你添加多个Key。假定你有若干电脑，你一会儿在公司提交，一会儿在家里提交，只要把每台电脑的Key都添加到GitHub，就可以在每台电脑上往GitHub推送了。
<br/>最后友情提示，在Git上托管的仓库分为 public和private 两种方式，顾名思义，public仓库可以被任何人看见，只能被自己修改。所以不应该把敏感信息放到public库中。
而private库目前的政策是只能有三个开发者，想更多的人加入需要升级为高级用户~~
<br/>如果你不想让别人看到Git库，有两个办法，一个把GitHub把公开的仓库变成私有的，这样别人就看不见了（不可读更不可写）。另一个办法是自己动手，搭一个Git服务器，因为是你自己的Git服务器，所以别人也是看不见的。这个方法我们后面会讲到的，相当简单，公司内部开发必备。



### （一）添加远程库
现在的情景是，你已经在本地创建了一个Git仓库后，又想在GitHub创建一个Git仓库，并且让这两个仓库进行远程同步，这样，GitHub上的仓库既可以作为备份，又可以让其他人通过该仓库来协作，真是一举多得。
<br/>首先登录github，然后在右上角找到+号下拉框里“new repository”按钮，新建一个仓库：
<br/>在“Repository name”中填入 gitfile，其他保持默认设置，点击“create repository”按钮，就成功创建了一个仓库。
<br/>此时github上的Gitfile这个仓库还是空的，github提供了如何把本地仓库与此仓库关联，以及如何把本地仓库的内容推送到github：
```
git remote add origin git@github.com:Tinymonarch/Gitfile.git
```
添加之后，远程库的名字就是`origin`，这是Git的默认叫法，也可以改成别的，但是`origin`这个名字一看就知道是远程库。
<br/>下一步就可以把本地库的所有内容推送到远程库上了：
```
$ git push -u origin master
Enumerating objects: 20, done.
Counting objects: 100% (20/20), done.
Delta compression using up to 8 threads.
Compressing objects: 100% (15/15), done.
Writing objects: 100% (20/20), 1.67 KiB | 428.00 KiB/s, done.
Total 20 (delta 4), reused 0 (delta 0)
remote: Resolving deltas: 100% (4/4), done.
To github.com:Tinymonarch/Gitfile.git
 * [new branch]      master -> master
Branch 'master' set up to track remote branch 'master' from 'origin'.
```
把本地库的内容推送到远程，用`git push`命令，实际上是把当前分支`master`推送到远程。
<br/>由于远程库是空的，我们第一次推送的`master`分支时，加上了`-u`参数，Git不但会把本地的`master`分支内容推送到远程的`master`分支，还会把本地的`master`分支和远程的`master`分支关联起来，在以后的推送或者拉取的时候就可以简化命令。
<br/>推送成功后，就可以在github页面看到远程库的内容和本地库同步了。
<br/>从现在起，只要本地库做了提交，就可以通过命令：
```
git push origin master
```
把本地`master`分支的最新修改推送至github，现在就拥有了真正的分布式版本库！！！

<html>
<h4 style="font-weight:normal">SSH警告：</h4>
</html>
当第一次使用Git的`clone`或者`push`命令连接github时，会得到一个警告：

```git
The authenticity of host 'github.com (xx.xx.xx.xx)' can't be established.
RSA key fingerprint is xx.xx.xx.xx.xx.
Are you sure you want to continue connecting (yes/no)?
```
这是因为Git使用SSH连接，而SSH连接在第一次验证GitHub服务器的Key时，需要你确认GitHub的Key的指纹信息是否真的来自GitHub的服务器，输入yes回车即可。
<br/>Git会输出一个警告，告诉你已经把GitHub的Key添加到本机的一个信任列表里了：
```
Warning: Permanently added 'github.com' (RSA) to the list of known hosts.
```
这个警告只会出现一次，后面的操作就不会有任何警告了。
<br/>如果你实在担心有人冒充GitHub服务器，输入yes前可以对照GitHub的RSA Key的指纹信息是否与SSH连接给出的一致。
<br/><br/>小结：
- 要关联一个远程库，使用命令`git remote add origin git@server-name:path/repo-name.git`；
- 关联后，用命令`git push -u origin master`第一次推送本地master分支的所有内容到远程；
- 此后，每次需要推送本地提交内容到远程，就用`git push origin master`。

<br/>分布式版本系统的最大好处之一是在本地工作完全不需要考虑远程库的存在，也就是有没有联网都可以正常工作，而SVN在没有联网的时候是拒绝干活的！当有网络的时候，再把本地提交推送一下就完成了同步，真是太方便了！








### （二）从远程库克隆

上面的模式是先有本地库，后有远程库，如何关联远程库。
<br/>现在假设从零开发，最好的方式其实是先创建远程库，然后从远程库克隆。
<br/>首先，登录github，创建一个新的仓库，名字叫做 `remotegit`，
<br/>勾选了 `initialize this repository with a README`，这样github会为我们创建一个`READ.md`文件。创建完毕后，可以看到`README.md`文件。
<br/>现在，远程库已经准备好了，下一步是用命令`git clone`克隆一个本地库：
```
$ git clone git@github.com:Tinymonarch/remotegit.git
Cloning into 'remotegit'...
Warning: Permanently added the RSA host key for IP address '52.74.223.119' to the list of known hosts.
remote: Enumerating objects: 3, done.
remote: Counting objects: 100% (3/3), done.
remote: Total 3 (delta 0), reused 0 (delta 0), pack-reused 0
Receiving objects: 100% (3/3), done.
```
```
$ cd remotegit/
$ ls
README.md
```
如果有多个人协作开发，那么每个人各自从远程克隆一份就可以了。
<br/>github给出的地址有两种，还可以用`https://github.com/Tinymonarch/remotegit.git`这样的，实际上，Git支持多种协议，默认的`git://`使用ssh，但也可以用https等其他协议。
<br/>使用https除了速度慢以外，每次推送都得输入口令，但是在某些只开放http端口的公司 内部就无法用ssh协议只能用http了。





## 四、分支管理

分支的英文叫 branch，想想看一棵树，有很多知，最后都汇总到了一个树干上。Git的分支也是这样的，每一个分支把自己的版本库推送到远程库。
<br/>分支在实际中有什么用呢？假设你准备开发一个新功能，但是需要两周才能完成，第一周你写了50%的代码，如果立刻提交，由于代码还没写完，不完整的代码库会导致别人不能干活了。如果等代码全部写完再一次提交，又存在丢失每天进度的巨大风险。
<br/>现在有了分支，就不用怕了。你创建了一个属于你自己的分支，别人看不到，还继续在原来的分支上正常工作，而你在自己的分支上干活，想提交就提交，直到开发完毕后，再一次性合并到原来的分支上，这样，既安全，又不影响别人工作。
<br/>其他版本控制系统如SVN等都有分支管理，但是用过之后你会发现，这些版本控制系统创建和切换分支比蜗牛还慢，简直让人无法忍受，结果分支功能成了摆设，大家都不去用。
<br/>但Git的分支是与众不同的，无论创建、切换和删除分支，Git在1秒钟之内就能完成！无论你的版本库是1个文件还是1万个文件。


### （一）创建与合并分支
在版本回退里，我们已经知道，每次提交，Git都把它们串成一条时间线，这条时间线就是一个分支。截止到目前，只有一条时间线，在Git里，这个分支叫主分支，即`master`分支。`HEAD`严格来说不是指向提交，而是指向`master`，`master`才是指向提交的，所以，`HEAD`指向的就是当前分支。
<br/>一开始的时候，`master`分支是一条线，Git用`master`指向最新的提交，再用`HEAD`指向`master`，就能确定当前分支，以及当前分支的提交点：

<img src="https://cdn.liaoxuefeng.com/cdn/files/attachments/0013849087937492135fbf4bbd24dfcbc18349a8a59d36d000/0">

每次提交，`master`分支都会向前一步，这样随着不断提交，`master`分支线也越来越长。



当我们创建新的分支时，例如`dev`，Git新建了一个指针叫`dev`，指向`master`相同的提交，再把`HEAD`指向`dev`，就表示当前分支在`dev`上：


<img src="https://cdn.liaoxuefeng.com/cdn/files/attachments/001384908811773187a597e2d844eefb11f5cf5d56135ca000/0">

可见，Git创建一个分支很快，因为除了增加一个`dev`指针，改了`HEAD`的指向，工作区的文件没有任何变化。
<br/>从现在开始，对工作区的修改和提交就是针对`dev`分支了，比如新提交一次后，`dev`指针往前移动一步，而`master`指针不变：
<img src="https://cdn.liaoxuefeng.com/cdn/files/attachments/0013849088235627813efe7649b4f008900e5365bb72323000/0" />

假如我们在`dev上`的工作完成了，就可以把`de`v合并到`master`上。Git怎么合并呢？最简单的方法，就是直接把`master`指向`dev`的当前提交，就完成了合并：

<img src="https://cdn.liaoxuefeng.com/cdn/files/attachments/00138490883510324231a837e5d4aee844d3e4692ba50f5000/0" />

所以Git合并分支也很快！就改改指针，工作区内容也不变！
<br/>合并完分支后，甚至可以删除`dev`分支。删除`dev`分支就是把`dev`指针给删掉，删掉后，我们就剩下了一条`master`分支：

<img src="https://cdn.liaoxuefeng.com/cdn/files/attachments/001384908867187c83ca970bf0f46efa19badad99c40235000/0" />




下面实践一下：
<br/>   首先创建`dev`分支，然后切换到`dev`分支：
```
$ git checkout -b dev
Switched to a new branch 'dev'
```
`git checkout`命令加上`-b`参数表示创建并切换，相当于以下两条命令：
```
$ git branch dev
$ git checkout dev
Switched to branch 'dev'
```
然后用`git branch`查看当前分支：
```
$ git branch
* dev
  master
```
可见`git branch`命令会列出所有分支，当前分支前面会有一个`*`号。
然后我们在`dev`分支上做修改并提交，比如在`readme.txt`新加一行：
```
Creating a new branch is quick.
```
然后提交：
```
$ git add readme.txt
$ git commit -m "branch test"
[dev 91935db] branch test
 1 file changed, 2 insertions(+), 1 deletion(-)
 
```
现在，`dev`分支的工作完成了，我们就可以切回`master`分支：
```
$ git checkout master
Switched to branch 'master'
Your branch is up to date with 'origin/master'.
```
切换回`master`分支后，再查看一个`readme.txt`文件，刚才添加的内容不见了！因为那个提交是在`dev`分支上，而`master`分支此刻的提交点并没有变：

<img src="https://cdn.liaoxuefeng.com/cdn/files/attachments/001384908892295909f96758654469cad60dc50edfa9abd000/0" />

现在，我们把`dev`的提交合并到`master`分支上：
```
$ git merge dev
Updating 49a0c20..91935db
Fast-forward
 readme.txt | 3 ++-
 1 file changed, 2 insertions(+), 1 deletion(-)
```
`git merge`命令用于合并指定分支到当前分支。合并后，再查看`readme.txt`的内容，就可以看到，和`dev`分支的最新提交是完全一样的。
<br/>注意到上面的`Fast-forward`信息，Git告诉我们，这次合并是“快进模式”，也就是直接把`master`指向`dev`的当前提交，所以合并速度非常快。
<br/>当然，也不是每次合并都能`Fast-forward`，还有其他方式的合并。
<br/>合并完成后，就可以放心地删除`dev`分支了：
```
$ git branch -d dev
Deleted branch dev (was 91935db).
```
删除后，查看`branch`，就只剩下`master`分支了:
```
$ git branch
* master
```
因为创建、合并和删除分支非常快，所以Git鼓励你使用分支完成某个任务，合并后再删掉分支，这和直接在`master`分支上工作效果是一样的，但过程更安全。

小结：
<br/>Git鼓励大量使用分支：
- 查看分支：`git branch`
- 创建分支：`git branch <name>`
- 切换分支：`git checkout <name>`
- 创建+切换分支：`git checkout -b <name>`
- 合并某个分支到当前分支：`git merge <name>`
- 删除分支：`git branch -d <name>`






### （二）解决冲突：
合并分支往往不是一帆风顺的，总会有冲突出现：
<br/>准备新的分支`feature1`，继续分支开发：
```
$ git checkout -b feature1
Switched to a new branch 'feature1'
```
修改`readme.txt`的最后一行，改为：
```
Creating a new branch is quick AND simple.
```
在分支`feature1`上提交修改：
```
$ git add readme.txt

$ git commit -m "AND simple"
[feature1 008403d] AND simple
 1 file changed, 1 insertion(+), 1 deletion(-)
```
切换到`master`分支上：
```
$ git checkout master
Switched to branch 'master'
Your branch is ahead of 'origin/master' by 1 commit.
  (use "git push" to publish your local commits)

```
Git还会自动提示我们当前`master`分支比远程的`master`分支要超前一个提交。
<br/>在`master`分支上把`readme.txt`文件最后一行改为：
```
Creating a new branch is quick & simple.
```
提交：
```
$ git add readme.txt

$ git commit -m "& simple"
[master 8801b2f] & simple
 1 file changed, 1 insertion(+), 1 deletion(-)
```
现在，`master`分支和`feature1`分支各自都分别有了新的提交，变成了这样：

<img src="https://cdn.liaoxuefeng.com/cdn/files/attachments/001384909115478645b93e2b5ae4dc78da049a0d1704a41000/0"/>

这种情况下，Git无法执行“快速合并”，只能试图把各自的修改合并起来，但这种合并就可能会有冲突，试一下：
```
$ git merge feature1
Auto-merging readme.txt
CONFLICT (content): Merge conflict in readme.txt
Automatic merge failed; fix conflicts and then commit the result.
```
Git告诉我们，`readme.txt`文件存在冲突，必须手动解决冲突后再提交。
<br/>`git status`也可以告诉我们冲突的文件：
```
$ git status
On branch master
Your branch is ahead of 'origin/master' by 2 commits.
  (use "git push" to publish your local commits)

You have unmerged paths.
  (fix conflicts and run "git commit")
  (use "git merge --abort" to abort the merge)

Unmerged paths:
  (use "git add <file>..." to mark resolution)

        both modified:   readme.txt

no changes added to commit (use "git add" and/or "git commit -a")
```
我们可以直接查看`readme.txt`文件的内容：
```
$ cat readme.txt
 Git is distributed a version control system.
 Git is free software distributed under the GPL.
 Git has a mutable index called stage.
 Git tracks changes.
<<<<<<< HEAD
 Creating a new branch is quick & simple.
=======
 Creating a new branch is quick AND simple.
>>>>>>> feature1
```
Git用`<<<<<<<`，`=======`，`>>>>>>>`标记出不同分支的内容，我们修改如下后保存：
```
 Creating a new branch is quick and simple.
```
再次提交之后，冲突解决。
```
$ git add readme.txt
$ git commit -m "conflict fixed"
[master 1ffc482] conflict fixed
```
现在`master`分支和`feature1`分支变成了如下图所示：
<img src="https://cdn.liaoxuefeng.com/cdn/files/attachments/00138490913052149c4b2cd9702422aa387ac024943921b000/0" />

用带参数的`git log`可以看到分支的合并情况：
```
$ git log --graph --pretty=oneline --abbrev-commit
*   1ffc482 (HEAD -> master) conflict fixed
|\
| * 008403d (feature1) AND simple
* | 8801b2f & simple
|/
* 91935db branch test
* 49a0c20 (origin/master) remove textdel.txt
* 46ebbc1 add test.txt
* 7d297b0 git tracks changes
* 1f50969 understand how stage works
* 82609ae append GPL
* a13932e add distributed
* 165fcf6 wrote a readme file

```

最后删除`feature1`分支，工作完成。
```
$ git branch -d feature1
Deleted branch feature1 (was 008403d).
```

小结：
<br/>当Git无法自动合并分支时，就必须先手动解决冲突。解决冲突后，再提交一次，合并完成。
<br/>解决冲突其实就是把Git合并失败的文件手动编辑为我们想要的内容，再提交。
<br/>用`git log --graph`可以查看分支合并图。


### （三）分支管理策略

通常合并分支时，如果可以，Git会用`Fast forward`模式，但这种模式下，删除分支后，会丢掉分支信息。
<br/>如果要强制禁用`Fast forward`模式，Git就会在merge的时候生成一个新的commit，这样从分支log上就能看到分支信息。
<br/>下面实践一下`git log --no-ff`

首先创建并切换`dev`分支：
```
$ git checkout -b dev
Switched to a new branch 'dev'
```
修改`readme.txt`文件，并提交：
```
$ git add readme.txt

$ git commit -m "add merge"
[dev feb2f15] add merge
 1 file changed, 1 insertion(+)
```

现在切换回`master`分支：（提示有领先远程库4个提交）
```
$ git checkout master
Switched to branch 'master'
Your branch is ahead of 'origin/master' by 4 commits.
  (use "git push" to publish your local commits)
```

准备合并`dev`分支，请注意`--no-ff`参数，表示禁用`Fast forward`:
```
$ git merge --no-ff -m "merge with no-ff" dev
Merge made by the 'recursive' strategy.
 readme.txt | 1 +
 1 file changed, 1 insertion(+)
```

因为本次合并会创建一个提交，所以我们加上`-m`参数，把commit描述写进去。
合并后，再用`git log`查看分支历史：
```
$ git log --graph --pretty=oneline --abbrev-commit
*   913e035 (HEAD -> master) merge with no-ff
|\
| * feb2f15 (dev) add merge
|/
*   1ffc482 conflict fixed
...
```

可以看到，不使用`Fast forward`模式，merge之后就像这样：
<img src="https://cdn.liaoxuefeng.com/cdn/files/attachments/001384909222841acf964ec9e6a4629a35a7a30588281bb000/0"/>

在实际开发中，我们应该安装几个基本原则来进行分支管理：
<br/>首先，`master`分支应该是非常稳定的，也就是仅用来发布新版本，平时不应该在上面开发；
<br/>开发都在`dev`分支上，也就是说`dev`分支是不稳定的，到某个时候，比如1.0版本发布时，再把`dev`分支合并到`master`上，在`master`分支上发布1.0版本；
<br/>你和你的团队每个人都在`dev`分支上开发，每个人都有自己的分支，时不时的往dev分支上合并就可以了。
<br/>所以团队合作看起来就是这样的：
<img src="https://cdn.liaoxuefeng.com/cdn/files/attachments/001384909239390d355eb07d9d64305b6322aaf4edac1e3000/0" />

总结一下，Git分支十分强大，在团队开发时应灵活运用。
<br/>合并分支时，加上`--no-ff`参数可以用普通模式合并，合并后可以通过`git log`来查看历史，能看出来曾经做过合并，而`Fast forward`模式合并就看不出来曾经做过合并。
















### （四）bug分支（保存现场）
软件开发中，bug就像家常便饭一样。有了bug就需要修复，在Git中，由于分支是如此的强大，所以，每个bug都可以通过一个新的临时分支来修复，修复后，合并分支，然后将临时分支删除。
<br/>当你接到一个修复一个代号101的bug的任务时，很自然地，你想创建一个分支`issue-101`来修复它，但是，等等，当前正在`dev`上进行的工作还没有提交：
```
$ git status
On branch dev
Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)

        new file:   hello.py

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

        modified:   readme.txt

```
并不是你不想提交，而是工作只进行到一半，还没法提交，预计完成还需1天时间。但是，必须在两个小时内修复该bug，怎么办？
<br/>幸好，Git还提供了一个`stash`功能，可以把当前工作现场“储藏”起来，等以后恢复现场后继续工作：
```
$ git stash
Saved working directory and index state WIP on dev: feb2f15 add merge
```
现在，用`git status`查看工作区，就是干净的（除非有没有被Git管理的文件），因此可以放心地创建分支来修复bug。

<br/>首先确定要在哪个分支上修复bug，假定需要在`master`分支上修复，就从`master`创建临时分支：

```
$ git checkout master
Switched to branch 'master'
Your branch is ahead of 'origin/master' by 6 commits.
  (use "git push" to publish your local commits)

$ git checkout -b issue-101
Switched to a new branch 'issue-101'
```
现在修复bug，需要把“Git is free software ...”改为“Git is a free software ...”，然后提交：
```
$ git add readme.txt

$ git commit -m "fix bug 101"
[issue-101 489bbd9] fix bug 101
 1 file changed, 1 insertion(+), 1 deletion(-)
```

修复完成后，切换到`master`分支，并完成合并，最后删除`issue-101`分支：
```
$ git checkout master
Switched to branch 'master'
Your branch is ahead of 'origin/master' by 6 commits.
  (use "git push" to publish your local commits)

$ git merge --no-ff -m "merged bug fix 101" issue-101
Merge made by the 'recursive' strategy.
 readme.txt | 2 +-
 1 file changed, 1 insertion(+), 1 deletion(-)
```

太棒了，原计划两个小时的bug修复只花了5分钟！现在，是时候接着回到`dev`分支干活了:
```
$ git checkout dev
Switched to branch 'dev'

$ git status
On branch dev
nothing to commit, working tree clean
```
工作区是干净的，刚才的工作现场存到哪去了？用git stash list命令看看：
```
$ git stash list
stash@{0}: WIP on dev: feb2f15 add merge
```
工作现场还在，Git把stash内容存在某个地方了，但是需要恢复一下，有两个办法：
<br/>一是用`git stash apply`恢复，但是恢复后，`stash`内容并不删除，你需要用`git stash drop`来删除；
<br/>另一种方式是用`git stash pop`，恢复的同时把`stash`内容也删了：
```
$ git stash pop
On branch dev
Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)

        new file:   hello.py

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

        modified:   readme.txt

Dropped refs/stash@{0} (1ea9eff5e71a673f79cb748e90f0d80c6b8479df)
```
再用`git stash list`查看，就看不到任何`stash`内容了：
```
$ git stash list
```
你可以多次`stash`，恢复的时候，先用`git stash list`查看，然后恢复指定的`stash`，用命令：
```
$ git stash apply stash@{0}
```
**小结：**
<br/>修复bug时，我们会通过创建新的bug分支进行修复，然后合并，最后删除；
<br/>当手头工作没有完成时，先把工作现场`git stash`一下，然后去修复`bug`，修复后，再`git stash pop` =`git stash apply <stash@{0}>`+`git stash drop <stash@{0}>`，回到工作现场。





### （五）Feature分支

软件开发中，总有无穷无尽的新的功能要不断添加进来。
<br/>添加一个新功能时，你肯定不希望因为一些实验性质的代码，把主分支搞乱了，所以，每添加一个新功能，最好新建一个`feature`分支，在上面开发，完成后，合并，最后，删除该`feature`分支。
<br/>现在，你终于接到了一个新任务：开发代号为`Vulcan`的新功能，该功能计划用于下一代星际飞船。
<br/>于是准备开发：
```
$ git checkout -b feature-vulcan
Switched to a new branch 'feature-vulcan'
```
很快开发完了：
```
$ git add vulcan.py

$ git commit -m "add feature vulcan"
[feature-vulcan 81df40d] add feature vulcan
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 vulcan.py
```

切回`dev`，准备合并：
```
$ git checkout dev
Switched to branch 'dev'
```
一切顺利的话，feature分支和bug分支是类似的，合并，然后删除。
<br/>但是！
<br/>就在此时，接到上级命令，因经费不足，新功能必须取消！
<br/>虽然白干了，但是这个包含机密资料的分支还是必须就地销毁：
```
$ git branch -d feature-vulcan
error: The branch 'feature-vulcan' is not fully merged.
If you are sure you want to delete it, run 'git branch -D feature-vulcan'.
```
销毁失败。Git友情提醒，`feature-vulcan`分支还没有被合并，如果删除，将丢失掉修改，如果要强行删除，需要使用大写的`-D`参数。。
<br/>现在我们强行删除：
```
$ git branch -D feature-vulcan
Deleted branch feature-vulcan (was 81df40d).
```

终于删除成功了！

**小结：**
<br/>开发一个新feature，最好新建一个分支；
<br/>如果要丢弃一个没有被合并过的分支，需要用`-D`参数强行删除。



### （六）多人协作

当你从远程仓库克隆时，实际上Git自动把本地的`master`分支和远程的`master`分支对应起来了，并且，远程仓库的默认名称是`origin`。
<br/>要查看远程库的信息，用`git remote`：
```
$ git remote
origin
```
还可以用`-v`参数显示详细信息：
```
$ git remote -v
origin  git@github.com:Tinymonarch/Gitfile.git (fetch)
origin  git@github.com:Tinymonarch/Gitfile.git (push)
```
上面显示了可以抓取和推送的`origin`的地址。如果没有推送权限，就看不到`push`的地址。

<html><h4 style="font-weight:normal">推送分支</h4></html>
推送分支，就是把该分支上的所有本地提交推送到远程库。推送时，要指定本地分支，这样，Git就会把该分支推送到远程库对应的远程分支上：

```
$ git push origin master
```
如果要推送其他分支，改成 `$ git push origin dev`即可。
<br/>但是，并不是一定要把本地分支推送远程：
 - `master`分支是主分支，因此要时刻与远程同步。
 - `dev`分支是开发分支，团队所有成员都需要在上面工作，所以也需与远程同步。
 - bug分支只用于在本地修复bug，就没必要推送到远程，除非需要公开bug修复历史。
 - feature分支是否推送远程，取决于是否和别人协同开发。 

<br/>总之，在Git中，分支完全可以在本地自己玩，是否推送远程，视情况而定。




<html><h4 style="font-weight:normal">抓取分支</h4></html>
多人协作时，大家都会往`master`和`dev`分支上推送各自的修改。
<br/>现在，模拟一个你的小伙伴，可以在另一台电脑（注意要把SSH Key添加到GitHub）或者同一台电脑的另一个目录下克隆：

```
$ git clone git@github.com:Tinymonarch/Gitfile.git
Cloning into 'Gitfile'...
remote: Enumerating objects: 20, done.
remote: Counting objects: 100% (20/20), done.
remote: Compressing objects: 100% (11/11), done.
Receiving objects: 100% (20/20), done.
Resolving deltas: 100% (4/4), done.
remote: Total 20 (delta 4), reused 20 (delta 4), pack-reused 0
```
当小伙伴从远程库clone时，默认情况下，你的小伙伴只能看见本地的`master`分支，用`git status`查看一下即可：
```
$ git branch
* master
```

现在小伙伴要在`dev`分支上开发，就必须创建远程`origin`的`dev`分支到本地，于是他用这个命令创建本地`dev`分支：

```
$ git checkout -b dev origin/dev
Switched to a new branch 'dev'
Branch 'dev' set up to track remote branch 'dev' from 'origin'.
```

现在他就可以在`dev`上继续修改，然后时不时的提交`dev`分支到远程：

```
$ git add env.txt

$ git commit -m "add env"
[dev 99207a9] add env
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 env.txt

$ git push origin dev
Enumerating objects: 3, done.
Counting objects: 100% (3/3), done.
Delta compression using up to 8 threads.
Compressing objects: 100% (2/2), done.
Writing objects: 100% (2/2), 303 bytes | 303.00 KiB/s, done.
Total 2 (delta 0), reused 0 (delta 0)
To github.com:Tinymonarch/Gitfile.git
   f072ad2..99207a9  dev -> dev
```


<br/>你的小伙伴已经向`origin/dev`分支推送了他的提交，而碰巧你也对同样的文件做了修改，并视图推送：
```
$ cat env.txt
env

$ git add env.txt

$ git commit -m "add new env"
[dev da54388] add new env
 1 file changed, 1 insertion(+)
 create mode 100644 env.txt
 
$ git push origin dev
To github.com:Tinymonarch/Gitfile.git
 ! [rejected]        dev -> dev (fetch first)
error: failed to push some refs to 'git@github.com:Tinymonarch/Gitfile.git'
hint: Updates were rejected because the remote contains work that you do
hint: not have locally. This is usually caused by another repository pushing
hint: to the same ref. You may want to first integrate the remote changes
hint: (e.g., 'git pull ...') before pushing again.
hint: See the 'Note about fast-forwards' in 'git push --help' for details.

```
推送失败，因为小伙伴的最新提交和你试图推送的提交有冲突，解决办法也很简单，Git提示我们，先用`git pull`把最新的提交从`origin/dev`抓下来，然后在本地合并，解决冲突，再推送：
```
$ git pull
There is no tracking information for the current branch.
Please specify which branch you want to merge with.
See git-pull(1) for details.

    git pull <remote> <branch>

If you wish to set tracking information for this branch you can do so with:

    git branch --set-upstream-to=origin/<branch> dev

```
`git pull`也失败了，因为没有指定本地`dev`和远程`dev`分支的连接，根据提示，设置`dev`和`origin/dev`的链接：
```
$ git branch --set-upstream-to=origin/dev dev
Branch 'dev' set up to track remote branch 'dev' from 'origin'.
```
再`git pull`:
```
$ git pull
Auto-merging env.txt
Merge made by the 'recursive' strategy.
```
这次`git pull`成功，但是合并会有冲突，需要手动解决，解决的方法和以前的办法一样。解决后，再提交，再推送：
```
$ git commit -m "fix env conflict"
[dev aae9a88] fix env conflict

$ git push origin dev
Enumerating objects: 10, done.
Counting objects: 100% (10/10), done.
Delta compression using up to 8 threads.
Compressing objects: 100% (5/5), done.
Writing objects: 100% (7/7), 644 bytes | 322.00 KiB/s, done.
Total 7 (delta 3), reused 0 (delta 0)
remote: Resolving deltas: 100% (3/3), completed with 1 local object.
To github.com:Tinymonarch/Gitfile.git
   99207a9..aae9a88  dev -> dev
```

因此，多人协作的工作模式往往是这样：

 1.  首先试图用 `git push origin <branch-name>`推送自己的修改；
 2.  如果推送失败，则因为远程分支比你本地的更新，需要先`git pull`试图合并；
 3.  如果合并有冲突，则解决冲突，并在本地提交；
 4.  没有冲突或者解决冲突后，再用`git push origin <branch-name>`就能推送成功。

<br/>如果`git pull`提示`no tracking information`，则说明本地分支与远程分支的链接没有建立，用命令`git branch --set-upstream-to <branch-name> origin/<branch-name>` 。
<br/>这就是多人工作的模式，一旦熟悉了就非常简单。

**小结**
- 查看远程库信息， `git remote -v`
- 本地新建的分支如果不push到远程，别人是不可见的；
- 从本地推送分支，使用`git push origin <branch-name>`，如果推送失败，用`git pull`抓取远程的新提交；
- 在本地创建和远程对应的分支，`git branch -b <branch-name> origin/<branch-name>`，本地与远程分支名称最好一致；
- 建立本地与远程分支的链接， `git branch --set-upstream-to <branch-name> origin/<branch-name>`；
- 从远程抓取分支，使用`git pull`，如果有冲突，先处理冲突。



### （七）Rebase

上一小节我们看到了，多人在同一个分支上协作时，容易出现冲突。即使没有冲突，后push的人也得先pull，在本地合并，再push才能成功。
<br/>每次合并后再push，分支就变成了这样：
```
$ git log --graph --pretty=oneline --abbrev-commit
*   ee40115 (HEAD -> dev, origin/dev) Merge branch 'dev' of github.com:Tinymonarch/Gitfile into dev
|\
| *   d16f08a Merge branch 'dev' of github.com:Tinymonarch/Gitfile into dev
| |\
| * | cb0f788 add wxy1
* | | ce47af6 add wxy2
| |/
|/|
* |   7affa1c (origin/master, master) Merge branch 'dev'
|\ \
| |/
| * aae9a88 fix env conflict
| *   df2e086 Merge branch 'dev' of github.com:Tinymonarch/Gitfile into dev
| |\
| | * 99207a9 add env
| * | da54388 add new env
| |/
* |   666bbd5 Merge branch 'dev'
|\ \
| |/
| * f072ad2 after bug
* |   f8cf727 merged bug fix 101
```
总之，看上去很乱，强迫症看不下去取，为什么Git提交的历史不能算一条干净的直线？
<br/>其实Git有一种称为 Rebase 的操作， “变基”。

<br/>在和远程分支同步后，我对`hello.py`做了两次提交。用`git log`命令看看：
```
$ git log --graph --pretty=oneline --abbrev-commit
* 3e9089a (HEAD -> master, origin/dev, dev) add comment
* c308496 add author
*   ee40115 Merge branch 'dev' of github.com:Tinymonarch/Gitfile into dev
|\
| *   d16f08a Merge branch 'dev' of github.com:Tinymonarch/Gitfile into dev
| |\
| * | cb0f788 add wxy1
* | | ce47af6 add wxy2
| |/
|/|
* |   7affa1c (origin/master) Merge branch 'dev'
|\ \
| |/
| * aae9a88 fix env conflict

```
乱的头皮发麻，命令`git rebase`执行一下：
```
$ git rebase
First, rewinding head to replay your work on top of it...
Applying: add wxy1
Applying: add wxy2
Applying: add author
Applying: add comment
```
```
$ git log --graph --pretty=oneline --abbrev-commit
* 8be7f66 (HEAD -> master) add comment
* ca47ba0 add author
* ed0dbcb add wxy2
* b83a3b1 add wxy1
*   7affa1c (origin/master) Merge branch 'dev'
|\
| * aae9a88 fix env conflict
| *   df2e086 Merge branch 'dev' of github.com:Tinymonarch/Gitfile into dev
| |\
| | * 99207a9 add env
| * | da54388 add new env
| |/
* |   666bbd5 Merge branch 'dev'
...
```
仔细一看，add的两次提交已经没有分叉了，但是下面的依然存在。
<br/>这里引用网友的评论：
<br/>这段看了很久没有代入感，后面去看git的文档（https://git-scm.com/book/zh/v2/Git-%E5%88%86%E6%94%AF-%E5%8F%98%E5%9F%BA）
就清晰了。就使用过程来说：
<br/>===只对尚未推送或分享给别人的本地修改执行变基操作清理历史；
<br/>===从不对已推送至别处的提交执行变基操作


## 五、标签管理

发布一个版本时，我们通常先在版本库中打一个标签（tag），这样，就唯一确定了打标签时刻的版本。将来无论什么时候，取某个标签的版本，就是把那个打标签的时刻的历史版本取出来。所以，标签也是版本库的一个快照。

Git的标签虽然是版本库的快照，但其实它就是指向某个commit的指针（跟分支很像对不对？但是分支可以移动，标签不能移动），所以，创建和删除标签都是瞬间完成的。

Git有commit，为什么还要引入tag？

“请把上周一的那个版本打包发布，commit号是6a5819e...”

“一串乱七八糟的数字不好找！”

如果换一个办法：

“请把上周一的那个版本打包发布，版本号是v1.2”

“好的，按照tag v1.2查找commit就行！”

所以，tag就是一个让人容易记住的有意义的名字，它跟某个commit绑在一起。

### （一）创建标签

在标签中创建标签很简单，首先切换到需要打表情的分支上：
<br/>然后，敲命令`git tag <name>`就可以打一个新标签：(可以用`git tag`显示所有标签)
```
$ git tag v1.0

$ git tag
v1.0
```
默认标签是打在了最新提交的commit上。有时候如果忘了打标签，现在又想起了了怎么办？
<br/>这时候可以找到历史提交的commit，然后打上就可以了：
```
$ git log --graph --pretty=oneline --abbrev-commit
* d635464 (HEAD -> master, tag: v1.0) add comment
* 6d701e5 add author
* bad8591 add wxy2
* 9f9fcde add wxy1
*   7affa1c (origin/master) Merge branch 'dev'
|\
| * aae9a88 fix env conflict
...

Administrator@WIN-76HP3UP5VUA MINGW64 ~/Desktop/git file (master)
$ git tag v0.9 7affa1c
```

再查看tag：
```
$ git tag
v0.9
v1.0
```
注意的是标签不是按时间顺序排列的，而是按字母顺序的，
<br/> 还可以创建带有说明的标签：
```
$ git tag -a v0.1 -m "version 0.1 released" 6d701e5
```

可以用`git show <tag-name>`查看详细信息：
```
$ git show v0.1
tag v0.1
Tagger: Tintmonarch <sap_wxy@163.com>
Date:   Thu Mar 21 19:04:01 2019 +0800

version 0.1 released

commit 6d701e5fbc207153096a6fc05281bdf6ab07ef4f (tag: v0.1)
Author: Tintmonarch <sap_wxy@163.com>
Date:   Thu Mar 21 18:30:49 2019 +0800

    add author

diff --git a/hello.py b/hello.py

...
```

**小结**
- 命令`git tag <tagname>`新建一个标签，默认为`HEAD`,也可以指定一个commit id；
- 命令`git tag -a <tagname> -m "comment"` 可以指定标签信息；
- 命令`git tag` 查看所有标签；
- 命令`git show <tagname>`查看标签详细信息。


### （二）操作标签

如果标签打错了，可以删除：
```
$ git tag -d v0.9
Deleted tag 'v0.9' (was 7affa1c)
```
因为创建的标签都存在本地，不会自动推送到远程，所以，打错的标签可以在本地安全得删除。
<br/>如果要推送某个标签到远程，使用命令`git push origin <tagname>`：
```
$ git push origin v0.1
Enumerating objects: 10, done.
Counting objects: 100% (10/10), done.
Delta compression using up to 8 threads.
Compressing objects: 100% (7/7), done.
Writing objects: 100% (8/8), 822 bytes | 274.00 KiB/s, done.
Total 8 (delta 3), reused 0 (delta 0)
remote: Resolving deltas: 100% (3/3), completed with 1 local object.
To github.com:Tinymonarch/Gitfile.git
 * [new tag]         v0.1 -> v0.1
```

或者一次性推送所有未推送标签：
```
$ git push origin --tags
Enumerating objects: 5, done.
Counting objects: 100% (5/5), done.
Delta compression using up to 8 threads.
Compressing objects: 100% (2/2), done.
Writing objects: 100% (3/3), 291 bytes | 145.00 KiB/s, done.
Total 3 (delta 1), reused 0 (delta 0)
remote: Resolving deltas: 100% (1/1), completed with 1 local object.
To github.com:Tinymonarch/Gitfile.git
 * [new tag]         v1.0 -> v1.0
```
如果标签已经推送到远程，删除标签就变得麻烦了一点点：先从本地删除：
```
$ git tag -d v1.0
Deleted tag 'v1.0' (was d635464)
```
然后从远程删除，命令还是push，但是参数不同：
```
$ git push origin :refs/tags/v1.0
To github.com:Tinymonarch/Gitfile.git
 - [deleted]         v1.0
```
想看远程标签是否删掉，可以登录github查看。

**小结**
- 命令`git push origin <tagname>`推送一个本地标签到远程；
- 命令`git push origin --tags`推送所有未推送标签到远程；
- 命令`git tag -d <tagname>`删除一个本地标签；
- 命令`git tag push :refs/tags/<tagname>`删除一个远程标签。






## 六、使用Github

我们一直用GitHub作为免费的远程仓库，如果是个人的开源项目，放到GitHub上是完全没有问题的。其实GitHub还是一个开源协作社区，通过GitHub，既可以让别人参与你的开源项目，也可以参与别人的开源项目。
<br/>在GitHub出现以前，开源项目开源容易，但让广大人民群众参与进来比较困难，因为要参与，就要提交代码，而给每个想提交代码的群众都开一个账号那是不现实的，因此，群众也仅限于报个bug，即使能改掉bug，也只能把diff文件用邮件发过去，很不方便。
<br/>但是在GitHub上，利用Git极其强大的克隆和分支功能，广大人民群众真正可以第一次自由参与各种开源项目了。
<br/>如何参与一个开源项目呢？比如人气极高的bootstrap项目，这是一个非常强大的CSS框架，你可以访问它的项目主页https://github.com/twbs/bootstrap，点“Fork”就在自己的账号下克隆了一个bootstrap仓库，然后，从自己的账号下clone：
```
$ git clone git@github.com:michaelliao/bootstrap.git
```
一定要从自己的账号下clone仓库，这样你才能推送修改。如果从bootstrap的作者的仓库地址`git@github.com:twbs/bootstrap.git`克隆，因为没有权限，你将不能推送修改。
<br/>Bootstrap的官方仓库`twbs/bootstrap`,你在GitHub上克隆的仓库`my/bootstrap`，以及你自己克隆到本地电脑的仓库，他们的关系就像下图显示的那样：

<br/>┌─ GitHub ────────────────────────────────────┐
<br/>│                                             │
<br/>│ ┌─────────────────┐     ┌─────────────────┐ │
<br/>│ │ twbs/bootstrap  │────>│  my/bootstrap   │ │
<br/>│ └─────────────────┘     └─────────────────┘ │
<br/>│                                  ▲          │
<br/>└──────────────────────────────────┼──────────┘
<br/>                                   ▼
<br/>                          ┌─────────────────┐
<br/>                          │ local/bootstrap │
<br/>                          └─────────────────┘

如果你想修复bootstrap的一个bug，或者新增一个功能，立刻就可以开始干活，干完后，往自己的仓库推送。
<br/>如果你希望bootstrap的官方库能接受你的修改，你就可以在GitHub上发起一个pull request。当然，对方是否接受你的pull request就不一定了。

**小结**
-   在github可以任意fork开源仓库。
-   自己拥有fork后的仓库的读写权限。
-   可以 pull request 给官方仓库贡献代码。




# 七、使用码云

使用GitHub时，国内的用户经常遇到的问题是访问速度太慢，有时候还会出现无法连接的情况（原因你懂的）。
<br/>如果我们希望体验Git飞一般的速度，可以使用国内的Git托管服务——码云（gitee.com）。
<br/>和GitHub相比，码云也提供免费的Git仓库。此外，还集成了代码质量检测、项目演示等功能。对于团队协作开发，码云还提供了项目管理、代码托管、文档管理的服务，5人以下小团队免费。
- 码云的免费版本也提供私有库功能，只是有5人的成员上限。

使用码云和使用GitHub类似，我们在码云上注册账号并登录后，需要先上传自己的SSH公钥。选择右上角用户头像 -> 菜单“修改资料”，然后选择“SSH公钥”，填写一个便于识别的标题，然后把用户主目录下的`.ssh/id_rsa.pub`文件的内容粘贴进去：点击“确定”即可完成并看到刚才添加的Key。
<br/><br/>如果我们已经有了一个本地的git仓库（例如，一个名为learngit的本地库），如何把它关联到码云的远程库上呢？
<br/>首先，我们在码云上创建一个新的项目，选择右上角用户头像 -> 菜单“控制面板”，然后点击“创建项目”,
<br/>项目名称最好与本地库保持一致,
<br/>然后，我们在本地库上使用命令git remote add把它和码云的远程库关联：
```
git remote add origin git@gitee.com:Tinymonarch/Gitfile.git
```
之后，就可以正常地用git push和git pull推送了！
如果在使用命令git remote add时报错：
```
git remote add origin git@gitee.com:Tinymonarch/Gitfile.git
fatal: remote origin already exists.
```
这说明本地已经关联了一个名叫`origin`的远程库，此时可以先用`git remote -v`查看一下远程库信息：
```
git remote -v
origin    git@github.com:Tinymonarch/Gitfile.git (fetch)
origin    git@github.com:Tinymonarch/Gitfile.git (push)
```
可以看到本地库已经关联了`origin`的远程库，并且该远程库指向github。
<br/>我们删除已有的github远程库：

```
git remote rm origin
```

再关联码云的远程库：
```
git remote add origin git@gitee.com:Tinymonarch/Gitfile.git
```
此时，我们再查看远程库信息：

```
git remote -v
origin    git@gitee.com:Tinymonarch/Gitfile.git (fetch)
origin    git@gitee.com:Tinymonarch/Gitfile.git (push)
```

现在可以看到，origin已经被关联到码云的远程库了。通过git push命令就可以把本地库推送到Gitee上。

<br/>有的小伙伴又要问了，一个本地库能不能既关联GitHub，又关联码云呢？
<br/>答案是肯定的，因为git本身是分布式版本控制系统，可以同步到另外一个远程库，当然也可以同步到另外两个远程库。
<br/>使用多个远程库时，我们要注意，git给远程库起的默认名称是origin，如果有多个远程库，我们需要用不同的名称来标识不同的远程库。
<br/>仍然以learngit本地库为例，我们先删除已关联的名为origin的远程库：
```git
git remote rm origin
```

然后，先关联github的远程库：
```
git remote add github git@github.com:Tinymonarch/Gitfile.git
```
注意，远程库的名称叫`github`了，不叫`origin`了。
<br/>接着，再关联码云：
```
git remote add gitee git@gitee.com:Tinymonarch/Gitfile.git
```
同样注意，远程库的名称叫`gitee`，不叫`origin`了。
<br/>现在我们用`git remote -v`查看远程库信息，可以看到两个：
```
git remote -v 
github    git@github.com:Tinymonarch/Gitfile.git (fetch)
github    git@github.com:Tinymonarch/Gitfile.git (push)
gitee    git@gitee.com:Tinymonarch/Gitfile.git (fetch)
gitee    git@gitee.com:Tinymonarch/Gitfile.git (push)
```
如果要推送到github远程：
```
git push github master
```
如果要推送到码云：
```
git push gitee master
```
这样一来，我们的本地库就可以关联多个远程库：
<br/>┌─────────┐ ┌─────────┐
<br/>│ GitHub  │ │  Gitee  │
<br/>└─────────┘ └─────────┘
<br/>     ▲           ▲
<br/>     └─────┬─────┘
<br/>           │
<br/>    ┌─────────────┐
<br/>    │ Local Repo  │
<br/>    └─────────────┘
<br/>码云同样有pr功能，可以让其他小伙伴加入到开源项目中来。







## 八、自定义Git

在前面的安装Git一节，我们配置了`user.name`和`user.email`，实际上，Git还有很多可配置项。
<br/>比如，让Git显示颜色，会让命令输出看起来很醒目：
```
$ git config --global color.ui true
```
下面我们来深入了解一些自定义。

### （一）忽略特殊文件

有些时候，你必须把某些文件放到Git工作目录中，但又不能提交它们，比如保存了数据库密码的配置文件啦，等等，每次git status都会显示Untracked files ...，有强迫症的心里肯定不爽。
<br/>好在Git考虑到了大家的感受，这个问题解决起来也很简单，在Git工作区的根目录下创建一个特殊的.gitignore文件，然后把要忽略的文件名填进去，Git就会自动忽略这些文件。
<br/>不需要从头写.gitignore文件，GitHub已经为我们准备了各种配置文件，只需要组合一下就可以使用了。所有配置文件可以直接在线浏览：https://github.com/github/gitignore
<br/>忽略文件的原则是：
1. 忽略操作系统自动生成的文件，比如缩略图等；
2. 忽略编译生成的中间文件、可执行文件等，也就是如果一个文件是通过另一个文件自动生成的，那自动生成的文件就没必要放进版本库，比如Java编译产生的.class文件；
3. 忽略你自己的带有敏感信息的配置文件，比如存放口令的配置文件。

<br/>举个例子：
<br/>假设你在Windows下进行Python开发，Windows会自动在有图片的目录下生成隐藏的缩略图文件，如果有自定义目录，目录下就会有`Desktop.ini`文件，因此你需要忽略Windows自动生成的垃圾文件：
```
# windows
Thumbs.db
ehthumbs.db
Desktop.ini
```
然后，继续忽略Python编译产生的`.pyc`、`.pyo`、`dist`等文件或目录：
```
# python
*.py[cod]
*.so
*.egg
*.egg-info
dist
build
```
加上你自己定义的文件，最终得到一个完整的.gitignore文件。
<br/>最后一步就是把`.gitignore`也提交到Git，就完成了！当然检验`.gitignore`的标准是`git status`命令是不是说`working directory clean`。
<br/>使用Windows的童鞋注意了，如果你在资源管理器里新建一个`.gitignore`文件，它会非常弱智地提示你必须输入文件名，但是在文本编辑器里“保存”或者“另存为”就可以把文件保存为`.gitignore`了。
<br/>有些时候，你想添加一个文件到Git，但发现添加不了，原因是这个文件被`.gitignore`忽略了：
```
$ git add test.so
The following paths are ignored by one of your .gitignore files:
test.so
Use -f if you really want to add them.
```
Git也提示了我们，如果我们真的想提交，就加上`-f`参数：
```
$ git add -f test.so
```
<br/>或者你发现是自己的`.gitignore`写的有问题，想找出来到底哪里写错了，可以用`git check-ignore`命令来查看：
```
$ git check-ignore -v test.so
.gitignore:8:*.so       test.so
```
Git会告诉我们，`.gitignore`的第八行规则强行忽略了该文件。



### （二）配置别名

Git还可以给Git命令指定别名，来简化命令.
<br/>以下命令就告诉Git，用`st`来代替`status` :
```
$ git config --global alias.st status
```
现在就可以用`git st`命令来查看状态了。
<br/>当然还可以有很多命令简写，比如用`co`表示`checkout`，`ci`表示`commit`，`br`表示`branch`：
```
$ git config --global alias.co checkout
$ git config --global alias.ci commit
$ git config --global alias.br branch
```
那么以后提交就可以写成：
```
$ git ci -m "lalalala"
```
`--global`参数是全局参数，也就是这些命令在这台电脑的所有Git仓库下都有用。

<br/>在撤销修改一节中，我们知道，命令git reset HEAD file可以把暂存区的修改撤销掉（unstage），重新放回工作区。既然是一个unstage操作，就可以配置一个unstage别名：
```
$ git config --global alais.unstage 'reset HEAD'
```
当你敲入命令：
```
$ git unstage test.py
```
实际上Git执行的是：
```
$ git reset HEAD test.py
```

<br/>配置一个`git last`，让其显示最后一次提交的信息：
```
$ git config --global alias.last 'log -1'
```
这样，用`git last`就能显示最近一次的提交了：
```
$ git st
On branch master
Your branch is ahead of 'origin/master' by 5 commits.
  (use "git push" to publish your local commits)
```

<br/>还有人把`lg`配置成了：
```
$ git config --global alias.lg "log --color --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit"
```
看一下效果：
```
$ git lg
* f8f6f61 - (HEAD -> master) add gitignore (39 minutes ago) <Tintmonarch>
* d635464 - add comment (6 days ago) <Tintmonarch>
* 6d701e5 - (tag: v0.1) add author (6 days ago) <Tintmonarch>
* bad8591 - add wxy2 (6 days ago) <Tintmonarch>
* 9f9fcde - add wxy1 (6 days ago) <Tintmonarch>
*   7affa1c - (origin/master) Merge branch 'dev' (6 days ago) <Tintmonarch>
|\
| * aae9a88 - fix env conflict (6 days ago) <Tintmonarch>
| *   df2e086 - Merge branch 'dev' of github.com:Tinymonarch/Gitfile into dev (6 days ago) <Tintmonarch>
| |\
| | * 99207a9 - add env (6 days ago) <Tintmonarch>
| * | da54388 - add new env (6 days ago) <Tintmonarch>
| |/
* |   666bbd5 - Merge branch 'dev' (6 days ago) <Tintmonarch>
|\ \
| |/
| * f072ad2 - after bug (7 days ago) <Tintmonarch>
* |   f8cf727 - merged bug fix 101 (7 days ago) <Tintmonarch>
|\ \
| * | 489bbd9 - fix bug 101 (7 days ago) <Tintmonarch>
|/ /
* |   913e035 - merge with no-ff (7 days ago) <Tintmonarch>
```

#### 配置文件

配置Git的时候，加上`--global`是针对当前用户起作用的，如果不加，那只针对当前的仓库起作用。
<br/>配置文件放哪了？每个仓库的Git配置文件都放在`.git/config`文件中：
```
$ cat config
[core]
        repositoryformatversion = 0
        filemode = false
        bare = false
        logallrefupdates = true
        symlinks = false
        ignorecase = true
[remote "origin"]
        url = git@github.com:Tinymonarch/Gitfile.git
        fetch = +refs/heads/*:refs/remotes/origin/*
[branch "master"]
        remote = origin
        merge = refs/heads/master
[branch "dev"]
        remote = origin
        merge = refs/heads/dev
[alias]
        co = checkout
        ci = commit
        br = branch
        unstage = reset HEAD
        last = log -1
```
别名就在[alias]后面，要删除别名，直接把对应的行删掉即可。
<br/>而当前用户的Git配置文件在用户主目录下的一个隐藏文件`.gitconfig`中：
```
$ cat .gitconfig
[user]
        name = Tintmonarch
        email = sap_wxy@163.com
[color]
        ui = true
[alias]
        st = status
        br = branch
        co = checkout
        ci = commit
        unstage = reset HEAD
        last = log -1
        lg = log --color --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit
```
配置别名也可以直接更改这个文件，改错了直接在文件里删掉再用命令修改皆可。


### （三）搭建Git服务器

在远程仓库一节中，我们讲了远程仓库实际上和本地仓库没啥不同，纯粹为了7x24小时开机并交换大家的修改。
<br/>GitHub就是一个免费托管开源代码的远程仓库。但是对于某些视源代码如生命的商业公司来说，既不想公开源代码，又舍不得给GitHub交保护费，那就只能自己搭建一台Git服务器作为私有仓库使用。
<br/>搭建Git服务器需要准备一台运行Linux的机器，强烈推荐用Ubuntu或Debian，这样，通过几条简单的apt命令就可以完成安装。
<br/>假设你已经有`sudo`权限的用户账号，下面，正式开始安装。
第一步，安装Git：
```
$ sudo apt-get install git
```
第二步，创建一个`git`用户，用来运行`git`服务：
```
$ sudo adduser git 
```
第三步，创建证书登录：
<br/>收集所有需要登录的用户的公匙，就是他们自己的`id_rsa.git`文件，把所有公匙导入到`home/git/.ssh/authorized_keys`文件里，一行一个。
<br/>第四步，初始化Git仓库：
<br/>先选定一个目录作为Git仓库，假设为`/srv/sample.git`，在`/srv`目录下输入命令：
```
$ sudo git init --bare sample.git
```
Git就会创建一个裸仓库，裸仓库没有工作区，因为服务器上的Git仓库纯粹是为了共享，所以不让用户直接登录到服务器上去改工作区，并且服务器上的Git仓库通常以`.git`结尾。然后，把owner改为`git`:
```
$ sudo chown -R git:git sample.git
```
第五步，禁用shell登录：
出于安全考虑，第二不步创建的git用户不允许登录shell，这可以通过编辑`/etc/passwd`文件完成。找到类似下面的一行：
```
git:x:1001:1001:,,,:/home/git:/bin/bash
```
改为：
```
git:x:1001:1001:,,,:/home/git:/usr/bin/git-bash
```
这样，`git`用户可以正常通过ssh使用git，但无法登录shell，因为我们为`git`用户指定的`git-shell`每一次登录就自动退出。
<br/>第六步，克隆远程仓库：
<br/>现在，可以通过`git clone`命令来远程克隆仓库了，在各自的电脑上运行：
```
$ git clone git@server:/srv/sample.git 
Cloning into 'sample'...
warning: You appear to have cloned an empty repository.
```
剩下的推送就按部就班了。

#### 管理公匙
如果团队很小，把每个人的公钥收集起来放到服务器的`/home/git/.ssh/authorized_keys`文件里就是可行的。如果团队有几百号人，就没法这么玩了，这时，可以用`Gitosis`来管理公钥。
<br/>这里我们不介绍怎么玩Gitosis了，几百号人的团队基本都在500强了，相信找个高水平的Linux管理员问题不大。

#### 管理权限
有很多不但视源代码如生命，而且视员工为窃贼的公司，会在版本控制系统里设置一套完善的权限控制，每个人是否有读写权限会精确到每个分支甚至每个目录下。因为Git是为Linux源代码托管而开发的，所以Git也继承了开源社区的精神，不支持权限控制。不过，因为Git支持钩子（hook），所以，可以在服务器端编写一系列脚本来控制提交等操作，达到权限控制的目的。Gitolite就是这个工具。
<br/>这里我们也不介绍Gitolite了，不要把有限的生命浪费到权限斗争中。

<br/><br/><br/>

# 期末总结

<br/>终于到了期末总结的时刻了！
<br/>经过几天的学习，相信你对Git已经初步掌握。一开始，可能觉得Git上手比较困难，尤其是已经熟悉SVN的，没关系，多操练几次，就会越用越顺手。
<br/>Git虽然极其强大，命令繁多，但常用的就那么十来个，掌握好这十几个常用命令，已经可以得心应手地使用Git了。
<br/>现在告诉你Git的官方网站：http://git-scm.com






























    
