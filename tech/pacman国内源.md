# pacman国内源
## 1. 在/etc/pacman.conf中增加配置
```
[archlinuxcn]
SigLevel = Optional TrustedOnly
Server = https://mirrors.ustc.edu.cn/archlinuxcn/$arch
```
## 2. 执行下面命令
```
pacman-mirror -c China
```
* 对于始终无法信任的情况，选择Optional TrustAll 即可，所有res都用这个测略