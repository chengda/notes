
# VirtualBox 安装 Mac OS 的步骤
## 1. 下载苹果安装盘
## 2. 创建 virtual box 虚拟机
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
## 5. 配置
## 5.1. 网络
## 5.2. 软件
