# 安装：
```
git config --global user.name "Vickie"
git config --global user.mail "wenjuntingai@163.com" 
```
注意git config命令的--global参数，用了这个参数，表示你这台机器上所有的Git仓库都会使用这个配置，当然也可以对某个仓库指定不同的用户名和Email地址。
# 创建版本库（repository）
## 1. 创建一个空目录：
```
mkdir learngit
cd learngit
pwd
/Users/Vickie/learngit
```
pwd命令用于显示当前目录,即/c/Users/Vickie/learngit
## 2. 通过git init命令把这个目录变成Git可管理的仓库
```
git init
Initialized empty Git repository in C:/Users/Vickie/learngit/
```
创建了一个空仓库，当前目录下多了.git目录，用来跟踪管理版本库，通常不做改动。如果没有看到.git目录，可能被隐藏了，使用命令ls -ah 可以看到。
## 把文件添加到版本库
1. 编写一个readme.txt文件；
2. 务必放到learngit目录下（子目录也可）；
3. 把文件放到Git仓库只要两步：
```
git add readme.txt
git commit -m "wrote a readme.txt"
[master (root-commit) eaadf4e] wrote a readme file
1 file changed, 2 insertions(+)
create mode 100644 readme.txt
```
commit 可以一次提交很多文件，可以多次add 不同的文件。
```
git add file1.txt
git add file2.txt file3.txt
git commit -m "add 3 files."
```