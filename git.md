
* git tag 用法

* 在当前版本打tag
```js
git tag -a 标签名字
git tag -a 标签名字 -m 为什么打标签说明
```
* 在之前的版本中追加tag
```js
git tag -a 标签名字 -m 为什么打标签说明 数字版本号
```

git branch feature // 新建分支

git checkout master // 切换回主分支

git log --oneline // 查看分支情况

git log --all --oneline // 将所有分支情况显示到一行上

git log --oneline --all -graph  // 图形化显示

git checkout master // 切换回主分支
git merge feature  // 合并feature 分支到master分支

git remote add origin  //  origin 其实是给远程仓库取名字 ， github 默认的远程仓库就是origin
