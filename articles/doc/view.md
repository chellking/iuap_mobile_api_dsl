# $view

$view是一个可以调用页面相关公共服务的全局对象。通过$view提供不同的方法，可以进行页面导航、页面传值等。

## $view.open()

$view.open()方法的作用是打开一个新页面

**语法**

```

$view.open({

 "viewid" : "xx.xx.xx.WindowId",

 "isKeep" : "true",

 "callback" : "mycallback()"

});

```

**参数**

+ **viewid**：目标页面（首字母大写）全名

+ **isKeep**：打开新页面的同时是否保留当前页面，true为保留，false为不保留

+ **callback**：可选，viewid页面关闭后，执行的回调JS，使用callback时，isKeep需为true

**实例1**

```

$view.open({

 "viewid" : "com.yyuap.myref.List",

 "isKeep" : "false"

})

```

**实例2**

```

$view.open({

 "viewid" : "com.yyuap.myref.List",

 "isKeep" : "true",

 "callback": function(){

 var ret = $param.getJSONObject("result");

 $id("label4").set("value", ret.id);

 $id("label9").set("value", ret.code);

 $id("label14").set("value", ret.name);

 }

})

```

**实例3（页面特效）**

```

//淡入

$view.open({

 "viewid" : "com.yyuap.demo.UMNetworkTest", //目标页面（首字母大写）全名

 "isKeep" : "true",

 "animation-direction" : "left",

 "animation-time" : "1000", //动画持续时间，以毫秒为单位

 "animation-type" : "Fade"//动作类型

});

//由右往左滑屏

$view.open({

 "viewid" : "com.yyuap.demo.UMNetworkTest", //目标页面（首字母大写）全名

 "isKeep" : "true",

 "animation-direction" : "left", //方向

 "animation-time" : "1000", //动画持续时间，以毫秒为单位

 "animation-type" : "Push" //动画持续时间，以毫秒为单位

});

//由左往右滑屏

$view.open({

 "viewid" : "com.yyuap.demo.UMNetworkTest", //目标页面（首字母大写）全名

 "isKeep" : "true",

 "animation-direction" : "right",

 "animation-time" : "1000",

 "animation-type" : "Push"

});

//由下往上滑屏

$view.open({

 "viewid" : "com.yyuap.demo.UMNetworkTest", //目标页面（首字母大写）全名

 "isKeep" : "true",

 "animation-direction" : "top",

 "animation-time" : "1000",

 "animation-type" : "Push"

});

//由上往下滑屏

$view.open({

 "viewid" : "com.yyuap.demo.UMNetworkTest", //目标页面（首字母大写）全名

 "isKeep" : "true",

 "animation-direction" : "bottom",

 "animation-time" : "1000",

 "animation-type" : "Push"

});

//交叉覆盖

$view.open({

 "viewid" : "com.yyuap.demo.UMNetworkTest", //目标页面（首字母大写）全名

 "isKeep" : "true",

 "animation-direction" : "bottom",

 "animation-time" : "1000",

 "animation-type" : "MoveIn"

});

//缩小效果

$view.open({

 "viewid" : "com.yyuap.demo.UMNetworkTest", //目标页面（首字母大写）全名

 "isKeep" : "true",

 "animation-direction" : "top",

 "animation-time" : "1000",

 "animation-type" : "suckEffect"

});

//翻转效果

$view.open({

 "viewid" : "com.yyuap.demo.UMNetworkTest", //目标页面（首字母大写）全名，

 "isKeep" : "true",

 "animation-direction" : "left",

 "animation-time" : "1000",

 "animation-type" : "oglFlip"

});

```

## $view.close()

$view.close()是用来关闭当前页面

**语法**

```

$view.close();

```

**参数**

*无*

**实例**

```

$view.close();

```

## $view.closeWithCallBack()

$view.close()是用来关闭当前页面，并返回数据给前一个页面（前一个页面需未关闭）

**语法**

```

$view.closeWithCallBack({

 "result1" : "{a:1, b:2}",

 "result2" : "{x:3, y:4}"

})

```

**参数**

+ 自定义参数: 可选，key-value形式，例如下例中的result

**实例1**

```

$view.closeWithCallBack({

 "result1" : "{a:1, b:2}",

 "result2" : "{x:3, y:4}"

})

```

