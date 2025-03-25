```python
一、git命令
```

git -h：用于显示 Git 命令的帮助信息
![alt text](<git -h.png>)

git status：显示当前工作树的状态。
![alt text](<git status.png>)

ping github.c![alt text](<ping github.com.png>)om：检查网络是否通信


git clone https://github.com/JiayiLiu07/big_data_project.git:克隆 远程的项目
![alt text](<git clone.png>)

git branch:显示所有本地分支，当前分支前会有一个星号（*）标记。![alt text](<git branch.png>)


git pull:用于从远程仓库获取（fetch）并合并（merge）当前分支的最新内容。（远程到本地）![alt text](<git pull.png>)


git push:用于将本地仓库的更新推送到远程仓库。（本地到远程）
![alt text](<git push.png>)

git checkout xxx：切换到xxx（其他)分支


二、修改 README.md文件 本地同步到远程的完整流程示例：
1. vim README.md：修改 README.md文件】
2. git add：【添加所有修改】将工作区的修改添加到暂存区的命令。
3. git status：【查看状态（确认已添加）】
4. git commit：【提交】用于永久保存代码变更的核心命令。它的作用是将当前工作目录中的修改（已通过 git add 添加到暂存区）记录到本地仓库，并附带一个描述性的提交信息（commit message），以便后续追踪历史。（仅保存到本地仓库）
5. git push：【git push】
