**根据黑马程序员的课程资料整理所得，仅用于学习使用，如有侵权，请联系删除**

## 1.MongoDB简单介绍

### 1.1 MongoDB应用场景

1. 应对三高需求
    - High performance - 对数据库高并发读写的需求。
    - Huge Storage - 对海量数据的高效率存储和访问的需求。
    - High Scalability && High Availability- 对数据库的高可扩展性和高可用性的需求。
2. 数据操作方面的共同特点
    - 数据量大
    - 写入操作频繁（读写都很频繁）
    - 价值较低的数据，对事务性要求不高  
        **对于这样的数据，我们更适合使用MongoDB来实现数据的存储。**
3. 使用时机
    - 什么时候选择MongoDB
    - 在架构选型上，除了上述的三个特点外，如果你还犹豫是否要选择它？可以考虑以下的一些问题：
    - 应用不需要事务及复杂 join 支持
    - 新应用，需求会变，数据模型无法确定，想快速迭代开发
    - 应用需要2000-3000以上的读写QPS（更高也可以）
    - 应用需要TB甚至 PB 级别数据存储
    - 应用发展迅速，需要能快速水平扩展
    - 应用要求存储的数据不丢失
    - 应用需要99.999%高可用
    - 应用需要大量的地理位置查询、文本查询
    - 如果上述有1个符合，可以考虑 MongoDB，2个及以上的符合，选择 MongoDB 绝不会后悔。

### 1.2 MongoDB简介

- MongoDB是一个开源、高性能、无模式的文档型数据库，当初的设计就是用于简化开发和方便扩展，是NoSQL数据库产品中的一种。是最像关系型数据库（MySQL）的非关系型数据库。
- 它支持的数据结构非常松散，是一种类似于 JSON 的 格式叫BSON，所以它既可以存储比较复杂的数据类型，又相当的灵活。
- MongoDB中的记录是一个文档，它是一个由字段和值对（field:value）组成的数据结构。MongoDB文档类似于JSON对象，即一个文档认为就是一个对象。字段的数据类型是字符型，它的值除了使用基本的一些类型外，还可以包括其他文档、普通数组和文档数组。

### 1.3 MongDB体系结构

- MySQL和MongoDB对比  
    ![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/5b6f93bd51fd1cf878364ad17156425b.png)  
    ![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/93323cf361356c47fdfdf56d85f82cea.png)

### 1.4 数据模型

1. MongoDB的最小存储单位就是文档(document)对象。文档(document)对象对应于关系型数据库的行。数据在MongoDB中以BSON（Binary-JSON）文档的格式存储在磁盘上。
2. BSON（Binary Serialized Document Format）是一种类json的一种二进制形式的存储格式，简称Binary JSON。BSON和JSON一样，支持内嵌的文档对象和数组对象，但是BSON有JSON没有的一些数据类型，如Date和BinData类型。
3. BSON采用了类似于 C 语言结构体的名称、对表示方法，支持内嵌的文档对象和数组对象，具有轻量性、可遍历性、高效性的三个特点，可以有效描述非结构化数据和结构化数据。这种格式的优点是灵活性高，但它的缺点是空间利用率不是很理想。
4. Bson中，除了基本的JSON类型：string,integer,boolean,double,null,array和object，mongo还使用了特殊的数据类型。这些类型包括date,object id,binary data,regular expression 和code。每一个驱动都以特定语言的方式实现了这些类型，查看你的驱动的文档来获取详细信息。

**BSON数据类型参考列表**：  
![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/7b313437c9249df8e61e7de983ff60d5.png)

### 1.5 MongoDB特点

1. **高性能**：
    - MongoDB提供高性能的数据持久性。特别是,对嵌入式数据模型的支持减少了数据库系统上的I/O活动。
    - 索引支持更快的查询，并且可以包含来自嵌入式文档和数组的键。（文本索引解决搜索的需求、TTL索引解决历史数据自动过期的需求、地理位置索引可用于构建各种 O2O 应用）mmapv1、wiredtiger、mongorocks（rocksdb）、in-memory 等多引擎支持满足各种场景需求。  
        Gridfs解决文件存储的需求。
2. **高可用性**：
    - MongoDB的复制工具称为副本集（replica set），它可提供自动故障转移和数据冗余。
3. **高扩展性**：
    - MongoDB提供了水平可扩展性作为其核心功能的一部分。
    - 分片将数据分布在一组集群的机器上。（海量数据存储，服务能力水平扩展）
    - 从3.4开始，MongoDB支持基于片键创建数据区域。在一个平衡的集群中，MongoDB将一个区域所覆盖的读写只定向到该区域内的那些片。
4. **丰富的查询支持**：
    - MongoDB支持丰富的查询语言，支持读和写操作(CRUD)，比如数据聚合、文本搜索和地理空间查询等。
5. 其他特点：如无模式（动态模式）、灵活的文档模型.

## 2.MongoDB 单机部署

### 2.1 下载

