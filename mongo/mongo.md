# MongoDB Notebook

[mongoDB官方中文手册](https://docs.mongoing.com/)

## database操作

+ **use myNewDb** 如果数据库不存在，则自动创建

## Collection操作

+ **db.createCollection("user",{})**  [显示创建集合](https://www.mongodb.com/zh-cn/docs/manual/reference/method/db.createCollection/#mongodb-method-db.createCollection)
+ **db.myNewCollection.insertOne({x:1})** 插入Doc,如果Coll不存在，则自动创建

## Doc操作

### insert

+ MongoDB 中的所有写入操作在单个文档级别上都是原子操作
+ 插入单个Doc
  
```javascript
    db.inventory.insertOne(
        { item: "canvas", qty: 100, tags: ["cotton"], size: { h: 28, w: 35.5, uom: "cm" } }
    )
```

+ 插入多个Doc

```javascript
  db.inventory.insertMany([
        { item: "journal", qty: 25, tags: ["blank", "red"], size: { h: 14, w: 21, uom: "cm" } },
        { item: "mat", qty: 85, tags: ["gray"], size: { h: 27.9, w: 35.5, uom: "cm" } },
        { item: "mousepad", qty: 25, tags: ["gel", "blue"], size: { h: 19, w: 22.85, uom: "cm" } }
    ])
```

### query

+ **db.inventory.find( {} )** 查询集合中所有文档
+ **{ \<field1>: \<value1>, ... }** 相等条件
  + **db.inventory.find( { "size.h": 28 } )**  按两级条件查询
+ **{ \<field1>: { \<operator1>: \<value1> }, ... }** 使用查询操作符指定条件
  + **db.inventory.find( { status: { $in: [ "A", "D" ] } } )**
  + [查询选择器](https://www.mongodb.com/zh-cn/docs/manual/reference/operator/query/#std-label-query-selectors)
