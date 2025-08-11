# Day 1 — My Learning Journey Begins 

## Date
2025-08-11

## What I Did Today
- Created my **first GitHub repository**.
- Learned what a `README.md` file is and how to write Markdown.
- Wrote and committed my **Day 1 learning log**.
- Practiced **SQL** — calculated user confirmation rates.

## Current Goal
My this week goal is to finish sql50 on leetcode by end of day 10,solving 5 Query each day and i will provide one solution with explaination each day that will help me track progress of each day.

## SQL Question & Solution
**Question:**  
Write a query to calculate the confirmation rate for each user from the `Signups` and `Confirmations` tables.

**Solution:**
```sql
SELECT 
    s.user_id,
    ROUND(IFNULL(AVG(c.action = 'confirmed'), 0), 2) AS confirmation_rate
FROM Signups AS s
LEFT JOIN Confirmations AS c
    ON s.user_id = c.user_id
GROUP BY s.user_id;
