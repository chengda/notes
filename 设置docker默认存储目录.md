# 设置docker默认存储目录
```
# vim /etc/docker/daemon.json
```
增加graph属性，值是docker存储目录。
```
{
    "graph": "/home/docker"
}
```