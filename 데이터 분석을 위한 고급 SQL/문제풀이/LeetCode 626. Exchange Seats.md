### 문제 링크
[LeetCode 626. Exchange Seats](https://leetcode.com/problems/exchange-seats)

풀이
```sql
select  a.id
     , case when mod(id , 2) = 1  THEN IFNULL((SELECT student FROM seat WHERE id = a.id + 1), a.student)
            else (select student from seat where id = a.id -1 )
        end as student
from seat a

```