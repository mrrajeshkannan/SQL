
# Hacker Rank Challenges 


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
