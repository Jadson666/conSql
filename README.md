data set

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

```sql
SELECT tableNameA.ColumnA, tableNameB.ColumnB, tableNameA.ColumnC
FROM tableNameA, tableNameB
WHERE tableNameA.ColumnC = tableNameB.ColumnC
```
