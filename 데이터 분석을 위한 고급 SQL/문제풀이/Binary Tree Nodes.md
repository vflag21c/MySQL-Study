### 문제 링크
[Binary Tree Nodes](https://www.hackerrank.com/challenges/binary-search-tree-1/problem)

풀이
```sql
select A.N, case WHEN A.P IS NULL THEN 'Root'
                 WHEN EXISTS(SELECT 1 FROM BST B WHERE A.N = B.P AND A.P IS NOT NULL) THEN 'Inner'
                 ELSE 'Leaf'
    END
from BST A
ORDER BY A.N
```