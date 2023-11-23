# How to import data from MongoDB to Hive or Hbase ? 

I would like to know how I can import data from MongoDB (documents) to Hive or Hbase ? 

Best option would be using Mongo hadoop connector with hive external tables but you need to built that jar manually or use prebuilt.

https://github.com/mongodb/mongo-hadoop/wiki/Hive-Usage

CREATE TABLE individuals
( 
  id INT,
  name STRING,
  age INT,
  work STRUCT<title:STRING, hours:INT>
)
STORED BY 'com.mongodb.hadoop.hive.MongoStorageHandler'
WITH SERDEPROPERTIES('mongo.columns.mapping'='{"id":"_id","work.title":"job.position"}')
TBLPROPERTIES('mongo.uri'='mongodb://localhost:27017/test.persons');
