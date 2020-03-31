# 1. 问题现象
- VirtualBox虚拟机，安装Win10操作系统
- 虚拟机中安装Office2013后，打开黑屏
- 按住Ctrl点击启动Word等Office程序可以打开进入“安全模式”

# 2. 问题原因
可能是因为office默认使用图形硬件加速，跟虚拟机环境有不匹配的地方。

# 3. 解决办法
既然是图形硬件加速问题，那就禁掉office的硬件加速。

- Win+R，输入regedit 打开注册表编辑器
- 在【HKEY_CURRENT_USER\Software\Microsoft\Office\15.0\Common】下面新建一个子项Graphics
- 在【HKEY_CURRENT_USER\Software\Microsoft\Office\15.0\Common\Graphics】下新建一个键，名称为：DisableHardwareAcceleration，值设置为1
- 重启，问题解决。
