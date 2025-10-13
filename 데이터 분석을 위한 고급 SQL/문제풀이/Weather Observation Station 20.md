### 문제 링크
[Weather Observation Station 20](https://www.hackerrank.com/challenges/weather-observation-station-20/problem)

풀이
```sql
select round(a.lat_n, 4)
from (
         select count(*) over() as cnt
         , lat_n
              , row_number() over(order by lat_n) rnk
         from station
     ) a
where ( a.cnt % 2 = 0 and rnk in (( cnt / 2), (cnt / 2) + 1))
   or ( a.cnt % 2 != 0 and rnk in(round( cnt / 2)) )
```