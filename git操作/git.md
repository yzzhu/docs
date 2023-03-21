# 初始化本地项目
```shell
cd existing_folder
git init
git remote add origin URL
git add .
git commit -m "init"
git push -u origin master
```

# 远端仓库同步
## 只有一个分支
- 先fork一个工程到自己名下
- git clone 自己名下的工程到本地
- 执行git remote add upstream 上游仓库url
- 后续每次本次仓库commit完成后，执行git fetch upstream/master同步上游代码至本地仓库
- 执行git merge upstream/master master 合并上游仓库代码到本地代码 可能会有冲突 处理
- 执行git push -u origin master 同步本地代码至远端仓库
  

# 分支同步
## 上游分支同步至远端
origin fork后 upstream又新建了分支(dev)，此时origin中没有这个分支，本地库中也没有
- 本地新建并切换至上游同名分支 git checkout -b dev 此时本地有了dev分支
- 将新的分支推送到origin git push -u origin dev  此时origin有了dev分支 且本地分支跟踪origin对应分支
- 拉取upstrem git fetch upstream 此时会获取到upstream的分支信息
- merge upstream dev分支至本地git merge upstream/dev dev
## 远端有分支 本地没有
- 先git fetch 获取远端分支信息
- git checkout -b dev1 origin/dev1即可 或者 git checkout --track origin/dev1 则自动创建dev1分支并跟踪origin/dev1
## 本地有分支 远端没有 
- git push -u origin dev1 即可
## 本地有 远端也有
- git checkout --track origin/dev1


# 常用命令
- git remote -v 查看远程仓库信息
- git remote add upstream URL 添加上游仓库
- git remote set-url upstream URL 修改上游仓库地址
- git status 查看本地库当前状态
- git stash 将当前工作区暂存 会有编号
- git stash list 查看当前git栈中暂存了哪些信息
- git stash pop 恢复暂存的信息，也可带上编号恢复制定暂存内容
- git log 查看commit历史
- git diff 查看不同commit 不同branch的不同