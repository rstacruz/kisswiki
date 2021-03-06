>`std::marker::Sized` is not implemented for `postgres::types::ToSql`

add type annotation:

```rust
var data_type_id: i32 = row.get(0);
```

## Float

for `f32` use `real`

https://github.com/sfackler/rust-postgres

## Concatenate column

`u.first_name || ' ' || u.last_name`

- http://stackoverflow.com/questions/19942824/how-to-concatenate-columns-in-a-postgres-select
- http://stackoverflow.com/questions/43870/how-to-concatenate-strings-of-a-string-field-in-a-postgresql-group-by-query

## describe

- table `\d+ tablename`

## order by limit slow

http://stackoverflow.com/questions/6037843/extremely-slow-postgresql-query-with-order-and-limit-clauses

## count

```sql
SELECT A.id, QTY.quantity FROM A
LEFT JOIN
    (SELECT COUNT(B.a_id) AS quantity, B.a_id FROM B GROUP BY B.a_id) AS QTY
ON A.id = QTY.a_id
```

Another variant:

```sql
SELECT A.id, COUNT(B.a_id) AS quantity FROM A
LEFT JOIN B ON B.a_id = A.id
GROUP BY A.id
```

http://stackoverflow.com/questions/4535782/select-count-of-rows-in-another-table-in-a-postgres-select-statement

## Conversion(WrongType(Int8))

Use i64

The "8" in Int8 refers to a byte count, not a bit count

https://github.com/sfackler/rust-postgres/issues/198#issuecomment-241345919

## last inserted ID

`INSERT INTO persons (lastname,firstname) VALUES ('Smith', 'John') RETURNING id;`

http://stackoverflow.com/questions/2944297/postgresql-function-for-last-inserted-id/2944481#2944481
