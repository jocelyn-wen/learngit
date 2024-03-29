<<<<<<< HEAD
# 版本退回

=======
## 版本退回
>>>>>>> 581cb35f579b3a3c1e7e88f92746f038cae335f7
用`git log`命令查看readme.txt文件一共有几个版本被提交到Git仓库里了：
```
git log
commit 103885de846b795073fefedfd050dcd437dc0e53 (HEAD -> master, origin/master, origin/HEAD)
Merge: 3af668f bbb01d4
Author: Victin <wenjuntingai@163.com>
Date:   Tue Dec 10 19:21:48 2019 +0800

Merge branch 'master' of https://github.com/Victin-Wen/learngit

commit 3af668faee40d841a121101433fc6c7d5c510572
Author: Victin <wenjuntingai@163.com>
Date:   Tue Dec 10 19:21:00 2019 +0800

Add

commit bbb01d4fdcd6fcf0f50d2f0ee255f5af91e34e2f
Author: Victin-Wen <57884453+Victin-Wen@users.noreply.github.com>
Date:   Tue Dec 10 18:53:07 2019 +0800
```
如果需要简洁版本：加参数 --pretty=oneline
```
git log --pretty=oneline
1094adb7b9b3807259d8cb349e7df1d4d6477073 (HEAD -> master) append GPL
e475afc93c209a690c39c13a46716e8fa000c366 add distributed
eaadf4e385e865d25c48e7ca9c8395c3f7dfaef0 wrote a readme file 
```
首先，Git必须知道当前版本是哪个版本，在Git中，用HEAD表示当前版本，也就是最新的提交，上一个版本就是HEAD^，上上一个版本就是HEAD^^，当然往上100个版本写成HEAD~100。
现在，我们要把当前版本append GPL回退到上一个版本add distributed，就可以使用git reset命令：
```
git reset --hard HEAD^
HEAD is now at e475afc add distributed
```
Git的版本回退速度非常快，因为Git在内部有个指向当前版本的HEAD指针，当你回退版本的时候，Git仅仅是把HEAD从指向append GPL：

命令git reflog用来记录你的每一次命令：
```
git reflog
e475afc HEAD@{1}: reset: moving to HEAD^
1094adb (HEAD -> master) HEAD@{2}: commit: append GPL
e475afc HEAD@{3}: commit: add distributed
eaadf4e HEAD@{4}: commit (initial): wrote a readme file
```
## 小结
HEAD指向的版本就是当前版本，因此，Git允许我们在版本的历史之间穿梭，使用命令git reset --hard commit_id。
穿梭前，用git log可以查看提交历史，以便确定要回退到哪个版本。
要重返未来，用git reflog查看命令历史，以便确定要回到未来的哪个版本。
