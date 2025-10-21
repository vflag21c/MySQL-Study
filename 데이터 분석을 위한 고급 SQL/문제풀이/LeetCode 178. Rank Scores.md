### 문제 링크
[LeetCode 178. Rank Scores](https://leetcode.com/problems/rank-scores/)

풀이
```sql
select score
     , dense_rank() over(order by score desc ) as 'rank'
from Scores
order by score desc;
```