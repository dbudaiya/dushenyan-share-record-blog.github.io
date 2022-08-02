---
title: Git
date: 2022-07-31 22:54:50
categories: 配置工具
---

## GIT是什么

---

自诞生于 2005 年以来，Git 日臻成熟完善，在高度易用的同时，仍然保留着初期设定的目标。它的速度飞快，极其适合管理大项目 。<br />Git 可以在 windows、Mac、Linux 全平台系统使用。
<a name="ffysq"></a>
## 官网指引

---

中文官网： [https://gitforwindows.org/](https://gitforwindows.org/)<br />下载地址：[https://git-scm.com/downloads](https://git-scm.com/downloads)
<a name="w6Vtr"></a>
## 安装

---

图像化软件
<a name="UNukc"></a>
## 配置

---

配置文件为 ~/.gitconfig ，执行任何 Git 配置命令后文件将自动创建。<br />第一个要配置的是你个人的用户名称和电子邮件地址。这两条配置很重要，每次 Git 提交时都会引用这两条信息，说明是谁提交了更新，所以会随更新内容一起被永久纳入历史记录：
```powershell
git config --global user.email "2645472474@qq.com"
git config --global user.name "dushenyan"
```
<a name="retlo"></a>
## 使用

---

工作流
```powershell
# 创建文件
touch a.txt

# 初始化新仓库 
git init

# 克隆代码 
git clone https://gitee.com/houdunwang/hdcms.git

# 克隆指定分支 
git clone -b dev git@gitee.com:houdunwang/hdcms.git

# 查看状态
git status

# 提交单个文件 
git add index.php

# 提交所有文件
git add -A

# 使用通配符提交 
git add *.js

# 提交到仓库中 
git commit -m '提示信息'

# 提交已经跟踪过的文件，不需要执行

add git commit -a -m '提交信息'
# 删除版本库与项目目录中的文件 
git rm index.php

# 只删除版本库中文件但保存项目目录中文件
git rm --cached index.php

# 如果有删除错了的文件hd.js 可输入下列命令
git checkout hd.js

# 修改最后一次提交 
git commit --amend
```
<a name="UmcR5"></a>
## 分支流程

---

大部分情况下不会直接在 master 分支工作，我们应该保护这个分支是最终开发完成代码健康可交付运行的。<br />所以功能和缺陷(bug)修复都会新建分支完成，除了这个概念外与基本流程使用是一样的。

1. **新建支付功能开发分支**
> git branch pay

2. **切换到新分支开始开发，这里的工作内容与上面的基础流程是一样的**
> git checkout pay

3. **开发完成执行提交 **
> git commit -m 'H5 支付功能'

4. **合并分支到 master**
> 切换到master分支<br />git checkout master

合并pay分支的代码<br />git merge pay

5. **提交代码到 master 远程分支**
> git push

<a name="xs4Qg"></a>
## 基本管理

---

<a name="wNQt3"></a>
### 工作区管理
git clean 命令用来从工作目录中删除所有没有跟踪（tracked）过的文件

1. git clean -n是一次 clean 的演习, 告诉你哪些文件会被删除
1. git clean -f删除当前目录下没有 tracked 过的文件，不会删除.gitignore 指定的文件
1. git clean -df删除当前目录下没有被 tracked 过的文件和文件夹
<a name="lHYYL"></a>
### 暂存区管理

1. 提交所有修改和新增的文件 git add .
1. 只提交修改文件不提交新文件 git add -u
1. 放弃没有提交的所有修改 git checkout .
1. 放弃指定文件的修改 git checkout hd.js
1. 查看暂存区文件列表 git ls-files -s
1. 查看暂存区文件内容 git cat-file -p 6e9a94
<a name="rcBqJ"></a>
### 版本库管理
使用 reset 恢复到历史提交点，重置暂存区与工作目录的内容。

1. 清空工作区和暂存区的改动 git reset --hard
1. 恢复前三个版本 git reset --hard HEAD^^^
1. 保留工作区的内容，把文件差异放进暂存区 git reset --soft
1. 恢复到指定提交版本（先通过 git log 查看版本号) git reset --hard b7b73147ca8d6fc20e451d7b36
<a name="ms94p"></a>
### 分支管理
分支用于为项目增加新功能或修复 Bug 时使用。

1. 创建分支 git branch dev
1. 查看分支 git branch
1. 切换分支 git checkout dev
1. 创建并切换分支 git checkout -b feature/bbs
1. 合并 dev 分支到 master
> git checkout master<br />git merge dev

6. 删除分支 git branch -d dev
6. 删除没有合并的分支git branch -D dev
6. 删除远程分支 git push origin :dev
6. 查看未合并的分支(切换到 master) git branch --no-merged
6. 查看已经合并的分支(切换到 master) git branch --merged
<a name="n1KDP"></a>
### Tag
Git 也可以对某一时间点上的版本打上标签 ，用于发布软件版本如 v1.0

1. 添加标签 git tag v1.0
1. 列出标签 git tag
1. 推送标签 git push --tags
1. 删除标签 git tag -d v1.0.1
1. 删除远程标签 git push origin :v1.0.1
<a name="WW6hq"></a>
### 日志查看

1. 查看日志 git log
1. 查看最近 2 次提交日志并显示文件差异 git log -p -2
1. 显示已修改的文件清单 git log --name-only
1. 显示新增、修改、删除的文件清单 git log --name-status
1. 一行显示并只显示 SHA-1 的前几个字符 git log --oneline
<a name="Iiri4"></a>
## 效率提升

---

<a name="roYPX"></a>
### 定义别名
通过创建命令别名可以减少命令输入量，有几种方式进行设置

1. **配置文件定义**

