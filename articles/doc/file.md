# $file

$file是提供上传下载文件的服务对象

## $file.upload()

上传文件，分以下两种情况

**1、上传到Tomcat服务器**

上传的文件保存在tomcat的apache-tomcat-7.0.57\webapps\umserver\download目录下。如果使用我们提供的tomcat只需将tomcat拷贝即可，不需要配置任何信息，如果是自己的tomcat等，只需将我们提供的umserver文件夹拷贝到tomcat对应的web目录下，tomcat即webapps下。

启动tomcat时进入目录apache-tomcat-7.0.57\bin\，打开startup.bat批处理文件，tomcat正常启动的前提是必须配有JAVA_HOME。使用上传下载服务后上传的文件保存在apache-tomcat-7.0.57\webapps\umserver\download目录下。

**2、上传到MA2.7服务器**

上传到MA2.7服务器上，需要对MA进行文件服务器的配置（MA2.7自带一个文件服务器），如下图：

![](/portal/upload/doc/20170223/20170223101247947.png)

进行如图配置之后，可直接通过$file.upload将文件上传到MA的服务器上

**注意：上传之后会返回一个key，请将key妥善保存，因为如果要想去MA取上传的这个文件key是门票**

**语法**

```

$file.upload({

 "url" : "http://10.2.112.22:8080/umserver/upload", //上传服务器端路径

 "filename" : "xxx/xxx/file.xxx", //上传文件的路径+文件名

 "bindfield" : "fileInfo", //上传后的返回值，类型为JSONObject（其中从键值url可以获取上传后该文件的url）

 "callback" : "uploadCB()"//上传后的回调方法

})

```

**参数**

+ **url**：上传服务器端路径,即配有tomcat的电脑的IP，每次只要替换IP、Port即可

+ **filename**：上传文件的路径+文件名

+ **bindfield**：上传后的返回值，类型为JSONObject（其中从键值url可以获取上传后该文件的url）

+ **callback**：上传后的回调方法

+ **compressionRatio**：按比例压缩图片大小，值为0-1，例如："compressionRatio" : 0.5

**实例**

```

var flag = -1;

var filename = "image.jpg";

$file.upload({

 "url" : "http://10.2.112.22:8080/umserver/upload",

 "filename" : "xxx/xxx/file.xxx",

 "bindfield" : "upload",

 "callback" : function uploadImageCallback() {

 var upload = $ctx.getString("upload");

 upload = $stringToJSON(upload); //upload.url即上传文件存放的URL，可根据该URL下载该文件

 $alert("服务器上文件存放的URL为:" + upload.url);

 flag = flag + 1;

 var badge = (upload.url).split(".");

 filename = "image" + flag + "." + badge[badge.length - 1];

 $alert("filename:" + filename);

 $file.download({

 "url" : upload.url,

 "locate" : "downloadTest/image",

 "filename" : filename,

 "override" : "true",

 "callback" : "downloadfromserverCB()"

 });

 }

});

function downloadfromserverCB() {

 var value = "downloadTest/image/" + filename;

 $alert("value = " + value);

 $id("image0").set("src", value);

}

```

## $file.download()

下载文件

**语法**

```

$file.download({

 "url" : "http://xxx/xxx/xxx.png", //下载文件的url

 "locate" : "download/image", //下载后文件存放的路径

 "filename" : "newfile.png", //下载后重命名的文件名

 "override" : "true", //下载后是否覆盖同名文件

 "callback" : "downloadCB()"//下载后的回调方法,locate+filename可以访问文件(即download/image/newfile.png)

})

```

**参数**

+ **url**：下载文件的url

+ **filename**：下载后重命名的文件名

+ **locate**：下载后文件存放的路径

+ **override**：下载后是否覆盖同名文件

+ **callback**：下载后的回调方法,locate+filename可以访问文件

**实例**

```

$file.download({

 "url" : "http://misc.360buyimg.com/lib/img/e/logo-201305.png",

 "locate" : "downloadTest/image",

 "filename" : "jd.png",

 "override" : "true",

 "callback" : "downloadImageCallback()"

});

```

## $file.open()

打开文件服务

**语法**

