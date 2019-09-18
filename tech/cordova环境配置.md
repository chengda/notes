# manjaro( archlinux ) 配置cordova环境
## 1. 安装环境软件
```
# sudo pacman -Sy nodejs
# sudo pacman -Sy npm
# sudo pacman -Sy android-sdk
# sudo pacman -Sy android-sdk-build-tools
# sudo pacman -Sy android-sdk-platform-tools
```
* 安装后要通过重启或者source /etc/profile使环境变量生效。

## 2. 安装android sdk target
```
# cd /opt/android-sdk/tools/bin
# sudo sdkmanager "platform-tools" "platforms;android-27"
```
## 3. 安装cordova
```
# npm install -g cordova
```
## 4. 创建cordova工程
```
# cordova create joys-mobile-app com.joysfintech.mobile.app  JoysCloud
```
* joys-mobile-app 工程目录名称
* com.joysfintech.mobile.app 默认的反向域名
* JoysCloud 应用名称

```
# cd joys-mobile-app
# cordova platform add android
```
## 5. 修改gradle仓库
默认jcenter仓库一般连不上，需要修改成国内仓库。
```
buildscript {
    repositories {
        maven{ url 'http://maven.aliyun.com/nexus/content/groups/public/'}
    }
}


allprojects {
    repositories {
        maven{ url 'http://maven.aliyun.com/nexus/content/groups/public/'}
    }
}
```
这几个地方都要修改：

* platform/android/build.gradle

* platform/android/app/build.gradle

* platfrom/android/CordovaLib/build.gradle

