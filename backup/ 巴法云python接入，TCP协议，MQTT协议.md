# 巴法云python接入，TCP协议，MQTT协议

## **第一，tcp协议连接**

说明： tcp服务器地址：[http://bemfa.com](https://link.zhihu.com/?target=http%3A//bemfa.com) 端口 8344

tcp协议详细订阅、发布指令，见接入文档：[点击跳转](https://link.zhihu.com/?target=https%3A//cloud.bemfa.com/docs/%23/%3Fid%3D_41-tcp%25e5%2588%259b%25e5%25ae%25a2%25e4%25ba%2591)

```python
# -*- coding: utf-8
import socket
import threading

def connTCP():
    global tcp_client_socket
    # 创建socket
    tcp_client_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
    # IP 和端口
    server_ip = 'bemfa.com'
    server_port = 8344
    try:
        # 连接服务器
        tcp_client_socket.connect((server_ip, server_port))
        #发送订阅指令
        substr = 'cmd=1&uid=4d9ec352e0376f2110a0c601a2857225&topic=led002\r\n'
        tcp_client_socket.send(substr.encode("utf-8"))
    except:
        time.sleep(2)
        connTCP()

#心跳
def Ping():
    # 发送心跳
    try:
        keeplive = 'ping\r\n'
        tcp_client_socket.send(keeplive.encode("utf-8"))
    except:
        time.sleep(2)
        connTCP()
    #开启定时，30秒发送一次心跳
    t = threading.Timer(30,Ping)
    t.start()


connTCP()
Ping()

while True:
    # 接收服务器发送过来的数据
    recvData = tcp_client_socket.recv(1024)
    if len(recvData) != 0:
        print('recv:', recvData.decode('utf-8'))
    else:
        print("conn err")
        connTCP()
```

## 第二，MQTT 协议连接

说明： mqtt服务器地址：[http://bemfa.com](https://link.zhihu.com/?target=http%3A//bemfa.com) 端口：9501

连接服务器

1.用户私钥作为连接MQTT服务器的客户端ID

2.连接时用户名和密码为空，或随意填写，即设备连接时不需要账号和密码

mqtt程序使用前需安装mqtt库文件，安装命令：

```text
pip3 install paho-mqtt
```

程序：

```python
# -*- coding: utf-8 -*-
# 以下代码在2021年10月21日 python3.10环境下运行通过

import paho.mqtt.client as mqtt

HOST = "bemfa.com"
PORT = 9501
client_id = "4d9ec352e0376f2110a0c601a2857225"                       
#连接并订阅
def on_connect(client, userdata, flags, rc):
    print("Connected with result code "+str(rc))
    client.subscribe("led00202")         # 订阅消息

#消息接收
def on_message(client, userdata, msg):
    print("主题:"+msg.topic+" 消息:"+str(msg.payload.decode('utf-8')))

#订阅成功
def on_subscribe(client, userdata, mid, granted_qos):
    print("On Subscribed: qos = %d" % granted_qos)

# 失去连接
def on_disconnect(client, userdata, rc):
    if rc != 0:
        print("Unexpected disconnection %s" % rc)


client = mqtt.Client(client_id)
client.username_pw_set("userName", "passwd")
client.on_connect = on_connect
client.on_message = on_message
client.on_subscribe = on_subscribe
client.on_disconnect = on_disconnect
client.connect(HOST, PORT, 60)
client.loop_forever()
```



run.vbs

```vbscript
Set ws = CreateObject("Wscript.Shell")
ws.run "cmd /c C:\Windows\shutdown\run.bat",0
```

run.bat

```bash
python -u C:\Windows\shutdown\sd.py > log.out
```