```

$file.open({

 "filename" : "log.txt", //文件全路径

 "filetype" : "txt", //支持手机能打开的格式*.txt,*.doc,*.pdf等

 "filepath" : "myfiles/mytxt/"

})

```

**参数**

+ **filename**：文件名

+ **filetype**：支持手机能打开的格式*.txt,*.doc,*.pdf等

+ **filepath**：文件路径

## $file.getFileInfo()

获取文件信息的服务

**语法**

```

$file.getFileInfo(filePath)//文件全路径，如"xxx/xxx/file.txt"

$file.getFileInfo({"path" : "xxx/xxx/file.xxx"})

```

**参数**

+ **filePath**:文件所在路径

+ **path**：绑定字段

**实例**

```

var info = $file.getFileInfo(“xxx/xxx.doc”);

$file.getFileInfo({

 "path" : "xxx/xxx/file.xxx"

})

var info = $ctx.getString("path")

```

## $file.ftpUpload()

Ftp文件上传

**语法**

```

$file.ftpUpload({

 "host" : "10.2.112.44",

 "port" : "21",

 "username" : "UAPFTP",

 "password" : "UAPFTP",

 "localFileFullName" : "/storage/emulated/0/DCIM/xxx.jpg",

 "compressionRatio" : "0.5",

 "remotePath" : "/UAPAndroid/test/sunny/",

 "remoteFileName" : "newname.jpg",

 "callback" : "my callback()"

})

```

**参数**

+ **host**:服务器ip

+ **port**:服务器端口

+ **username**:登陆ftp的用户名

+ **password**:登陆ftp的密码

+ **localFileFullName**:手机端相对路径下的文件名

+ **compressionRatio**:按比例压缩,值为0-1

+ **remotePath**:上传到服务端的路径

+ **remoteFileName**:上传到服务器端文件名，默认取原文件名

+ **callback**:可选，上传成功后回调

**实例**

【对应的CSS】

```

<div id="panel0">

 <input id="textbox0" maxlength="256" placeholder="host" value="10.2.112.27" type="text"/>

 <input id="textbox1" maxlength="256" placeholder="port" value="21" type="text"/>

</div>

<div id="panel2">

 <input id="textbox4" maxlength="256" placeholder="username" value="UAPFTP" type="text"/>

 <input id="textbox5" maxlength="256" placeholder="password" value="UAPFTP" type="text"/>

</div>

<input id="textbox6" maxlength="256" placeholder="remotePath" value="/UAPAndroid/test/sunny/" type="text"/>

<input id="button0" value="点击上传" class="textbtnclass" onclick="this.button0_onclick()" type="button"/>

<imageselector id="imageselector0"/>

<input id="button1" value="点击下载" class="textbtnclass" onclick="this.button1_onclick()" type="button"/>

<image id="image0" scaletype="fitcenter" src="picture"/>

```

【对应JS】

```

//上传

var host;

var port;

var username;

var password;

var remotePath;

function com$requirement0724$Ftp1Controller$button0_onclick(sender, args) {

 host = $id("textbox0").get("value");

 port = $id("textbox1").get("value");

 username = $id("textbox4").get("value");

 password = $id("textbox5").get("value");

 remotePath = $id("textbox6").get("value");

 var str1 = $id("imageselector0").get("selectedimages");

 var str = $stringToJSON(str1);

 for (var i = 0; i < str.length; i++) {

 var pic = str[i]

 var index = pic.lastIndexOf("/");

 var path = pic.substring(0, index);

 $file.ftpUpload({

 "host" : "10.2.112.44",

 "port" : "21",

 "username" : "UAPFTP",

 "password" : "UAPFTP",

 "localFileFullName" : "/storage/emulated/0/DCIM/xxx.jpg", //相对路径下的文件名

 "compressionRatio" : "0.5", //取值范围0-1

 "remotePath" : "/UAPAndroid/test/sunny/", //上传路径

 "remoteFileName" : "newname.jpg", //上传后的新的文件名，如未指定，则取原文件名

 "callback" : "uploadcallback()"

 });

 }

}

function uploadcallback(sender, args) {

 $alert("上传完成：args:" + $jsonToString(args));

}

```

