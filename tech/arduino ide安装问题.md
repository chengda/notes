# arduino ide安装问题
## 1. 无法在模块路径中找到主题引擎：“murrine”
```
# sudo pacman -Sy gtk-engine-murrine
```
## 2. java.lang.UnsatisfiedLinkError: sun.font.FreetypeFontScaler.initIDs
```
# sudo pacman -Sy jdk8
```
## 3. java.lang.NullPointerException 	at processing.app.BaseNoGui.onBoardOrPortChange
```
# sudo pacman -S arduino-avr-core
```