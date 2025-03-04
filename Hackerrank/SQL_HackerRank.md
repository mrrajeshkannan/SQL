# HackerRank Basic Select


[Revising the Select Query I](https://www.hackerrank.com/challenges/revising-the-select-query/problem)
```sql
SELECT * FROM CITY WHERE COUNTRYCODE = 'USA' AND POPULATION >= 100000;
```

<br /> 


[Revising the Select Query II](https://www.hackerrank.com/challenges/revising-the-select-query-2/problem)
```sql
SELECT NAME 
FROM CITY 
WHERE COUNTRYCODE = 'USA' 
AND 
POPULATION >= 120000;
```

<br /> 

[Select All](https://www.hackerrank.com/challenges/select-all-sql/problem)  

Query all columns (attributes) for every row in the CITY table.  


```sql
SELECT * FROM CITY;
```

<br /> 

[select-by-id](https://www.hackerrank.com/challenges/select-by-id/problem)
```sql
SELECT *  
FROM CITY  
WHERE ID = 1661;
 ```



<br /> 

[Japanese Cities' Attributes](https://www.hackerrank.com/challenges/japanese-cities-attributes/problem)
```sql
SELECT * FROM CITY WHERE COUNTRYCODE = 'JPN';
 ```


<br /> 

[Weather Observation Station 8](https://www.hackerrank.com/challenges/weather-observation-station-8/problem)
<br /> 
Query the list of CITY names from STATION which have vowels (i.e., a, e, i, o, and u) as both their first and last characters. Your result cannot contain duplicates.
```sql
SELECT DISTINCT(CITY) FROM STATION 
WHERE 
(SUBSTR (CITY,1,1)= 'A' 
OR 
SUBSTR(CITY,1,1)= 'E'
OR 
SUBSTR(CITY,1,1)= 'I'
OR 
SUBSTR(CITY,1,1)= 'O'
OR 
SUBSTR(CITY,1,1)= 'U')
 AND 
(SUBSTR(CITY,length(city),1)='a'
OR
SUBSTR(CITY,length(city),1)='e'
OR
SUBSTR(CITY,length(city),1)='i'
OR
SUBSTR(CITY,length(city),1)='o'
OR
SUBSTR(CITY,length(city),1)='u')
ORDER BY CITY;
 ```

<br /> 

[Employee Names](https://www.hackerrank.com/challenges/name-of-employees/problem)
<br /> 
Write a query that prints a list of employee names (i.e.: the name attribute) from the Employee table in alphabetical order.

Input Format
```sql
SELECT NAME FROM EMPLOYEE ORDER BY NAME ;
 ```
