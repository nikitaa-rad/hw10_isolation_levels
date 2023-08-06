<table>
<tr>
<th> Transaction 1 </th>
<th> Transaction 2 </th>
</tr>
<tr>
<td>

```sql
BEGIN;
SELECT name FROM users WHERE age > 17;
-- retrieves Alice and Bob
```

</td>
<td>
</td>
</tr>
<tr>
<td></td>
<td>

```sql
BEGIN;
INSERT INTO users VALUES (3, 'Carol', 26);
COMMIT;
```

</td>
</tr>
<tr>
<td>

```sql
SELECT name FROM users WHERE age > 17;
-- READ UNCOMMITTED retrieves Alice, Bob and Carol (phantom read)
-- READ COMMITTED retrieves Alice, Bob and Carol (phantom read)
-- REPEATABLE READ retrieves Alice, Bob and Carol (phantom read)
-- SERIALIZABLE retrieves Alice and Bob (phantom read has been avoided)
COMMIT;
```

</td>
<td>
</td>
</tr>
</table>
