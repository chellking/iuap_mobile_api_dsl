# $encryption
加密相关服务

## $encryption.md5()
以utf-8字符集进行md5加密服务

**语法**```$encryption.md5("这里是以utf-8字符集进行md简单加密字符串")```

**参数**+ 字符串

**实例**```var value=$id("button1").get("value");$encryption.md5(value);```

## $encryption.md5HexUtf8()
以utf-8字符集进行md5加密服务

**语法**```$encryption.md5HexUtf8("这里是以utf-8字符集进行md加密的字符串")```

**参数**+ 字符串

**实例**```var value=$id("button1").get("value");$encryption.md5HexUtf8(value);```
