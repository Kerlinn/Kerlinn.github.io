# Neo4j

### 修改密码

```cypher
:server change-password
```



### 导入

```sql
USING PERIODIC COMMIT 1000
LOAD CSV WITH HEADERS FROM "file:///event.csv" AS line
CREATE (event:EVENT{e_id:line.e_id, time:line.time, text:line.text})
```

用下面的命令取代


```sql
CALL {
    LOAD CSV WITH HEADERS FROM "file:///event.csv" AS line
    CREATE (event:EVENT{e_id:line.e_id, time:line.time, text:line.text})
} IN TRANSACTION
```



