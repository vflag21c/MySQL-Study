### 강의 링크
[Leetcode 184. Department Highest Salary](https://leetcode.com/problems/department-highest-salary/)

풀이
```sql
SELECT SUB.Dname as Department , M.name as Employee , M.Salary
FROM Employee M
         JOIN (
    SELECT D.name AS Dname
         , E.name AS Ename
         , MAX(E.salary) OVER (PARTITION BY D.id ) AS MaxSalary
    FROM Employee E
             JOIN Department D
                  ON E.departmentId = D.id
) SUB ON ( M.name = SUB.Ename)
WHERE SUB.MaxSalary = M.Salary
```