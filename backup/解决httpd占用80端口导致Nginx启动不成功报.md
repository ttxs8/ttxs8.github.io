## 解决httpd占用80端口导致Nginx启动不成功报nginx: [emerg] bind() to 0.0.0.0:80 failed (98: Address already in use)

## 一、问题描述

​    今天在建自己小网站时[启动Nginx](https://so.csdn.net/so/search?q=%E5%90%AF%E5%8A%A8Nginx&spm=1001.2101.3001.7020)时，发现其报下列错误，意思是因为[80端口被占用](https://so.csdn.net/so/search?q=80%E7%AB%AF%E5%8F%A3%E8%A2%AB%E5%8D%A0%E7%94%A8&spm=1001.2101.3001.7020)导致Nginx启动失败。

![202401221211069](https://github.com/ttxs8/ttxs8.github.io/assets/58286237/253ed50f-5fc1-4183-a9e0-10dc4523bc5e)



## 二、分析问题

​    既然是因为[80端口被占用](https://so.csdn.net/so/search?q=80端口被占用&spm=1001.2101.3001.7020)了，那我们就要首先排查错误缘由，使用下面该命令对80端口进行摸排，结果显示80端口被httpd这个程序一直占用着。

```perl
netstat -ntlp|grep 80
```

![202401221211030](https://github.com/ttxs8/ttxs8.github.io/assets/58286237/3bc2fa3f-cd73-4366-93f2-b79d24c05e1c)

 

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

![202401221211064](https://github.com/ttxs8/ttxs8.github.io/assets/58286237/eb3b09d8-9b60-461c-86c6-5cf77a8742c1)
<!-- ##{"timestamp":1705884703}## -->