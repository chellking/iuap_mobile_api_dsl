
# $document
在JSController中可以通过全局对象$document来获取和操作当前页面内的控件。$document是一个全局对象，在JSController的任何function中都可以直接使用。$document对象近似于HTML DOM编程中的document对象，区别在于多加了一个$符号。

## $document.getElementById()
$document.getElementById是根据指定的控件Id（查找）获取该控件，其返回值是一个抽象控件类型Element。

**语法**```$document.getElementById(ID)$id(ID)```

**参数**+ **ID**:控件的id

**实例**```<label id="label2">年龄</label>$document.getElementById("label2");```

## $document.getAttribute()
通过getAttribute(attrName)方法可以获取控件的属性值

**语法**```$id(ID).getAttribute(attrName)$id(ID).get(attrName)```

**参数**+ **attrName**: 控件的属性名称

**实例**```<label id="label2">年龄</label>$id("label2").get("text");//得到label显示的信息，即年龄```

## $document.setAttribute()
通过setAttribute(attrName,attrValue)方法可以设置控件的属性值

**语法**```$id(ID).setAttribute(attrName,attrValue)$id(ID).set(attrName,attrValue)```

**参数**+ **attrName**: 控件的属性名称+ **attrValue**: 设置的控件的属性值

**实例**```<label id="label2">年龄</label>$id("label2").set("text","姓名");//设置label显示的信息，即姓名```

## $document.createElement()
通过$document.createElement()方法来动态创建控件

**语法**```$document.createElement("controlId")```

**参数**+ **controlId**：要创建控件的id

**实例**```var new_ele = $document.createElement("label");new_ele.set("id", "label1")new_ele.set("value", "xxx")new_ele.set("width", "25")new_ele.set("height", "50")new_ele.set("color", "#036EB8")new_ele.set("onclick", "removeItem()")new_ele.set("font-size", "16")```

## $document.appendChild()
通过$id().appendChild()方法把动态创建的控件放入某容器

**语法**```$id(ID).appendChild()```

**实例**```var new_ele = $document.createElement("label");new_ele.set("id", "label1")new_ele.set("value", "xxx")new_ele.set("width", "25")new_ele.set("height", "50")new_ele.set("color", "#036EB8")new_ele.set("onclick", "removeItem()")new_ele.set("font-size", "16")$id("div1").appendChild(new_ele)```

## $document.remove()
通过$document().remove()方法来删除容器内所有的控件，含容器本身

**语法**```$id("id").remove();```

**参数**+ **Id**：容器ｉｄ

**实例**```$id("div1").remove();//把id为div1的容器及容器内的控件删除```

## $document.removeAllChild()
通过$document().removeAllChild ()方法来删除动态创建容器内的控件

**语法**```$id("id").removeAllChild();```

**参数**+ **Id**：容器ｉｄ

**实例**```$id("div1").removeAllChild();

//把id为div1的容器内创建的动态控件删除```

## $id.focus()
通过$id().focus()方法指定输入类控件获得焦点

**语法**```$id(id).focus();```

**参数**+ **Id**：输入类控件的id

**实例**```$id("textbox0").focus();//textbox0文本输入控件获得焦点```

## $id.blur()
通过$id().blur()方法指定输入类控件失去焦点

**语法**```$id(ID).blur();```

**参数**+ **Id**：容器ｉｄ

**实例**```$id("textbox0").blur();//textbox0文本输入控件失去焦点```

## $id.insert()
通过$id().insert()方法在焦点处插入文本

**语法**```$id(ID).insert(content);$id(ID).insert(index,content);```

**参数**+ **content**：文本+ **index**：在输入类控件第几个字符处插入文本，从0开始**实例**```$id("textbox0").insert(4，"美好的一天")//把美好的一天插入textbox0控件的第五个字符处```
