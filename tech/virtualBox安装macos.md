
# VirtualBox 安装 Mac OS 的步骤
## 1. 下载苹果安装盘

Mac OS 10.13下载链接：https://pan.baidu.com/s/1OpUIKmLdVuo4mZ_duuyrYA 提取码: e99c

## 2. 创建 virtual box 虚拟机

* 类型选择MacOS 64位

* 内存建议分配8G

* 磁盘分配50G以上

* 显存调到最大128M

* 网络设为为桥接网络

* 光盘挂载上面下载的安装盘iso文件，且启动顺序光盘优先


## 3. 修改虚拟机参数
```
vboxmanage modifyvm macos --cpuidset 00000001 000106e5 00100800 0098e3fd bfebfbff

vboxmanage setextradata macos "VBoxInternal/Devices/efi/0/Config/DmiSystemProduct" "iMac11,3"

vboxmanage setextradata macos "VBoxInternal/Devices/efi/0/Config/DmiSystemVersion" "1.0"

vboxmanage setextradata macos "VBoxInternal/Devices/efi/0/Config/DmiBoardProduct" "Iloveapple"

vboxmanage setextradata macos "VBoxInternal/Devices/smc/0/Config/DeviceKey" "ourhardworkbythesewordsguardedpleasedontsteal(c)AppleComputerInc"

vboxmanage setextradata macos "VBoxInternal/Devices/smc/0/Config/GetKeyFromRealSMC" 1

vboxmanage setextradata macos VBoxInternal2/EfiGopMode 4

vboxmanage setextradata macos VBoxInternal2/EfiGraphicsResolution 1440x900
```
## 4. 安装 Mac OS

按提示安装即可

* 安装过程中选择语言，简体中文

* 安装找不到磁盘，在顶部工具菜单下选择磁盘工具，抹掉内置磁盘，创建新的磁盘

* 继续安装macOS -> 选择刚创建的磁盘 -> 安装

## 5. 配置
## 5.1. 网络

在【系统偏好设置】-【网络】下设置，可设置固定IP等。

## 5.2. 软件

* 安装RVM

```
$ curl -L https://get.rvm.io | bash -s stable
```

* 安装Ruby
```
//列出已知的ruby版本
$ rvm list known

//可以选择现有的rvm版本来进行安装（以2.6.3为例）
$ rvm install 2.6.3
```
  安装Ruby过程中会自动安装HomeBrew

* 用HomeBrew安装软件 （以安装nodejs为例）

```
//查找软件
brew search node

//安装软件
brew install node
```

* 安装Xcode

最简单当然是在AppStore中安装，如果新版本不支持当前操作系统版本，那么需要手工下载老版本的xcode。

官方下载地址：https://developer.apple.com/download/more/

macos 10.13 可用的xcode最新版本是 xcode 9.0.1

## 附录：

* 本文参考以下资料

https://blog.csdn.net/kaluosifa/article/details/87919734
