# 参数sender和args使用说明



> 为控件添加的每一个事件都会携带sender和args参数，所有的回调也都可以接收这两个参数。



sender可以获取触发该事件的控件的id，args用于获取该事件的上下文数据。



## sender示例



如点到任意button，会弹出点到的具体是哪个



```html

<input id="button1" value="2" onclick="click()" type="button"/>

<input id="button0" value="1" onclick="click()" type="button"/>

```



button对应的事件都是onclick="click()"



```javascript

function click(sender, args){

 $alert("你选中了"+ sender);//选中控件的id

}

```



## args示例



如获取控件执行touch事件时，获取当前位置坐标



```html

<div id="panel0" ontouch="yidong()"/>

<div id="panel1" ontouch="yidong()"/>

<label id="label2">当前坐标</label>

<label id="label3"/>

```



```javascript

function yidong(sender, args){

 $id("label3").set("value", args);//在label3中显示执行touch事件，当前位置坐标

}

```



## 回调中接收参数示例



```javascript

function requestData(){

 $service.callAction({

 viewid: "nc.mobile.pull.query_application.QueryApplicationController",//部署在MA上的Controller的包名

 action: "queryApplication",//后台Controller的方法名,

 params: {json:JSON.stringify(queryCondition)},//自定义参数，json格式

 autoDataBinding: false,//请求回来的数据会在Context中，是否进行数据绑定，默认不绑定

 contextmapping: "filedNameOrFieldPath",//将返回结果映射到指定的Context字段上，支持fieldName和xx.xxx.fieldName字段全路径，如未指定contextmapping则替换整个Context

 callback: "queryDataSuccessCallBack()",//请求成功后回调js方法

 error: "queryDataErrorCallBack()",//请求失败回调的js方法

 });

}



function queryDataSuccessCallBack(sender, args){

 $alert("成功：" + args.err_msg);

}



function queryDataErrorCallBack(sender, args){

 $alert("失败：" + args.err_msg);

}

```

**$alert("失败：" + args.err_msg);中args.err_msg就是从参数中取出的调用MA错误时的错误信息。**


