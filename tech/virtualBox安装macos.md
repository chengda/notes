
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

## 5. 配置



## 5.1. 网络
## 5.2. 软件
## 附录：

* 本文参考以下资料

https://blog.csdn.net/kaluosifa/article/details/87919734
