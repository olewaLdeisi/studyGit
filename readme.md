# 学习git命令笔记
## 1. 基础命令
+ `git init` 创建版本库
+ `git status` 版本库变化
+ `git diff` 变化内容
+ `git add` 添加修改
+ `git commit` 保存快照
+ `git log` 日志查看
## 2. 版本回退
+ `git reset --hard HEAD^`
  退回到上一个版本，上上个版本则是两个`^`，撤销某次提交，但此次之后的修改都会被退回到暂存区，有mixed，soft，hard模式
  + soft HEAD位置修改，索引不修改，工作树不修改 
  + mixed HEAD位置修改，索引修改，工作树不修改 
  + hard HEAD位置修改，索引修改，工作树修改   
    应用场景:
  + 复原修改过的索引的状态 mixed
  + 彻底取消最近的提交 hard
  + 只取消提交 soft
+ `git checkout -- 文件名` 丢弃工作区的修改，回退改文件最近一次commit或add的状态
态
 + `git revert` 撤销某次操作，
   此次操作之前和之后的commit和history都会保留，并且把这次撤销作为一次新的提交
## 3. 远程仓库
+ `git remote add origin git@github.com:michaelliao/learngit.git`
  本地仓库关联远程仓库
+ `git push origin master` 提交到远程仓
+ `git clone git@github.com:michaelliao/gitskills.git` 克隆到本地仓   
+ `git remote` 或者 `git remote -v `查看远程库信息
+ `git push origin 分支名` 推送到分支
+ `git checkout -b dev origin/dev` 创建远程`origin`的`dev`分支到本地
+ `git pull` 抓取最新提交
+ `git branch --set-upstream-to=origin/dev dev`
  指定本地`dev`分支与远程`origin/dev`分支的链接
+ `git rebase` 可以把本地未push的分叉提交历史整理成直线 [rebase](http://gitbook.liuhui998.com/4_2.html)
## 4. 分支管理
+ `git checkout -b 分支名` 创建分支，加上-b参数表示创建并切换，相当于执行`git
  branch 分支名` 和 `git checkout 分支名`
+ `git branch` 查看当前分支
+ `git branch -d dev` 删除分支, `-D`强制删除
+ `git checkout 分支名` 切换分支
+ `git merge 分支名` 合并'分支名'到当前分支
+ `git log --graph --pretty=oneline --abbrev-commit` 查看合并分支情况
+ `git merge --no-ff -m "merge with no-ff" dev` 禁用Fast forward 
+ `git stash` 保存工作现场, 可切换别的分支进行修改提交后，返回原来现场
  + `git stash list` 查看刚才的工作现场
  + `git stash apply` 恢复，但是恢复后，stash内容并不删除，你需要用`git
    stash drop`来删除, `git stash apply stash@{0}` 恢复到指定的stash
  + `git stash pop` 恢复的同时把stash内容也删了  
## 标签管理
+ `git tag 标签名` 给当前分支最新提交的commit打标签, 后可加commit id