# cordova热更新
## 1. 热更新准备工作
### 1.1. 开发准备
#### 1.1.1. 安装热更新插件
进入 cordova工程，执行：

    # cordova plugin add cordova-hot-code-push-plugin 

#### 1.1.2. 配置config.xml
在根元素内增加下面内容：

    <chcp>
        <auto-download enabled="true" />
        <auto-install enabled="true" />
        <native-interface version="1" />    
        <config-file url="https://************/www/chcp.json" />
    </chcp>

config-file：配置文件 chcp.json 从服务器上加载的路径（必须的配置项）
auto-download：是否自动下载热更新代码，默认是 true
auto-install：是否自动安装热更新代码，默认是 true
native-interface：当前 native side 的版本号

#### 1.1.3. 安装热更新脚手架

    # sudo npm install -g cordova-hot-code-push-cli
 
* 安装过程中可能会出现下面的异常：

        ngrok - install failed { [Error: EACCES: permission denied, 
        open '/usr/lib/node_modules/cordova-hot-code-push-cli/node_modules/ngrok/bin/
        aHR0cHM6Ly9iaW4uZXF1aW5veC5pby9jLzRWbUR6QTdpYUhiL25ncm9rLXN0YWJsZS1saW51eC1hbWQ2NC56aXA=.zip']...
 
 应该是权限问题引起的，但为什么root也没有权限没有深究，可以通过下面方法解决：

    # sudo npm config set unsafe-perm=true
 

#### 1.1.4. 初始化热更新环境

进入cordova工程目录，执行：

    # cordova-hcp init

该命令执行过程中会要求回答一系列问题：
 
    Project name: 你现在的项目名称所需.
    Amazon S3 Bucket name:亚马逊上的S3桶的名字。可以跳过。
    Amazon S3 region: 亚马逊S3地区。可以跳过。
    iOS app identifier: 应用程序商店的应用程序ID。App升级是跳转应用商店进行升级。
    Android app identifier: 可以App在应用商城的地址，或者是apk的下载地址。
    Update method: 何时执行更新。
        start: 在启动应用程序时安装更新。
        resume: 在恢复应用程序(从背景移动到前景状态)或启动时，安装更新；默认使用。
        now: 从服务器加载更新后立即安装。
    Enter full URL to directory where cordova-hcp build result will be uploaded: 完整路径。

命令执行成功后会生成cordova-hcp.json文件，内容如下：

    {
      "name": "",//可为空
      "ios_identifier": "id123456789",//应用在App store id(可为空)
      "android_identifier": "",//应用在应用商城上的地址或者App的下载地址(可为空)
      "update": "start",//在应用启动时安装
      "min_native_interface": 1,//可用以做App升级（可以不填)
      "content_url":
      "http://************/cordova/www"//www文件在服务器上的地址
    }

#### 1.1.5. 在www目录下生成热更新配置文件
进入cordova工程，执行命令：

    # cordova-hcp build

该名称会生成下面两个文件：

* chcp.json: 包含发布相关信息：热更新代码版本号，应用 native side 版本号等等
* chcp.manifest: 包含项目热更新代码(静态)文件信息：文件名和文件哈希值

执行此命令会在chcp.json文件中增加"release":"当前时间"字段。（默认使用时间戳，格式为：yyyy.MM.dd-HH.mm.ss），插件将版本号进行字符串相等比较来判断是否存在新版本。
"release": "2017.06.07-16.30.20",//唯一web项目版本号,用与热更新web内容的更新。（必需）

#### 1.1.6. 编译cordova app
进入cordova工程，执行编译命令：

    #cordova build android

安装app就不写了啊。
    
### 1.2. 部署准备
以下步骤在部署服务器上进行。部署服务器需要预先安装nodejs和npm。
#### 1.2.1. 安装热更新脚手架
* 参见1.1.3

#### 1.2.1. 建立app发布工作目录
比如建立下面的目录结构：

/var/opt/cordova  
/var/opt/cordova/www

#### 1.2.2. 初始化热更新环境
进入app发布工作目录，本例中是/var/opt/cordova，执行下面命令：

    # cordova-hcp init

* 参照1.1.4进行操作。

#### 1.2.3. 发布代码到www目录
*  **注意：** 必须包含index.html，且index.html中必须引入cordova.js，因为触发更新的代码写在cordova.js中，不引入不会更新。

#### 1.2.4. 构建热更新版本
在热更新工作目录下：

    # cordova-hcp build
    
会在www文件中生成chcp.json和chcp.manifest

#### 1.2.4. 配置web服务器
比如nginx，alias www目录，让www目录下的文件可以被通过网络访问，这个url要跟前面config.xml和cordova-hcp.json中的url一致。

## 2. 日常更新
日常更新如果不涉及原生部分，那么只需要把h5页面文件上传到部署服务器的www目录下，然后在部署工作目录下执行：

    # cordova-hcp build

就会自动更新www目录下的chcp.json和chcp.manifest文件。重新打开app就可以自动更新了。

* 注意：为了客户体验，热更新是异步执行的。 第一次打开app，只会下载新版本但不会更新；第二次打开app才会更新，但仍然是异步更新的，如果更新能容较多，可能需要等待一会才能看到更新后的效果。