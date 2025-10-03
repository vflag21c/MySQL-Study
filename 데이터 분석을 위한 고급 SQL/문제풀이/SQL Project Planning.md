### 문제 링크
[SQL Project Planning](https://www.hackerrank.com/challenges/sql-projects/problem)

풀이
```sql
 with a as (
    select
        START_DATE,
        RANK() OVER(ORDER BY START_DATE ASC) as rn1
    from Projects a
    WHERE NOT EXISTS ( SELECT 1 FROM Projects WHERE a.START_DATE = end_date)
),
      b as (
          select end_date
               , RANK() over(order by end_date asc) as rn2
          from Projects b
          where not exists (select 1 from Projects where b.end_date = START_DATE)
      )
 select a.START_DATE, b.end_date
 from a
          join b on (a.rn1 = b.rn2)
 order by end_date - START_DATE asc;
```