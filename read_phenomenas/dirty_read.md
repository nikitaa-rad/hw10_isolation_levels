<table>
<tr>
<th> Transaction 1 </th>
<th> Transaction 2 </th>
</tr>
<tr>
<td>

```sql
START TRANSACTION;
SELECT age
FROM users
WHERE name = 'Alice';
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
START TRANSACTION;
UPDATE users
SET age = 42
WHERE name = 'Alice';
```

</td>
</tr>
<tr>
<td>

```sql
SELECT age
FROM users
WHERE name = 'Alice';
-- retrieves 42 in Read Uncommitted 
-- even it is not committed by Transaction 2
```

</td>
<td>
</td>
</tr>
</table>
