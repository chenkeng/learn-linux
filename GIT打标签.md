*Git 打标签*

    首先切换到要打标签的分支上面
```js
git branch
* dev
  master
git checkout master
Switched to branch 'master'
```
    敲命令git tag <name>就可以打一个新标签：

```js
git tag V1.0

```
    可以用命令git tag查看所有标签：

```js
git tag
V1.0

```
    默认标签是打在最新提交的commit上的。有时候，如果忘了打标签，比如，现在已经是周五了，但应该在周一打的标签没有打，怎么办？
    方法是找到历史提交的commit id，然后打上就可以了：

```js
git log --pretty=oneline --abbrev-commit
3f063d8 (HEAD -> master, tag: V1.0, origin/master, origin/HEAD) merged bug fix 101
a8b5c5e fix bug 101
c0d98d6 conflict fixed
24f92f4 coship
1f9f1d5 money
f8c2cfa branch test
c6bdeb5 remove test.txt
c61ac4f add test.txt
35b7969 append GPL
136d10c add two lines
1186b5e creat a new file readme
```

    比方说要对coship这次提交打标签，它对应的commit id是24f92f4，敲入命令：
```js
git tag V0.9 24f92f4

```
再用命令git tag查看标签：
```js
git tag
V0.9
V1.0
```
标签不是按时间顺序列出，而是按字母排序的。可以用git show <tagname>查看标签信息：

```js
git show V0.9
commit 45e3ab8dbb3e13acd16a3e2e08a83f1dfdde7ca5 (tag: v5.0)
Author: chenkeng <chenchaohan@outlook.com>
Date:   Sun Sep 16 18:20:11 2018 +0800

    coship

diff --git a/readme.txt b/readme.txt
index a4c0762..ced6222 100644
--- a/readme.txt
+++ b/readme.txt
@@ -1,3 +1,4 @@
Git is a distributed version control system.
Git is free software distributed under the GPL
I love work
+coship coship and coship
```
    可以看到，v0.9确实打在coship这次提交上。还可以创建带有说明的标签，用-a指定标签名，-m指定说明文字：

```js
git tag -a V0.1 -m "version 0.1 released" 1186b5e
```
    如果标签打错了，也可以删除：
```js
git tag -d V0.1
Deleted tag 'V0.1' (was fee78aa)
```

创建的标签都只存储在本地，不会自动推送到远程。所以，打错的标签可以在本地安全删除。如果要推送某个标签到远程，使用命令
```js
git push origin <tagname> 
```

```js
git push origin V1.0
Total 0 (delta 0), reused 0 (delta 0)
To github.com/chenkeng/learnJava.git

 * [new tag]         V1.0 -> V1.0
```

    一次性推送全部尚未推送到远程的本地标签：
```js
git push origin --tags
Total 0 (delta 0), reused 0 (delta 0)
To github.com/chenkeng/learnJava.git

 * [new tag]         V0.9 -> V0.9
```

    如果标签已经推送到远程，要删除远程标签就麻烦一点，先从本地删除：
```js
git tag -d V0.9
Deleted tag 'V0.9' (was 24f92f4)

```

    然后，从远程删除。删除命令也是push，但是格式如下：
```js
git push origin :refs/tags/V0.9
To github.com/chenkeng/learnJava.git

 - [deleted]         V0.9

```


    切换到标签版本
```js
git checkout v1.0
```