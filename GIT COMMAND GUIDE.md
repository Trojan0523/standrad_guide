GIT COMMAND GUIDE

> 赶紧总结一下之前用到过的一些Git指令，以后别忘了

- git 本地分为工作区和暂存区，工作区即为当前未提交仍在写的代码区域，暂存区为add . / commit 后提交的代码存放区域

  ```
  // 版本历史
  Your branch is ahead of 'origin/master' by 1 commit
  	(use "git push" to publish your local commits)
  // 暂存区
  Changes to be commited: 
  	(use "git reset HEAD <file>... to unstage")
  // 工作区
  Untracked files: 
  	(use "git add <file>..." to include in what will be commited)
  ```

- git clone -b branch_name remote-url 从远端地址拉取项目的指定分支

- git config user.name/user.email (--local / --global) git设置当前环境或全局环境git用户名和git邮箱

- git branch -a （all）查看所有分支

- git checkout branch_name 切换到此分支

- git branch -d branch_name (-D 强制删除未合并) 删除选中分支

- git checkout -b branch_name 创建分支并将分支切换到创建分支中

- git log 查看commit历史

- git reflog 查看父分支中所有分支的commit提交

- git status 查看当前修改状态

- git add xxx.js / . 添加某个文件或所有文件到暂存区

- git commit -m "xxx: xxx"提交暂存区中文件，并为此提交填写提交信息

- git reset xxx.js / . 清除暂存区中某个或所有文件

- git merge branch_name 合并分支名分支到此分支

- git stash 冻结未提交代码到脏目录

- git stash save "stash message" 给每一个stash带上一个提交信息

- git stash list 脏目录提交列表查看

- git stash pop 将冻结代码释放到当前分支

- git reset --mixed HEAD^ 回退前一个提交 文件保留

- git reset --hard HEAD^ 强制回退前一个提交，提交文件不保留

- git push --set-upstream origin branch_name 本地创建新分支但是orgin远端没有，需要在push前创建远端当前分支

- git rebase branch_name 将分支名分支提交合并为一个提交合并到当前分支中(如果有冲突需要处理完冲突然后再进行合并)：

  ```
  git checkout branch_name
  git rebase target_branch_name
  merge confilct (处理冲突)...
  git add . (处理完冲突文件然后添加到暂存区)
  git rebase --continue || git rebase --abort (不想合并，退出当前合并)
  ```

- squash 多个commits成一个commit

  ```
  merge feature 到指定分支
  git checkout branch_name 切换到指定分支 
  git merge --squash feature
  git commit -m "squash: 这是一次squash commit"
  git push
  ```

- git push (--force 危险：不要强制推送分支) 将提交到本地暂存区分支提交到远端仓库

- git fetch 更新origin/*下所有分支，用于更新remote分支

- git pull 更新远端提交到本地分支中

- git merge --abort 取消一次合并

- git revert Head/[commit Hash] 回退一次commit

- git remote -v 查看origin远端仓库地址

- 创建一个新项目上传到git

  ```
  git init 初始化项目
  touch README.md
  git add .
  git commit -m "feat: first commit"
  git remote add origin remote repository URL
  ```

- Oh-my-zsh 常用命令

  - gst - git status
  - gaa - git add .
  - gcmsg "" - git commit -m ""
  - gp - git push
  - glog git log --online --decorate --graph
  - gl - git pull
  - gf - git fetch