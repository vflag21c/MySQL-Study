### 문제 링크
[LeetCode 185. Department Top Three Salaries](https://leetcode.com/problems/department-top-three-salaries/description/)

풀이
```sql
SELECT SUB.Department, M.name AS Employee , M.Salary
  FROM (
        SELECT D.name as Department
            , E.name as Employee
            , DENSE_RANK() OVER (PARTITION BY D.id ORDER BY E.Salary DESC) as s_rank
        FROM Employee E
        JOIN Department D
          ON E.departmentId = D.id
  ) SUB JOIN Employee M
          ON (M.name = SUB.Employee)
WHERE SUB.S_RANK <= 3
```