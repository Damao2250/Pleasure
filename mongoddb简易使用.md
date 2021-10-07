1. 配置数据库路径

    到  C:\Windows\System32\cmd.exe 目录下运行cmd

    运行  mongod --dbpath D:\data\db  （D:\data\db 自己新建目录）

2. MongoDB - 连接（启动 MongoDB 服务）

    你只需要在 MongoDB 安装目录的 bin 目录下执行 mongodb 即可。

3. 创建数据库

    ```js
    use DATABASE_NAME
    //如果数据库不存在，则创建数据库，否则切换到指定数据库。
    show dbs

    //查看所有数据库
    ```
4. 删除数据库

```js
    db.dropDatabase()
    //删除当前数据库，默认为 test，你可以使用 db 命令查看当前数据库名

```

5. 删除合集

```js
    //collection为表名（下同）
    db.collection.drop()

    //以下实例删除了 user 数据库中的集合 site：
    use user
    //switched to db user
    show tables
    //site
    db.site.drop()
    //true
    show tables
    //
```

6. 创建合集（相当于表）

```js
    db.createCollection(name, options)
    //name: 要创建的集合名称
    //options: 可选参数, 指定有关内存大小及索引的选项

    show collections
    //查看合集
```
7. 插入文档

```js
    db.COLLECTION_NAME.insert({'a':'A','b':'B'})
    //使用 insert() 或 save() 方法向集合中插入文档
    // COLLECTION_NAME 是集合名，如果该集合不在该数据库中， MongoDB 会自动创建该集合并插入文档。
    //以json字符串格式插入
```
8. 更新文档

```js
    //query : update的查询条件，类似sql update查询内where后面的。
    //update : update的对象和一些更新的操作符（如$,$inc...）等，也可以理解为sql update查询内set后面的
    //upsert : 可选，这个参数的意思是，如果不存在update的记录，是否插入objNew,true为插入，默认是false，不插入。
    //multi : 可选，mongodb 默认是false,只更新找到的第一条记录，如果这个参数为true,就把按条件查出来多条记录全部更新。
    //writeConcern :可选，抛出异常的级别。

    db.collection.update(
        <query>,
        <update>,
        {
            upsert: <boolean>,
            multi: <boolean>,
            writeConcern: <document>
        }
    )   
```
9. 删除文档

```js
    //query :（可选）删除的文档的条件。
    //justOne : （可选）如果设为 true 或 1，则只删除一个文档。
    //writeConcern :（可选）抛出异常的级别。

    db.collection.remove(
    <query>,
        {
            justOne: <boolean>,
            writeConcern: <document>
        }
    )

```

10. 查文档
```js
    //query ：可选，使用查询操作符指定查询条件
    //projection ：可选，使用投影操作符指定返回的键。查询时返回文档中所有键值， 只需省略该参数即可（默认省略）。
    db.collection.find(query, projection)

    //pretty() 方法以格式化的方式来显示所有文档

    db.collection.find().pretty()

```

11. 根据 _id 删除

    
    + 需要先 var ObjectID = require('mongodb').ObjectID;
    + 然后再 collection.findAndRemove({_id: new ObjectID(id)}

