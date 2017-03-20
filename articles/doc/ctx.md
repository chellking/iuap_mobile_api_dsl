# $ctx

CTX上下文

## $ctx.dataBind()

把context的数据绑定到控件

**语法**

```

$ctx.dataBind();

```

**参数**

*无*

**实例**

```

//假设textbox0绑定字段为name

<input id = "textbox0" bindfield = "name" / >

$ctx.put("name", "123");

alert($id("textbox0").get("value"));

//此时不能从控件上获取name的值，因为没有数据绑定

$ctx.dataBind();

//数据绑定

alert($id("textbox0").get("value"));

//此时可以获取name的值123，因为已经做过数据绑定

```

## $ctx.dataCollect()

收集当前页面控件的数据，即把控件的数据收集到对应的context字段上

**语法**

```

$ctx.dataCollect();

```

**参数**

*无*

**实例**

```

//假设dateinput0绑定字段为mydate 触发onchange事件后执行mychange()

<input id = "dateinput0" bindfield = "mydate" onchange = "mychange()" >

function mychange() {

 alert($id("dateinput0").get("value"))//可以获取控件上的值

 alert($ctx.getString("mydate"))//不能获取，因为还未数据收集

 $ctx.dataCollect();

 //调用数据收集，将控件写入context的mydate字段

 alert($ctx.getString("mydate"));

 //此时获取可以，因为已经调用过数据收集

}

```

## $ctx.push()

把数据push到ctx里并显示到控件

**语法**

```

$ctx.push();

```

**参数**

+ json对象

**实例**

```

<listView id="listview0" bindfield="mydata" onload="onload()">

function onload() {

 var json = {

 "mydata" : []

 };

 for (var i = 1; i < 10; i++) {

 var person = {};

 person.no = i.toString();

 person.name = "木子" + i.toString();

 json.mydata.push(person);

 }

 $ctx.push(json);

 //把数据push进页面的数据上下文即ctx里

}

```

## $ctx.put()

将key写入ctx里，写完之后要执行$ctx.dataBind()才能显示到控件

**语法**

```

$ctx.put(key,value);

```

**参数**

+ key-value键值对

**实例**

```

<label id="label1" bindfield="num">label</label>

function this.onclick(sender, args) {

 $ctx.put("num", "把值put到ctx里");

 $ctx.dataBind();

}

```

## $ctx.getString()

将当前数据上下文指定数据，以字符串形式返回

**语法**

```

$ctx.getString()

$ctx.getString(fieldName)

```

**参数**

+ 没有参数或指定一个字段名

**返回值**

+ 若无参数，则返回当前数据上下文对应的字符串

+ 若有参数，则返回指定字段对应的字符串

**实例1**

```

//假设当前Context对应的JSON为{"x":{"a":"1"},"y":{"b":"2"}}

var str = $ctx.getJSONString();

alert(str);

//str结果为字符串{"x":{"a":"1"},"y":{"b":"2"}}

```

**实例2**

```

//假设当前Context对应的JSON为{"x":{"a":"1"},"y":{"b":"2"}}

var str = $ctx.getJSONString("y");

//str结果为字符串{"b":"2"}

alert(str)

```

## $ctx.getJSONObject()

将当前数据上下文中指定数据，以JSONObject形式返回

**语法**

```

$ctx.getJSONObject()

$ctx.getJSONObject(fieldName)

```

**参数**

+ 若无参数，则返回当前数据上下文对应的字符串

+ 若有参数，则返回指定字段对应的字符串

**返回值**

+ 将当前数据上下文对应的字符串

**实例1**

```

var str = $ctx.getJSONObject();//str结果为JSON对象

$alert(str)

```

**实例2**

```

//假设当前Context对应的JSON为{"x":{"a":"1"},"y":{"b":"2"}}

var str = $ctx.getJSONObject("y");//str结果为JSON对象{"b":"2"}

$alert(str)

```

## $ctx.getJSONArray()

将当前数据上下文指定数据以数组形式返回，常用于获取列表的数据

**语法**

```

 $ctx.getJSONArray(fieldName)

```

**参数**

+ 字段名

**返回值**

+ 将当前数据上下文中指定字段对应的数组

**实例**

```

//假设当前数据上下文为{"users":[{"name":"张三"},{"name":"李四"}]}

var users = $ctx.getJSONArray("users");

alert(users.length)//结果为2

```

## $ctx.setApp()

可以存储应用级的context，可以用这个方法存储登陆用户信息

**语法**

```

$ctx.setApp({

 "a" : "x",

 "b" : "#{plug.x}",

 "c" : "#{name}",

 "d" : "#{cursor.x}"

})

```

**参数**

+ Json对象

**实例**

```

$ctx.setApp({

 "username" : $ctx.getString("username"),

 "userpwd" : $ctx.getString("userpwd")

});

```

## $ctx.getApp()

获取存储应用级的context中内容，常与setApp结合使用。

另外在Config\application.properties配置文件中写的键值对，也可以通过$ctx.getApp()获取。

**语法**

```

 $ctx.getApp(expr)

```

**参数**

+ 获取指定字段

**返回值**

+ 返回指定字段对应的字符串

**实例**

```

var username = $ctx.getApp("username");

```


