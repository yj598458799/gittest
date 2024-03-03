# git cheat sheet

## 初始化

- git init name 创建一个新的本地代码库
- git config --global(local/system) --list 显示配置
- git config --global user.name "yinjing" 修改名字
- git config --global user.email "xxx@qq.com" 设置邮箱

## 本地操作

- git add file 将文件保存到暂存区
- git add . 将所有文件保存到暂存区
- git commit -am “xxx” 将暂存区的修改保存到代码库
- git commit -amend 撤销上一次提交，重新提交(使用于提交错误时，可以先修改再add，再使用此命令。历史记录只有一次)
- git status 查看当前状态，列出所有新修改、暂存区文件修改情况
- git log -n 显示最近n次commit记录
- git log --pretty=oneline 显示一行
- git log --pretty=format:"%h - %an ,%ar : %s" 格式化输出
- git reflog 显示所有操作记录
- git 
### 撤销

- git reset --hard commit_id 回滚版本
- git reset head~ 撤销本次提交，工作区变为本次提交的修改
- git reset HEAD file 将暂存区修改撤销,不影响工作区的修改
- git checkout file/. 将工作区修改撤销掉

### 暂存

- git stash 将工作区修改内容保存到贮藏区
- git stash pop 将贮藏区内容恢复到工作区
- git tag 列出代码库中所有的tag
- git tag -a <版本号> -m message 新增一个版本号

### 标签

- git tag v1.0   简单标签，只存储当前的commit的sha1值
- git tag -a v2.0 -m "我的v.2.0版本"   （创建一个新对象，会产生一个新的commit/sha1）存储信息，其中包含了当前的commit的sha1值
- git push origin v1.0 v2.0 推送标签 
- git push origin --tags
- git push origin v1.0
- 完整 git push origin refs/tags/v1.0:refs/tags/v1.0

- 远程新增标签
git pull  :如果远端新增标签，则pull 可以将新增的标签拉去到本地；如果远程是删除标签，则pull无法感知
git fetch orgin tag v4.0

- 删除远程标签
git push origin  :refs/tags/v1.0

注意：如果将远程标签删除，其他用户无法直接感知 

### 比较

- git diff file 查看工作区和暂存区差别
- git diff dev 查看分支差别
- git diff HEAD
- git diff --cached
- git diff commit_id

## 分支

- git branch -a 列出本地所有分支
- git switch -c name 创建一个新的name的分支
- git switch name 切换分支

### 创建跟踪分支

- git checkout --track origin/name  创建一个name的跟踪分支
- git checkout name 切换分支，如果刚好只有一个名字与之匹配的远程分支会自动创建跟踪分支
- git checkout -b name origin/name 切换分支，创建一个自定义名称的跟踪分支
- git branch -u origin/name 修改正在跟踪的上游分支
- git merge name 将name分支和当前分支合并
- git branch -d name 删除name 分支
- git branch -vv 查看设置的所有跟踪分支

## 远程操作

- git clone 项目url path 从远程库下周整个代码库和历史记录，path为本地仓库名
- git remote add <remote> <url> 链接一个远程库
- git fetch 从远程代码库下周所有变动
- git pull 从远程库拉取代码并将当前分支和它合并
- git push [remote][branch] 将当前代码库推送到远程remote库的branch分支
- git remote add origin local 为远程分支添加一个本地跟踪分支

## github

- 配置ssh：先在本地配置，发送给远程
- 本地生成ssh：ssh-keygen -t rsa -C 598458799@qq.com  一直回车
- github 设置ssh公钥
- 测试连通性：ssh -T git@github.com
- github建立仓库
- 本地项目-远程项目关联：git remote add origin git@github.com:yj598458799/mygit.git （本地先执行git init）
- 将本地仓库关联到Github流程(先在服务器创建一个空仓库，再将本地仓库按照空仓库的提示推送即可)

