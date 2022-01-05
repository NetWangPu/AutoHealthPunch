# AutoHealthPunch
#### 用于北京交通大学海滨学院的班级魔方健康打卡

项目参考 [Link](https://github.com/Chef5/Curl-banjimofang)

代码稍作修改

## 部署教程

1 安装php环境

``yum install php``

2 安装git创建目录获取代码

``yum install git``

``cd /home && mkdir test && cd test``

``git clone https://github.com/NetWangPu/AutoHealthPunch.git``

3 配置参数 

``vim ./AutoHealthPunch/user/dxever.json``

参数说明：
- `phone`:  登录手机号
- `pwd`:  登录密码
- `suburl`:  依次点击 自己班级->健康汇报->每日健康情况，然后复制当前页的浏览器地址url
- `sig`:  表现症状
- `isTri`:  就医情况
- `isSpl`:  隔离情况
- `reTou`:  最新接触
- `site`:  地址
- `isEmail`:  是否启用邮件通知（启用需要配置邮箱，见最后）

关于体温：会随机取36.3~37.2

> 一开始使用的微信登录，找不到手机号和密码。 

> **解决** ：手机号是自己微信手机号，密码可以在 http://k8n.cn/resetpwd/student 进行设置

4 创建任务 

``crontab -e``

 空白处添加代码

`` 00 08 * * * cd /home/test/AutoHealthPunch && php -f auto.php``

> 其中 00 08 表示每天早上8点进行自动提交，前一个数表示分钟，后一个数表示时钟，可自己调整
