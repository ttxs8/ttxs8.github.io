## 解决httpd占用80端口导致Nginx启动不成功报nginx: [emerg] bind() to 0.0.0.0:80 failed (98: Address already in use)

## 一、问题描述

​    今天在建自己小网站时[启动Nginx](https://so.csdn.net/so/search?q=%E5%90%AF%E5%8A%A8Nginx&spm=1001.2101.3001.7020)时，发现其报下列错误，意思是因为[80端口被占用](https://so.csdn.net/so/search?q=80%E7%AB%AF%E5%8F%A3%E8%A2%AB%E5%8D%A0%E7%94%A8&spm=1001.2101.3001.7020)导致Nginx启动失败。

 ![img](https://ttxsimage.oss-cn-beijing.aliyuncs.com/typea/202401221211069.png)



## 二、分析问题

​    既然是因为[80端口被占用](https://so.csdn.net/so/search?q=80端口被占用&spm=1001.2101.3001.7020)了，那我们就要首先排查错误缘由，使用下面该命令对80端口进行摸排，结果显示80端口被httpd这个程序一直占用着。

```perl
netstat -ntlp|grep 80
```

![img](https://ttxsimage.oss-cn-beijing.aliyuncs.com/typea/202401221211030.png)

 

##  三、解决办法

​    在网上找过一些办法，结果都杀不死该进程。如kill -9 端口号 这些等都无用。

​    经过查找资料得知，使用下面这个命令，然后再重启Nginx即可完成成功运行。

```cobol
fuser -k 80/tcp



 



cd /usr/local/nginx/sbin



 



./nginx 
```



## 四、运行结果

​    输入公网ip，完美运行成功！！！

## ![img](https://ttxsimage.oss-cn-beijing.aliyuncs.com/typea/202401221211064.png)
<!-- ##{"timestamp":1705884703}## -->