**实例2**

```

$view.closeWithCallBack({

 "result" : $id("listview0").get("row")

});

```

## $view.openPop()

$view.openPop()方法是打开一个浮动窗口

**语法**

```

$view.openPop(jsonArgs)

```

**参数**

+ **viewid**：必选，打开的浮动窗口的id

+ **autoclose**：可选，自动关闭的时间，单位为毫秒

+ **popgravity**：可选，弹开方式，值为popbottom|poptop|popleft|popright|popcenter

**实例**

```

$view.openPop({

 "viewid" : "panel0", //显示的控件的id，通常是一个容器控件div

 "popgravity" : "popbottom", //popcenter|poptop|popbottom|popleft|popright,弹出后最终显示的位置

 "autoclose" : "1000"//弹出后多长时间(毫秒)后自动消失

})

```

## $view.closePop()

$view.closePop()方法是关闭浮动

**语法**

```

$view.closePop(jsonArgs)

```

**参数**

+ **viewid**：必选，当前页面的widget

**实例**

```

var params = {

 "viewid" : "panel0"

};

$view.closePop(params)

```

## $view.openDialog()

$view.openDialog()方法是打开一个自定义的对话框

**语法**

```

$view.openDialog(jsonArgs)

```

**参数**

+ **style**：对话框弹出样式，含ok-cancel | waitdialog | text-dialog

+ **title**：标题

+ **message**：提示信息

+ **okaction**：点击确定按钮时触发的action

+ **cancelaction**：点击取消按钮时触发的action

+ **okbuttontitle**：确定按钮显示名称

+ **cancelbuttontitle**：取消按钮显示名称

**实例**

```

var params = {

 "title" : "dialog",

 "message" : "天空中最亮的星也有权利争取最美的灿烂",

 "okbuttontitle" : "确定",

 "cancelbuttontitle" : "取消",

 "style" : "ok-cancel",

 "okaction" : "ok()",

 "cancelaction" : "cancel()"

};

$view.openDialog(params);

function ok() {

 $alert("click ok button");

}

function cancel() {

 $alert("click cancel button");

}

```

## $view.openPicker()

$view.openPicker()方法打开一个自定义的选择器

**语法**

```

$view.openPicker(jsonArgs)

```

**参数**

+ **pickercount**：picker的段数，默认值为1

+ **datasource**：绑定特殊结构的数据源

+ **title**：标题

+ **okbuttontitle**：确定按钮显示文本

+ **cancelbuttontitle**：取消按钮显示文本

+ **picker1binder**：picker1收集再context中的字段名

+ **picker2binder**：picker2收集再context中的字段名

+ **picker3binder**：picker3收集再context中的字段名

+ **okaction**：点击确定按钮时触发的action，事件中会收集picker中所选中的数据加入到context中

+ **onselectedchange1**：picker1选中值发生改变后的事件

+ **onselectedchange2**：picker2选中值发生改变后的事件

+ **onselectedchange3**：picker3选中值发生改变后的事件

**实例**

```

var params = {

 "okaction" : "save()",

 "title" : "Hello Picker",

 "pickercount" : "3",

 "datasource" : {

 "picker" : [{

 "select" : [{

 "value" : 1,

 "content" : 1

 }, {

 "value" : 2,

 "content" : 2

 }, {

 "value" : 3,

 "content" : 3

 }]

 }, {

 "select" : [{

 "value" : 1,

 "content" : "张三"

 }, {

 "value" : 2,

 "content" : "李四"

 }, {

 "value" : 3,

 "content" : "王五"

 }]

 }, {

 "select" : [{

 "value" : 25,

 "content" : 25

 }, {

 "value" : 23,

 "content" : 23

 }, {

 "value" : 26,

 "content" : 26

 }]

 }]

 },

 "picker1binder" : "no",

 "picker2binder" : "name",

 "picker3binder" : "age"

};

$view.openPicker(params);

function save() {

 var data = $ctx.getString("name");

 data = $stringToJSON(data);

 var result = data.content;

 $alert(result);

}

```

可以通过var no = $ctx.getString("no")得到的是一个json形式的String，如{“value”:”1”,”content”:”1”}，使用no = $stringToJSON(no);转化成JSON对象，然后通过no.content或者no.value取得相应的值。


