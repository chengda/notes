# idea字体锯齿问题
idea的字体在linux下着实难看，锯齿严重。
intellij有自己修改过的openjdk，对这个问题有专门的优化。
* https://bintray.com/jetbrains/intellij-jdk
>JetBrains Runtime is a runtime environment for running IntelliJ Platform based products on Windows, Mac OS X, and Linux. JetBrains Runtime is based on OpenJDK project with some modifications. These modifications include: Subpixel Anti-Aliasing, enhanced font rendering on Linux, HiDPI support, ligatures, some fixes for native crashes not presented in official build, and other small enhancements. 
>
>JetBrains Runtime is not a certified build of OpenJDK. Please, use at your own risk.

所以，解决idea字体锯齿问题的方案有两个：
1. 直接下载内嵌jre的idea包
或者
2. 已经安装了不含jre的idea的，可以通过上面的那个地址单独下载jdk。

如果使用pacman，那么还有一个办法。
在/etc/pacman.conf中增加配置
```
[archlinuxcn]
SigLevel = Optional TrustedOnly
Server = https://mirrors.ustc.edu.cn/archlinuxcn/$arch
```
然后可以通过pacman安装idea及idea-jre
```
# sudo pacman -S intellij-idea-ultimate-edition
# sudo pacman -S intellij-idea-ultimate-edition-jre
```
idea和idea-jre会被安装在/opt下面同一个目录下。