修改配置文件 ~/.gitconfig 并添加以下命令别名配置段
> [alias]<br />	a = add .<br />	c = commit<br />	s = status<br />	l = log<br />	b = branch

现在可以使用 git a 实现 git add . 一样的效果了。

2. **系统配置定义**

window 用户可以修改~/.bashrc 或 ~/.bash_profile文件。<br />mac/linux 修改 ~/.zshrc 文件中定义常用的别名指令，需要首先安装 zsh 命令行扩展
```json
alias gs="git status"
alias gc="git commit -m "
alias gl="git log --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit  "
alias gb="git branch"
alias ga="git add ."
alias go="git checkout"
```
命令行直接使用 gs 即可以实现 git status 一样的效果了。<br />window 系统需要使用 git for window 中的 Git Base 软件
<a name="a65WB"></a>
### .gitignore
.gitignore 用于定义忽略提交的文件

- 所有空行或者以注释符号 ＃ 开头的行都会被 Git 忽略。
- 匹配模式最后跟反斜杠（/）说明要忽略的是目录。
- 可以使用标准的 glob 模式匹配。
```javascript
.idea
/vendor
.env
/node_modules
/public/storage
*.txt
```
<a name="cNnLy"></a>
### 冲突解决
不同分修改同一个文件或不同开发者修改同一个分支文件都可能造成冲突，造成无法提交代码。

1. 使用编辑器修改冲突的文件
1. 添加暂存 git add . 表示已经解决冲突
1. git commit 提交完成
<a name="oPHbm"></a>
### Stashing
当你正在进行项目中某一部分的工作，里面的东西处于一个比较杂乱的状态，而你想转到其他分支上进行一些工作。问题是，你不想提交进行了一半的工作，否则以后你无法回到这个工作点。<br />“暂存” 可以获取你工作目录的中间状态——也就是你修改过的被追踪的文件和暂存的变更——并将它保存到一个未完结变更的堆栈中，随时可以重新应用。

1. 储藏工作 git stash
1. 查看储藏列表 git stash list
1. 应用最近的储藏 git stash apply
1. 应用更早的储藏 git stash apply stash@{2}
1. 删除储藏git stash drop stash@{0}
1. 应用并删除储藏 git stash pop
<a name="TEVxr"></a>
## 远程仓库
下面是最热的Github进行讲解，使用码云、codeing 等国内仓库使用方式一致，就不在赘述了。
<a name="QDnj5"></a>
### SSH

- **生成秘钥**

使用 ssh 连接 Github 发送指令更加安全可靠，也可以免掉每次输入密码的困扰。查看本机密钥：
> ssh-keygen -t rsa

一直按回车键直到结束。系统会在~/.ssh 目录中生成 id_rsa和id_rsa.pub，即密钥id_rsa和公钥id_rsa.pub。

- **向 GitHub 添加秘钥**

点击 New SSH key 按钮，添加上面生成的 id_rsa.pub 公钥内容。
<a name="OiLDT"></a>
### 关联远程

1. 创建本地库并完成初始提交
```powershell
echo "# hd-xj" >> README.md
git init
git add README.md
git commit -m "first commit"
```

2. 添加远程仓库
```powershell
git remote add origin git@github.com:houdunwang/hd-xj.git
```

3. 查看远程库
```powershell
git remote -v
```

4. 推送数据到远程仓库
```powershell
git push -u origin master
```

5. 删除远程仓库关联
```powershell
git remote rm origin
```

通过 clone 克隆的仓库，本地与远程已经自动关联，上面几步都可以省略。
<a name="wv00K"></a>
### pull
拉取远程主机某个分支的更新，再与本地的指定分支合并。

1. 拉取 origin 主机的 ask 分支与本地的 master 分支合并 git pull origin ask:ask
1. 拉取 origin 主机的 ask 分支与当前分支合并 git pull origin ask
1. 如果远程分支与当前本地分支同名直接执行 git pull
<a name="ZsmAp"></a>
### push
git push命令用于将本地分支的更新，推送到远程主机。它的格式与git pull命令相似。

1. 将当前分支推送到origin主机的对应分支(如果当前分支只有一个追踪分支 ，可省略主机名)
> git push origin

2. 使用-u选项指定一个默认主机 ,这样以后就可以不加任何参数直播使用git push。
> git push -u origin master

3. 删除远程ask分支 
> git push origin --delete ask

4. 本地 ask 分支关联远程分支并推送 
> git push --set-upstream origin ask

<a name="umFfO"></a>
### 多库提交
我可以将代码提交到多个远程版本库中，比如后盾人的 [课程代码](https://gitee.com/houdunren/code) 就提交到了 Github 与 Gitee 两个库中。
```powershell
# 增加一个远程库
git remote add github git@github.com:houdunwang/coding.git

# 提交到远程库
git push github
```
也可以创建命令一次提交到两个库(注：参考上面的命令设置章节)
> alias gp="git push & git push github"



补充。。。 多库提交 别名 安装 工作原理  服务器架设

---

相关网站<br />[https://www.liaoxuefeng.com/wiki/896043488029600/896067074338496](https://www.liaoxuefeng.com/wiki/896043488029600/896067074338496)<br />[https://www.runoob.com/git/git-tutorial.html](https://www.runoob.com/git/git-tutorial.html)<br />[https://www.cnblogs.com/imyalost/p/8762522.html](https://www.cnblogs.com/imyalost/p/8762522.html)<br />[https://blog.csdn.net/adasdvvv/article/details/121299834](https://blog.csdn.net/adasdvvv/article/details/121299834)<br />[https://www.cnblogs.com/my-freedom/p/5701427.html](https://www.cnblogs.com/my-freedom/p/5701427.html)<br />[

](https://www.cnblogs.com/my-freedom/p/5701427.html)

