# docker安装oracle12c数据库
```
sudo docker pull absolutapps/oracle-12c-ee
```

```
$ docker run -d --name oracle \
  --privileged -v $(pwd)/oradata:/u01/app/oracle \
  -p 8080:8080 -p 1521:1521 absolutapps/oracle-12c-ee 
```

### Additional options

ORACLE_SID - Oracle SID (default to ORCL)  
SERVICE_NAME - $ORACLE_SID  
Listener port - 1521  
EM port - 8080  
SYS, SYSTEM passwords: oracle  
Amount of memory 40% set by INIT_MEM_PST

