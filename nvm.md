# 使用 nvm （node version manager） 轻松管理node各个版本
1. 下载安装 nvm
```js
curl https://raw.githubusercontent.com/creationix/nvm/v0.13.1/install.sh | bash

source ~/.bash_profile
```
2. 列出所有版本（远程）
```js
nvm list-remote
```
3. 安装相应版本
```js
nvm install v8.9.3
```
4. 查看已经安装的版本
```js
nvm list
```
5. 切换版本
```js
nvm use v8.9.4
```
6. 设置默认版本
```js
nvm alias default v8.9.4
```
7. 使用系统的版本
```js
nvm use system
```

************************************

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
// rich branch addd ...
git checkout master // 切换回主分支
// change rich branch /////
git log --oneline // 查看分支情况

git log --all --oneline // 将所有分支情况显示到一行上
git log --oneline --all -graph  // 图形化显示
git checkout master // 切换回主分支
git merge feature  // 合并feature 分支到master分支

git remote add origin  //  origin 其实是给远程仓库取名字 ， github 默认的远程仓库就是origin
