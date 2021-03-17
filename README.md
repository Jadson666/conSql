# Consql
this library is to implement formal CRUD functionality by simply configure the columns and table name in consql.json 

for example, following config will able to start a server which accept `GET, POST, PUT, DELETE`

```json
{
  "collection": [
    {
      "column": ColumnA,
      "table": tableNameA
    },
    {
      "column": ColumnB,
      "table": tableNameB
    },
    {
      "column": ColumnC,
      "table": [tableNameA, tableNameB]
    }
  ]
}
```

ColumnC is join condition of TableNameA and TableNameB
the above configuration is equal to 

the above configuration will start a `http server` accept

1. GET

```sql
SELECT tableNameA.ColumnA, tableNameB.ColumnB, tableNameA.ColumnC
FROM tableNameA, tableNameB
WHERE tableNameA.ColumnC = tableNameB.ColumnC
```

2. PUT
```sql
UPDATE tableNameA
SET ColumnA = ?, ColumnC = ?
WHERE tableNameA.ColumnC

UPDATE tableNameB
SET ColumnB = ?, ColumnC = ?
WHERE tableNameB.ColumnC
```

3. POST
```sql
INSERT INTO tableNameA (ColumnA, ColumnC)
VALUES (?,?)

INSERT INTO tableNameB (ColumnB, ColumnC)
VALUES (?,?)
```

4. DELETE
```sql
DELETE FROM tableNameA
WHERE ColumnC = ?

DELETE FROM tableNameB
WHERE ColumnC = ?
```
