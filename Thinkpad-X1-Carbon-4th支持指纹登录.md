# 1. 设备
Thinkpad X1 carbon 2016(Gen 4)

# 2. 参考archlinux wiki
https://wiki.archlinux.org/index.php/Lenovo_ThinkPad_X1_Carbon_(Gen_4)#Fingerprint_Reader

https://aur.archlinux.org/packages/libfprint-vfs009x-git/

# 3. 步骤
## 3.1. 克隆源码
```
git clone https://aur.archlinux.org/libfprint-vfs009x-git.git
```
## 3.2. 构建打包
```
makepkg
```
如果遇到缺少依赖，请根据提示进行安装。
## 3.3. 离线安装
我这生成的文件包是：libfprint-vfs009x-git-1:1.90.1.r5.ge34de1d-2-x86_64.pkg.tar.zst
```
sudo pacman -U libfprint-vfs009x-git-1:1.90.1.r5.ge34de1d-2-x86_64.pkg.tar.zst
```
遇到与已经安装的软件包冲突，请根据提示选择删除原有软件包。
## 3.4. 录入指纹
```
fprintd-enroll
```
## 3.5. 验证指纹
```
fprintd-verify
```
