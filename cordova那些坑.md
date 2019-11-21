## 1. plugin和platform安装顺序的坑
原来以为顺序不重要，结果被阿里云的推送（https://www.npmjs.com/package/cordova-plugin-aliyun-push）插件坑了一把。

**现象：**

第一次安装好阿里云推送插件，测试正常。后来删除和重新添加了android平台，结果死活不能用。

**原因：**

阿里云推送插件中有一个hook脚本

    <hook type="after_plugin_add" src="scripts/afterPluginAdd.js"/>
    
这个脚本会修改android的配置文件。如果安装插件以后，再新添加android平台，这个脚本就不会执行，导致android的配置文件错误。

**解决办法：**

只要管理好顺序喽。先添加平台，再添加插件。
