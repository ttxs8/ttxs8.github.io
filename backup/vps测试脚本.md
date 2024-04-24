## vps测试脚本

1. ### 综合性测试脚本 秋水逸冰 | Bench.sh


- 网址：https://bench.sh/﻿

- 使用方法：

  ```bash
  wget -qO- bench.sh | bash
  ```

- 内容：系统基本信息显示、IO测试、全球主要节点测速

- 简介：测试项目涵盖了大多数常用指标，大多数情况下跑一遍这个就能大致判断VPS的好坏，非常实用的快速测试脚本

2. ### 全面性能测试脚本 秋水逸冰 | UnixBench.sh

- 网址：https://teddysun.com/245.html

- 使用方法：

  ```bash
  wget --no-check-certificate  https://github.com/teddysun/across/raw/master/unixbench.sh
  chmod +x unixbench.sh
  ./unixbench.sh
  ```

- 内容：系统调用、读写、进程、图形化测试、2D、3D、管道等

- 简介：性能测试项目非常全面，但是跑一次要用上很多时间，而且UnixBench

- 

3. ### 流媒体测试脚本

- 网址：https://github.com/lmc999/RegionRestrictionCheck

- 使用方法： 

  ```bash
  bash <(curl -L -s check.unlock.media)
  ```

- 内容：国际上各大流媒体平台以及部分游戏可用性测试

- 简介：非常全面的流媒体测试脚本，可以选择各种地区，根据地区不同测试所选地区的流媒体和游戏，结果也准确

- 

4. ### 检测VPS回程国内三网路由


- 网址：https://github.com/zhucaidan/mtr_trace

- 使用方法：

  ```bash
  curl https://raw.githubusercontent.com/zhucaidan/mtr_trace/main/mtr_trace.sh|bash
  ```

- 内容：三大运营商7大主流线路测试

- 简介：非常简洁易懂，再也不用去记各种IP前缀和AS号了，用起来也很简单

5. ###  网络测速脚本


- 网址：https://github.com/uxh/superspeed

- 使用方法：

  ```bash
  bash <(curl -Lso- https://git.io/superspeed_uxh)
  ```

- 内容：全国各个地区各大运营商网速测速

- 简介：比起Bench.sh自带的测速，这个只有国内节点，但是测速节点非常多，结果更加全面 

