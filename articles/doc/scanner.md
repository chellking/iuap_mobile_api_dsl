

# $scanner

$scanner是提供二维码扫描的服务对象

**使用二维码扫描相关服务需要先勾选二维码扫描插件**，如下图操作：

![](/portal/upload/doc/20170302/20170302163535416.png)

## $scanner.open()

打开二维码扫描

**语法**

```

$scanner.open({

 "bindfield" : "xxxfieldName",

 "callback" : "mycallback()"

});

```

**参数**

+ **bindfield**：二维码扫描结果保存字段

+ **callback**：扫描完成后回调

**实例**

```

$scanner.open({

 "bindfield" : "code",

 "callback" : "mycallback()"

});

function mycallback() {

 var json = $ctx.getString("code");

 $alert("二维码扫描结果:" + json);

}

$scanner.open({

 "bindfield" : "code",

 "callback" : "mycallback2()"

});

function mycallback2() {

 var json = $ctx.getString("code");

 $alert("二维码扫描结果:" + json);

}

```

## $scanner.generateQRCode()

把字符串生成二维码

**语法**

```javascript

$scanner.generateQRCode()

```

**参数**

+ **twocode-size**：二维码正方形的边长

+ **twocode-content**：生成二维码所需的字符串

**实例**

```

function com$requirement0724$TwocodeImageController$onclick(sender, args) {

 var text = $id("textbox0").get("value");

 var len = $id("textbox1").get("value");

 var twocodepath = $scanner.generateQRCode({

 "size" : len, //二维码正方形的宽高

 "content" : text//生成二维码所需的源文字

 });

 $id("image0").set("src", twocodepath);

}

```


