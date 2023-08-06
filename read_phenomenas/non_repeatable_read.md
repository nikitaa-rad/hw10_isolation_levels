<table>
<tr>
<th> Transaction 1 </th>
<th> Transaction 2 </th>
</tr>
<tr>
<td>

```sql
BEGIN;
SELECT age FROM users WHERE id = 1;
-- retrieves 20
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
UPDATE users SET age = 21 WHERE id = 1;
COMMIT;
```

</td>
</tr>
<tr>
<td>

```sql
SELECT age FROM users WHERE id = 1;
-- READ UNCOMMITTED retrieves 21 (non-repeatable read)
-- READ COMMITTED retrieves 21 (non-repeatable read)
-- REPEATABLE READ retrieves 20 (non-repeatable read has been avoided)
-- SERIALIZABLE retrieves 20 (non-repeatable read has been avoided)
COMMIT;
```

</td>
<td>
</td>
</tr>
</table>
