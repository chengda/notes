# manjaro安装baidu云盘客户端
## 1. 思路
百度政治觉悟很高，适时推出了baidu云盘客户端的linux版！
目前支持麒麟和ubuntu，官网可下载rpm和deb包。
要在manjaro或者archlinux上安装，需要手工解包。

## 2. 步骤
### 2.1. 安装rpm解包工具
```
# pacman -Sy rpmextract
```
### 2.2. 下载baidunetdisk
```
# wget http://issuecdn.baidupcs.com/issue/netdisk/LinuxGuanjia/baidunetdisk_linux_2.0.1.rpm
```
### 2.3. 解包
```
# rpmextract baidunetdisk_linux_2.0.1.rpm
```
### 2.4. 移至适当目录
手工安装的软件一般放在/usr/local/下，所以按惯例移动一下文件位置。

解包后当前目录下会产生opt和usr两个目录，opt中是软件，usr中是桌面快捷方式。

#### 2.4.1. 移动软件目录
```
# mv ./opt/baidunetdisk /usr/local/
```
#### 2.4.2. 移动快捷方式目录
```
# mv ./usr/share/* /usr/local/share/
```
#### 2.4.3. 修改快捷方式
```
# vim /usr/local/share/applications/baidunetdisk.desktop
```
```
[Desktop Entry]
Name=baidunetdisk
Comment=百度网盘
Exec="/usr/local/baidunetdisk/baidunetdisk" %U
Terminal=false
Type=Application
Icon=baidunetdisk
StartupWMClass=baidunetdisk
Categories=Network;

```
* 主要就是修改执行文件的目录：Exec="/usr/local/baidunetdisk/baidunetdisk" %U

#### 2.4.4. 使用
在应用程序中查找baidunetdisk，就能找到软件快捷图标了。
