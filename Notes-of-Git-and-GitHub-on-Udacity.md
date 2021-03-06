# Notes of [Udacity's Git & GitHub Course](https://www.udacity.com/course/how-to-use-git-and-github--ud775)

[Git Documentation]([https://git-scm.com/book/zh/v2/%E8%B5%B7%E6%AD%A5-%E5%85%B3%E4%BA%8E%E7%89%88%E6%9C%AC%E6%8E%A7%E5%88%B6](https://git-scm.com/book/zh/v2/起步-关于版本控制))

I think this is an good introduction to version control system for a green hand.

- To learn Git:  a version control system
- To learn GitHub: a code sharing and collaboration platform
- To learn to use a Unix-style command line
    + Bash prompt
    + Git Bash
---

## Lesson 1 Why Version Control & Forms

### 使用命令行对比两个脚本的差异

- Windows FC (file compare) use it in command prompt

`FC file_1 file_2`

- Mac/Linux/Git Bash Diff (difference)

`diff -u file_1 file_2`

The -u option stands or unified diff format and it will make the output a little easier to read.

- A simple text editor
    + Sublime
    + Notepad++
    + Emacs
    + Vim

- Not a rich-text editor
    + Microsoft Word
    + OpenOffice

### 从Git Bash用命令行打开文本编辑器，设置为notepad++

- [Git Bash 设置Notepad++作为默认编辑器](https://blog.csdn.net/qq_36595013/article/details/80955542) 没有解决问题
- [git bash简单调用notepad++应用编辑文本的设置](https://jingyan.baidu.com/article/22fe7cedf2c8c93002617f93.html) done，还是环境变量的锅，先设置环境变量，然后设置Git中的默认编辑器

### Git Bash一些命令
```
cd ~                        # 更改目录 directory，“目录”比“文件夹”更具备计算机科学含义
mkdir version-control       # 创建 version-control 目录
notepad++ text.txt          # 使用notepad++，打开/创建 text.txt（需要先配置环境变量）
pwd                         # 打印工作目录
ls                          # 列出目录下文件

rm .git -rf                 #delete local repository
```

#### 使用短行
> 如果文件包含很长的行，则会降低许多命令行工具（包括 Git）的实用性。 例如，如果使用 diff 比较两个将所有内容都放在同一行上的文件，则 diff 只会显示这两个文件是不同的文件，而无法指出哪里不同。

>因此，在编写反思文件或其他纯文本文件时，确保每行长短适中是一种好做法。将行限制为多长是个人喜好问题。 许多开发者都将行限制为不超过 80 到 120 个字符。 有些编辑器能自动插入换行符，但在 Sublime 等其他编辑器中，如果想另起一行，请记得按下 Enter。

### Version Control Examples

- saving manual copies
- dropbox
- Google Docs
- Wikipedia

### Version Control Systems for Code

- CVS concurrent version systems
- SVN subversion
- Mercurial hg in short
- Git
    + 为每项逻辑更改进行一次提交 vs at regular internals
    + automatically vs manually
    + Git was innovated in 2005.
    + Git is British slang for sth ≈ unpleasant person.

#### Commits
to make looking through a old version more meaningful

`git log` check previous commits

`git diff`

#### Repository

A Git repository is a collection of files that are tracked by Git as a conhesive unit.

commits with multiple files (they are connected, for example, they have the same function or variable)

`stat <file>`

`git --version` Git 在版本 1.8 中添加了许多新功能

`git help <command>` To get information about how to use a Git command, like `git help diff`

#### git clone

`git clone <url>` clone a repository from one computer to another

`git config --global color.ui auto` 全局彩色diff输出

停止查看 git bash中的输出，按 q（表示退出）

#### Checking Out Prior Commits

to reset all of ur files to how they were at the time that commit was made

`git checkout <commit ID>`

> version control makes u more of a risk taker

prompt里commit id有*****，代表code有改动，但尚未commit

tab自动补全command，或者显示可能的command（windows下MinttyGW缺省设置已经十分省心）

`mv <file> <file_new name>` 移动文件，默认保存至home directory

[Git个性化设置](https://www.cnblogs.com/BugBrother/p/6963484.html)

[windows setting](https://classroom.udacity.com/courses/ud775/lessons/2980038599/concepts/33417185870923)

#### 修改 commit message

`git commit --amend`  修改上一条提交的commit message

---

## Lesson 2 Git


### 创建新仓库

`ls -a` 可以看到隐藏文件

`git init` 初始化/创建当前directory为Git Repository

`git status`

`touch <file>` 新建文件

### Three Areas

- working directory

- staging area

`git add <file>` 添加至暂存区

`git reset <file>` 从暂存区移除

- repository

[Git提交样式指南](https://github.com/udacity/frontend-nanodegree-styleguide-zh/blob/master/%E5%89%8D%E7%AB%AF%E5%B7%A5%E7%A8%8B%E5%B8%88%E7%BA%B3%E7%B1%B3%E5%AD%A6%E4%BD%8D%E6%A0%B7%E5%BC%8F%E6%8C%87%E5%8D%97%20-%20Git.md)
[English Version](http://udacity.github.io/frontend-nanodegree-styleguide/css.html)

`git diff no argument` 对比working directory & staging area

`git diff --staged` 对比staging area & repository

`git reset --hard` discard any changes in either the working directory or the working area **(be careful since this is inreversible)**

[Git取消commit](https://www.cnblogs.com/lyy-2016/p/6509707.html)

`git checkout master`

在源码最后添加新代码，要加一个回车符，否则用diff命令时会警告

### Branch

**checkout可以是commit也可以是branch**

#### master

main branch

> every time u create a repository, Git creates a master branch 4 u.

> the current last commit on a branch = the tip of that branch

#### 创建、查看

`git branch` show current branches

`git branch <branch name>` 创建新的branch

**head ** 指当前所在/checked out的commit

**remote branch ** 他人创建的branch

`git log --graph (--oneline) <branch_1> <branch_2>` visualization

#### detached head

`git checkout -b new_branch_name`

#### reachability

git log & commit & parents

**unreachable commits** 第19讲

`git checkout -b <new_branch_name>`

#### merging

`git merge <branch_1> <branch_2>`

`git show`

`git branch -d <branch_name>` 删除branch (merge后只删除了label，commits还在)

`git merge --abort` 将文件恢复到开始合并前的状态

> 合并冲突（Windows 与 Unix 系统之间的换行符）
背景：按下键盘上的“Enter”键时，实际上是告诉计算机在文本文件中插入一个不可见的字符，以便指示计算机应新起一行。Unix 系统会添加一个名为“换行”符的字符（或者 LF 或 \），而 Windows 系统会添加两个字符，即“回车”和“换行”（或者 CRLF 或 \r\n）。

>> Caroline 的文件包含 LF，因为她的文件是在使用 LF 的 Mac OSX 上编辑的。如果某 Windows 用户要编辑 Caroline 的文件，Windows 文本编辑器可能会将所有 LF 均转换为 CRLF，以便该用户能够编辑文件。在该 Windows 用户将她的文件与 Caroline 的文件合并时，不同的 LF 和 CRLF 字符将会造成合并冲突。

>>> 要修复此问题，Windows 用户应将 autocrlf 全局属性设置为 true：git config --global core.autocrlf true。有关更多信息，请访问以下网址：https://help.github.com/articles/dealing-with-line-endings/#platform-all


`git log -n2` 仅显示最新的2个commit

## Lesson 3 Share on GitHub

### remote 

- push data

- pull data

`git remote`

`gite remote add <name> <http url>`

`git push <remote> <branch>`

[github获取token](<https://blog.csdn.net/u014175572/article/details/55510825>) 新建了一个token，似乎没什么用？

`git pull`

### forking

**文件名长度超出windows路径长度限制** `git config --system core.longpaths true`

fork会自动创建一个remote，默认名称为original，可以用`git remote -v`确认详细信息

`git pull` = `git fetch` + `git merge`

**branch_1 is up to date with branch_2** 两个分支指向相同的commit

**out of sync** each branch has a commit not present in the other

稍微有点儿绕的origin/master （理解为最后一次pull/clone下来的保存在本地的remote的commit情况）是一个远程追踪分支），同时local还有一个master branch，在本地的commit实际上是改变的master，实例见下图

![origin-master](https://github.com/gearhere/version-control/blob/master/origin-master.png)

#### fast-forward merges

It occurs when merging two commits, where one is ancestor of the other.

#### After forking

> 在协同构建公共版本库时，标准的做法是在Fork内的非 master 分支中进行更改。这样一来，可以轻松让你的 master 分支与原始版本库的 master 保持同步，并在准备好时将 master 中的更改合并到分支中。

### pull request

请求被pull进GitHub上的branch里

#### upstream

another remote points to the original repository on GitHub

![upstream](https://github.com/gearhere/version-control/blob/master/upstream.png)

### 几种命令的结果对比（important）

纠错：运行 `git pull` 时，工作目录和暂存区也会更新

![operation-outcome](https://github.com/gearhere/version-control/blob/master/operation-outcome.png)

## 其他Linux Command Line

清屏命令 `clear`

## Questions

### Related

- 你认为，手动选择何时创建提交（像在 Git 中做的那样）与自动保存版本（如 Google Docs 所做的那样）各有何优缺点？
- use version control on homework
- Git Bash theme（美观，效率）
- GitHub密码缓存

### Unrelated
- [Linux和UNIX的关系及区别](http://c.biancheng.net/view/707.html)
- [Notepad++ 直接调用cmd窗口运行Python程序](https://blog.csdn.net/sunflower_sara/article/details/81038310)
- 华为系统
- 听课时如果有两块屏幕就好了，一个打字，一个播放视频，键盘同时操控
- [LaTex入门安装教程](https://www.imooc.com/article/45497)
