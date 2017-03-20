# $device

$device是获取设备信息的服务对象

## $device.getTimeZoneID()

获取时区ID

**语法**

```

$device.getTimeZoneID();

```

## $device.getTimeZoneDisplayName()

获取时区DisplayName

**语法**

```

$device.getTimeZoneDisplayName();

```

## $device.getLocation()

获取位置信息（***此方法通过高德地图获取位置，使用时请先参照《DSL控件指南-高级-高德地图》配置应用签名-keystore***）

**语法**

```

$device.getLocation({

 "bindfield" : "location", //位置信息回写的绑定字段

 "callback" : "getLocationCallBack()", //回调执行的JS方法

 "single" : "true", //是否只获取1次

 "isgetaddress" : "true", //是否需要获取地址

 "network" : "true" //是否使用wifi定位

})

```

**参数**

+ **bindfield**：位置信息回写的绑定字段

+ **callback**：回调执行的JS方法

+ **single**：是否只获取1次

+ **isgetaddress**：是否需要获取地址

+ **network**：是否使用wifi定位

**实例**

```

$device.getLocation({

 "bindfield" : "location",

 "callback" : function() {

 $alert($ctx.getString("location"));

 },

 "single" : "true",

 "isgetaddress" : "false",

 "network" : "false"

});

```

## $device.openWebView()

打开网页

**语法**

```

$device.openWebView({

 "url" : "http://www.yyuap.com"

});

```

**参数**

+ **url**：打开网页的URL

## $device.getInternalMemoryInfo()

获取内部存储信息

**语法**

```

$device.getInternalMemoryInfo()

```

## $device.getExternalStorageInfo()

获取外部存储信息，该服务只针对Android

**语法**

```

$device.getExternalStorageInfo();

```

## $device.getMemoryInfo()

获取存储信息

**语法**

```

$device.getMemoryInfo();

```

## $device.getDeviceInfo()

获取设备信息

**语法**

```

$device.getDeviceInfo();

```

## $device.getDeviceInfo()

获取设备信息

**语法**

```

$device.getDeviceInfo({

 "bindfield" : "dinfo", //信息回写的绑定字段

 "callback" : "getDeviceInfoCallBack()" //回调执行的JS方法

})

```

## $device.getScreenHeight()

获取手机屏幕的高度

**语法**

```

$device.getScreenHeight();

```

## $device.getScreenWidth()

获取手机屏幕的宽度

**语法**

```

$device.getScreenWidth();

```

## $device.getScreenDensity()

像素密度，通常是2或3

**语法**

```

$device.getScreenDensity();

```

## $device.notify()

提醒服务

**语法**

```

$device.notify({

 "sendTime" : "2015-02-03 13:54:30", //提示时间

 "sendBody" : "您设置了消息提醒事件", //提示文字内容

 "icon" : "app.png"//图标

})

```

## $device.capturePhoto()

获取手机相册图片

**语法**

```

$device.capturePhoto({

 "bindfield" : "image", //存放图片返回值的Context字段名

 "callback" : "capturePhotoCB()"//回调JS方法

})

```

**参数**

+ **bindfield**：存储照片的字段

+ **callback**：回调

**用法**

```

$device.capturePhoto({

 "bindfield" : "image", //存放图片返回值的Context字段名

 "callback" : function() {

 var img = $ctx.getString("image");

 $id("image0").set("src", img);

 }

});

```

## $device.screenShot()

手机截屏服务

**语法**

```

$device.screenShot({

 "bindfield" : "dinfo",

 "callback" : "xxx()"

})

```

**参数**

+ **bindfield**：信息回写的绑定字段

+ **callback**：回调执行的js方法

**用法**

```

function com$yonyou$aaa$Device117Controller$button13_onclick(sender, args) {

 $device.screenShot({

 "bindfield" : "dinfo", //信息回写的绑定字段

 "callback" : "getScreenShotCallBack()" //回调执行的JS方法

 })

}

function getScreenShotCallBack() {

 var info = $ctx.getString("dinfo");

 $id("image0").set("src", info);

}

```

