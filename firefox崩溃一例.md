# firefox崩溃一例
## 现象
几乎所有网页都打不开，全部报崩溃。

## 解决
地址栏输入 ```about:config```，筛选条件中输入 ```browser.tabs.remote.autostart```，将其值设置为false。 如下图：
![authostart](_v_images/20190420233300699_1234124829.png)
