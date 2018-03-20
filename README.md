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


m.show()
+---+-------+-------------+------+
|_id|    age|           id|  name|
+---+-------+-------------+------+
|  1|     25|    [1,7,sai]|Milind|
|  2|Testing|[2,null,null]|Ramesh|
+---+-------+-------------+------+


scala> val c = sqlContext.sql("select id['_b']from sai").show();
+----+
| _c0|
+----+
| sai|
|null|
+----+

c: Unit = ()

scala> m.printSchema()
root
 |-- _id: long (nullable = true)
 |-- age: string (nullable = true)
 |-- id: struct (nullable = true)
 |    |-- _VALUE: long (nullable = true)
 |    |-- _a: long (nullable = true)
 |    |-- _b: string (nullable = true)
 |-- name: string (nullable = true)



