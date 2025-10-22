### 문제 링크
[LeetCode 262. Trips and Users](https://leetcode.com/problems/trips-and-users/)

풀이
```sql
WITH B AS(
    SELECT REQUEST_AT, STATUS, B.BANNED AS B_BAN, C.BANNED AS C_BAN
    FROM TRIPS A
             JOIN USERS B
                  ON A.CLIENT_ID = B.USERS_ID
             JOIN USERS C
                  ON A.DRIVER_ID = C.USERS_ID
)
SELECT TOT.REQUEST_AT as 'Day',  ROUND( TOT.CAN_CNT / TOT.tot_cnt, 2 ) as 'Cancellation Rate'
FROM (
         SELECT A.REQUEST_AT
              , COUNT(*)
              , (SELECT COUNT(*) FROM B WHERE A.REQUEST_AT = REQUEST_AT AND STATUS LIKE 'cancelled%' AND B.B_BAN = 'NO' AND B.C_BAN = 'NO') AS can_cnt
              , (SELECT COUNT(*) FROM B WHERE A.REQUEST_AT = REQUEST_AT AND B.B_BAN = 'NO' AND B.C_BAN = 'NO' ) AS tot_cnt
         FROM TRIPS A
         GROUP BY A.REQUEST_AT
     ) TOT
```