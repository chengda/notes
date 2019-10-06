# git命令
## 1. 撤销所有修改（未提交）
    # git checkout .
    # git clean -xdf
## 2. stash 命令
stash是用来管理本地未提交的变更缓存的，变更被缓存后，当前工作区就变成干净的了，避免pull冲突。

### 2.1. 缓存本地修改
```
# git stash
```
或者
```
# git stash save 'xxxxxx'
```
### 2.2. 恢复本地修改
* 恢复上一次缓存的修改，并丢弃该次缓存  
```
# git stash pop
```
* 应用上次缓存，但并不丢弃缓存  
```
# git stash apply
```
### 2.3. 查看本地缓存
```
# git stash list
```
### 2.3. 删除本地缓存
* 删除本地某次缓存  
```
# git stash drop stash名称（在list中可以看到，类似stash@{0}）
```
* 删除本地所有缓存  
```
# git stash clear
```

## 3. config
### 3.1. 保存身份信息
```
git config --global credential.helper store
```
