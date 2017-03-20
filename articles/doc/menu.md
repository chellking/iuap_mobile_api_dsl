# $menu$menu是实现菜单的服务对象

## $menu.openDropDownList()$menu.openDropDownList()该方法用来打开下拉菜单

**语法**
```
$menu.openDropDownList(jsonArgs)

```

**参数**+ **controlid**：必选，目标控件的id+ **dropDownListWidth**：必选，菜单项的宽度+ 
**dropItemsArray**：必选，菜单项内容，格式为JSON数组+ **background**：可选，菜单背景色+ 
**color**：可选，菜单项字体颜色+ 
**font-size**：可选，字体大小+ 
**halign**：可选，菜单项文字对齐方式，值为center,right,left,+ **split-color**：可选，菜单分割线颜色+ 
**panelstyle**：可选，设置是否有边框，若设置有边框则属性值为"round-div"+ 
**border-color**：可选，边框颜色+ 
**showtype**：可选，与目标控件的对齐方式，默认为居中对齐，right:右对齐，left:左对齐，设置right或left之后若超出屏幕，则默认为居中对齐

**实例**
```

$menu.openDropDownList({ "controlid" : "menubtn", "dropDownListWidth" : "200", "background" : "#f5f5f5", "panelstyle" : "round-div", "border-color" : "#d2d2d2", "showtype" : "right", "dropItemsArray" : [{ "name" : "菜单1", //菜单项名称 "action" : "menuaction()", //点击该菜单项时执行的JS方法 "image" : "btn_fav.png"//菜单项的icon }, { "name" : "菜单2", //菜单项名称 "action" : "menuaction()", //点击该菜单项时执行的JS方法 "image" : "btn_fav.png"//菜单项的icon }, { "name" : "菜单3", //菜单项名称 "action" : "menuaction()", //点击该菜单项时执行的JS方法 "image" : "btn_fav.png"//菜单项的icon }]});function menuaction(sender, args) { $alert("args:" + $jsonToString(args)); $alert("点击了" + args.name);}

```
