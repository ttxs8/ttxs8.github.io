# PicGo + 阿里云OSS图床

## 注册

配置阿里云OSS 在浏览器搜索阿里云OSS，即可找到 [[官网](https://www.aliyun.com/product/oss)](https://www.aliyun.com/product/oss)。

注册,开通对象储存 注册账户并实名后，进入你的控制台
 ![image-20220111194645144](https://ttxsimage.oss-cn-beijing.aliyuncs.com/typea/202305121022326.png#pic_left)

选择对象储存并开通。

## 创建bucket

 ![image-20220111194540431](https://ttxsimage.oss-cn-beijing.aliyuncs.com/typea/202305121022990.png#pic_left)

创建bucket 在左侧选择概览，然后在右侧创建一个新的`bucket`
 ![image-20220111195034924](https://ttxsimage.oss-cn-beijing.aliyuncs.com/typea/202305121022128.png#pic_left)

注意：

`Bucket`名字不能有大写字母 服务器就近选择 图床选择标准存储 读写权限公共读
 ![image-20220111195753835](https://ttxsimage.oss-cn-beijing.aliyuncs.com/typea/202305121022040.png#pic_left)

创建完成后，你的`bucket`应该就出现在了左侧。

## 配置对象存储

找到你的地域节点 点击你的`bucket`名
 ![image-20220111200207252](https://ttxsimage.oss-cn-beijing.aliyuncs.com/typea/202305121022940.png#pic_left)

然后点击`bucket`下的概览
 ![image-20220111200304506](https://ttxsimage.oss-cn-beijing.aliyuncs.com/typea/202305121022864.png#pic_left)

在访问域名一栏找到你的地域节点，后面会用到。
只需要复制`oss-cn-shenzhen`即可，不需要后面的`.aliyuncs.com`。

找到你的`Key` 来到右上角，鼠标放在你的头像上，在弹出的框里选择`AccessKey`管理

 ![image-20220111200832708](https://ttxsimage.oss-cn-beijing.aliyuncs.com/typea/202305121022064.png#pic_left)

在弹出的选项框里，选择“继续使用”

进入后，创建一个`AccessKey`

在弹出的界面里，记住你的`accessKeyId`和`accessKeySecret`

给你的阿里云账户充值。收费问题 阿里云OSS的各项收费是独立的！

对于图床而言，有两种收费形式

以充值的方式使用储存容量以及流量(默认状态) 按年/月收费，购买一定存储包。流量额外收费 也就是说，即便你购买了下图的存储包，你依旧要为访问图床的流量付钱！

下图是在默认状态下，容量和流量收费的价格

图床使用的是标准型，请勿购买其他类型

储存容量：0.12元/GB/月 图片上传到阿里OSS流量：免费 外网流出流量(如typora访问图床图片)：闲时0.25元/GB，忙时0.50元/GB

 ![image-20220104193905591](https://ttxsimage.oss-cn-beijing.aliyuncs.com/typea/202305121022553.png#pic_left)

仔细算算，我们图床的数据量其实很小的

0.12元/1GB/1个月，一年就是1.44元，远低于40GB的9元收费！

截图/照片以平均0.5mb/张估算，1gb可存放超过1600张图片！

数据低于6GB的情况下直接充值，以GB付费其实比购买储存包更加值得！

注意事项 记得给阿里云账户充值！！别到时候欠费停用了！！ 刚开始作图床的时候，直接充值使用即可，无需购买容量包！

到这里，我们阿里云OSS基本配置完毕了😎

## 配置picgo

图床设置 在图床设置里面选择阿里云`OSS`，依照以下步骤填写信息。如图：

 ![image-20220523113647743](https://ttxsimage.oss-cn-beijing.aliyuncs.com/typea/202305121022807.png#pic_left)

### 图床配置

 ![image-20220111203313899](https://ttxsimage.oss-cn-beijing.aliyuncs.com/typea/202305121033537.png)

**设定`Keyld`**：填写刚刚获得的`AccessKeyID`

**设定`KeySecret`**：填写`AccessKeyIDSecret`

**设定储存空间名**：填写`bucket`名称（这里填写的是`bucket`名称，不是浏览器里的域名）

**确认存储区域**：填写你的地域节点，注意复制的格式

**指定存储路径**：其实就是自定义一个文件夹的名字，以/结尾，它会自动在你的bucket里面创建一个文件夹，并把图片上传进去

弄完之后，记得“确定”，并点击“设置为默认图床”！

### picgo设置

在设置里打开时间戳重命名和上传后自动复制`URL`

时间戳重命名：以上传时间来重命名图片，避免同名的图片无法上传（该设置不影响本地图片名）

 ![image-20220111204114564](https://ttxsimage.oss-cn-beijing.aliyuncs.com/typea/202305121022306.png#pic_left)

## 配置typora

进入typora主界面，点击左上角的“文件-偏好设置” -- > 选择图像 -- > 插入图片时上传图片

下面的选项全勾上

上传服务选择`PicGo(app)`

`PicGo`路径：找到`picgo.exe`文件，不是安装包的路径！！！！

 ![image-20220104193025600](https://ttxsimage.oss-cn-beijing.aliyuncs.com/typea/202305121022519.png#pic_left)

大功告成！ 设置完毕后，我们点击验证图片上传选项

如果弹出以下弹窗，我们的图床就搞定了！😀

 ![image-20220111205131635](https://ttxsimage.oss-cn-beijing.aliyuncs.com/typea/202305121022638.png#pic_left)

最后新建一个文件，验证图片是否正常上传

日常写作的时候，我们只需要复制图片，在typora里面粘贴即可，无需拖动！

当你的图片链接显示为阿里云的网络链接，而不是本地路径时，配置完成。

 ![image-20220111205318201](https://ttxsimage.oss-cn-beijing.aliyuncs.com/typea/202305121022980.png#pic_left)

作者：black-cat
出处：https://www.cnblogs.com/Kylin-lawliet/p/16446536.html