### 문제 링크
[Weather Observation Station 5](https://www.hackerrank.com/challenges/weather-observation-station-5/problem)

풀이
```sql
SELECT CITY AS CITY, LENGTH(CITY) AS LEN
  FROM STATION
 ORDER BY LEN, CITY
 LIMIT 1;

SELECT CITY, LENGTH(CITY) AS LEN
  FROM STATION
 ORDER BY LEN DESC, CITY ASC
 LIMIT 1
```