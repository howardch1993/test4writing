## <center><font size=6 color=#8B0000 face="微软雅黑">**RMySQL在R语言下的使用**</font></center>

> [RMySQL](https://github.com/rstats-db/RMySQL) is a database interface and MySQL driver for R. This version complies with the database interface definition as implemented in the package DBI 0.2-2.
也就是说RMySQL作为数据库的接口，而由包DBI进行具体数据库操作。

### <center><font size=5 color=#00BFFF face="微软雅黑">**安装**</font></center>

**<font face="黑体">在此之前，请确认MySQL已经安装并配置好</font>**

```
#RMySQL
install.packages("RMySQL",repos="http://mirrors.xmu.edu.cn/CRAN/")
```

### <center><font size=5 color=#00BFFF face="微软雅黑">**常用函数**</font></center>
|函数名 |主要用途 |例子 |备注 |
|------|--------|-----|-----|
|dbConnect |连接数据库 |`dbConnect(RMySQL::MySQL(),user="root",password="admin",dbname="rmysql")` | |
|dbSendQuery |发送命令到数据库 |`dbSendQuery(con,"set names gbk")` |经常与*dbFetch*和*dbClearResult*搭配使用 |
|dbFetch |获取前一条命令返回的结果 |`dbFetch(res,n=-1)` |*fetch*的作用相同,其中*n*为返回结果的最大行数,*n=-1*为返回所有记录 |
|dbGetQuery |发送命令到数据库 |`dbGetQuery(con,"select * from mtcars")` |作用与*dbSendQuery*类似 |
|dbWriteTable |给数据库写入数据 |`dbWriteTable(con,"mtcars4",mtcars)` |为数据库创建一个*mtcars4*的表数据为*mtcars*;可以添加参数*append=T*插入数据,*overwrite=T*覆盖写入 |
|dbListTables |列举数据库包含的表 |`dbListTables(con)` | |
|dbListFields |列举表包含的字段 |`dbListFields(con,"mtcars")` | |
|dbReadTable |浏览表 |`dbReadTable(con,"mtcars")` | |
|dbDisconnect |断开数据库 |`dbDisconnect(con)` | |
|dbExistsTable |判断表存在 |`dbExistsTable(con,"mtcars")` | |
|dbRemoveTable |移除表 |`dbRemoveTable(con,"mtcars")` | |
<font size = 2>* con为MySQL连接对象;res为sendquery后保存的对象;mtcars为R自带的表数据</font>