## $file.ftpDownload()

Ftp文件下载

**语法**

```

$file.ftpDownload({

 "host" : "10.2.112.44",

 "port" : "21",

 "username" : "UAPFTP",

 "password" : "UAPFTP",

 "remoteFileFullName" : "/UAPAndroid/test/sunny/serverFile.jpg",

 "localPath" : "/storage/emulated/0/aaaaanewPath/ccc/",

 "localFileName" : "newname.jpg",

 "callback" : "my callback()"

})

```

**参数**

+ **host**:服务器ip

+ **port**:服务器端口

+ **username**:登陆ftp的用户名

+ **password**:登陆ftp的密码

+ **localPath**:下载路径

+ **localFileName**: 下载后的新的文件名，如未指定，则取原文件名

+ **callback**:可选，上传成功后回调

**实例**

【对应的CSS】

```

<div id="panel0">

 <input id="textbox0" maxlength="256" placeholder="host" value="10.2.112.27" type="text"/>

 <input id="textbox1" maxlength="256" placeholder="port" value="21" type="text"/>

</div>

<div id="panel2">

 <input id="textbox4" maxlength="256" placeholder="username" value="UAPFTP" type="text"/>

 <input id="textbox5" maxlength="256" placeholder="password" value="UAPFTP" type="text"/>

</div>

<input id="textbox6" maxlength="256" placeholder="remotePath" value="/UAPAndroid/test/sunny/" type="text"/>

<input id="button0" value="点击上传" class="textbtnclass" onclick="this.button0_onclick()" type="button"/>

<imageselector id="imageselector0"/>

<input id="button1" value="点击下载" class="textbtnclass" onclick="this.button1_onclick()" type="button"/>

<image id="image0" scaletype="fitcenter" src="picture"/>

```

【对应JS】

```

//下载

var i = 0;

function com$requirement0724$Ftp1Controller$button1_onclick(sender, args) {

 var path = $service.call("UMDevice.getAppAlbumPath", {}, true)

 $file.ftpDownload({

 "host" : "10.2.112.44",

 "port" : "21",

 "username" : "UAPFTP",

 "password" : "UAPFTP",

 "remoteFileFullName" : "/UAPAndroid/test/sunny/serverFile.jpg",

 "localPath" : "/storage/emulated/0/aaaaanewPath/ccc/",

 "localFileName" : "newname.jpg", //下载后的新的文件名，如未指定，则取原文件名

 "callback" : "downloadcallback()"

 })

}

function downloadcallback(sender, args) {

 args = $stringToJSON(args);

 $alert("下载完成：" + args.downloadfilefullpath);

 $id("image0").set("src", args.downloadfilefullpath);

}

```

## $file.write()

此方法不开放，请使用等效方法$cache.write()的语法2

## $file.read()

此方法不开放，请使用等效方法$cache.read()的语法2

## $file.remove()

写文件。

*待补充*

## $file.exists()

判断文件是否存在。

*待补充*

## $file.openFileSelector()（仅安卓）

打开文件选择器。

*待补充*

## $file.fileToByte()(待添加)

文件转换成字节数组

**语法**

```javascript

var byteArray = $file.fileToByte({

 "filePath" : "", //文件路径

 "charset" : "UTF-8" //字符集

})

```

**参数：**

+ **filePath**：文件路径

+ **charset**：字符集，默认UTF-8

**返回值：**

+ **byteArray**：字节数组

**示例代码：**

```javascript

var byteArray = $file.fileToByte({

 "filePath" : "image/IUAP_45672.jpg",

 "charset" : "UTF-8"

})

```

## $file.byteToFile()(待添加)

字节数组转换成文件

**语法**

```javascript

var $file.byteToFile({

 "byteArray" : new Array(), //字节数组

 "charset" : "UTF-8", //字符集

 "filePath" : "" //文件路径

})

```

**参数：**

+ **byteArray**：字节数组

+ **charset**：字符集，默认UTF-8

+ **filePath**：文件路径

**示例代码：**

```javascript

$file.byteToFile({

 "byteArray" : new Array(),

 "charset" : "UTF-8",

 "filePath" : "image/IUAP_45672.jpg"

})

```


