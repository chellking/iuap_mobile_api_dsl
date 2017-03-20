# $js

常用JS方法

## $js.hideLoadingBar()

隐藏loading

**语法**

```

$js.hideLoadingBar()

```

**参数**

*无*

**实例**

```

$js.hideLoadingBar()

```

## $js.showLoadingBar()

显示loading

**语法**

```

$js.showLoadingBar()

$js.showLoadingBar({

 "opacity" : "0.6",

 "background" : "#e3f4dd"

})

```

**参数**

+ **opacity**：透明度，0-1直接的数字

+ **background**：蒙版背景色，#000000-#ffffff之间

**实例**

```

$js.showLoadingBar()

$js.showLoadingBar({

 "opacity" : "0.6",

 "background" : "#e3f4dd"

})

```

**说明**

Android的loading图标可配置；iOS用的就是iOS原生图标，不可配置

图片支持格式：.gif、.png

配置步骤：找到工程相应的主题，如在ios7主题：

xxx\UI\themes\ios7\drawable下把图标放置进去

图片命名必须是publicloading.gif或者publicloading.png

## $js.backConfirm()

Android手机back键确认弹窗

**语法**

```

$js.backConfirm()

```

**参数**

*无*

**实例**

```

$js.backConfirm()//在onload事件写上此方法，按back键时会调用

```

## $js.randomUUID()

生成UUID的方法服务

**语法**

```

$js.randomUUID()

```

**参数**

*无*

**返回值**

+ 小写字符，如38400000-8cf0-11bd-b23e-10b96e4ef00d

**实例**

```

var uuid = $js.randomUUID();

```

## $js.getTimeTicks()

获取当前时间的方法服务

**语法**

```

$js.getTimeTicks()

```

**参数**

*无*

**返回值**

+ 自1970-01-01开始的时间戳 是一个long类型对应的字符串

**实例**

```

var time = $js.getTimeTicks();

```

## $js.urlEncode()

提供URL编码服务

**语法**

```

$js.urlEncode()

```

**参数**

*无*

**实例**

```

$js.urlEncode("需要编码的字符串");

var value=$id(“label1”).get(“value”);

$js.urlEncode(value);//把label1的value值进行编码

```

## $js.urlDecode()

提供URL解码服务

**语法**

```

$js.urlDecode("需要解码的字符串")

```

**参数**

*无*

**实例**

```

$js.urlDecode("需要解码的字符串")

var value=$id(“label1”).get(“value”);

$js.urlDecode (value);//把label1的value值进行解码

```

## $js.runjs()

在JSController中使用$js.runjs()来调用WebControl中的JS方法,在WebControl中使用$js.runjs()来调用在JSController中的JS方法

**语法**

```

$js.runjs({

 "controlid" : "webcontrol0",//webControl的id

 "func" : "xxx()"//要执行位于webControl中的js方法名

})

$js.runjs({

 "func" : "xxx()"//要执行位于JSController中的js方法名

})

```

**实例**

在WebControl中调用JSController的JS方法

```

function myfunction(){

 $js.runjs({"func":"com$yonyou$demo_webview$HomePageController$button0_onclick()"})

}

```

在JSController中使用$js.runjs()来调用WebControl中的JS方法


