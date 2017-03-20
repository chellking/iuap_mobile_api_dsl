# $camera

$camera是对相机、图库等操作的服务对象

## $camera.open()

$camera.open()该方法用来打开系统相机，支持回调callback。通常获取相机拍摄的照片通过callback来实现。

**语法**

```

$camera.open(jsonArgs)

```

**参数**

+ **bindfield**：存储照片的字段

+ **callback**：回调

+ **compressionRatio**：按比例压缩图片大小，值为0-1，例如："compressionRatio" : 0.5

**实例1**

```

//open的时候指定了bindfield，callback中可以通过bindfield来获取照片

$camera.open({

 "bindfield" : "image",

 "callback" : function() {

 var img = $ctx.getString("image");

 $id("image0").set("src", img);

 }

});

```

**实例2**

```

//open的时候指定了bindfield，callback中可以通过bindfield来获取照片

$camera.open({

 "bindfield" : "image",

 "compressionRatio" : 0.5,

 "callback" : function() {

 var img = $ctx.getString("image");

 $id("image0").set("src", img);

 }

});

```

## $camera.openPhotoAlbum()

$camera.openPhotoAlbum()该方法用来打开系统相册

**语法**

```

$camera.openPhotoAlbum(jsonArgs)

```

**参数**

+ **bindfield**：存储照片的字段

+ **callback**：回调

+ **compressionRatio**：按比例压缩图片大小，值为0-1，例如："compressionRatio" : 0.5

**实例**

```

$camera.openPhotoAlbum({

 "bindfield" : "image",

 "callback" : function() {

 var img = $ctx.getString("image");

 $id("image0").set("src", img);

 }

});

```


