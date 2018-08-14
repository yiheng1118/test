# 子站接口安装

### 1 解压FuyouRestClient.zip 文件

解压后文件仅一个目录为：

```text
apache-tomcat-9.0.6
```

解压JDK1.8.zip文件。

### 2 修改启动文件。

进入：解压目录下\apache-tomcat-9.0.6\bin 打开startup.bat文件，修改前两行。JAVA\_HOME为解压JDK1.8的目录。TOMCAT\_HOME为FuyouRestClient.zip解压目录下\apache-tomcat-9.0.6\bin

```text
SET JAVA_HOME=d:\jdk1.8
SET TOMCAT_HOME=D:\apache-tomcat-9.0.6\bin
```

注意：该服务系统默认端口为：8090, 改端口默认配置，建议不要修改！

### 3 修改数据配置

  打开文件 \apache-tomcat-9.0.6\webapps\FuyouRest\WEB-INF\classes\request\_url\_config.properties   user数据库账号名、password数据库账户名密码、jdbcUrl修改后面ip地址和databaseName为对应数据名。publickey为公钥文件。

```text

#\u6570\u636e\u5e93\u8fde\u63a5\u4fe1\u606f
user=YXPT
password=2EitIuT1Z/9HtIaA61iWVpdZluVbHD9O1HDPeRiV906z1fQ9VswYg/u9qbawuVXDXiLuWF0XxMaj3OPql5/J6g==
driverClass=com.microsoft.sqlserver.jdbc.SQLServerDriver
jdbcUrl=jdbc:sqlserver://127.0.0.1:1433;databaseName=FYMOP
publicKey=MFwwDQYJKoZIhvcNAQEBBQADSwAwSAJBAN1lQZuMUv37eXgmRHqsfKd1lbJYdkugoHIoIXBb9+JfeC89PGnJH87c8iFn1ajitev9rDvFCsXYP3TIsEzI+HMCAwEAAQ==

```

### 4 修改request\_url\_config.properties

打开文件 \apache-tomcat-9.0.6\webapps\FuyouRest\WEB-INF\classes\request\_url\_config.properties

A 修改主站对接地址,userDomain为主站正式对接环境ip和端口。

```text
urlDomain=http://192.168.2.107:18090
```

B 修改子站对应客户ID customId，改用户由福忧网开设，通过联系福忧网获取。

```text
customId=01510136
```

C 火车票回掉地址配置，ip为当前服务器外网ip地址，端口为当前服务访问端口。

```text
trainNotifyUrl = http://127.0.0.1:28090/FuyouRest/TcNotifyHandler/
```

### 5 短信通道配置

打开文件 \apache-tomcat-9.0.6\webapps\FuyouRest\WEB-INF\classes\sms.properties  找到如下配置

```text
#\u77ed\u4fe1\u53d1\u9001#
sms.smsurl=http://sms-api.luosimao.com/v1/send.json
sms.SpCode=\u3010\u798f\u4f18\u7f51\u3011
sms.LoginName=api
sms.Password=key-3809c7c5af43430a4f0c1524fefdf94c
```

目前福忧网所有短信使用螺丝帽短信供应商，请自行注册账号，注册地址：[https://luosimao.com/](https://luosimao.com/) 登录后做如下操作：

1. 短信签名申请:
2. 短信模版申请（具体模板参考"所有模板内容"）
3. API key获取
4. IP白名单（当前环境外网访问IP）

以上操作可登录螺丝帽官网后进入[https://luosimao.com/docs/api/](https://luosimao.com/docs/api/) 查看。

素有模板内容：

1. 欢迎使用账户激活业务，您本次的激活验证码是\#\#\#
2. 欢迎使用企业批量分配积分业务，您本次交易的验证码是\#\#\#
3. 欢迎使用积分转信用卡业务，您绑定信用卡的验证码是\#\#\#
4. 欢迎使用账号重置邮箱业务，您的验证码是\#\#\#
5. 您已经修改了交易密码，请您妥善保管好个人资料。
6. 您已经修改了登录密码，请您妥善保管好个人资料。
7. 欢迎使用账号修改邮箱业务，您的验证码是\#\#\#
8. 欢迎使用账号修改手机号业务，您的验证码是\#\#\#
9. 欢迎使用企业采购消费业务，您本次交易的验证码是\#\#\#
10. 您本次的验证码是\#\#\#
11. 您的企业已经成功为您开通个人账号\#\#\#请及时登录并激活您的个人账号\#\#\#以便正常使用
12. 您通过找回密码功能,重置了您的登录密码，新登录密码为：\#\#\#。建议您尽快重新设置登录密码。
13. 您好，恭喜您获得\#\#\#张优惠券，可在会员中心--“我的优惠券”中查看。
14. 欢迎您的到来，您的用户名：\#\#\#，电子邮件：\#\#\#。请妥善保管好您的注册信息。
15. 您的订单已经关闭，欢迎您继续选购其他商品。订单号：\#\#\#，关闭原因：\#\#\#。
16. 我们很高兴的通知您，您的订单已备货完成，可以随时去提货了，订单号：\#\#\#，提货码：\#\#\#。
17. 感谢您的订购，您的订单已经提交成功，订单号：\#\#\#。
18. 您的订单已经成功支付，订单号：\#\#\#，订单金额：\#\#\#。
19. 恭喜您预定成功，请在规定的时间内及时支付尾款，过期定金将不予以退还，请您谅解！订单号：\#\#\#，订单定金：\#\#\#，订单尾款：\#\#\#，订单尾款支付时间段：\#\#\# - \#\#\# 【\#\#\#】
20. 我们已经为您处理了订单退款相关业务，订单号：\#\#\#，退款金额：\#\#\#。
21. 我们很高兴的通知您，您订购的商品已经寄出，请您注意查收，订单号：\#\#\#。
22. 尊敬的用户\#\#\#您的积分已到账\#\#\#
23. 欢迎使用找回密码业务，您本次的验证码是\#\#\#
24. 尊敬的用户\#\#\#您好，您的订单已生成，订单号为\#\#\#请确认到货付款后进入企业中心回复以便及时激活，本次回复的验证码是\#\#\#
25. 欢迎使用企业分配积分业务，您本次交易的验证码是\#\#\#

### 5 修改CACode

进入福利行，在系统管理-&gt;其它-&gt;配置业务字典:搜索类型代码 S00072，修改右侧字典项名称，内容为当前子站用户对应CACode，具体cacode联系福优网获取。

![](../.gitbook/assets/image%20%281%29.png)

### 6 重启服务。

重启后，登录福忧网验证。

### 7 白名单备案

服务部署完成后，需要把当前服务对外网提供的ip和端口告知福优网，福优网要对子站进行ip白名单备案。