1. MongoDB官网:[https://www.mongodb.com/try/download/community-kubernetes-operator  
    ](https://www.mongodb.com/try/download/community-kubernetes-operator)  
    ![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/e2ad00f98af107204052d3526902186a.png)
    
2. 解压安装启动
    
    - 将压缩包解压到一个目录中。
    - 在解压目录中，手动建立一个目录用于存放数据文件，如 data/db  
        ![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/d748dacfe1908acecb8fa516ecd254c0.png)
3. 启动方式
    
    - 方式1：命令行参数方式启动服务
        - 在 bin 目录中打开命令行提示符，输入如下命令：
        - `mongod --dbpath=..\data\db`
        - 我们在启动信息中可以看到，mongoDB的默认端口是27017，如果我们想改变默认的启动端口，可以通过–port来指定端口。
        - 为了方便我们每次启动，可以将安装目录的bin目录设置到环境变量的path中， bin 目录下是一些常用命令，比如 mongod 启动服务用的，mongo 客户端连接服务用的。
    - 方式2：配置文件方式启动服务
        - 在解压目录中新建 config 文件夹，该文件夹中新建配置文件 mongod.conf ，内如参考如下：

```
storage:
#The directory where the mongod instance stores its data.Default Value is "\data\db" on Windows.
dbPath: D:\02_Server\DBServer\mongodb-win32-x86_64-2008plus-ssl-4.0.1\data
```

详细配置项内容可以参考官方文档：[https://docs.mongodb.com/manual/reference/configuration-options/](https://docs.mongodb.com/manual/reference/configuration-options/)

**【注意】**

- 配置文件中如果使用双引号，比如路径地址，自动会将双引号的内容转义。如果不转义，则会报错：`error-parsing-yaml-config-file-yaml-cpp-error-at-line-3-column-15-unknown-escape-character-d`
    - 解决：  
        a. 对 \ 换成 / 或 \  
        b. 如果路径中没有空格，则无需加引号。
- 配置文件是以`yaml`格式写的,所以在具体配置前要一个`tab`键,否则会报如下错误`Unrecognized option: storage`
- 配置文件中不能以Tab分割字段
    - 解决：
        - 将其转换成空格。
        - 启动方式：`mongod -f ../config/mongod.conf 或 mongod --config ../config/mongod.conf`
        - 更多参数配置：

```
systemLog:
destination: file
#The path of the log file to which mongod or mongos should send all diagnostic logging information
path: "D:/02_Server/DBServer/mongodb-win32-x86_64-2008plus-ssl-4.0.1/log/mongod.log"
logAppend: true
storage:
journal:
enabled: true
#The directory where the mongod instance stores its data.Default Value is "/data/db".
dbPath: "D:/02_Server/DBServer/mongodb-win32-x86_64-2008plus-ssl-4.0.1/data"
net:
#bindIp: 127.0.0.1
port: 27017
setParameter:
enableLocalhostAuthBypass: false
```

### 2.2 Compass图形化界面客户端连接

1. Compass官网：[https://www.mongodb.com/products/compass](https://www.mongodb.com/products/compass)
2. 打开`MongoDBCompassCommunity.exe`应用程序
3. 连接即可,注意,之前的cmd窗口不能关闭  
    ![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/3ff736191fe02bdbdcf2a9b4a7d90346.png)  
    ![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/2bd8edbaf2e6ce0ad94c05432f6da641.png)

### 2.3 Shell命令连接数据库

**因为新版MongoDB无mongo.exe文件,因此我们要去官网下载MongoDB Shell**  
官网:[https://www.mongodb.com/try/download/shell](https://www.mongodb.com/try/download/shell)

- 下载后解压,并将bin目录所在路径天降到环境变量`Path`中  
    ![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/e490f1e87dabd070faf20d9307cd2e56.png)
- 打开cmd,输入mongosh命令,即可连接成功(先启动服务在mongodb的bin目录下打开cmd并输入`mongod -f ../conf/mongod.conf`)  
    ![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/b3a6c310eb341d14f5cec3f3b6d3ca02.png)

## 3.基本常用命令

### 3.1 数据库操作

#### 3.1.1选择和创建数据库

- 选择和创建数据库的语法格式：

```
use 数据库名称
```

- 如果数据库不存在则自动创建，例如，以下语句创建 spitdb 数据库：

```
use articledb
```

- 查看有权限查看的所有的数据库命令

```
show dbs
或
show databases
```

- **注意: 在 MongoDB 中，集合只有在内容插入后才会创建! 就是说，创建集合(数据表)后要再插入一个文档(记录)，集合才会真正创建。**
- 查看当前正在使用的数据库命令

```
db
```

- MongoDB 中默认的数据库为 test，如果你没有选择数据库，集合将存放在 test 数据库中。
- 另外：
    - 数据库名可以是满足以下条件的任意UTF-8字符串。
    - 不能是空字符串（“”)。
    - 不得含有’ '（空格)、.、$、/、\和\0 (空字符)。
    - 应全部小写。
    - 最多64字节。
- 有一些数据库名是保留的，可以直接访问这些有特殊作用的数据库。
    - **admin**： 从权限的角度来看，这是"root"数据库。要是将一个用户添加到这个数据库，这个用户自动继承所有数据库的权限。一些特  
        定的服务器端命令也只能从这个数据库运行，比如列出所有的数据库或者关闭服务器.
    - **local**: 这个数据永远不会被复制，可以用来存储限于本地单台服务器的任意集合
    - **config**: 当Mongo用于分片设置时，config数据库在内部使用，用于保存分片的相关信息。

#### 3.1.2 数据库的删除

- MongoDB 删除数据库的语法格式如下：

```
db.dropDatabase()

```

- 提示：主要用来删除已经持久化的数据库

### 3.2 集合操作

- 集合，类似关系型数据库中的表。
- 可以显示的创建，也可以隐式的创建。

#### 3.2.1 集合的显式创建（了解）

- 基本语法格式：

```
db.createCollection(name)
```

- 参数说明：
    - `name`: 要创建的集合名称
- 集合的命名规范：
    - 集合名不能是空字符串""。
    - 集合名不能含有\0字符（空字符)，这个字符表示集合名的结尾。
    - 集合名不能以"system."开头，这是为系统集合保留的前缀。
    - 用户创建的集合名字不能含有保留字符。有些驱动程序的确支持在集合名里面包含，这是因为某些系统生成的集合中包含该字符。除非你要访问这种系统创建的集合，否则千万不要在名字里出现$。

#### 3.2.2 集合的隐式创建(常用）

- 当向一个集合中插入一个文档的时候，如果集合不存在，则会自动创建集合。

#### 3.2.3 集合的删除

- 集合删除语法格式如下：

```
db.collection.drop()
或
db.集合.drop()
```

- 返回值
    - 如果成功删除选定集合，则 drop() 方法返回 true，否则返回 false。

### 3.3 文档基本CRUD

- 文档（document）的数据结构和 JSON 基本一样。
- 所有存储在集合中的数据都是 BSON 格式。

#### 3.3.1 文档的插入

1. 单个文档插入  
    使用`insert()` 或 `save()` 方法向集合中插入文档，语法如下：

```
db.collection.insert(
<document or array of documents>,
{
writeConcern: <document>,
ordered: <boolean>
}
)
```

- 参数：  
    ![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/cbb4281c34560f8cadcc180367db914c.png)
    
- 提示：
    
    - mongo中的数字，默认情况下是double类型，如果要存整型，必须使用函数NumberInt(整型数字)，否则取出来就有问题了。
    - 插入当前日期使用 new Date()
    - 插入的数据没有指定 _id ，会自动生成主键值
    - 如果某字段没值，可以赋值为null，或不写该字段。
- 注意：
    
    1. 文档中的键/值对是有序的。
    2. 文档中的值不仅可以是在双引号里面的字符串，还可以是其他几种数据类型（甚至可以是整个嵌入的文档)。
    3. MongoDB区分类型和大小写。
    4. MongoDB的文档不能有重复的键。
    5. 文档的键是字符串。除了少数例外情况，键可以使用任意UTF-8字符。  
        文档键命名规范：
        - 键不能含有\0 (空字符)。这个字符用来表示键的结尾。
        - .和$有特别的意义，只有在特定环境下才能使用。
        - 以下划线"_"开头的键是保留的(不是严格要求的)。

2. 批量插入

- 语法：

```
db.collection.insertMany(
[ <document 1> , <document 2>, ... ],
{
writeConcern: <document>,
ordered: <boolean>
}
)

```

- 参数：  
    ![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/f60e37b2250ecd941b47cce8f2cb949e.png)
- 提示：
    - 插入时指定了 _id ，则主键就是该值。
    - 如果某条数据插入失败，将会终止插入，但已经插入成功的数据不会回滚掉。
    - 因为批量插入由于数据较多容易出现失败，因此，可以使用try catch进行异常捕捉处理，测试的时候可以不处理。如（了解）：

```
try {
db.comment.insertMany([
# 插入的数据集合
]);
} catch (e) {
print (e);
}
```

#### 3.3.2 文档的基本查询

- 查询数据的语法格式如下：

```
db.collection.find(<query>, [projection])

```

- 参数：  
    ![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/6f7a873388f17445cbbe604c4fca4ecf.png)
- 查询所有
- 如果我们要查询spit集合的所有文档，我们输入以下命令

```
db.comment.find()
或
db.comment.find({})
```

- 查询指定id

```
db.comment.find({userid:'1003'})
```

- 指定id但只要一个文档

```
db.comment.findOne({userid:'1003'})
```

- 投影查询（Projection Query）：
    - 如果要查询结果返回部分字段，则需要使用投影查询（不显示所有字段，只显示指定的字段）。
        - 如：查询结果只显示 _id、userid、nickname :`>db.comment.find({userid:"1003"},{userid:1,nickname:1})`,其中默认 _id 会显示
        - 如：查询结果只显示 、userid、nickname ，不显示 _id ：`>db.comment.find({userid:"1003"},{userid:1,nickname:1,_id:0})`
        - 再例如：查询所有数据，但只显示 _id、userid、nickname :`>db.comment.find({},{userid:1,nickname:1})`

#### 3.3.3 文档的更新

- 更新文档的语法：

```
db.collection.update(query, update, options)
//或
db.collection.update(
	<query>,
	<update>,
	{
	upsert: <boolean>,
	multi: <boolean>,
	writeConcern: <document>,
	collation: <document>,
	arrayFilters: [ <filterdocument1>, ... ],
	hint: <document|string> // Available starting in MongoDB 4.2
	}
)

```

- 参数：  
    ![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/f2c56030da5d31ae598f94ecc0a76bfc.png)
- 提示:主要关注前四个参数即可。
- 覆盖修改,例如

```
db.comment.update({_id:"1"},{likenum:NumberInt(1001)})
```

- 局部修改

```
db.comment.update({_id:"2"},{$set:{likenum:NumberInt(889)}})
```

- 批量的修改

```
//默认只修改第一条数据
db.comment.update({userid:"1003"},{$set:{nickname:"凯撒2"}})
//修改所有符合条件的数据
db.comment.update({userid:"1003"},{$set:{nickname:"凯撒大帝"}},{multi:true})
```

- 列值增长的修改
    - 如果我们想实现对某列值在原有值的基础上进行增加或减少，可以使用 $inc 运算符来实现。  
        需求：对3号数据的点赞数，每次递增1

```
db.comment.update({_id:"3"},{$inc:{likenum:NumberInt(1)}})
```

#### 3.3.4 删除文档

- 删除文档的语法结构：

```
db.集合名称.remove(条件)
```

- 以下语句可以将数据全部删除，请慎用

```
db.comment.remove({})
```

- 如果删除_id=1的记录，输入以下语句

```
db.comment.remove({_id:"1"}
```

### 3.4 文档的分页查询

#### 3.4.1 统计查询

- 统计查询使用count()方法，语法如下：

```
db.collection.count(query, options)
```

- 参数：  
    ![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/ef05c4939986384c5e12663d8694bbca.png)
    
- 统计所有记录数：
    

```
db.collection.count()
```

- 按条件统计记录数：

```
db.collection.count({userid:"1003"})
```

- 提示：默认情况下 count() 方法返回符合条件的全部记录条数。

#### 3.4.2 分页列表查询

- 可以使用limit()方法来读取指定数量的数据，使用skip()方法来跳过指定数量的数据。
- 基本语法如下所示：

```
>db.COLLECTION_NAME.find().limit(NUMBER).skip(NUMBER)
```

#### 3.4.3 排序查询

- sort() 方法对数据进行排序，sort() 方法可以通过参数指定排序的字段，并使用 1 和 -1 来指定排序的方式，其中 1 为升序排列，而 -1 是用于降序排列。
- 语法如下所示：

```
db.COLLECTION_NAME.find().sort({KEY:1})
或
db.集合名称.find().sort(排序方式)
```

- 提示：skip(), limilt(), sort()三个放在一起执行的时候，执行的顺序是先 sort(), 然后是 skip()，最后是显示的 limit()，和命令编写顺序无关。

### 3.5 文档的更多查询

#### 3.5.1 正则的复杂条件查询

- MongoDB的模糊查询是通过正则表达式的方式实现的。格式为：

```
db.collection.find({field:/正则表达式/})
或
db.集合.find({字段:/正则表达式/})
```

- 提示：正则表达式是js的语法，直接量的写法。  
    例如，我要查询评论内容包含“开水”的所有文档，代码如下：

```
db.collections.find({content:/开水/})
```

#### 3.5.2 比较查询

- `<, <=, >, >=` 这个操作符也是很常用的，格式如下:

```
db.集合名称.find({ "field" : { $gt: value }}) // 大于: field > value
db.集合名称.find({ "field" : { $lt: value }}) // 小于: field < value
db.集合名称.find({ "field" : { $gte: value }}) // 大于等于: field >= value
db.集合名称.find({ "field" : { $lte: value }}) // 小于等于: field <= value
db.集合名称.find({ "field" : { $ne: value }}) // 不等于: field != value
```

#### 3.5.3 包含查询

- 包含使用`$in`操作符。 示例：查询评论的集合中userid字段包含1003或1004的文档

```
db.comment.find({userid:{$in:["1003","1004"]}})
```

- 不包含使用`$nin`操作符。 示例：查询评论集合中userid字段不包含1003和1004的文档

```
db.comment.find({userid:{$nin:["1003","1004"]}})
```

#### 3.5.4 条件连接查询

我们如果需要查询同时满足两个以上条件，需要使用`$and`操作符将条件进行关联。（相 当于SQL的and） 格式为：

```
$and:[ { },{ },{ } ]
```

- 类似的还有`$or`

### 3.6 常用命令小结

```
选择切换数据库：use articledb
插入数据：db.comment.insert({bson数据})
查询所有数据：db.comment.find();
条件查询数据：db.comment.find({条件})
查询符合条件的第一条记录：db.comment.findOne({条件})
查询符合条件的前几条记录：db.comment.find({条件}).limit(条数)
查询符合条件的跳过的记录：db.comment.find({条件}).skip(条数)
修改数据：db.comment.update({条件},{修改后的数据}) 或db.comment.update({条件},{$set:{要修改部分的字段:数据})
修改数据并自增某字段值：db.comment.update({条件},{$inc:{自增的字段:步进值}})
删除数据：db.comment.remove({条件})
统计查询：db.comment.count({条件})
模糊查询：db.comment.find({字段名:/正则表达式/})
条件比较运算：db.comment.find({字段名:{$gt:值}})
包含查询：db.comment.find({字段名:{$in:[值1，值2]}})或db.comment.find({字段名:{$nin:[值1，值2]}})
条件连接查询：db.comment.find({$and:[{条件1},{条件2}]})或db.comment.find({$or:[{条件1},{条件2}]})

```

## 4 索引-Index

### 4.1 概述

- 索引支持在MongoDB中高效地执行查询。如果没有索引，MongoDB必须执行全集合扫描，即扫描集合中的每个文档，以选择与查询语句匹配的文档。这种扫描全集合的查询效率是非常低的，特别在处理大量的数据时，查询可以要花费几十秒甚至几分钟，这对网站的性能是非常致命的。
- 如果查询存在适当的索引，MongoDB可以使用该索引限制必须检查的文档数。
- 索引是特殊的数据结构，它以易于遍历的形式存储集合数据集的一小部分。索引存储特定字段或一组字段的值，按字段值排序。索引项的排序支持有效的相等匹配和基于范围的查询操作。此外，MongoDB还可以使用索引中的排序返回排序结果。
- 官网文档：[https://docs.mongodb.com/manual/indexes/](https://docs.mongodb.com/manual/indexes/)
- 了解：
    - MongoDB索引使用B树数据结构（确切的说是B-Tree，MySQL是B+Tree）

### 4.2 索引的类型

#### 4.2.1 单字段索引

- MongoDB支持在文档的单个字段上创建用户定义的升序/降序索引，称为单字段索引（Single Field Index）。  
    对于单个字段索引和排序操作，索引键的排序顺序（即升序或降序）并不重要，因为MongoDB可以在任何方向上遍历索引。  
    ![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/88e1b38ae683ee321ad5d01f8a1b1861.png)

#### 4.2.2 复合索引

- MongoDB还支持多个字段的用户定义索引，即复合索引（Compound Index）。
- 复合索引中列出的字段顺序具有重要意义。例如，如果复合索引由 { userid: 1, score: -1 } 组成，则索引首先按userid正序排序，然后在每个userid的值内，再在按score倒序排序。  
    ![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/8c0eeecd7d8b754e41e093648bf2f17a.png)

#### 4.2.3 其他索引

- 地理空间索引（Geospatial Index）
    - 为了支持对地理空间坐标数据的有效查询，MongoDB提供了两种特殊的索引：返回结果时使用平面几何的二维索引和返回结果时使用球面几何的二维球面索引。
- 文本索引（Text Indexes）
    - MongoDB提供了一种文本索引类型，支持在集合中搜索字符串内容。这些文本索引不存储特定于语言的停止词（例如“the”、“a”、“or”），而将集合中的词作为词干，只存储根词。
- 哈希索引（Hashed Indexes）
    - 为了支持基于散列的分片，MongoDB提供了散列索引类型，它对字段值的散列进行索引。这些索引在其范围内的值分布更加随机，但只支持相等匹配，不支持基于范围的查询。

### 4.3 索引的管理操作

#### 4.3.1 索引的查看

- 说明：返回一个集合中的所有索引的数组。
- 语法：

```
db.collection.getIndexes()
```

- 提示：该语法命令运行要求是MongoDB 3.0+
- **默认_id索引**：MongoDB在创建集合的过程中，在 _id 字段上创建一个唯一的索引，默认名字为 _id_ ，该索引可防止客户端插入两个具有相同值的文=档，您不能在_id字段上删除此索引。
- **注意**：该索引是唯一索引，因此值不能重复，即 _id 值不能重复的。在分片集群中，通常使用 _id 作为==片键==。

#### 4.3.2 索引的创建

- 说明：在集合上创建索引。
- 语法：

```
db.collection.createIndex(keys, options)
```

- 参数：  
    ![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/86cc9964e2c4aa1cd02fc12b65736671.png)
    
- options（更多选项）列表：  
    ![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/56cb758da955778a5a71f9d66c6901c3.png)
    
- 提示：
    
    - 注意在 3.0.0 版本前创建索引方法为 `db.collection.ensureIndex()` ，之后的版本使用了 `db.collection.createIndex()` 方法，  
        ensureIndex() 还能用，但只是 createIndex() 的别名。
- 单字段索引
    

```
> db.collection.createIndex({userid:1})
```

- 复合索引：对 userid 和 nickname 同时建立复合（Compound）索引：

```
> db.collection.createIndex({userid:1,nickname:-1})
```

- 查看索引：

```
> db.collection.getIndexes()
```

- compass中：  
    ![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/7e7c2c2ab9b30d87b91f168f0658449f.png)

#### 4.3.3 索引的移除

- 说明：可以移除指定的索引，或移除所有索引

1. 指定索引的移除

- 语法：

```
db.collection.dropIndex(index)
```

- 参数：  
    ![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/9c609f35172a6dbf2666a0bf73f11b0d.png)

2. 所有索引的移除

- 语法：

```
db.collection.dropIndexes()
```

### 4.4 索引的使用

#### 4.4.1 执行计划

- 分析查询性能（Analyze Query Performance）通常使用执行计划（解释计划、Explain Plan）来查看查询的情况，如查询耗费的时间、是否基于索引查询等。
- 那么，通常，我们想知道，建立的索引是否有效，效果如何，都需要通过执行计划查看。
- 语法：

```
db.collection.find(query,options).explain(options)
```

- 例如:查看根据userid查询数据的情况：

```
> db.comment.find({userid:"1003"}).explain()
```

- 在具体信息中关键点看： `"stage" : "COLLSCAN"`, 表示全集合扫描,或者`"stage" : "IXSCAN"` ,基于索引的扫描
- compass查看：  
    ![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/b73dd132ef35cb8bfd5570d5595b35e4.png)  
    ![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/83055d87b583f31780546a260d3d1c03.png)

#### 4.4.2 涵盖的查询

- Covered Queries
    
- 当查询条件和查询的投影仅包含索引字段时，MongoDB直接从索引返回结果，而不扫描任何文档或将文档带入内存。 这些覆盖的查询可以非常有效。  
    ![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/0311b2cbb5d1ccb8356342fb845db3c4.png)
    
- 更多：[https://docs.mongodb.com/manual/core/query-optimization/#read-operations-covered-query](https://docs.mongodb.com/manual/core/query-optimization/#read-operations-covered-query)
    
- Compass中查看:  
    ![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/2fe1515b70e1a7de4e24d29b00e1c05f.png)
    

## 5 IDEA配置MongoDB

### 5.1 技术选型

#### 5.1.1 mongodb-driver（了解）

- mongodb-driver是mongo官方推出的java连接mongoDB的驱动包，相当于JDBC驱动。
- 官方驱动说明和下载：[http://mongodb.github.io/mongo-java-driver/](http://mongodb.github.io/mongo-java-driver/)
- 官方驱动示例文档：[http://mongodb.github.io/mongo-java-driver/3.8/driver/getting-started/quick-start/](http://mongodb.github.io/mongo-java-driver/3.8/driver/getting-started/quick-start/)

#### 5.1.2 SpringDataMongoDB

- SpringData家族成员之一，用于操作MongoDB的持久层框架，封装了底层的mongodb-driver。
- 官网主页： [https://projects.spring.io/spring-data-mongodb/](https://projects.spring.io/spring-data-mongodb/)

### 5.2 微服务模块搭建

1. 搭建项目工程article，pom.xml引入依赖：

```xml
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0"
xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
<modelVersion>4.0.0</modelVersion>
<parent>
<groupId>org.springframework.boot</groupId>
<artifactId>spring-boot-starter-parent</artifactId>
<version>2.1.6.RELEASE</version>
<relativePath/> <!-- lookup parent from repository -->
</parent>
<groupId>cn.itcast</groupId>
<artifactId>article</artifactId>
<version>1.0-SNAPSHOT</version>
<dependencies>
<dependency>
<groupId>org.springframework.boot</groupId>
<artifactId>spring-boot-starter-test</artifactId>
<scope>test</scope>
</dependency>
<dependency>
<groupId>org.springframework.boot</groupId>
<artifactId>spring-boot-starter-data-mongodb</artifactId>
</dependency>
</dependencies>
</project>
```

2. 创建application.yml

```yml
spring:
#数据源配置
data:
mongodb:
# 主机地址
host: 192.168.40.141
# 数据库
database: articledb
# 默认端口是27017
port: 27017
#也可以使用uri连接
#uri: mongodb://192.168.40.134:27017/articledb
```

3. 创建启动类(就是springboot的启动类)

- jiuyou.article.ArticleApplication

```java
package cn.itcast.article;
import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;
@SpringBootApplication
public class ArticleApplication {
public static void main(String[] args) {
SpringApplication.run(ArticleApplication.class, args);
}
}
```

4. 启动项目，看是否能正常启动，控制台没有错误。

### 5.3 实体类的编写

- 创建实体类 创建包jiuyou.article，包下建包po用于存放实体类，创建实体类
- jiuyou.article.po.Comment

```java
package cn.itcast.article.po;
import org.springframework.data.annotation.Id;
import org.springframework.data.mongodb.core.index.Indexed;
import org.springframework.data.mongodb.core.mapping.Document;
import org.springframework.data.mongodb.core.mapping.Field;
import java.io.Serializable;
import java.time.LocalDateTime;
import java.util.Date;
/**
* 文章评论实体类
*/
//把一个java类声明为mongodb的文档，可以通过collection参数指定这个类对应的文档。
//@Document(collection="mongodb 对应 collection 名")
// 若未加 @Document ，该 bean save 到 mongo 的 comment collection
// 若添加 @Document ，则 save 到 comment collection
@Document(collection="comment")//可以省略，如果省略，则默认使用类名小写映射集合
//复合索引
// @CompoundIndex( def = "{'userid': 1, 'nickname': -1}")
public class Comment implements Serializable {
//主键标识，该属性的值会自动对应mongodb的主键字段"_id"，如果该属性名就叫“id”,则该注解可以省略，否则必须写
@Id
private String id;//主键
//该属性对应mongodb的字段的名字，如果一致，则无需该注解
@Field("content")
private String content;//吐槽内容
private Date publishtime;//发布日期
//添加了一个单字段的索引
@Indexed
private String userid;//发布人ID
private String nickname;//昵称
private LocalDateTime createdatetime;//评论的日期时间
private Integer likenum;//点赞数
private Integer replynum;//回复数
private String state;//状态
private String parentid;//上级ID
private String articleid;
//getter and setter.....
public String getId() {
return id;
}
public void setId(String id) {
this.id = id;
}
public String getContent() {
return content;
}
public void setContent(String content) {
this.content = content;
}
public Date getPublishtime() {
return publishtime;
}
public void setPublishtime(Date publishtime) {
this.publishtime = publishtime;
}
public String getUserid() {
return userid;
}
public void setUserid(String userid) {
this.userid = userid;
}
public String getNickname() {
return nickname;
}
public void setNickname(String nickname) {
this.nickname = nickname;
}
public LocalDateTime getCreatedatetime() {
return createdatetime;
}
public void setCreatedatetime(LocalDateTime createdatetime) {
this.createdatetime = createdatetime;
}
public Integer getLikenum() {
return likenum;
}
public void setLikenum(Integer likenum) {
this.likenum = likenum;
}
public Integer getReplynum() {
return replynum;
}
public void setReplynum(Integer replynum) {
this.replynum = replynum;
}
public String getState() {
return state;
}
public void setState(String state) {
this.state = state;
}
public String getParentid() {
return parentid;
}
public void setParentid(String parentid) {
this.parentid = parentid;
}
public String getArticleid() {
return articleid;
}
public void setArticleid(String articleid) {
this.articleid = articleid;
}
@Override
public String toString() {
return "Comment{" +
"id='" + id + '\'' +
", content='" + content + '\'' +
", publishtime=" + publishtime +
", userid='" + userid + '\'' +
", nickname='" + nickname + '\'' +
", createdatetime=" + createdatetime +
", likenum=" + likenum +
", replynum=" + replynum +
", state='" + state + '\'' +
", parentid='" + parentid + '\'' +
", articleid='" + articleid + '\'' +
'}';
}
}
```

- 说明：索引可以大大提升查询效率，一般在查询字段上添加索引，索引的添加可以通过Mongo的命令来添加，也可以在Java的实体类中通过注解添加。

1. 单字段索引注解@Indexed  
    org.springframework.data.mongodb.core.index.Indexed.class  
    声明该字段需要索引，建索引可以大大的提高查询效率。

- Mongo命令参考：

```
db.comment.createIndex({"userid":1})
```

2. 复合索引注解@CompoundIndex  
    org.springframework.data.mongodb.core.index.CompoundIndex.class  
    复合索引的声明，建复合索引可以有效地提高多字段的查询效率。

- Mongo命令参考：

```
db.comment.createIndex({"userid":1,"nickname":-1})
```

### 5.4 基本增删改查

1. 创建数据访问接口 jiuyou.article包下创建dao包，包下创建接口

- jiuyou.article.dao.CommentRepository

```java
package cn.itcast.article.dao;
import cn.itcast.article.po.Comment;
import org.springframework.data.domain.Page;
import org.springframework.data.domain.Pageable;
import org.springframework.data.mongodb.repository.MongoRepository;
//评论的持久层接口
public interface CommentRepository extends MongoRepository<Comment,String> {
}
```

2. 创建业务逻辑类 jiuyou.article包下创建service包，包下创建类

- jiuyou.article.service.CommentService

```java
package cn.itcast.article.service;
import cn.itcast.article.dao.CommentRepository;
import cn.itcast.article.po.Comment;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.stereotype.Service;
import java.util.List;
//评论的业务层
@Service
public class CommentService {
//注入dao
@Autowired
private CommentRepository commentRepository;
/**
* 保存一个评论
* @param comment
*/
public void saveComment(Comment comment){
//如果需要自定义主键，可以在这里指定主键；如果不指定主键，MongoDB会自动生成主键
//设置一些默认初始值。。。
//调用dao
commentRepository.save(comment);
}
/**
* 更新评论
* @param comment
*/
public void updateComment(Comment comment){
//调用dao
commentRepository.save(comment);
}
/**
* 根据id删除评论
* @param id
*/
public void deleteCommentById(String id){
//调用dao
commentRepository.deleteById(id);
}
/**
* 查询所有评论
* @return
*/
public List<Comment> findCommentList(){
//调用dao
return commentRepository.findAll();
}
/**
* 根据id查询评论
* @param id
* @return
*/
public Comment findCommentById(String id){
//调用dao
return commentRepository.findById(id).get();
}
}
```

3. 新建Junit测试类，测试保存和查询所有：

- jiuyou.article.service.CommentServiceTest

```java
package cn.itcast.article.service;
import cn.itcast.article.ArticleApplication;
import cn.itcast.article.po.Comment;
import org.junit.Test;
import org.junit.runner.RunWith;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.boot.test.context.SpringBootTest;
import org.springframework.data.domain.Page;
import org.springframework.test.context.junit4.SpringRunner;
import java.time.LocalDateTime;
import java.util.List;
//测试评论的业务层
//SpringBoot的Junit集成测试
@RunWith(SpringRunner.class)
//SpringBoot的测试环境初始化，参数：启动类
@SpringBootTest(classes = ArticleApplication.class)
public class CommentServiceTest {
//注入Service
@Autowired
private CommentService commentService;
/**
* 保存一个评论
*/
@Test
public void testSaveComment(){
Comment comment=new Comment();
comment.setArticleid("100000");
comment.setContent("测试添加的数据");
comment.setCreatedatetime(LocalDateTime.now());
comment.setUserid("1003");
comment.setNickname("凯撒大帝");
comment.setState("1");
comment.setLikenum(0);
comment.setReplynum(0);
commentService.saveComment(comment);
}
/**
* 查询所有数据
*/
@Test
public void testFindAll(){
List<Comment> list = commentService.findCommentList();
System.out.println(list);
}
/**
* 测试根据id查询
*/
@Test
public void testFindCommentById(){
Comment comment = commentService.findCommentById("5d6a27b81b8d374798cf0b41");
System.out.println(comment);
}
}
```

### 5.5 根据上级ID查询文章评论的分页列表

1. CommentRepository新增方法定义

```java
//根据父id，查询子评论的分页列表
Page<Comment> findByParentid(String parentid, Pageable pageable);
```

2. CommentService新增方法

```java
/**
* 根据父id查询分页列表
* @param parentid
* @param page
* @param size
* @return
*/
public Page<Comment> findCommentListPageByParentid(String parentid,int page ,int size){
return commentRepository.findByParentid(parentid, PageRequest.of(page-1,size));
}
```

3. junit测试用例：

- jiuyou.article.service.CommentServiceTest

```java
/**
* 测试根据父id查询子评论的分页列表
*/
@Test
public void testFindCommentListPageByParentid(){
Page<Comment> pageResponse = commentService.findCommentListPageByParentid("3", 1, 2);
System.out.println("----总记录数："+pageResponse.getTotalElements());
System.out.println("----当前页数据："+pageResponse.getContent());
}
```

4. 测试可以用Compass快速插入一条测试数据,这里不做演示了

### 5.6 MongoTemplate实现评论点赞

- 我们看一下以下点赞的临时示例代码： CommentService 新增updateThumbup方法

```java
/**
* 点赞-效率低
* @param id
*/
public void updateCommentThumbupToIncrementingOld(String id){
Comment comment = CommentRepository.findById(id).get();
comment.setLikenum(comment.getLikenum()+1);
CommentRepository.save(comment);
}
```

- 以上方法虽然实现起来比较简单，但是执行效率并不高，因为我只需要将点赞数加1就可以了，没必要查询出所有字段修改后再更新所有字段。(蝴蝶效应)我们可以使用`MongoTemplate`类来实现对某列的操作。

1. 修改CommentService

```java
//注入MongoTemplate
@Autowired
private MongoTemplate mongoTemplate;
/**
* 点赞数+1
* @param id
*/
public void updateCommentLikenum(String id){
//查询对象
Query query=Query.query(Criteria.where("_id").is(id));
//更新对象
Update update=new Update();
//局部更新，相当于$set
// update.set(key,value)
//递增$inc
// update.inc("likenum",1);
update.inc("likenum");
//参数1：查询对象
//参数2：更新对象
//参数3：集合的名字或实体类的类型Comment.class
mongoTemplate.updateFirst(query,update,"comment");
}
```

2. 测试用例：

- jiuyou.article.service.CommentServiceTest

```java
/**
* 点赞数+1
*/
@Test
public void testUpdateCommentLikenum(){
//对3号文档的点赞数+1
commentService.updateCommentLikenum("3");
}
```

- 执行测试用例后，发现点赞数+1了;

**作者水平有限,第六节以后较为粗略QAQ,可以去看官方文档,那儿更详细,官方文档:[https://www.mongodb.com/docs/manual/introduction/](https://www.mongodb.com/docs/manual/introduction/)**

## 6. 副本集-Replica Sets

### 6.1 简介

- MongoDB中的副本集（Replica Set）是一组维护相同数据集的mongod服务。 副本集可提供冗余和高  
    可用性，是所有生产部署的基础。
- 也可以说，副本集类似于有自动故障恢复功能的主从集群。通俗的讲就是用多台机器进行同一数据的异  
    步同步，从而使多台机器拥有同一数据的多个副本，并且当主库当掉时在不需要用户干预的情况下自动  
    切换其他备份服务器做主库。而且还可以利用副本服务器做只读服务器，实现读写分离，提高负载。
    1. 冗余和数据可用性
        - 复制提供冗余并提高数据可用性。 通过在不同数据库服务器上提供多个数据副本，复制可提供一定级别的容错功能，以防止丢失单个数据库服务器。
        - 在某些情况下，复制可以提供增加的读取性能，因为客户端可以将读取操作发送到不同的服务上， 在不同数据中心维护数据副本可以增加分布式应用程序的数据位置和可用性。 您还可以为专用目的维护其他副本，例如灾难恢复，报告或备份。
    2. MongoDB中的复制
        - 副本集是一组维护相同数据集的mongod实例。 副本集包含多个数据承载节点和可选的一个仲裁节点。在承载数据的节点中，一个且仅一个成员被视为主节点，而其他节点被视为次要（从）节点。
            
        - 主节点接收所有写操作。 副本集只能有一个主要能够确认具有{w：“most”}写入关注的写入; 虽然在某些情况下，另一个mongod实例可能暂时认为自己也是主要的。主要记录其操作日志中的数据集的所有更改，即oplog。  
            ![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/70930f1d30f1fd90908395ffec0d6588.png)
            
        - 辅助(副本)节点复制主节点的oplog并将操作应用于其数据集，以使辅助节点的数据集反映主节点的数据  
            集。 如果主要人员不在，则符合条件的中学将举行选举以选出新的主要人员。
            
    3. 主从复制和副本集区别
        - 主从集群和副本集最大的区别就是副本集没有固定的“主节点”；整个集群会选出一个“主节点”，当其挂掉后，又在剩下的从节点中选中其他节点为“主节点”，副本集总有一个活跃点(主、primary)和一个或多个备份节点(从、secondary)。

### 6.2 副本集的三个角色

- 副本集有两种类型三种角色
- 两种类型：
    - 主节点（Primary）类型：数据操作的主要连接点，可读写。
    - 次要（辅助、从）节点（Secondaries）类型：数据冗余备份节点，可以读或选举。
- 三种角色：
    - 主要成员（Primary）：主要接收所有写操作。就是主节点。
        
    - 副本成员（Replicate）：从主节点通过复制操作以维护相同的数据集，即备份数据，不可写操作，但可  
        以读操作（但需要配置）。是默认的一种从节点类型。
        
    - 仲裁者（Arbiter）：不保留任何数据的副本，只具有投票选举作用。当然也可以将仲裁服务器维护为副本集的一部分，即副本成员同时也可以是仲裁者。也是一种从节点类型。  
        ![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/ecce7595ac5e09f29768578bdc921a18.png)
        
    - 关于仲裁者的额外说明：
        
        - 您可以将额外的mongod实例添加到副本集作为仲裁者。 仲裁者不维护数据集。 仲裁者的目的是通过响应其他副本集成员的心跳和选举请求来维护副本集中的仲裁。 因为它们不存储数据集，所以仲裁器可以是提供副本集仲裁功能的好方法，其资源成本比具有数据集的全功能副本集成员更便宜。
        - 如果您的副本集具有偶数个成员，请添加仲裁者以获得主要选举中的“大多数”投票。 仲裁者不需要专用  
            硬件。
        - 仲裁者将永远是仲裁者，而主要人员可能会退出并成为次要人员，而次要人员可能成为选举期间的主要  
            人员。
        - 如果你的副本+主节点的个数是偶数，建议加一个仲裁者，形成奇数，容易满足大多数的投票。
        - 如果你的副本+主节点的个数是奇数，可以不加仲裁者。

### 6.3 副本集架构目标

- 一主一副本一仲裁

![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/19a3517cc0b85c5cea13f622e7088432.png)

### 6.4 副本集的创建

#### 6.4.1 第一步：创建主节点

1. 建立存放数据和日志的目录

```
#-----------myrs
#主节点
mkdir -p /mongodb/replica_sets/myrs_27017/log \ &
mkdir -p /mongodb/replica_sets/myrs_27017/data/db
```

2. 新建或修改配置文件：

```
vim /mongodb/replica_sets/myrs_27017/mongod.conf
```

3. myrs_27017：

```
systemLog:
#MongoDB发送所有日志输出的目标指定为文件
destination: file
#mongod或mongos应向其发送所有诊断日志记录信息的日志文件的路径
path: "/mongodb/replica_sets/myrs_27017/log/mongod.log"
#当mongos或mongod实例重新启动时，mongos或mongod会将新条目附加到现有日志文件的末尾。
logAppend: true
storage:
#mongod实例存储其数据的目录。storage.dbPath设置仅适用于mongod。
dbPath: "/mongodb/replica_sets/myrs_27017/data/db"
journal:
#启用或禁用持久性日志以确保数据文件保持有效和可恢复。
enabled: true
processManagement:
#启用在后台运行mongos或mongod进程的守护进程模式。
fork: true
#指定用于保存mongos或mongod进程的进程ID的文件位置，其中mongos或mongod将写入其PID
pidFilePath: "/mongodb/replica_sets/myrs_27017/log/mongod.pid"
net:
#服务实例绑定所有IP，有副作用，副本集初始化的时候，节点名字会自动设置为本地域名，而不是ip
#bindIpAll: true
#服务实例绑定的IP
bindIp: localhost,192.168.0.2
#bindIp
#绑定的端口
port: 27017
replication:
#副本集的名称
replSetName: myrs
```

4. 启动节点服务：

```
[root@bobohost replica_sets]# /usr/local/mongodb/bin/mongod -f
/mongodb/replica_sets/myrs_27017/mongod.conf
about to fork child process, waiting until server is ready for connections.
forked process: 54257
child process started successfully, parent exiting
```

#### 6.4.2 第二步：创建副本节点

1. 建立存放数据和日志的目录

```
#-----------myrs
#副本节点
mkdir -p /mongodb/replica_sets/myrs_27018/log \ &
mkdir -p /mongodb/replica_sets/myrs_27018/data/db
```

2. 新建或修改配置文件：

```
vim /mongodb/replica_sets/myrs_27018/mongod.conf
```

3. myrs_27018：

```
systemLog:
#MongoDB发送所有日志输出的目标指定为文件
destination: file
#mongod或mongos应向其发送所有诊断日志记录信息的日志文件的路径
path: "/mongodb/replica_sets/myrs_27018/log/mongod.log"
#当mongos或mongod实例重新启动时，mongos或mongod会将新条目附加到现有日志文件的末尾。
logAppend: true
storage:
#mongod实例存储其数据的目录。storage.dbPath设置仅适用于mongod。
dbPath: "/mongodb/replica_sets/myrs_27018/data/db"
journal:
#启用或禁用持久性日志以确保数据文件保持有效和可恢复。
enabled: true
processManagement:
#启用在后台运行mongos或mongod进程的守护进程模式。
fork: true
#指定用于保存mongos或mongod进程的进程ID的文件位置，其中mongos或mongod将写入其PID
pidFilePath: "/mongodb/replica_sets/myrs_27018/log/mongod.pid"
net:
#服务实例绑定所有IP，有副作用，副本集初始化的时候，节点名字会自动设置为本地域名，而不是ip
#bindIpAll: true
#服务实例绑定的IP
bindIp: localhost,192.168.0.2
#bindIp
#绑定的端口
port: 27018
replication:
#副本集的名称
replSetName: myrs
```

4. 启动节点服务：

```
[root@bobohost replica_sets]# /usr/local/mongodb/bin/mongod -f
/mongodb/replica_sets/myrs_27018/mongod.conf
about to fork child process, waiting until server is ready for connections.
forked process: 54361
child process started successfully, parent exiting
```

#### 6.4.3 第三步：创建仲裁节点

1. 建立存放数据和日志的目录

```
#-----------myrs
#仲裁节点
mkdir -p /mongodb/replica_sets/myrs_27019/log \ &
mkdir -p /mongodb/replica_sets/myrs_27019/data/db
```

2. 仲裁节点：  
    新建或修改配置文件：

```
vim /mongodb/replica_sets/myrs_27019/mongod.conf
```

3. myrs_27019：

```
systemLog:
#MongoDB发送所有日志输出的目标指定为文件
destination: file
#mongod或mongos应向其发送所有诊断日志记录信息的日志文件的路径
path: "/mongodb/replica_sets/myrs_27019/log/mongod.log"
#当mongos或mongod实例重新启动时，mongos或mongod会将新条目附加到现有日志文件的末尾。
logAppend: true
storage:
#mongod实例存储其数据的目录。storage.dbPath设置仅适用于mongod。
dbPath: "/mongodb/replica_sets/myrs_27019/data/db"
journal:
#启用或禁用持久性日志以确保数据文件保持有效和可恢复。
enabled: true
processManagement:
#启用在后台运行mongos或mongod进程的守护进程模式。
fork: true
#指定用于保存mongos或mongod进程的进程ID的文件位置，其中mongos或mongod将写入其PID
pidFilePath: "/mongodb/replica_sets/myrs_27019/log/mongod.pid"
net:
#服务实例绑定所有IP，有副作用，副本集初始化的时候，节点名字会自动设置为本地域名，而不是ip
#bindIpAll: true
#服务实例绑定的IP
bindIp: localhost,192.168.0.2
#bindIp
#绑定的端口
port: 27019
replication:
#副本集的名称
replSetName: myrs
```

启动节点服务：

```
[root@bobohost replica_sets]# /usr/local/mongodb/bin/mongod -f
/mongodb/replica_sets/myrs_27019/mongod.conf
about to fork child process, waiting until server is ready for connections.
forked process: 54410
child process started successfully, parent exiting
```

#### 6.4.4 第四步：初始化配置副本集和主节点

- 使用客户端命令连接任意一个节点，但这里尽量要连接主节点(27017节点)：

```
/usr/local/mongodb/bin/mongo --host=180.76.159.126 --port=27017
```

- 结果，连接上之后，很多命令无法使用，，比如 show dbs 等，必须初始化副本集才行  
    准备初始化新的副本集：
- 语法：

```
rs.initiate(configuration
```

- 选项：
    - configuration: [https://www.mongodb.com/docs/manual/reference/replica-configuration/#replica-set-configuration-document](https://www.mongodb.com/docs/manual/reference/replica-configuration/#replica-set-configuration-document)  
        ![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/e45cbb4b4a6f4a9861bda147f67eee9b.png)
- 初始化完成后
    - “ok”的值为1，说明创建成功。
    - 命令行提示符发生变化，变成了一个从节点角色，此时默认不能读写。稍等片刻，回车，变成主节  
        点。

#### 6.4.5 第五步：查看副本集的配置内容

- 说明：返回包含当前副本集配置的文档。
- 语法：`rs.conf(configuration)`
- 提示：
    - `rs.config()`是该方法的别名。
    - configuration：可选，如果没有配置，则使用默认主节点配置。
- 说明：
    1. “_id” : “” ：副本集的配置数据存储的主键值，默认就是副本集的名字
    2. “members” ：副本集成员数组，该成员不是仲裁节点： “arbiterOnly” : false ，优先级（权重值）： “priority” : 1
    3. “settings” ：副本集的参数配置。

**提示：副本集配置的查看命令，本质是查询的是 system.replset 的表中的数据：**

```
myrs:PRIMARY> use local
switched to db local
myrs:PRIMARY> show collections
oplog.rs
replset.election
replset.minvalid
replset.oplogTruncateAfterPoint
startup_log
system.replset
system.rollback.id
myrs:PRIMARY> db.system.replset.find()
```

#### 6.4.6 第六步：查看副本集状态

- 检查副本集状态。
- 说明：
- 返回包含状态信息的文档。此输出使用从副本集的其他成员发送的心跳包中获得的数据反映副本集的当前状态。
- 语法：`rs.status()`
- 说明：在展示的信息中
    1. “set” : “” ：副本集的名字
    2. “myState” : 1：说明状态正常
    3. “members” ：副本集成员数组
    4. “health” : 1 , 该节点是健康的：

#### 6.4.7 第七步:添加副本从节点

- 在主节点添加从节点，将其他成员加入到副本集
- 语法：

```
rs.add(host, arbiterOnly)
```

- 选项：  
    ![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/f5cdb24180ee34b0a3a276ab8d2cfe74.png)
    
- 主机成员的配置文档：
    

```
{
_id: <int>,
host: <string>, // required
arbiterOnly: <boolean>,
buildIndexes: <boolean>,
hidden: <boolean>,
priority: <number>,
tags: <document>,
slaveDelay: <int>,
votes: <number>
}

```

#### 6.4.8 第八步：添加仲裁从节点

- 添加一个仲裁节点到副本集
- 语法：

```
rs.addArb(host)
```

### 6.5 副本集的数据读写操作

- 登录节点命令:`[root@bobohost ~]# /usr/local/mongodb/bin/mongo --host 180.76.159.126 --port 27018`
- 如果直接读取,发现从节点不能读取集合的数据。当前从节点只是一个备份，不是奴隶节点，无法读取数据，写当然更不  
    行。
- 因为默认情况下，从节点是没有读写权限的，可以增加读的权限，但需要进行设置。
- 设置读操作权限：
- 说明：
    - 设置为奴隶节点，允许在从成员上运行读的操作
- 语法：

```
rs.slaveOk()
#或
rs.slaveOk(true)
```

- 提示：  
    该命令是 `db.getMongo().setSlaveOk()` 的简化命令。
- 插入成功后,发现可以读,但是不可以写
- 仲裁者节点，不存放任何业务数据的，登录查看发现，它只存放副本集配置等数据。

### 6.6主节点的选举原则

- MongoDB在副本集中，会自动进行主节点的选举，主节点选举的触发条件：
    
    1. 主节点故障
    2. 主节点网络不可达（默认心跳信息为10秒）
    3. 人工干预（rs.stepDown(600)）
- 一旦触发选举，就要根据一定规则来选主节点。
    
- 选举规则是根据票数来决定谁获胜：
    
    - 票数最高，且获得了“大多数”成员的投票支持的节点获胜。
    - “大多数”的定义为：假设复制集内投票成员数量为N，则大多数为 N/2 + 1。例如：3个投票成员，则大多数的值是2。当复制集内存活成员数量不足大多数时，整个复制集将无法选举出Primary，复制集将无法提供写服务，处于只读状态。
    - 若票数相同，且都获得了“大多数”成员的投票支持的，数据新的节点获胜。数据的新旧是通过操作日志oplog来对比的。
- 在获得票数相同的时候，优先级（priority）参数影响重大。
    
    - 可以通过设置优先级（priority）来设置额外票数。优先级即权重，取值为0-1000，相当于可额外增加  
        0-1000的票数，优先级的值越大，就越可能获得多数成员的投票（votes）数。指定较高的值可使成员  
        更有资格成为主要成员，更低的值可使成员更不符合条件。默认情况下，优先级的值是1
- 【了解】修改优先级
    
    1. 先将配置导入cfg变量`myrs:SECONDARY> cfg=rs.conf()`
    2. 然后修改值（ID号默认从0开始）：`myrs:SECONDARY> cfg.members[1].priority=2` ）
    3. 重新加载配置:`myrs:SECONDARY> rs.reconfig(cfg)`

### 6.7 Compass连接副本集

- 如果使用云服务器需要修改配置中的主节点ip

```
var config = rs.config();
config.members[0].host="180.76.159.126:27017";rs.reconfig(config)
```

- compass连接：

```
Connect to Host
```

![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/56be0f27ff7d4d779b843ad8d11bc82c.png)  
![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/1171db92557ea501ba3726ede0f3dd60.png)

### 6.8 SpringDataMongoDB连接副本集

- 副本集语法：

```
mongodb://host1,host2,host3/articledb?
connect=replicaSet&slaveOk=true&replicaSet=副本集名字
```

- 其中：
    
    - slaveOk=true：开启副本节点读的功能，可实现读写分离。
    - connect=replicaSet：自动到副本集中选择读写的主机。如果slaveOK是打开的，则实现了读写分  
        离
- **注意**：
    
    - 主机必须是副本集中所有的主机，包括主节点、副本节点、仲裁节点。
    - SpringDataMongoDB自动实现了读写分离：
    - 写操作时，只打开主节点连接
    - 读操作是，同时打开主节点和从节点连接，但使用从节点获取数据
- 完整的[连接字符串](https://so.csdn.net/so/search?q=%E8%BF%9E%E6%8E%A5%E5%AD%97%E7%AC%A6%E4%B8%B2&spm=1001.2101.3001.7020)的参考（了解）：
    
- MongoDB客户端连接语法：
    

```
mongodb://[username:password@]host1[:port1][,host2[:port2],...[,hostN[:portN]]]
[/[database][?options]]

```

- mongodb:// 这是固定的格式，必须要指定。
- username:password@ 可选项，如果设置，在连接数据库服务器之后，驱动都会尝试登陆这个  
    数据库
- host1 必须的指定至少一个host, host1 是这个URI唯一要填写的。它指定了要连接服务器的地址。如果要连接复制集，请指定多个主机地址。
- portX 可选的指定端口，如果不填，默认为27017
- /database 如果指定username:password@，连接并验证登陆指定数据库。若不指定，默认打开test 数据库。
- ?options 是连接选项。如果不使用/database，则前面需要加上/。所有连接选项都是键值对name=value，键值对之间通过&或;（分号）隔开
- 标准的连接格式包含了多个选项(options)，如下所示：  
    ![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/573216533ff5ea58efa460bc8afd456d.png)

## 7. 分片集群-Sharded Cluster

### 7.1 分片概念

- 分片（sharding）是一种跨多台机器分布数据的方法， MongoDB使用分片来支持具有非常大的数据集和高吞吐量操作的部署。
- 换句话说：分片(sharding)是指将数据拆分，将其分散存在不同的机器上的过程。有时也用分区(partitioning)来表示这个概念。将数据分散到不同的机器上，不需要功能强大的大型计算机就可以储存更多的数据，处理更多的负载。
- 具有大型数据集或高吞吐量应用程序的数据库系统可以会挑战单个服务器的容量。例如，高查询率会耗尽服务器的CPU容量。工作集大小大于系统的RAM会强调磁盘驱动器的I / O容量。
- 有两种解决系统增长的方法：垂直扩展和水平扩展。
- 垂直扩展意味着增加单个服务器的容量，例如使用更强大的CPU，添加更多RAM或增加存储空间量。可用技术的局限性可能会限制单个机器对于给定工作负载而言足够强大。此外，基于云的提供商基于可用的硬件配置具有硬性上限。结果，垂直缩放有实际的最大值。
- 水平扩展意味着划分系统数据集并加载多个服务器，添加其他服务器以根据需要增加容量。虽然单个机器的总体速度或容量可能不高，但每台机器处理整个工作负载的子集，可能提供比单个高速大容量服务器更高的效率。扩展部署容量只需要根据需要添加额外的服务器，这可能比单个机器的高端硬件的总体成本更低。权衡是基础架构和部署维护的复杂性增加。
- MongoDB支持通过分片进行水平扩展。

### 7.2 分片集群包含的组件

- MongoDB分片群集包含以下组件：
    
    - 分片（存储）：每个分片包含分片数据的子集。 每个分片都可以部署为副本集。
    - mongos（路由）：mongos充当查询路由器，在客户端应用程序和分片集群之间提供接口。
    - config servers（“调度”的配置）：配置服务器存储群集的元数据和配置设置。 从MongoDB 3.4开始，必须将配置服务器部署为副本集（CSRS）。
- 下图描述了分片集群中组件的交互：  
    ![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/70b40f5d7d389a1b960df65cf2004998.png)
    
- MongoDB在集合级别对数据进行分片，将集合数据分布在集群中的分片上。
    
- 27018 if mongod is a shard member；
    
- 27019 if mongod is a config server member
    

### 7.3 分片集群架构目标

- 两个分片节点副本集（3+3）+一个配置节点副本集（3）+两个路由节点（2），共11个服务节点。  
    ![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/d3fdb3d81fbe0710fe0bfae92ee60907.png)

### 7.4 分片（存储）节点副本集的创建

#### 7.4.1 创建两套副本集

- 创建副本集过程与6.4节相似,这里只讲需要做出改变的位置
- 准备存放数据的目录时还要准备一个存放日志的目录

```
#-----------myshardrs01
mkdir -p /mongodb/sharded_cluster/myshardrs01_27018/log \ &
mkdir -p /mongodb/sharded_cluster/myshardrs01_27018/data/db \ &
mkdir -p /mongodb/sharded_cluster/myshardrs01_27118/log \ &
mkdir -p /mongodb/sharded_cluster/myshardrs01_27118/data/db \ &
mkdir -p /mongodb/sharded_cluster/myshardrs01_27218/log \ &
mkdir -p /mongodb/sharded_cluster/myshardrs01_27218/data/db
```

- 在配置文件中加入以下内容

```
sharding:
#分片角色
clusterRole: shardsvr
```

![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/21dccea19b5f7257b4587dfb4a52439b.png)

- config server:[https://www.mongodb.com/docs/manual/reference/glossary/#term-config-server](https://www.mongodb.com/docs/manual/reference/glossary/#term-config-server)
- shard:[https://www.mongodb.com/docs/manual/reference/glossary/#term-shard](https://www.mongodb.com/docs/manual/reference/glossary/#term-shard)
- 注意：设置sharding.clusterRole需要mongod实例运行复制。 要将实例部署为副本集成员，请使用  
    replSetName设置并指定副本集的名称。
- 新建或修改配置文件：

```
vim /mongodb/sharded_cluster/myshardrs01_27118/mongod.conf
```

```
systemLog:
#MongoDB发送所有日志输出的目标指定为文件
destination: file
#mongod或mongos应向其发送所有诊断日志记录信息的日志文件的路径
path: "/mongodb/sharded_cluster/myshardrs01_27218/log/mongod.log"
#当mongos或mongod实例重新启动时，mongos或mongod会将新条目附加到现有日志文件的末尾。
logAppend: true
storage:
#mongod实例存储其数据的目录。storage.dbPath设置仅适用于mongod。
dbPath: "/mongodb/sharded_cluster/myshardrs01_27218/data/db"
journal:
#启用或禁用持久性日志以确保数据文件保持有效和可恢复。
enabled: true
processManagement:
#启用在后台运行mongos或mongod进程的守护进程模式。
fork: true
#指定用于保存mongos或mongod进程的进程ID的文件位置，其中mongos或mongod将写入其PID
pidFilePath: "/mongodb/sharded_cluster/myshardrs01_27218/log/mongod.pid"
net:
#服务实例绑定的IP
bindIp: localhost,192.168.0.2
#绑定的端口
port: 27218
replication:
replSetName: myshardrs01
sharding:
clusterRole: shardsvr

```

#### 7.4.2 配置节点副本集

- 将上节配置文件中最后一行的`clusterRole`改为`configsvr`即可,其他大同小异

#### 7.4.3 路由节点的创建与操作

- 只需要准备存放日志的目录
- 修改配置文件最后一行

```
sharding:
#指定配置节点副本集
configDB:
myconfigrs/180.76.159.126:27019,180.76.159.126:27119,180.76.159.126:27219
```

- properties配置文件参考

```
logpath=/mongodb/sharded_cluster/mymongos_27017/log/mongos.log
logappend=true
bind_ip_all=true
port=27017
fork=true
configdb=myconfigrs/180.76.159.126:27019,180.76.159.126:27119,180.76.159.126:272
19
```

#### 7.4.4 在路由节点上进行分片配置操作

- 使用命令添加分片：

1. 添加分片：
    - 语法：`sh.addShard("IP:Port")`

- 提示：如果添加分片失败，需要先手动移除分片，检查添加分片的信息的正确性后，再次添加分片。  
    移除分片参考(了解)：

```
use admin
db.runCommand( { removeShard: "myshardrs02" } )
```

- 注意：如果只剩下最后一个shard，是无法删除的,移除时会自动转移分片数据，需要一个时间过程。完成后，再次执行删除分片命令才能真正删除。

2. 开启分片功能：sh.enableSharding(“库名”)、sh.shardCollection(“库名.集合名”,{“key”:1})
    
3. 集合分片
    

- 对集合分片，你必须使用 sh.shardCollection() 方法指定集合和分片键。
    
- 语法：`sh.shardCollection(namespace, key, unique)`
    
- 参数：  
    ![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/a7e148e19dd90d62f2eff205c28c3522.png)
    
- 对集合进行分片时,你需要选择一个 片键（Shard Key） , shard key 是每条记录都必须包含的,且建立了索引的单个字段或复合字段,MongoDB按照片键将数据划分到不同的 数据块 中,并将 数据块 均衡地分布到所有分片中.为了按照片键划分数据块,MongoDB使用 基于哈希的分片方式（随机平均分配）或者基于范围的分片方式（数值大小分配） 。
    
- 用什么字段当片键都可以，如：nickname作为片键，但一定是必填字段。
    
- 分片规则一：哈希策略
    
    - 对于 基于哈希的分片 ,MongoDB计算一个字段的哈希值,并用这个哈希值来创建数据块.在使用基于哈希分片的系统中,拥有”相近”片键的文档 很可能不会 存储在同一个数据块中,因此数据的分离性更好一些.
- 分片规则二：范围策略
    
    - 对于 基于范围的分片 ,MongoDB按照片键的范围把数据分成不同部分.假设有一个数字的片键:想象一个从负无穷到正无穷的直线,每一个片键的值都在直线上画了一个点.MongoDB把这条直线划分为更短的不重叠的片段,并称之为 数据块 ,每个数据块包含了片键在一定范围内的数据.
    - 在使用片键做范围划分的系统中,拥有”相近”片键的文档很可能存储在同一个数据块中,因此也会存储在同  
        一个分片中.
    - 如使用作者年龄字段作为片键，按照点赞数的值进行分片：
    - 注意的是：
        - 一个集合只能指定一个片键，否则报错。
        - 一旦对一个集合分片，分片键和分片值就不可改变。 如：不能给集合选择不同的分片键、不能更新分片键的值。
        - 根据age索引进行分配数据。
- 基于范围的分片方式与基于哈希的分片方式性能对比：
    
- 基于范围的分片方式提供了更高效的范围查询,给定一个片键的范围,分发路由可以很简单地确定哪个数  
    据块存储了请求需要的数据,并将请求转发到相应的分片中.
    
- 不过,基于范围的分片会导致数据在不同分片上的不均衡,有时候,带来的消极作用会大于查询性能的积极  
    作用.比如,如果片键所在的字段是线性增长的,一定时间内的所有请求都会落到某个固定的数据块中,最终  
    导致分布在同一个分片中.在这种情况下,一小部分分片承载了集群大部分的数据,系统并不能很好地进行  
    扩展.
    
- 与此相比,基于哈希的分片方式以范围查询性能的损失为代价,保证了集群中数据的均衡.哈希值的随机性  
    使数据随机分布在每个数据块中,因此也随机分布在不同分片中.但是也正由于随机性,一个范围查询很难  
    确定应该请求哪些分片,通常为了返回需要的结果,需要请求所有分片.
    
- 如无特殊情况，一般推荐使用 Hash Sharding。
    
- 而使用 _id 作为片键是一个不错的选择，因为它是必有的，你可以使用数据文档 _id 的哈希作为片键。
    
- 这个方案能够是的读和写都能够平均分布，并且它能够保证每个文档都有不同的片键所以数据块能够很  
    精细。
    
- 似乎还是不够完美，因为这样的话对多个文档的查询必将命中所有的分片。虽说如此，这也是一种比较  
    好的方案了。
    
- 理想化的 shard key 可以让 documents 均匀地在集群中分布：  
    ![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/fd7f83ff77cf091b88feb317e98ea0b0.png)
    
- 显示集群的详细信息：
    

```
mongos> db.printShardingStatus()
```

- 查看均衡器是否工作（需要重新均衡时系统才会自动启动，不用管它）：

```
mongos> sh.isBalancerRunning()
```

- 查看当前Balancer状态：

```
mongos> sh.getBalancerState()
```

### 7.5 Compass连接分片集群

- compass连接：  
    ![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/1a2150ca20a2dab09df721625474e872.png)
    
- 提示：和连接单机mongod一样。  
    连接成功后，上方有mongos和分片集群的提示：  
    ![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/f54b6b99702fe0405572a70b52aaab4e.png)
    

### 7.6 SpringDataMongDB连接分片集群

- Java客户端常用的是SpringDataMongoDB，其连接的是mongs路由，配置和单机mongod的配置是一样的。
- 多个路由的时候的SpringDataMongoDB的客户端配置参考如下：

```
spring:
#数据源配置
data:
mongodb:
# 主机地址
# host: 180.76.159.126
# 数据库
# database: articledb
# 默认端口是27017
# port: 27017
#也可以使用uri连接
# uri: mongodb://192.168.40.134:28017/articledb
# 连接副本集字符串
# uri:
mongodb://180.76.159.126:27017,180.76.159.126:27018,180.76.159.126:27019/article
db?connect=replicaSet&slaveOk=true&replicaSet=myrs
#连接路由字符串
uri: mongodb://180.76.159.126:27017,180.76.159.126:27117/articledb

```

### 7.7 清除节点数据（备用）

- 如果在搭建分片的时候有操作失败或配置有问题，需要重新来过的，可以进行如下操作：
    - 第一步：查询出所有的测试服务节点的进程：`[root@bobohost sharded_cluster]# ps -ef |grep mongo`
        - 根据上述的进程编号，依次中断进程：
    - 第二步：清除所有的节点的数据：`rm -rf /mongodb/sharded_cluster/myconfigrs_27019/data/db/*.* \ &`
    - 第三步：查看或修改有问题的配置
    - 第四步：依次启动所有节点，不包括路由节点:`/usr/local/mongodb/bin/mongod -f /mongodb/sharded_cluster/myshardrs01_27018/mongod.conf`
    - 第五步：对两个数据分片副本集和一个配置副本集进行初始化和相关配置
    - 第六步：检查路由mongos的配置，并启动mongos`/usr/local/mongodb/bin/mongod -f /mongodb/sharded_cluster/mymongos_27017/mongos.cfg`
    - 第七步：mongo登录mongos，在其上进行相关操作。

## 8. 安全认证

### 8.1 MongoDB的用户和角色权限简介

- 默认情况下，MongoDB实例启动运行时是没有启用用户访问权限控制的，也就是说，在实例本机服务  
    器上都可以随意连接到实例进行各种操作，MongoDB不会对连接客户端进行用户验证，这是非常危险  
    的。
- mongodb官网上说，为了能保障mongodb的安全可以做以下几个步骤：
    1. 使用新的端口，默认的27017端口如果一旦知道了ip就能连接上，不太安全。
    2. 设置mongodb的网络环境，最好将mongodb部署到公司服务器内网，这样外网是访问不到的。公  
        司内部访问使用vpn等。
    3. 开启安全认证。认证要同时设置服务器之间的内部认证方式，同时要设置客户端连接到集群的账号  
        密码认证方式。
- 为了强制开启用户访问控制(用户验证)，则需要在MongoDB实例启动时使用选项 --auth 或在指定启动  
    配置文件中添加选项 auth=true 。
- 在开始之前需要了解一下概念

1. 启用访问控制：
    - MongoDB使用的是基于角色的访问控制(Role-Based Access Control,RBAC)来管理用户对实例的访问。  
        通过对用户授予一个或多个角色来控制用户访问数据库资源的权限和数据库操作的权限，在对用户分配  
        角色之前，用户无法访问实例。
    - 在实例启动时添加选项 --auth 或指定启动配置文件中添加选项 auth=true 。
2. 角色：
    - 在MongoDB中通过角色对用户授予相应数据库资源的操作权限，每个角色当中的权限可以显式指定，  
        也可以通过继承其他角色的权限，或者两都都存在的权限。
3. 权限：
    - 权限由指定的数据库资源(resource)以及允许在指定资源上进行的操作(action)组成。
        1. 资源(resource)包括：数据库、集合、部分集合和集群；
        2. 操作(action)包括：对资源进行的增、删、改、查(CRUD)操作。
    - 在角色定义时可以包含一个或多个已存在的角色，新创建的角色会继承包含的角色所有的权限。在同一  
        个数据库中，新创建角色可以继承其他角色的权限，在 admin 数据库中创建的角色可以继承在其它任意  
        数据库中角色的权限。

- 关于角色权限的查看，可以通过如下命令查询（了解）：

```
// 查询所有角色权限(仅用户自定义角色)
> db.runCommand({ rolesInfo: 1 })
// 查询所有角色权限(包含内置角色)
> db.runCommand({ rolesInfo: 1, showBuiltinRoles: true })
// 查询当前数据库中的某角色的权限
> db.runCommand({ rolesInfo: "<rolename>" })
// 查询其它数据库中指定的角色权限
> db.runCommand({ rolesInfo: { role: "<rolename>", db: "<database>" } }
// 查询多个角色权限
> db.runCommand(
{
rolesInfo: [
"<rolename>",
{ role: "<rolename>", db: "<database>" },
...
]
}
)
```

- 常用的内置角色：
    - 数据库用户角色：read、readWrite;
    - 所有数据库用户角色：readAnyDatabase、readWriteAnyDatabase、  
        userAdminAnyDatabase、dbAdminAnyDatabase
    - 数据库管理角色：dbAdmin、dbOwner、userAdmin；
    - 集群管理角色：clusterAdmin、clusterManager、clusterMonitor、hostManager；
    - 备份恢复角色：backup、restore；
    - 超级用户角色：root
    - 内部角色：system  
        ![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/db380e7efccef5f7981aadede3ec4fa2.png)

### 8.2 单实例环境

#### 8.2.1添加用户和权限

- 创建两个管理员用户，一个是系统的超级管理员 myroot ，一个是admin库的管理用户  
    myadmin

```
//切换到admin库
> use admin
//创建系统超级用户 myroot,设置密码123456，设置角色root
//> db.createUser({user:"myroot",pwd:"123456",roles:[ { "role" : "root", "db" :
"admin" } ]})
//或
> db.createUser({user:"myroot",pwd:"123456",roles:["root"]})
Successfully added user: { "user" : "myroot", "roles" : [ "root" ] }
//创建专门用来管理admin库的账号myadmin，只用来作为用户权限的管理
> db.createUser({user:"myadmin",pwd:"123456",roles:
[{role:"userAdminAnyDatabase",db:"admin"}]})
Successfully added user: {
"user" : "myadmin",
"roles" : [
{
"role" : "userAdminAnyDatabase",
"db" : "admin"
}
]
}
//查看已经创建了的用户的情况：
> db.system.users.find()
{ "_id" : "admin.myroot", "userId" : UUID("9a0a698c-73ad-4c45-8f33-
e8a90d3ad689"), "user" : "myroot", "db" : "admin", "credentials" : { "SCRAM-SHA1" : { "iterationCount" : 10000, "salt" : "4tXXi9g9wMlrR32e+NleyA==",
"storedKey" : "78EXQoWeA6lLYTTzcQrtJuWLcmg=", "serverKey" :
"xwze/lGcQ7FI5cSFoilY4CW4Wks=" }, "SCRAM-SHA-256" : { "iterationCount" : 15000,
"salt" : "+Hq2Y6PiNFkDEBYFertTaZSWI9FqbkYGdHaFkg==", "storedKey" :
"gUZ5Wyl7dsjtu77Isw2dsJ+Ck4fKiKZteUh/CuJoQj4=", "serverKey" :
"4WiBApuB435LNPP49DxKwJ+YGcRaWZNvEq/Ibkr5Lxo=" } }, "roles" : [ { "role" :
"root", "db" : "admin" } ] }
{ "_id" : "admin.myadmin", "userId" : UUID("be9c832e-f894-4ffd-b76b62940707aab2"), "user" : "myadmin", "db" : "admin", "credentials" : { "SCRAMSHA-1" : { "iterationCount" : 10000, "salt" : "KIIoSNfp5kTgpUExtTKDTA==",
"storedKey" : "39509XHQiWi8HWLc6qMDf13WcSs=", "serverKey" :
"zKkJAKH3HgPL35/a6hkhBaCD1WE=" }, "SCRAM-SHA-256" : { "iterationCount" : 15000,
"salt" : "v76GZgBAKsWNewB7mo6dhSE59ME3HFJ5T9UXlQ==", "storedKey" :
"CwHtBiww04Y0hycHKqq4VIS5QnnuAne59+iPFooIhkk=", "serverKey" :
"HQk3RTSWDABGwxYPEiEC2+iK/rGTL6ROAD0HQEJI0F8=" } }, "roles" : [ { "role" :
"userAdminAnyDatabase", "db" : "admin" } ] }
//删除用户
> db.dropUser("myadmin")
true
> db.system.users.find()
//修改密码
> db.changeUserPassword("myroot", "123456")
```

```
//创建(切换)将来要操作的数据库articledb,
> use articledb
switched to db articledb
//创建用户，拥有articledb数据库的读写权限readWrite，密码是123456
> db.createUser({user: "bobo", pwd: "123456", roles: [{ role: "readWrite", db:
"articledb" }]})
//> db.createUser({user: "bobo", pwd: "123456", roles: ["readWrite"]})
Successfully added user: {
"user" : "bobo",
"roles" : [
{
"role" : "readWrite",
"db" : "articledb"
}
]
}
//测试是否可用
> db.auth("bobo","123456")
1
```

- 提示：
    1. 本案例创建了两个用户，分别对应超管和专门用来管理用户的角色，事实上，你只需要一个用户即  
        可。如果你对安全要求很高，防止超管泄漏，则不要创建超管用户。
    2. 和其它数据库（MySQL）一样，权限的管理都差不多一样，也是将用户和权限信息保存到数据库对  
        应的表中。Mongodb存储所有的用户信息在admin 数据库的集合system.users中，保存用户名、密码  
        和数据库信息。
    3. 如果不指定数据库，则创建的指定的权限的用户在所有的数据库上有效，如 {role:  
        “userAdminAnyDatabase”, db:“”}
    4. 以开启认证的方式启动服务
        - 有两种方式开启权限认证启动服务：一种是参数方式，一种是配置文件方式。
            - 参数方式:在启动时指定参数 --auth ，如：`/usr/local/mongodb/bin/mongod -f /mongodb/single/mongod.conf --auth`
            - 配置文件方式;在mongod.conf配置文件中加入：

```
security:
#开启授权认证
authorization: enabled
```

#### 8.2.2 SpringDataMongoDB连接认证

- 使用用户名和密码连接到 MongoDB 服务器，你必须使用`'username:password@hostname/dbname'` 格式，`'username'`为用户名，`'password'` 为密码。
- 目标：使用用户bobo使用密码 123456 连接到MongoDB 服务上。
- application.yml：

```yml
spring:
#数据源配置
data:
mongodb:
# 主机地址
# host: 180.76.159.126
# 数据库
# database: articledb
# 默认端口是27017
# port: 27017
#帐号
# username: bobo
#密码
# password: 123456
#单机有认证的情况下，也使用字符串连接
uri: mongodb://bobo:123456@180.76.159.126:27017/articledb

```

### 8.3副本集环境

- 对于搭建好的mongodb副本集，为了安全，启动安全认证，使用账号密码登录。
    
- 副本集环境使用之前搭建好的，架构如下：  
    ![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/4ebe9da3c68de4356e300a747a0cc379.png)
    
- 对副本集执行访问控制需要配置两个方面:
    
    1. 副本集和共享集群的各个节点成员之间使用内部身份验证，可以使用密钥文件或x.509证书。密钥文  
        件比较简单，本文使用密钥文件，官方推荐如果是测试环境可以使用密钥文件，但是正式环境，官方推  
        荐x.509证书。原理就是，集群中每一个实例彼此连接的时候都检验彼此使用的证书的内容是否相同。  
        只有证书相同的实例彼此才可以访问
    2. 使用客户端连接到mongodb集群时，开启访问授权。对于集群外部的访问。如通过可视化客户端，  
        或者通过代码连接的时候，需要开启授权。
    3. 在keyfile身份验证中，副本集中的每个mongod实例都使用keyfile的内容作为共享密码，只有具有正确  
        密钥文件的mongod或者mongos实例可以连接到副本集。密钥文件的内容必须在6到1024个字符之  
        间，并且在unix/linux系统中文件所有者必须有对文件至少有读的权限。

**除了创建key环境,其他步骤基本与单实例相同,在这里简单介绍key相关**

1. 创建副本集认证的key文件
    - 第一步：生成一个key文件到当前文件夹中。
    - 可以使用任何方法生成密钥文件。例如，以下操作使用openssl生成密码文件，然后使用chmod来更改  
        文件权限，仅为文件所有者提供读取权限

```
[root@bobohost ~]# openssl rand -base64 90 -out ./mongo.keyfile
[root@bobohost ~]# chmod 400 ./mongo.keyfile
[root@bobohost ~]# ll mongo.keyfile
-r--------. 1 root root 122 8月 14 14:23 mongo.keyfile
```

- 提示：
    - 所有副本集节点都必须要用同一份keyfile，一般是在一台机器上生成，然后拷贝到其他机器上，且必须  
        有读的权限，否则将来会报错： `permissions on /mongodb/replica_sets/myrs_27017/mongo.keyfile are too open`
    - 一定要保证密钥文件一致，文件位置随便。但是为了方便查找，建议每台机器都放到一个固定的位置，  
        都放到和配置文件一起的目录中。
    - 这里将该文件分别拷贝到多个目录中：

```
[root@bobohost ~]# cp mongo.keyfile /mongodb/replica_sets/myrs_27017
[root@bobohost ~]# cp mongo.keyfile /mongodb/replica_sets/myrs_27018
[root@bobohost ~]# cp mongo.keyfile /mongodb/replica_sets/myrs_27019
```

2. 修改配置文件指定keyfile

- 分别编辑几个服务的mongod.conf文件，添加相关内容：
- 例如,在`/mongodb/replica_sets/myrs_27017/mongod.conf`中加上

```
security:
#KeyFile鉴权文件
keyFile: /mongodb/replica_sets/myrs_27017/mongo.keyfile
#开启认证方式运行
authorization: enabled
```