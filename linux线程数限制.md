# linux线程数限制
## 1. 起因
Java程序中遇到下面的异常：
```
Exception in thread “main” java.lang.OutOfMemoryError: unable to create new native thread
```
为了排查问题，顺便研究了一下linux中线程的数量限制

## 2. 限制
在64位系统中，这里就不考虑物理内存和虚拟内存的限制了，这个是最基本的资源，没有内存一切都白扯了。

### 2.1. 内核限制
```
linux-iu85:~ # cat /proc/sys/kernel/pid_max 
32768
linux-iu85:~ # cat /proc/sys/kernel/threads-max 
29298
```
### 2.2. 虚拟内存区域限制
```
linux-iu85:~ # cat /proc/sys/vm/max_map_count 
65530
```
java每创建一个线程会建立两个映射，所以线程数不能超过这个值的一半。

### 2.3. 用户资源限制
```
linux-iu85:~ # ulimit -u
14649
```
**注意：**这个参数只对linux普通用户有效，对root用户没有限制

可以通过配置/etc/security/limits.conf永久修改该参数。

### 2.4. 控制组资源限制
```
linux-iu85:~ # find /sys/fs/cgroup/pids/ -name "pids.max"
```
这个命令可以搜索到所有跟进程（线程）最大数量相关的配置文件。

一般情况有关的是（以root用户为例）：
```
linux-iu85:~ # cat /sys/fs/cgroup/pids/user.slice/user-0.slice/pids.max 
12288
```
**说明：**“user-0"这里的0就是root用户的id。其他用户可以先从/etc/passwd中查找id。

