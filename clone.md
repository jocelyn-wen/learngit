# clone:
```
git clone https://github.com/Victin-Wen/learngit    (mylocalfoldername)
cd mylocalfoldername
ls //lookthrough files
```
## 如果添加远程github仓库时提示fatal: remote origin already exists 错误解决办法
1. 先删除远程Git库，
2. 再添加；
3. 如果执行git remote rm origin 报错可手动修改gitconfig内容
- 将dev分支合并到master上： `git merge dev`
- 合并完成后删除dev： `git branch -d dev`
- 查看branch： `git branch`
- 创建并切换到新的分支： `git switch -c dev` //
- 直接切换到已有的分支： `git switch master `//`git checkout master`
- 已成功添加并提交了一个readme.txt文件，修改。
- 运行 `git status`查看结果
 ```
git status
On branch master
Changes not staged for commit:
(use "git add <file>..." to update what will be committed)
(use "git checkout -- <file>..." to discard changes in working directory)

modified:   readme.txt

no changes added to commit (use "git add" and/or "git commit -a")
```
git status命令可以让我们时刻掌握仓库当前的状态，上面的命令输出告诉我们，readme.txt被修改过了，但还没有准备提交的修改。
虽然Git告诉我们readme.txt被修改了，但如果能看看具体修改了什么内容, 需要用git diff这个命令看看：
```
git diff readme.txt 
diff --git a/readme.txt b/readme.txt
index 46d49bf..9247db6 100644
--- a/readme.txt
+++ b/readme.txt
@@ -1,2 +1,2 @@
-Git is a version control system.
+Git is a distributed version control system.
 Git is free software.
```
git diff顾名思义就是查看difference，显示的格式正是Unix通用的diff格式，可以从上面的命令输出看到，我们在第一行添加了一个distributed单词。
提交修改和提交新文件是同样的两步：
`git add readme.txt`

在第二步之前再运行git status看看当前仓库的状态：
```
git status
On branch master
Changes to be committed:
(use "git reset HEAD <file>..." to unstage)

modified:   readme.txt
```
`git status`告诉我们，将要被提交的修改包括readme.txt，下一步，就可以放心地提交了：
```
git commit -m "add distributed"
[master e475afc] add distributed
1 file changed, 1 insertion(+), 1 deletion(-)
```
提交后再运行`git status`看看当前仓库的状态：
```
git status
On branch master
nothing to commit, working tree clean
```
Git告诉我们当前没有需要提交的修改，而且，工作目录是干净（working tree clean）的。
小结
随时掌握工作区的状态，使用`git status`命令。
如果`git status`查看文件是否被修改过，`git diff`可以查看修改的内容。
