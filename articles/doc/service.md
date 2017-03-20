

# $service

与服务器服务处理

## $service.writeConfig()

写配置文件

**语法**

```

$service.writeConfig({

 "host" : "10.2.112.58", //向configure中写入host键值

 "port" : "8080" //向configure中写入port键值

})

```

+ key-value键值对

**实例**

```

$service.writeConfig({

 "host" : "10.2.112.58", //向configure中写入host键值

 "port" : "8080" //向configure中写入port键值

})

```

## $service.openHTTPS()

开启HTTPS，通常在调用callAction、post、get之前执行

**语法**

```

$service.openHTTPS({

 "ishttps" : "true"//是否开启https传输

})

```

**参数**

+ **ishttps**：是否开启https传输

**实例1：callAction开启HTTPS**

```

$service.openHTTPS({

 "ishttps" : "true"//是否开启https传输

})

$service.callAction({

 "viewid" : "xxx.xxx.xx", //后台带包名的Controller名

 "action" : "methodName", //方法名,

 "params" : {

 "a" : 1,

 "b" : 2

 }, //自定义参数

 "autoDataBinding" : true, //请求完毕后，是否进行数据绑定，如果没有该属性，则默认不绑定。

 "contextmapping" : "fieldPath", //将返回结果映射到指定的Context字段上，如果没有该属性，则默认为替换整个Context

 "callback" : "mycallback()", //请求回来后执行的js方法

 "error" : "myerror()"//失败回调的js方法

})

```

**实例2：post、get开启HTTPS**

```

$service.openHTTPS({

 "ishttps" : "true"//是否开启https传输

})

var url = "http://www.dnetzj.com/httpclient/nethomersssearch";

$service.get({

 "url" : url,

 "callback" : function() {

 $service.call("UMJS.hideLoadingBar", {});

 var result = $ctx.param("result");

 //get和post的CallBack中获取返回结果都从result中获取

 result = $stringToJSON(result);

 //将字符串转换成JSON对象

 $alert("CountPage:" + result.CountPage);

 }

});

```

```

$service.openHTTPS({

 "ishttps" : "true"//是否开启https传输

})

var args = {};

args["url"] = "http://academy.yonyou.com/api/loginLx.ashx";

args["data"] = {

 key : "6480-4230-27FD-8AA0",

 user : "apitest",

 pwd : "123456"

};

args["callback"] = "postCallback()";

$service.post(args);

function postCallback() {

 $alert("JS调用Post请求");

 $alert($ctx.getString());

 var result = $ctx.param("result");

 // CallBack中获取返回结果都从result中获取

 $alert(result);

 //result是字符串

 result = $stringToJSON(result);

 //将字符串转换成JSON对象

 if (result.status == false || result.status == "false") {

 alert("result.status == " + result.status + "\n" + "result.errCode == " + result.errCode + "\n" + "result.errMsg == " + result.errMsg);

 } else if (result.status == true || result.status == "true") {

 alert("result.status == " + result.status + "\n" + "result.userName == " + result.userName);

 }

}

```

## $service.callAction()

访问MA服务器，调用MA上指定Controller类的指定方法

**语法**

```

$service.callAction({

 "viewid" : "xxx.xxx.xx", //后台带包名的Controller名

 "action" : "methodName", //方法名,

 "params" : {

 a : 1,

 b : 2

 }, //自定义参数

 "autoDataBinding" : true, //请求完毕后，是否进行数据绑定，如果没有该属性，则默认不绑定。

 "contextmapping" : "fieldPath", //将返回结果映射到指定的Context字段上，如果没有该属性，则默认为替换整个Context

 "callback" : "mycallback()", //请求回来后执行的js方法

 "error" : "myerror()", //失败回调的js方法

 "header" : {

 "Content-Type" : "application/x-www-form-urlencoded",

 "User-Agent" : "imgfornote"

 }

})

```

**参数**

+ **viewid**：后台带包名的Controller名，即在src/public包下建立的类

+ **action**：上述类中的方法名

+ **params**：自定义参数，json格式

+ **autoDataBinding**: 请求结束后，是否进行数据绑定，如果无该属性，则默认不绑定

+ **contextmapping**：context中字段的全路径，如果没有指定该属性，则默认为替换整个Context。

 + 取值可以为常量"none"，表示若有返回数据也将不做任何操作，即不会影响Context

 + 取值可以是带全路径的字段名，例如a，a.b, a.b.c,

 + 取值可以是{a:x,b:y}，表示返回数据中的x替换Context中的a字段，返回数据中的y替换Context中的b字段

+ **callback**：请求成功后执行的js方法

+ **error**：请求失败后执行的js方法

+ **timeout：可选参数，超时时间，单位为秒**

+ **mauploadpath：可选参数，携带文件的路径**

 + 多个文件批量上传时，mauploadpath参数中的多个文件用","分割

 + 详细使用方法参阅 移动运行支撑平台（MA）-MA开发指导下的***《获取手机端上传的文件流》***

 + 使用此参数需要勾选**上传（upload）插件**，详见***《获取手机端上传的文件流》***

+ **header**：可选参数，请求头，值为JSON

**实例**

【Java部分】

```java

//viewid中描述的Java类

//viewid中描述的Java类

package com.yonyou;

import com.yonyou.um.webmvc.controller.UMController;

public class Data extends UMController {

 public String getResult() {

 // this.getClientData("key"); //all data

 Object dd = this.getParaFromClient("mydata");

 return "{result:\"hello,uap mobile.data is:" + dd + "\"}";

 }

}

```

【JS部分】

