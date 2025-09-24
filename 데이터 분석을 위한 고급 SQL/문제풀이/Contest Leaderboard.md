### 문제 링크
[Contest Leaderboard](https://www.hackerrank.com/challenges/contest-leaderboard/problem)

풀이
```sql
SELECT T.HACKER_ID, T.NAME, SUM(T.SCORE)
FROM (
         SELECT S.HACKER_ID, H.name, max(S.score) AS SCORE
         FROM Hackers H
                  JOIN Submissions S
                       ON H.hacker_id = S.hacker_id
         GROUP BY S.HACKER_ID, H.name, S.challenge_id
         HAVING max(S.score) > 0
     ) T
GROUP BY T.HACKER_ID, T.NAME
ORDER BY SUM(T.SCORE) DESC, T.HACKER_ID ASC
```