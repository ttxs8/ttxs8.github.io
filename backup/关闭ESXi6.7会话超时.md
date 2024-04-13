关闭ESXi6.7会话超时

![image](https://github.com/ttxs8/ttxs8.github.io/assets/58286237/28a222f7-095d-459c-918e-4f056a74d97e)

ESXi6.7默认会话超时参数为900秒，十五分钟自动登出，很麻烦需要关闭
![image](https://github.com/ttxs8/ttxs8.github.io/assets/58286237/328798da-bd82-42df-aac5-4b7e9dfe1d6b)

然后重新登陆页面收到这个提示


![image](https://github.com/ttxs8/ttxs8.github.io/assets/58286237/6c31e1ea-206d-40ca-b4da-22994590b2f3)


管理--高级设置，找到UserVars.HostClientSessionTimeout，编辑选项


![image](https://github.com/ttxs8/ttxs8.github.io/assets/58286237/54c1e7eb-ed7e-455f-84a9-9c24a05890ee)


设置新值为0，永久不超时，点击保存，刷新页面生效

<!-- ##{"timestamp":1674136493}## -->