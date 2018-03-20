# xml-in-s

scala> val m = sqlContext.read.format("xml").option("rowTag","student").load("/user/cloudera/u.xml");
m: org.apache.spark.sql.DataFrame = [_id: bigint, age: string, id: bigint, name: string]

scala> m.printSchema();
root
 |-- _id: long (nullable = true)
 |-- age: string (nullable = true)
 |-- id: long (nullable = true)
 |-- name: string (nullable = true)


scala> m.first
res1: org.apache.spark.sql.Row = [1,25,1,Milind]

scala> m.take(2)
res2: Array[org.apache.spark.sql.Row] = Array([1,25,1,Milind], [2,Testing,2,Ramesh])

scala> m.foreach(println)
[1,25,1,Milind]
[2,Testing,2,Ramesh]
