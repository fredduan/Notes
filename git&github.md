### git安装
- https://www.udacity.com/wiki/ud775/install-git


### git命令（MAC）
#### 1. 基本命令
- git --version :查看git的版本
- which git : 查看git环境路径
- git clone url : 从url复制一个repository到本地当前路径下
- git log : 进入一个repository后，输入该命令可以查看所有的commit(提交)历史
- git config --global color.ui auto : 获得彩色的diff输出
- git diff first_commit_id second_commit_id : diff用来比较两个commit的区别
- git diff : 没有后面的参数时，该命令比较的是working directory和staging area的不同
- git diff --staged : 比较的是staging area和repository
- git checkout first_commit_id : 用来暂时将文件退回到checkout的commit
- git config --global core.editor "atom --wait" : 将Atom设置为默认的文档编辑器,并使用“atom --wait”用terminal打开atom
- git init : 在一个路径下使用这个命令，将会让该路径成为一个新的repository
- git status : 输出当前repository的状态信息
- git add file : 将文件加入暂存区（staging area）
- git commit : 提交，将会打开Atom编辑器，然后在COMMIT_EDITMSG里写上你对这次提交的注释，然后保存
- git commit -m "some messages" : 提交，不会打开Atom，后面写的一句话相当于在COMMIT_EDITMSG里写的注释
- git reset --hard : 将working directory和staging area中（还未commit）的改变清除（注意：一旦清除，无法找回）

#### 2. branch
- git branch : 不带任何参数，输出当前branch。其中，前面带*号的branch是会被更新的branch
- git branch branch_name : 后面加个名字，会新建一个该命名的branch
- git checkout branch_name : 令branch_name这个branch成为当前的branch，相当于cd进入一个路径
- git log --graph --oneline branch_name : 可视化，查看一个branch的结构

#### 3. merge
- git merge branch_name_1 branch_name_2 : 第二个branch将会并入第一个branch,在合并时，要保证当前带*的branch至少是两个合并的branch中的一个
- git show commit_id : 用来在不知道一个commit的parent是谁时，显示commit和它的parent的不同点
- git branch -d branch_name : 用来删除一个branch
- git merge --abort : 将文件恢复到你开始合并之前的状态
- git config --global core.autocrlf true : Windows 将 autocrlf 全局属性设置为 true。用于解决window和linux用户的回车换行符在合并时的冲突

### github命令（MAC）
#### 1. 基本命令
- git remote : 查看所有remote的repository
- git remote -v : 查看所有remote的更多信息
- git remote add remote_name URL : 将github上的repository添加到本地，并取名为remote_name
- git push remote_name branch_name : 将本地的commit推到github上去
- git pull remote_name branch_name : 将github上的commit下拉到本地
- git fetch remote_name : 下载github上master的commit，但是仅用它更新本地的远程副本分支，默认为origin/master，而不是真正的本地master，这样你的本地repository就有origin和master两个分支了，可以用merge将两个分支合并，实现pull的功能。这种方式用于当本地的commit和github上的commit不同步时，避免二者冲突。
- git config --system core.longpaths true : 修改window路径长度限制


## github新建、提交、下载流程
### 新建
- 在github上面新建一个repository
- clone到本地
- 在本地文件夹里新建文件等等
### 提交
- git add -a: 将所有文件加入到缓存区
- git commit -a: 将所有缓存区的东西提交
- git push origin master: 将所有“origin”remote的commit推到github上的“master”branch上
### 下载
- git pull origin master: 将github上的“master”branch上的commit下拉到本地的“origin”remote
