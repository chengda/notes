

# 1. 安装输入法
```
sudo pacman -S fcitx5-im 
```
``` 
# fcitx5-im 包组提供了:
# fcitx5                本体
# fcitx5-configtool     配置文件
# fcitx5-qt             对 Qt5 程序的支持
# fcitx5-gtk            对 GTK 程序的支持
 
# fcitx5-qt4-gitAUR     对 Qt4 程序的支持，此包不再fcitx5-im里面，有需要再另行安装。
``` 
 
# 2. 中文支持
fcitx5仅提供基本框架，仅提供英文支持，如果要输入其他语言，则需要输入法引擎。
```
sudo pacman -S fcitx5-chinese-addons
```
 
# 3. 环境配置
```
vim ~/.pam_environment  #写入以下内容
----------------------------------------
INPUT_METHOD  DEFAULT=fcitx5
GTK_IM_MODULE DEFAULT=fcitx5
QT_IM_MODULE  DEFAULT=fcitx5
XMODIFIERS    DEFAULT=\@im=fcitx5
``` 
 
# 4. 开机自启动
```
sudo cp /usr/share/applications/fcitx5.desktop  /etc/xdg/autostart/ 
```
 
# 5. 注销当前用户或者重启，应该就可以看到fcitx输入法了
 
 
