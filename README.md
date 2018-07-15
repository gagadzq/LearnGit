#Git初学#
 学习过程主要参考[git基础知识整理](https://www.shiyanlou.com/questions/2999)

##Git与SVN区别##
* SVN每个版本都依赖与上一个版本
* Git每个版本都是独立存在的，直接记录快照
* Git可以在本地commit，SVN commit需要提交到主机
* Git能保证数据完整性

##Git三种状态##
Git三种状态包括已提交、已修改、已暂存<br/>
三个工作区域：Git仓库、工作目录、暂存区域

![](https://git-scm.com/book/en/v2/images/areas.png)
基本的Git工作流程如下：<br/>
>1. 在工作目录中修改文件
>2. 暂存文件，将文件的快照放入暂存区域
>3. 提交更新，找到暂存区域的文件，将快照永久存储到Git仓库目录 

查看当前文件状态：`git status`、`git status -s`

```
$ git status -s
 M README			<!--修改的文件，未放入暂存区-->
MM Rakefile			<!--被修改并提交到暂存区后又在工作区中被修改-->
A  lib/git.rb       <!--新添加到暂存区的文件-->
M  lib/simplegit.rb       <!--修改的文件，已放入暂存区-->
?? LICENSE.txt         <!--未跟踪的文件-->
```
##Git配置##

（忽略安装过程）<br/>
Git自带 git config 设置控制Git外观和行为的配置变量<br/>

* /etc/gitconfig 全局系统配置
* ~/.gitconfig 或 ~/.config/git/config 只针对当前用户
* .git/config 当前仓库

###设置用户信息###
```
$ git config --global user.name "John Doe"
$ git config --global user.email johndoe@example.com
```
###检查信息配置###
git config --list：列出Git所有配置

```
$ git config --list
user.name=John Doe
user.email=johndoe@example.com
color.status=auto
color.branch=auto
color.interactive=auto
color.diff=auto
```

##获取Git仓库##

* git init： 初始化仓库，创建.git初始化目录（文件没有被跟踪）
* git add： 对指定文件跟踪，添加当前目录到git中
* git commit -m "first commit"： 放入暂存区中
* git clone [url]： 克隆现有仓库

##Git基础##
####Git生命周期如下####

![Git生命周期](https://git-scm.com/book/en/v2/images/lifecycle.png)

####在项目中创建新的README文件####

```
$ echo 'My Project' > README
$ git add README
$ git status
On branch master
Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)

    new file:   README
```

####忽略文件####
创建.gitignore文件，告诉Git那些文件不需要/需要添加到版本管理中

```
$ cat .gitignore
*.[oa]
*~
!*/mtk/
!*.zip
```

* 所有空行或者以 ＃开头的行都会被 Git 忽略。
* 可以使用标准的 glob 模式(简化的正则)匹配。
* 匹配模式可以以（/）开头防止递归。
* 匹配模式可以以（/）结尾指定目录。
* 要忽略指定模式以外的文件或目录，可以在模式前加上惊叹号（!）取反.

####查看尚未暂存文件的修改####

`git diff` 查看尚未暂存的文件更新了哪些部分,比较工作目录和暂存区的差异

`git diff --staged` 查看已暂存的下次将要提交的

####提交文件####

`git commit`  进入编译器,里面包含更改信息

`git commit -m` "内容" :直接提交内容,不进入编译器

`git commit -a` 提交所有已跟踪的文件,包括未add到缓存区的.(但不会提交未跟踪的)

####移除文件####
`gim rm` 从暂存区移除文件（已跟踪文件）

`git rm -f 文件` 强制删除，防止删除未add到缓存区的文件

`git rm --cached 目录/` 不删除工作区文件

####移动文件####

`$ git mv file_from file_to`




