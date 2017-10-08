[TOC]

## Git 指令

### 创建版本库

```
$ mkdir git_repo //创建文件夹git_repo，该文件夹作为git版本库
$ cd git_repo // 切换到git_repo目录下
$ git init  // 在git_repo目录下初始化版本库
```

### 把文件添加到版本库

```
$ git add <file> //把file添加到版本库
$ git commit -m 'message' //将更改提交到版本库，可以添加多个文件，一次提交。message是提交的备注，一定要添加，且用单引号括起来。
```

### 查看版本库

```
$ git status //查看版本库状态，包含已提交，已修改未添加，已添加未提交
$ git diff <file> //查看已修改未提交的文件修改内容
$ git log  --pretty=oneline //查看提交历史日志，也就是-m 'message' 记录的内容 参数pretty可以省略
```

### 版本回退

git中，`HEAD`表示当前版本，`HEAD^`表示上个版本，上上个版本用表示`HEAD^^`。往上100个版本记`HEAD～100`

```
git reset --hard HEAD^ //回退到上个版本。
git reflog //查看命令历史。
git reset --hard commit_id //根据commit_id回退到指定版本。其中commit_id可以根据git reflog 或git log 查看。
git diff HEAD -- <file> 查看工作区和版本库该文件的区别。
```

### 撤销修改

#### 未提交暂存区

修改过后，未使用`git add`提交到暂存区

```
git checkout -- <file>
```

#### 已提交暂存区

修改过后，使用`git add`提交到暂存区。这时候需要先回退暂存区的修改。再使用`git checkout`。

```
git reset HEAD <file>
```

#### 已提交版本库

使用版本回退方法撤销修改。

### 删除文件

删除工作区的文件后，可以选择从版本库恢复文件，也可以删除版本库的文件。

```
git rm <file> //删除版本库中的文件
```


### 添加远程库

添加远程库之前，需要配置证书，暂且不讨论。

```
git remote add origin <git url> //把本地仓库关联到GitHub上已有的仓库。远程库的名字是origin.
git push -u origin master //把本地库所有内容推送到远程库。第一次推送需要-u参数。
```

### 克隆远程库

```
git clone <git url> //从已有的远程库上，把内容克隆到本地来。
```

* **注：Git支持多种协议，包括`https`,但通过`ssh` 支持的原生Git速度更快。**

### 创建分支

```
git branch <分支> //创建分支
git checkout <分支> //切换分支

git checkout -b <分支> //也可以合并成一条指令

git branch //查看当前分支 当前分支前面会用* 标记
```

### 合并分支

```
git merge <分支> //合并分支。
git branc -d <分支> //合并分支之后，就可以放心的删除之前新建的分支。
```

合并分支时，如果有冲突需要解决冲突。解决冲突之后，才可以使用`git add` `git commit` 提交最终合并结果。

```
 git log --graph --pretty=oneline --abbrev-commit //查看分支合并情况
```

 **下面是我测试的内容，仅供参考**

```
*   28e86b5 conflict fixed
|\  
| * 49df264 call dev
* | d80aa32 call master
|/  
* ba6b11e crate a new branch
* 49681bd add test file
* 9702823 readme.txt 文件添加部分内容
* 0d9eeb4 修改ｒｅａｄｍｅ
* a0e7003 wrote a readme file
```

### 强制合并分支

git中，分支合并，默认使用`Fast forward` 模式，该模式下，如果有冲突需要手动合并。强制禁用该模式，git就会在merge时，生成一个新的commit。

```
git merge --no-ff -m "merge with no-ff" <分支> //强制合并，由于会生成一个新的commit，因此需要-m参数。把commit描述写进去。
```

### 保存工作现场

常用于，当前功能未开发完成，需要紧急修复一个bug，因此需要把当前所做修改保存起来（并未提交到暂存区）。待bug修复完毕，再切到当前工作区继续开发。

```
git stash //保存当前工作区
git stash apply //恢复之前保存的工作区，但并不删除stash内容
git stash drop //删除stash内容

git stash pop　//恢复的同时删除stash内容

git stash list //查看stash历史，保存多次的时候，会列举出每个stash id。

git stash apply <stash id> //恢复指定stash

```

### 强制删除分支

```
git branch -d <分支> //合并后可删除该分支
git branch -D <分支> //未合并，打算丢弃分之后删除该分支
```

### 合作开发

```
git remote //查看远程库信息
git remote -v //查看更详细的远程库信息
git push origin master //推送分支，通常是主分支，也可以切换成其他分支。
```

当从远程库clone时，默认只能抓取`master`分支。如果在子分支上合作开发，需要创建相同的子分支。

```
git branch --set-upstream-to=origin/<branch> <branch> //将本地分支链接到远程分支上

git pull //从远程分支获取内容
```

在本地新增子分支流程

- 如果远程仓库分支

```
git branch <子分支> //本地新建子分支
git push origin <子分支> //子分支发布到远程仓库
git checkout <子分支> //切换到新建的子分支
```

- 如果远程仓库有子分支

```
git checkout -b <子分支> origin/<子分支> //本地新建子分支并切换过去
```

- 在子分支目录下，获取远程仓库内容

```
git pull //获取远程仓库内容
```

- 获取内容失败，需要将本地子分支关联到远程子分支

```
git branch --set-upstream-to=origin/<分支> <分支>  //例子：git branch --set-upstream-to=origin/master master。就是两个分支名称，用空格分隔
```

```
git push origin :<分支> //删除远程仓库的分支，冒号代表删除
```

### 创建标签

标签的作用使提交记录更加规范化。commit id 是一串sha1，不好辨认。

```
git tag <tag> //最近提交的commit上创建标签
git tag <tag> <commit id> //指定的commit上添加标签
git tag -a <tag> -m "说明文字" <commit id> // 创建带有说明的标签
git tag //查看所有标签

git show <tag> //查看标签信息

```

**还可以通过`-s`用私钥签名一个标签，后续讨论。

### 操作标签

```
git tag -d <tag> //删除标签
git push origin <tag> //推送标签到远程
git push origin --tags //一次性推送全部尚未推送的本地标签到远程
git push origin :refs/tags/<tag> //删除远程标签，需要现在本地删除
```

### 配置别名

别名是为了方便输入指令

```
git config --global alias.br branch //`br` 表示`branch`
```

使用时：

```
git br <分支>
```

**配置文件存在于仓库目录下 `.git/config` 和用户主目录下`.gitconfig`中**