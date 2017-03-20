# $cache

$cache是当前本地缓存服务对象，可以用来读写缓存数据

## $cache.write()、$cache.read()

$cache.write()方法用来写缓存数据和缓存文件，$cache.read()方法用来读取缓存数据内容

**语法1**

```

$cache.write (key,value)

$cache.read(key)

```

**参数**

+ **key**：缓存的键值

+ **value**：缓存中存储的值

**实例**

```

//测试缓存字符串

var salarypswd = "000001";

$cache.write("salarypswd", salarypswd);

var newpsw = $cache.read("salarypswd");

$alert(newpsw)

$alert("取出来的值为:" + newpsw); //应该为000001

var str1 = "{m:1,n:2,p:aaa}";

$alert("开始测试缓存字符串" + str1 + "");

$cache.write("str1", str1);

var new_str1 = $cache.read("str1");

$alert(new_str1)

$alert("取出来的值为:" + new_str1); //应该为字符串{m:1,n:2,p:aaa}

var obj1 = {

 m : 1,

 n : 2,

 p : "aaa"

};

$alert("*****开始测试缓存json对象为" + $jsonToString(obj1) + "*****");

$cache.write("obj1", obj1);

var new_obj1 = $cache.read("obj1");

$alert(new_obj1); //取出来的是一个字符串

$alert("取出来的值为:" + new_obj1);

var json1 = $stringToJSON(new_obj1);

$alert("$stringToJSON(new_obj1) = " + json1); //此时json1是一个object

$alert("$jsonToString(json1) = " + $jsonToString(json1));

```

**语法2**

```

$cache.write(filePath, content)

$cache.read(filePath)

```

**参数**

+ **filePath**: 缓存文件的路径+文件名

+ **content**: 写入缓存文件中的内容

**实例**

```

$cache.write("filetest/test.txt", "天空中最微弱的星也有权利争取最美的灿烂");

var value = $cache.read("filetest/test.txt");

$alert("文件内容:" + value);

```


