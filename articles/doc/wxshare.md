# $wxshare
提供简单的微信分享能力。

## $wxshare.init()
初始化分享能力。

**语法**
```
$wxshare.init({ "appid" : "wx853ca6a405d3947d"});
```**参数**+ **appid**：验证分享能力的ID,需在微信开放平台获取

**实例**
```
$wxshare.init({ "appid" : "wx853ca6a405d3947d"//appid需要到微信开放平台获取});
```

## $wxshare.sendText()
分享文字。

**语法**
```
$wxshare.sendText({ "type" : "friendsCircle|friend", "text" : sharedes})
```

**参数**+ **type**：分享类型（friend表示分享给好友；friendsCircle表示分享到朋友圈）+ **text**：需要分享的文字

**实例（分享给朋友）**
```
$wxshare.sendText({ "type" : "friend", "text" : "分享文字"})
```

**实例（分享到朋友圈）**
```
$wxshare.sendText({ "type" : "friendsCircle", "text" : "分享文字"})
```

## $wxshare.sendTextandImage()
分享文字和图片。

**语法**
```
$wxshare.sendTextandImage({ "type" : "friendsCircle|friend", "url" : "http://mobile.yyuap.com/", "title" : "图文测试", "des" : sharedes, "image" : shareimage});
```

**参数**+ **type**：分享类型（friend表示分享给好友；friendsCircle表示分享到朋友圈）+ **url**：需要分享的URL+ **title**：标题+ **des**：需要分享的文字描述+ **image**：需要分享的图片

**实例（分享给朋友）**
```
$wxshare.sendTextandImage({ "type" : "friend", "url" : "http://mobile.yyuap.com/", "title" : "图文测试", "des" : "分享文字", "image" : shareimage});
```

**实例（分享到朋友圈）**
```
$wxshare.sendTextandImage({ "type" : "friendsCircle", "url" : "http://mobile.yyuap.com/", "title" : "图文测试", "des" : "分享文字", "image" : shareimage});
```
