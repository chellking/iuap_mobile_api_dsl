# $sqlite
$sqlite是数据库服务对象，可以进行数据库增、删、改、查等操作

## $sqlite.openDB()
$sqlite.openDB()方法用来打开或创建数据库表

**语法**```var param = { "db" : 'qq.db'}$sqlite.openDB(param)```

**参数**+ **db**: 操作的数据库名称

**实例**```var param = { "db" : 'qq.db'}$sqlite.openDB(param);```

## $sqlite.execSql()$sqlite.execSql()方法用来执行SQL语句

**语法**```$sqlite.execSql(db,sql)```

**参数**+ **db**: 操作的数据库名称+ **sql**: 执行的sql语句+ **callback**: 执行的sql语句后结果执行的callbackk**实例**```var sql = "CREATE TABLE person (_id INTEGER PRIMARY KEY AUTOINCREMENT, name VARCHAR, xclass VARCHAR)";var param = { "db" : dbname, "sql" : sql, "callback":"mycallback()"};$sqlite.execSql(param);``````function mycallback(sender,arg){ $alert(arg);}```

## $sqlite.queryByPage()
$sqlite. queryByPage ()方法用来查询数据库，返回类型为json数组格式的字符串

**语法**```$sqlite.queryByPage(jsonArgs)```

**参数**+ **db**：数据库名称+ **sql**：执行的sql语句+ **pageSize**： pageSize，每页的记录数，从1开始+ **pageIndex**：pageIndex，页号索引，从0开始

**返回值**+ 字符串string类型数组

**实例**```function query_data(pageindex, queryKeyword) { var sql = "select * from person"; if (queryKeyword) { sql += " where xclass like '%" + queryKeyword + "%'"; } var param = { "db" : dbname, "sql" : sql, "pageIndex" : pageindex, //pageIndex=页号，从0开始 "pageSize" : 100 //pageSize=每页的记录数，从1开始 } var data = $sqlite.queryByPage(param); var rs = { "list" : data } $ctx.push(rs);}```

## $sqlite.query()
$sqlite.query()用来查询数据库

**语法**```$sqlite.query(jsonArgs)```

**参数**+ **db**：数据库名称+ **sql**：执行的sql语句+ **startIndex**：可选，从第几条记录开始， Index表示从0开始+ **endIndex**：可选，到第几条记录结束（返回值包含该条）

**返回值**+ 字符串string类型数组实例```function query_data(startIndex, endIndex, queryKeyword) { var sql = "select * from person"; if (queryKeyword) { sql += " where xclass like '%" + queryKeyword + "%'"; } var param = { "db" : dbname, "sql" : sql, "startIndex" : startIndex, //起始记录索引号(含) "endIndex" : endIndex //结束记录索引号(含) } var data = $sqlite.query(param); var rs = { "list" : data } $ctx.push(rs);}```1、指定startIndex，endIndex的用法```javascript$sqlite.query({ "db" : dbname, "sql" : sql, "startIndex" : 0, //从第几条记录开始 "endIndex" : 9 //到第几条记录结束(含)});```

2、不指定startIndex和endIndex则表示全部数据```javascript$sqlite.query({ "db" : dbname, "sql" : "select * form table1 where name like '%张%'",});```

3、仅仅指定了startIndex，未指定endIndex或endIndex=-1，则表示从startIndex开始的全部数据```javascript$sqlite.query({ "db" : dbname, "sql" : "select * form table1 where name like '%张%'", "startIndex" : 20, //从第21条记录开始的全部数据});

$sqlite.query({ "db" : dbname, "sql" : "select * form table1 where name like '%张%'", "startIndex" : 20, //从第21条记录开始的全部数据 "endIndex" : -1 //到第几条记录结束(含)});```

## $sqlite.exist()
$sqlite.exist()方法用来判断数据库是否已经创建存在

**语法**```$sqlite. exist(db)```

**参数**+ **db**：数据库名称返回值：+ **字符串**：true|false

**实例**```var param = { "db" : dbname}if ($sqlite.exist(param) == "false") { initDB();}```
