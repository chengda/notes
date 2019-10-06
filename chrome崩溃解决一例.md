# chrome崩溃解决一例
## 现象：
部分网站打开时显示“哎唷，网站崩溃了”，一般是下载内容比较多时

## 解决：
 
* 卸载
```
# sudo pacman -Rsn google-chrome
```
* 清理配置文件
```
# rm -fr ~/.config/google-chrome
```
* 重新安装
```
# sudo pacman -Sy google-chrome
```