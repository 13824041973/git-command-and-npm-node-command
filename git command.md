学习自：向军大叔

```
https://www.bilibili.com/video/BV154411g7Wm
```

```
https://doc.houdunren.com/git/1%20%E6%8E%8C%E6%8F%A1GIT.html
```

###### <...>代表括号里的东西需要自己填写

# 基础

pwd            查看你现在所处的位置
mkdir         创建目录
touch         创建文件 
ls                查看目录列表
ls -a            查看所有目录列表(包括隐藏的)
ll                 查看详细目录列表

rm -rf *      删除所有目录(跑路命令)

# 配置个人信息

```git
git config --global user.email <yourEmail>
```

```
git config --global user.name <yourUserName>
```

###### alias给命令起别名

给add命令加别名a

```
git config --global alias.a add
```

##### 查看全局配置

直接命令行输入 cd 切换到家目录后

```
subl .gitconfig  (用sublime打开.gitconfig)
```

或者用自带的vim打开

```
vim .gitconfig
```

###### vim的操作和linux几乎一样，按i进入编辑模式，按ESC后按住（SHIFT+；），出现命令行，输入q直接退出，输入wq表示保存后退出

# 仓库

初始化仓库

```
git init
```

查看没有被管理的文件

```
git clean -n
```

把master分支下的文件打包成lyl.zip压缩包，解压后显示的文件夹为  lyl/

```
git archive master --prefix='lyl/' --forma=zip > lyl.zip
```

### git clone

从现有git库拷贝克隆

```
git clone
```

##### 远程克隆库到本地 

后面 + <folderName...> 代表克隆到本地的指定文件夹里面

```
git clone <url...>
```

仅克隆指定分支

```
git clone -b <branchName...> <url...>
```

### 工作区

查看工作区的状态

```
git status
```

### 暂存区

添加单一目标文件到暂存区

```
git add <目标目录...>
```

添加当前目录下所有文件到暂存区

```
git add .
```

### 仓库区

提交到本地仓库

```
git commit -m '描述提交的内容'
```

修改git提交记录

###### ps：进入后输入i进行编辑模式，esc退出，最后 :wq回车保存

```
git commit --amend
```

设置git提交忽略的配置文件

```
touch .gitignore
```

```
subl .gitignore
```

修改文件名

```
git mv <目标文件名...> <要修改成的文件名...>
```

### 使用log查看历史操作

查看log信息

```
git log
```

查看log的详细信息

```
git log -p
```

查看最近几次log的信息，数字可变动

```
git log -数字
```

查看简略的log信息（一行显示）

```
git log --oneline
```

简略的查看详细log信息

```
git log --name-status
```

### branch 分支

查看分支

```
git branch
```

创建分支

```
git branch <branchName...>
```

切换分支

```
git checkout <branchName...>
```

删除分支

```
git branch -d <branchName...>
```

强制删除分支   

###### ps:未合并的分支用-d删除不了

```
git branch -D <branchName...>
```

创建分支并切换到该分支

```
git checkout -b <branchName...>
```

 合并分支   

###### ps:注意切换到master分支再合并

```
git merge <branchName...>
```

查看与该分支的提交点相同的分支  

###### ps:新创建的分支提交点是跟master的一样的

```
git branch --merged
```

与该分支的提交点不相同的分支

```
git branch --no-merged
```

### stash 临时储存区

#### ps:将本地没提交的内容（还没commit的）进行缓存并从当前分支移除，缓存的数据结构为堆栈，先进后出。stash 只会操作被git追踪的文件，所以新增的文件记得git add .

将没有提交的内容缓存并移除，而这条缓存名称为最新一次提交的commit -m的内容

```
git stash
```

查看目前缓存的列表

```
git stash list
```

恢复最新的那条暂时储存区数据

```
git stash apply
```

恢复最新的那条暂时储存区数据，且删除此条暂时储存区

```
git stash pop
```

恢复指定的那条暂时储存区数据

```
git stash apply stash@{（num...）}
```

删除指定的那条缓存数据

```
git stash drop stash@{（num...）}
```

删除所有缓存数据

```
git stash clear
```

### rebase 变基，可以理解为改变基底

将待变基分支指向基分支的最新提交  

例如：将ask分支重新指向master分支的最新提交上,(指向master的最新的commit上，这样就算两个分支同时工作，那最后也能在master分支上合并ask分支了。)

###### ps:在需要变基的分支上用！

```
git rebase master
```

### 配置SSH密匙       看 向军大叔 P28

#### 服务器做主角

```
git clone 项目
git add .
git commit -m '测试本地仓库与远程仓库链接'
git push         （推送到远程仓库）
然后现在本地仓库和远程仓库就是一样的了
```

#### 本地做主角

```
先在本地“初始化仓库”并“初始提交”
git remote add origin <创建项目时需要连接的那个SSH链接...>             添加远程仓库
git remote -v                                                       查看远程库
git push -u origin master                                           推送数据到远程仓库
```

### GitHub

提交库文件至远程库

```
git push
```

从远程库拉取

```
git pull
```

将本地分支与远程分支同步并且推送数据

```
git push --set-upstream origin <branchName...>
```

拷贝远程某个分支

###### ps：记得先创建好分支并切换到该分支后再运行该命令

```
git pull origin <branchName...>
```

拷贝远程某个分支到本地的某某分支；（重命名）  

###### ps：实践时发现会自动合并分支到master

```
git pull origin <branchName...>:<branchName...>
```

删除远程分支

```
git push origin --delete <branchName...>
```

