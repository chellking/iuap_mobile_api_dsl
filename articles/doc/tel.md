# $tel$tel是与电话、短信、邮件相关的服务对象

## $tel.call()打电话

**语法**```$tel.call("139***")```

**参数**+ **tel**：拨打的电话号码

**实例**```var tel = $id("telnum").get("value");//获取文本框中输入的电话号码$tel.call(tel);```

## $tel.sendMsg()发短信服务，支持群发短信

**语法**```$tel.sendMsg({ "tel" : "139***,1397***",//电话号码 "body" : "hello"//短信内容})```

**参数**+ **tel**：发送短信的电话号码+ **body**：发送短信的内容

**实例**```var telnum = $id("telnum").get("value")//输入类控件;$tel.sendMsg({ "tel" : telnum, //电话号码 "body" : "hello send message test"//短信内容});```

## $tel.sendMail()发邮件服务，支持群发邮件

**语法**```$tel.sendMail({ "receive" : "wwww@qq.com,lll@163.com", //收件人 "title" : "hello", //邮件主题 "content" : "欢迎使用UAP Mobile"//邮件内容})```

**参数**+ **receive**：收件人的邮箱账号+ **title**：邮件主题+ **content**：邮件内容

**实例**```$tel.sendMail({ "receive" : "xxx@163.com", //收件人 "title" : "hello", //邮件主题 "content" : "欢迎使用UAP Mobile"//邮件内容});```

## $tel.saveContact()保存联系人

**语法**```javascript$tel.saveContact({})```

**参数**+ **tel**：手机号码+ **employeename**：联系人名称+ **jobname**：职位+ **orgname**：部门名称+ **address**：单位地址+ **email**：邮箱+ **officetel**：办公电话

**实例**```$tel.saveContact({ "tel" : "139****", "employeename" : "张三", "jobname" : "职员", "orgname" : "开发部", "address" : "北京市海淀区***", "email" : "zhangsan@yonyou.com", "officetel" : "6243****"});```


