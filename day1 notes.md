# Day 1 - My SQL Learning Journey

##  Topics Covered
- Basic SQL queries
- Understanding `JOIN`
- Calculating confirmation rates

## Mistakes I Made
1. **Null outputs issue** – I was getting `NULL` instead of numbers.
2. **Forgot to group results** – I didn’t use `GROUP BY` at first, so results were wrong.
3. **Overcomplicating joins** – I added unnecessary conditions in the `ON` clause.


##  How I Fixed Them
- Used `IFNULL()` or `AVG()` to handle `NULL` values.
- Added `GROUP BY user_id` to group results correctly.
- Simplified my join condition to only match `user_id`.


##  Tips for Beginners
- Always check if your aggregation functions are dividing by zero or encountering `NULL`.
- Start with a simple query, then add complexity step-by-step.
- Understand the difference between `AVG()` and `SUM()/COUNT()`.


##  Final Query of the Day
```sql
SELECT s.user_id,
       ROUND(IFNULL(AVG(c.action = 'confirmed'), 0), 2) AS confirmation_rate
FROM Signups AS s
LEFT JOIN Confirmations AS c
    ON s.user_id = c.user_id
GROUP BY s.user_id;
