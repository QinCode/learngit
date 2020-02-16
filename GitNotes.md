# Git学习笔记

## 1 Git安装

​	在Windows上安装时，直接安装软件。安装成功后输入下列代码修改用户名与邮箱：

```lisp
$ git config --global user.name "Your Name"
$ git config --global user.email "email@example.com"
```

## 2创建版本库

​	可以直接创建一个空目录，最好放在无中文目录路径中。也可以使用**git**的命令窗口创建

```
$ mkdir learngit
$ cd learngit
$ pwd
/Users/michael/learngit
```

**mkdir** 命令是创建文件夹，**cd** 命令是跳转至目录，**pwd**命令是查看当前路径

​	使用git命令设置当前目录为**git**仓库，如下：

```
$ git init
```

​	第一步：当要提交相关文件时，将文件放在**仓库文件夹中**，首先使用```$ git add```命令将文件增添（此处为**readme.txt**）。

```$ git add readme.txt```

​	第二步：使用```git commit```命令提交至仓库，如下：

```lua
$ git commit -m "wrote a readme file"
[master (root-commit) eaadf4e] wrote a readme file
 1 file changed, 2 insertions(+)
 create mode 100644 readme.txt
```

​	-m 加后面的字符串，是要填写提交说明，**内容随意**。

​	另外，还可以一次增添多个文件，再统一提交，如：

```lua
$ git add file1.txt
$ git add file2.txt file3.txt
$ git commit -m "add 3 files."
```

## 3 修改管理

	### 3.1 修改和提交

​	在修改提交至**仓库**的文件后，使用```git status```命令查看修改状态。如：

![查看修改状态](https://ae01.alicdn.com/kf/H88c2839376d6423e8a9f590b7ab3c7adt.png)

​	该命令可以让我们时刻查看仓库文件状态。但若要知道具体新修改了什么内容，可以使用```git diff```命令查看具体修改：

![查看修改](https://ae01.alicdn.com/kf/H046faf9a34994123a9d2ceac050c18f13.png)

​	另外，可以**直接使用```git diff```命令**，查看全部修改。

​	修改完成后，若要提交至Git仓库，重复提交步骤即可。即使用```$ git add```和```git commit```命令。

### 3.2版本回退

​	修改一次或多次仓库文件并提交后，要想查看修改的历史记录可使用```$ git log```命令查看，如下：

![查看修改历史](https://ae01.alicdn.com/kf/Hc37499f6ceb64ff99bcef7d9d7edf3d5t.png)



​	在Git中，用`HEAD`表示当前版本，也就是最新的提交`1094adb...`（注意我的提交ID和你的肯定不一样），上一个版本就是`HEAD^`，上上一个版本就是`HEAD^^`，当然往上100个版本写100个`^`比较容易数不过来，所以写成`HEAD~100`。

​	要想回退当前修改的仓库文件至以前的版本，可以使用`git reset`命令：

![当前文件版本回退](https://ae01.alicdn.com/kf/H8442fcdcc98a4463bcea3529b247e18aT.png)

​	

​	如果出现回退过多，或者想找回更新的版本，可以用`git reset`命令，但要将**HEAD**换成版本号前几位，如图：

​							![版本前进](https://ae01.alicdn.com/kf/H2e385ef8890a4db193104fc67264bbceH.png)



​	要想查看自己更新的所有版本的**版本号**，可以使用`git reflog`命令，如图：

![查看版本号](C:\Users\32838\AppData\Roaming\Typora\typora-user-images\image-20200216195129757.png)

​	该命令可以看见对**仓库文件**的版本操作。

​	

​	综上所述，只要知道相应版本号，就可以随意**回退**或**前进**至相应版本。

### 3.3撤销修改

​	当修改文件后提交前，想要回退到修改。除了手动删除修改内容并版本回退外，还可以使用`git checkout -- file`命令，使得该文件回退至最近一次`git commit`或`git add`时的状态（**即回退至上一次`git commit`或`git add`时**）。可用来解决`git add`，但未提交，版本库中无`git add`时的版本的情况。例如：





