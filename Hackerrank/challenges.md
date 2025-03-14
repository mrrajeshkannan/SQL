
# Hacker Rank Challenges 

All the solutations are works well in ORACLE.

[The PADS](https://www.hackerrank.com/challenges/the-pads/problem)

```sql
SELECT Name ||'('|| substr(Occupation,1,1) ||')'
FROM OCCUPATIONS 
order by Name;

SELECT 'There are a total of ' || COUNT(1) || ' ' || lower(Occupation) ||'s.'
FROM OCCUPATIONS
GROUP BY Occupation
ORDER BY COUNT(1), Occupation;
```

<br /> 



[New Companies](https://www.hackerrank.com/challenges/the-company/problem)

```sql
SELECT 
C.COMPANY_CODE, 
C.FOUNDER , 
COUNT(DISTINCT LM.LEAD_MANAGER_CODE), 
COUNT(DISTINCT SM.SENIOR_MANAGER_CODE),
COUNT(DISTINCT M.MANAGER_CODE), 
COUNT(DISTINCT E.EMPLOYEE_CODE)
FROM COMPANY C FULL JOIN LEAD_MANAGER LM
ON C.COMPANY_CODE=LM.COMPANY_CODE FULL JOIN SENIOR_MANAGER SM
ON LM.COMPANY_CODE=SM.COMPANY_CODE FULL JOIN MANAGER M
ON SM.COMPANY_CODE=M.COMPANY_CODE FULL JOIN EMPLOYEE E
ON M.COMPANY_CODE=E.COMPANY_CODE
GROUP BY C.COMPANY_CODE, C.FOUNDER
ORDER BY C.COMPANY_CODE;
```

<br /> 



[Occupations](https://www.hackerrank.com/challenges/occupations/problem)

```sql
WITH rk AS (
    SELECT 
        NAME,
        OCCUPATION,
        ROW_NUMBER() OVER (PARTITION BY OCCUPATION ORDER BY NAME) AS RN
    FROM OCCUPATIONS
)
SELECT 
    MIN(CASE WHEN OCCUPATION = 'Doctor' THEN NAME END) AS Doctor,
    MIN(CASE WHEN OCCUPATION = 'Professor' THEN NAME END) AS Professor,
    MIN(CASE WHEN OCCUPATION = 'Singer' THEN NAME END) AS Singer,
    MIN(CASE WHEN OCCUPATION = 'Actor' THEN NAME END) AS Actor
FROM rk
GROUP BY RN
ORDER BY RN;
```

<br /> 



[weather-observation-station-14](https://www.hackerrank.com/challenges/weather-observation-station-14/problem)

```sql
SELECT ROUND(MAX(LAT_N),4)
FROM STATION
WHERE LAT_N < 137.2345;
```

<br /> 



[weather-observation-station-15](https://www.hackerrank.com/challenges/weather-observation-station-15/problem)

```sql
SELECT ROUND(LONG_W, 4)  
FROM STATION  
WHERE LAT_N = (SELECT MAX(LAT_N) FROM STATION WHERE LAT_N < 137.2345);
```

<br /> 



[weather-observation-station-16](https://www.hackerrank.com/challenges/weather-observation-station-16/problem)

Query the smallest Northern Latitude (LAT_N) from STATION that is greater than 38.7780, Round your answer to  decimal places.

```sql
SELECT ROUND(MIN(LAT_N),4)
FROM STATION
WHERE LAT_N > 38.7780;
```

<br /> 


[weather-observation-station-17](https://www.hackerrank.com/challenges/weather-observation-station-17/problem)

Query the Western Longitude (LONG_W)where the smallest Northern Latitude (LAT_N) in STATION is greater than 38.7780. Round your answer to  decimal places.

```sql
SELECT ROUND(LONG_W,4)
FROM STATION
WHERE LAT_N = (SELECT MIN(LAT_N) FROM STATION WHERE LAT_N > 38.7780);
```

<br /> 



[weather-observation-station-18](https://www.hackerrank.com/challenges/weather-observation-station-18/problem)


```sql
SELECT ROUND(MAX(LAT_N)-MIN(LAT_N) + MAX(LONG_W)-MIN(LONG_W),4)
FROM STATION;
```

<br /> 

[weather-observation-station-19](https://www.hackerrank.com/challenges/weather-observation-station-19/problem)


```sql
SELECT ROUND(SQRT(POWER((B-A),2)+POWER((D-C),2)),4)
FROM
(
    SELECT
        MIN(LAT_N) AS A,
        MAX(LAT_N) AS B,
        MIN(LONG_W) AS C,
        MAX(LONG_W) AS D
    FROM STATION
);
```

<br /> 




[print-prime-numbers](https://www.hackerrank.com/challenges/print-prime-numbers/problem)


```sql
WITH numbers AS (
    SELECT LEVEL AS num
    FROM dual
    CONNECT BY LEVEL <= 1000
)
SELECT LISTAGG(num, '&') WITHIN GROUP (ORDER BY num) AS prime_numbers
FROM numbers n
WHERE num > 1 
AND NOT EXISTS (
    SELECT 1 
    FROM numbers d
    WHERE d.num > 1 
    AND d.num < n.num 
    AND MOD(n.num, d.num) = 0
);
```

<br /> 
