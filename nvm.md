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