## $device.saveContact()

把信息写入通讯录

**语法**

```

$device.saveContact({

 "tel" : "139****", //手机号码

 "employeename" : "张三", //联系人名称

 "jobname" : "职员", //职位

 "orgname" : "开发部", //部门名称

 "address" : "北京市海淀区***", //单位地址

 "email" : "zhangsan@yonyou.com", //邮箱

 "officetel" : "6243****"//办公电话

})

```

## $device.openAddressBook()

打开通讯录

**语法**

```

$device.openAddressBook();

```

## $device.getContacts()

获取手机通讯录

**语法**

```

$device.getContacts()

```

**参数**

*无*

**实例**

```

var value=$device.getContacts();

alert(value);

```

注意：使用此方法时，一定要在application.xml文件中权限页面，把允许访问联系人的权限勾上

## $device.currentOrientation()

获取手机横竖屏状态，返回值为 "portrait" | "landscape", 表示 横屏 or 竖屏

**语法**

```

$device.currentOrientation()

```

**参数**

*无*

**实例**

```

function com$requirement0724$OrientationController$change(sender, args) {

 var currentOrientation = $device.getContacts();

 if ( currentOrientation = "portrait") {

 }

 if ( currentOrientation = "landscape") {

 }

}

```

## $device.generateQRCode()

把字符串生成二维码

**语法**

```

$device.generateQRCode()

```

**参数**

+ **twocode-size**：二维码正方形的边长

+ **twocode-content**：生成二维码所需的字符串

**实例**

```

function com$requirement0724$TwocodeImageController$onclick(sender, args) {

 var text = $id("textbox0").get("value");

 var len = $id("textbox1").get("value");

 var twocodepath = $device.generateQRCode({

 size : len, //二维码正方形的宽高

 content : text//生成二维码所需的源文字

 });

 $id("image0").set("src", twocodepath);

}

```

## $device.getAlbumPath()

获取相册路径 - Android独有

**语法**

```

$device.getAlbumPath()

$device.getAlbumPath({

 "allFolders" : true, //是否获取相册中所有文件夹

 "callback" : "mycallback()"

})

$device.getAlbumPath({

 "allFolders" : false, //是否获取相册中所有文件夹

 "callback" : "mycallback()"

})

```

**参数**

+ 1、无参数

+ 2、json对象 - allFolders:true|false 是否获取设备相册中所有文件夹callback:xxx() 回调方法

**返回值**

+ callback的方法中args中存储获取的相册路径信息，通过args.result获取；

+ 当allFolders=true时，args.result为数组，获取的是设备相册中所有路径信息；

+ 当allFolders=false时，args.result获取的是设备系统相册的路径

**实例**

```

var path = $device.getAlbumPath()//获取相册路径

$device.getAlbumPath({

 "allFolders" : "true", //是否获取相册中所有文件夹

 "callback" : "getAlbumPathCB()"

})

function getAlbumPathCB(sender, args) {

 $alert(args.result);

}

$device.getAlbumPath({

 "allFolders" : "false", //是否获取相册中所有文件夹

 "callback" : "getAlbumPathCB()"

})

function getAlbumPathCB(sender, args) {

 $alert(args.result);

}

```

## $device.getAppAlbumPath()

获取相机服务存放照片的存储路径

**语法**

```

$device.getAppAlbumPath()

```

**参数**

*无*

**实例**

```

var path =$device.getAppAlbumPath()//获取相机服务拍照的路径

```

## $device.openApp()

打开第三方App。

## $device.openFlashLight()

打开闪关灯服务。

注：$scanner.open()参数openFlashLight为true，可自动打开闪关灯。系统在扫码callback中自动关闭，无需代码显示关闭闪光灯。

## $device.closeFlashLight()

关闭闪光灯服务。

*待补充*


