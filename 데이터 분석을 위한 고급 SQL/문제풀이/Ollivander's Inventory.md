### 문제 링크
[Ollivander's Inventory](https://www.hackerrank.com/challenges/harry-potter-and-wands/problem)

풀이
```sql
SELECT T.id, T.age, T.coins_needed, T.power
FROM (
         SELECT
             w.id,
             wp.age,
             w.coins_needed,
             w.power,
             RANK() OVER (PARTITION BY wp.age, w.power ORDER BY w.coins_needed ASC) rnk
         FROM Wands w
                  JOIN Wands_Property wp
                       ON w.code = wp.code
         WHERE wp.is_evil = 0
     ) T
where T.rnk = 1
order by 4 desc, 2 desc
```