```javascript

//调用callAction

$service.writeConfig({

 "host" : "10.2.112.58", //向configure中写入host键值

 "port" : "8085"//向configure中写入port键值

})

$service.callAction({

 "viewid" : "com.yonyou.Data", //后台带包名的Controller名

 "action" : "getResult", //方法名,

 "mydata" : "{a:123,b:465}", //自定义参数

 "callback" : "cbcallma()", //请求回来后执行的ActionID

 "error" : "errorcallma()"//失败回调的ActionId

});

function cbcallma() {

 var result = $ctx.getJSONObject().result;

 $alert(result);

}

function errorcallma() {

 $alert("error!");

}

```

## $service.get()

向HTTP服务器发送get请求.

**语法**

```

$service.get({

 "url" : "www.xxx.comxxxxxx.html",

 "callback" : function(sender, arges) {

 $alert(eval(arges.result));

 },

 "header" : {

 "Content-Type" : "application/x-www-form-urlencoded",

 "User-Agent" : "imgfornote"

 },

 "timeout" : "5"

})

```

**参数**

+ **url**：必选参数，get请求的URL

+ **callback**：可选参数，get请求成功的回调js方法

+ **timeout**: 可选参数，超时时间，单位为秒

+ **header**:可选参数，该参数对应一个json，方便开发者设置请求的header

**实例**

```

var url = "http://www.dnetzj.com/httpclient/nethomersssearch";

$service.get({

 "url" : url,

 "callback" : function() {

 $service.call("UMJS.hideLoadingBar", {});

 var result = $ctx.param("result");

 //get和post的CallBack中获取返回结果都从result中获取

 result = $stringToJSON(result);

 //将字符串转换成JSON对象

 $alert("CountPage:" + result.CountPage);

 }

});

```

## $service.post()

向HTTP服务器发送post请求。

**语法**

```

$service.post({

 "url" : "www.xxx.comxxxxxx.html",

 "data" : {

 "a" : 1,

 "b" : 2

 },

 "callback" : function(sender, arges) {

 $alert(eval(arges.result));

 },

 "header" : {

 "Content-Type" : "application/x-www-form-urlencoded",

 "User-Agent" : "imgfornote"

 },

 "timeout" : 5

})

```

**参数**

+ **url**：必选参数，post请求的URL

+ **data**：可选参数，如果有此数据，必须封装在data中，post请求的要写入的数据，须为json对象

+ **callback**：可选参数，post请求成功后的回调js方法

+ **timeout**:可选参数，超时时间，单位为秒

+ **header**:可选参数，该参数对应一个json，方便开发者设置请求的header

**实例**

```

var args = {};

args["url"] = "http://academy.yonyou.com/api/loginLx.ashx";

args["data"] = {

 key : "6480-4230-27FD-8AA0",

 user : "apitest",

 pwd : "123456"

};

args["callback"] = "postCallback()";

$service.post(args);

function postCallback() {

 $alert("JS调用Post请求");

 $alert($ctx.getString());

 var result = $ctx.param("result");

 // CallBack中获取返回结果都从result中获取

 $alert(result);

 //result是字符串

 result = $stringToJSON(result);

 //将字符串转换成JSON对象

 if (result.status == false || result.status == "false") {

 alert("result.status == " + result.status + "\n" + "result.errCode == " + result.errCode + "\n" + "result.errMsg == " + result.errMsg);

 } else if (result.status == true || result.status == "true") {

 alert("result.status == " + result.status + "\n" + "result.userName == " + result.userName);

 }

}

```

## $service.call()

该方法用来调我们已有的服务和第三方扩展服务。

**语法**

```

 $service.call("UMCtx.dataBind", {}, false)

```

**参数**

+ **UMCtx.dataBind**：服务名,字符串类型。规则为xxx.yyy，其中xxx表示原生服务的类名，yyy表示该类下的一个方法

+ **{}**：该服务的参数，json对象类型。该json对象的key值是该原生服务的参数名，value值为对应的参数值。一个服务可以有多个参数,用一个json对象来表达

+ **false**：异步执行或同步执行，布尔类型，如果该服务需要立即获取返回值的通常为同步调用，参数为ture；有回调方法的则为异步，参数为false。其中callback定义在第二个参数中，该参数是可选参数，没有该参数时，默认为异步调用

**实例1(同步调用)**

```

$service.call("getListProperty", {

 "controlId" : "listview0",

 "rowindex" : 2,

 "childcontrolId" : "label0",

 "propertyname" : "value"

}, true);// 单列表行内的控件属性,我们提供的服务一般不需要这么用，我们对提供的服务都进行了封装

```

**实例2(异步调用)**

```

$service.call("UMdevice.opencamere", {

 "bindfield" : "xxxfieldName",

 "callback" : "mycallback()"

}, false);

```

## $service.readConfig()

读配置文件。

**语法**

```

$service.readConfig(key)//获取Configure中key的键值

```

**参数**

+ key值

**实例**

```

var host = $service.readConfig("host");

```

## $service.loadConfig()

必须先使用writeConfig，才能使用loadConfig，将writeConfig写入config文件中的值加载到context中，使用$ctx.get(“”);获取相应的值。

**语法**

```

$service.loadConfig({

 "host" : "field1", //将host的值写入当前Context的field1字段

 "port" : "field2"//将ip的值写入当前Context的field2字段

})

```

**参数**

+ JSON格式，其中key：writeConfig中的key值，fieldname：context的字段名，可任意

**实例**

```

//将config中的host和ip的值分别写入Context中的fieldA或FieldB字段中

$service.loadConfig({

 "host" : "fieldA",

 "port" : "fieldB"

});

```


