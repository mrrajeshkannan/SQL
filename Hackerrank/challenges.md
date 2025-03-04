
# Hacker Rank Challenges 


[The PADS](https://www.hackerrank.com/challenges/the-pads/problem)

Sample Input    <div right> Your right-aligned content here. </div>


![image](https://github.com/user-attachments/assets/f968b652-37fa-4eaa-886f-395a8ececca4)



Ashely(P) </br>
Christeen(P) </br>
Jane(A)</br>
Jenny(D)</br>
Julia(A)</br>
Ketty(P)</br>
Maria(A)</br>
Meera(S)</br>
Priya(S)</br>
Samantha(D)</br>
There are a total of 2 doctors.</br>
There are a total of 2 singers.</br>
There are a total of 3 actors.</br>
There are a total of 3 professors.</br>

Explanation

The results of the first query are formatted to the problem description's specifications.
The results of the second query are ascendingly ordered first by number of names corresponding to each profession (), and then alphabetically by profession (, and ).

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
