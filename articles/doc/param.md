
# $param

页面间交互可以传递、接受参数。通过$param对象提供的API可以获取当前页面间传递的参数

下面说明一下目标页面com.yyuap.demo.List页面如何使用这3个API获取参数过来的参数

## $param.getString()

无论参数值原始类型，该方法统一将参数转化为字符串类型

**语法**

```

$param.getString(paramName)

```

**参数**

+ **paramName**：参数名称

**实例**

```

$view.open({

 "viewid" : "com.yyuap.demo.List", //目标页面（首字母大写）全名，

 "isKeep" : "false",

 "data1" : {

 a : 1,

 b : 2

 }, //参数是JSONObject

 "data2" : [{

 a : 1,

 b : 2

 }, {

 x : 1,

 y : 2

 }], //参数是JSONArray

 "data3" : "{x:1,y:2}", //参数是JSONObject对应的String

 "data4" : "[{a:1, b:2},{x:1,y:2}]", //参数是JSONArray对应的String

 "data5" : "hello world"//参数是String

});

```

```javascript

var data1 = $param.getString("data1");

```

**结果**："{a:1,b:2}"

**解释**：open方法中data1是一个JSONObject，使用getString方法会将参数值转化为String

```javascript

var data2 = $param.getString("data2");

```

**结果**："[{a:1,b:2},{x:1,y:2}]"

**解释**：open方法中data2是一个JSONArray，使用getString方法将参数值转化为String形式

```javascript

var data3 = $param.getString("data3");

```

**结果**："{x:1,y:2}"

**解释**：open方法中data3原本就是字符串，使用getString方法将参数值转化为String形式

```javascript

var data4 = $param.getString("data4");

```

**结果**："[{a:1,b:2},{x:1,y:2}]"

**解释**：open方法中data4原本就是字符串，使用getString方法将参数值转化为String形式

```javascript

var data5 = $param.getString("data5");

```

**结果**："hello world"

**解释**：将参数值转化为String形式

## $param.getJSONObject()

无论参数值原始类型，该方法统一将参数转化为JSONObject类型，如果转化失败，返回null

**语法**

```

$param.getJSONObject(paramName)

```

**参数**

+ **paramName**：参数名称

**实例**

```

$view.open({

 "viewid" : "com.yyuap.demo.List", //目标页面（首字母大写）全名，

 "isKeep" : "false",

 "data1" : {

 a : 1,

 b : 2

 }, //参数是JSONObject

 "data2" : [{

 a : 1,

 b : 2

 }, {

 x : 1,

 y : 2

 }], //参数是JSONArray

 "data3" : "{x:1,y:2}", //参数是JSONObject对应的String

 "data4" : "[{a:1, b:2},{x:1,y:2}]", //参数是JSONArray对应的String

 "data5" : "hello world"//参数是String

});

```

```javascript

var data = $param.getJSONObject("data1");

```

**结果**：{a:1,b:2}

**解释**：open方法中data1是一个JSONObject，使用getJSONObject方法会将参数值转化为JSONObject

```javascript

var data = $param.getJSONObject("data3");

```

**结果**：{a:1,b:2}

**解释**：将参数值转化为JOSNObject

以下转化失败，以下返回null

```javascript

var data2 = $param.getJSONArray("data2");

var data4 = $param.getJSONObject("data4");

var data5 = $param.getJSONObject("data5");

```

**结果**：null

**解释**：转化失败，返回null

## $param.getJSONArray()

将参数值转化为一个JSON数组，转化失败有提示，返回null

**语法**

```

$param.getJSONArray(paramName)

```

**参数**

+ **paramName**：参数名称

**实例**

```

$view.open({

 "viewid" : "com.yyuap.demo.List", //目标页面（首字母大写）全名，

 "isKeep" : "false",

 "data1" : {

 a : 1,

 b : 2

 }, //参数是JSONObject

 "data2" : [{

 a : 1,

 b : 2

 }, {

 x : 1,

 y : 2

 }], //参数是JSONArray

 "data3" : "{x:1,y:2}", //参数是JSONObject对应的String

 "data4" : "[{a:1, b:2},{x:1,y:2}]", //参数是JSONArray对应的String

 "data5" : "hello world"//参数是String

});

```

```javascript

var data = $param.getJSONArray("data2");

```

**结果**：[{a:1,b:2},{x:1,y:2}]

**解释**：将参数值转化为JSONArray

```javascript

var data3 = $param.getJSONArray("data4");

```

**结果**：[{a:1,b:2},{x:1,y:2}]

**解释**：将参数值转化为JOSNArray

以下转化失败，以下返回null

```javascript

$param.getJSONArray("data1");

$param.getJSONArray("data3");

$param.getJSONArray("data5");

```


