# manjaro多个程序莫名其妙闪退或无法打开
## 原因分析
原来正常，自从清理了一遍软件包以后就出现各种异常。
清理用的命令是：
 
     # sudo pacman -Rsn $(pacman -Qdtq)

可能删除了一些不该删除的配置信息。
这个问题可能是因为修改了系统的最大栈尺寸导致的。

## 解决办法

    # ulimit -s 102400

