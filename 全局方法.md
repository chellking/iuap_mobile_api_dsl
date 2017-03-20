## $alert()

弹出一个警告框，显示该参数对应的字符串。

**语法**

```

$alert(String|Object)

```

**参数**

 &emsp;&emsp;该方法可以接收一个字符串或一个JSON对象，

 &emsp;&emsp;如果参数是字符串，则显示字符串，

 &emsp;&emsp;如果参数是JSON对象，则显示该JSON对象的对应的字符串形式。

**返回值**

 &emsp;&emsp;无

**实例**

```

$alert("abc")//结果为显示字符串abc

$alert({a:1,b:2,c:3})//结果为字符串{"a":1,"b":2,"c":3}

```

## $confirm()

弹出一个对话框，显示该参数对应的字符串。

**语法**

```

$confirm(String)

```

**参数**

 &emsp;&emsp;该方法可以接收一个字符串

 &emsp;&emsp;参数是字符串，则显示字符串

**返回值**

 &emsp;&emsp; true||false

**实例**

```

if($confirm("需要保存吗")){

 $alert("ok");

}

```

## $toast()

 弹出toast弹窗

**语法**

```

$toast();

```

**参数**

 &emsp;&emsp;无

**实例**

```

$toast("这里录入了xxx信息")//在屏幕下方出现这里录入了xxx信息弹窗

```

## $jsonToString()

 将一个JSON对象转化为字符串。

**语法**

```

$jsonToString(JSONObject)

```

**参数**

 &emsp;&emsp;该方法可以接受一个JSON对象

**返回值**

 &emsp;&emsp;返回JSON对象对应的字符串。

**实例**

```

var str = $jsonToString({a:1,b:2,c:3});//结果为字符串{"a":1,"b":2,"c":3}

alert(str);

```

## $stringToJSON()

 将一个字符串转化为一个JSON对象。

**语法**

```

$stringToJSON(String)

```

**参数**

 &emsp;&emsp;该方法可以接受一个字符串

**返回值**

 &emsp;&emsp;返回该字符串对应的JSON对象。如果转换失败，则返回原值。

**实例**

```

var str = "{\"a\":1,\"b\":2,\"c\":3}"

var json = $stringToJSON (str);//结果为JSON对象{"a":1,"b":2,"c":3}

```

## $isJSONObject()

 判断参数是否是一个JSONObject

**语法**

```

$isJSONObject(Object)

```

**参数**

 &emsp;&emsp;该方法可以接受一个任意类型的对象

**返回值**

 &emsp;&emsp;如果是一个JSON对象，则返回true，否则返回false

**实例**

```

var p1 = "{\"a\":1,\"b\":2,\"c\":3}"

var result = $isJSONObject(p1);//result为false

var p2 = {"a":1,"b":2,"c":3}

var result = $isJSONObject(p2);//result为true

var p3 = "abc"

var result = $isJSONObject(p3);//result为false

var p4 = [{"x":"abc"},{"y":"def"}]

var result = $isJSONObject(p4);//result为false

```

## $isJSONArray()

 判断参数是否是一个数组

**语法**

```

$isJSONArray(Object)

```

**参数**

 &emsp;&emsp;该方法可以接受一个任意类型的对象

**返回值**

 &emsp;&emsp;如果是一个数组对象，则返回true，否则返回false

**实例**

```

var p1 = "{\"a\":1,\"b\":2,\"c\":3}"

var result = $isJSONArray(p1);//result为false

var p2 = {"a":1,"b":2,"c":3}

var result = $isJSONArray(p2);//result为false

var p3 = "[1,2,3]"

var result = $isJSONArray(p3);//result为false

var p4 = [{"x":"abc"},{"y":"def"}]

var result = $isJSONArray(p4);//result为true

```

## $isPlainObject()

 判断参数是否为object

**语法**

```

$isPlainObject(obj)

```

**参数**

 &emsp;&emsp;该方法可以接受一个任意类型的对象

**返回值**

 &emsp;&emsp;如果是一个object对象，则返回true，否则返回false

**实例**

```

var p1 = "{\"a\":1,\"b\":2,\"c\":3}"

var result = $isPlainObject(p1);//result为false

var p2 = {"a":1,"b":2,"c":3}

var result = $isPlainObject;//result为true

var p3 = "[1,2,3]"

var result = $isJSONArray(p3);//result为false

var p4 = [{"x":"abc"},{"y":"def"}]

var result = $isJSONArray(p4);//result为true

```

## $isFunction()

判断参数是否是一个function

**语法**

```

$isFunction(Object)

```

**参数**

 &emsp;&emsp;该方法可以接受一个任意类型的对象

**返回值**

 &emsp;&emsp;如果是一个function，则返回true，否则返回false

**实例**

```

var p1 = "{\"a\":1,\"b\":2,\"c\":3}"

var result = $isFunction(p1);//result为false

var p2 = function(e){alert(e)}

var result = $isFunction(p2);//result为true

var p3 = "[1,2,3]"

var result = $isFunction(p3);//result为false

var p4 = [{"x":"abc"},{"y":"def"}]

var result = $isFunction(p4);//result为false

```

## String.trim()

 将字符串除去前后两端的空格

**语法**

```

String.trim()

```

**参数**

 &emsp;&emsp;无

**返回值**

 &emsp;&emsp;返回字符串除去前后的空格的字符串

**实例**

```

var str = " abc ";

var result = str.trim();//result为"abc"

```

## String.ltrim()

将字符串除去左边的空格

**语法**

```

String.trim()

```

**参数**

 &emsp;&emsp;无

**返回值**

 &emsp;&emsp; 返回字符串除去前后的空格的字符串

**实例**

```

var str = " abc ";

var result = str.trim();//result为"abc "

```

## String.rtrim()

 将字符串除去右边的空格

**语法**

```

String.ltrim()

```

**参数**

 &emsp;&emsp;无

**返回值**

 &emsp;&emsp;返回字符串除去前后的空格的字符串

**实例**

```

var str = " abc ";

var result = str.ltrim();//result为" abc"

```

## Array.remove()

 移除指定索引位置的数组元素

**语法**

```

Array.remove()

```

参数

 &emsp;&emsp;无

**返回值**

 &emsp;&emsp;返回移除指定索引位置的数组元素后的数组

**实例**

```

var array = [1,2,3,4,5];

var result = array.remove(1);//result为[1,3,4,5]

var result = result.remove(1);//result为[1,4,5]

```


