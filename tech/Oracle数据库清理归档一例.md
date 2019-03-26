# Oracle数据库清理归档一例
## 1. 现象
数据库无法连接，sqlplus可以以dba身份在服务器登录，startup mount正常，alter database open报错。

## 2. 原因
数据库存储使用了裸设备，所以df命令看文件系统都没有空间问题。

## 3. 解决
查看空间问题：

    # su - oracle
    # sqlplus /nolog
    # sqlplus> conn / as sysdba
    # sqlplus> startup mount
    # sqlplus> select name,total_mb,free_mb from v$asm_diskgroup;  --查看磁盘组剩余空间

清理归档日志

    # su - grid用户
    # asmcmd
    # ASMCMD> cd arch/orcl（归档日志目录）
    # ASMCMD> rm -fr 要删除的目录
