# gitlab访问被禁止问题
## 现象：
gitlab所有请求都返回Forbidden。

## 原因：
Gitlab使用rack_attack做了并发访问的限制。
由于采用nginx做了代理，所以对于gitlab来讲，所有请求来自于nginx服务器。该IP一旦被锁，所有请求都无法到达gitlab。

## 解决方案：
将Gitlab的IP设置为白名单即可。
步骤如下：

* 打开/etc/gitlab/gitlab.rb文件。
* 查找gitlab_rails['rack_attack_git_basic_auth']关键词。
* 取消注释
* 修改ip_whitelist白名单属性，加入Gitlab部署的IP地址。  
gitlab_rails['rack_attack_git_basic_auth'] = { 'enabled' => true, 'ip_whitelist' => ["127.0.0.1","nginx服务器IP"], 'maxretry' => 300, 'findtime' => 5, 'bantime' => 60 }
* 配置好后，执行gitlab-ctl reconfigure即可。