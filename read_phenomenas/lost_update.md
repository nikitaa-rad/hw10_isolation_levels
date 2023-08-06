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
SELECT age
FROM users
WHERE name = 'Alice';
-- retrieves 20, since no updates have been made
```

</td>
</tr>
<tr>
<td>

```sql
UPDATE users SET age = age + 5 WHERE name = 'Alice';
COMMIT;
-- now Alice's age is 25 in the database.
```

</td>
<td>
</td>
</tr>
<tr>
<td>
</td>
<td>

```sql
UPDATE users SET age = age - 2 WHERE name = 'Alice';
COMMIT;
-- now Alice's age is 23 in the database.
-- The result will be 23, which means the +5 years update made by Session
-- 1 got overwritten or 'lost' by the -2 years update made by Session 2.
```

</td>
</tr>
</table>
