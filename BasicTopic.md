# Basic topic for SQL
•	SQL is a structure query language using SQL user can ACCESS, RETRIVE, STORE & MANAPULATE THE DATA IN DATABASE.
LANGUAGE-> SQL, PLSQL,
TOOL	-> SQLPLUS, Isqlplus, Toad, SQLDeveloper

## ORACLE SEARCH Procedure:-
```
Step1: SEARCH ORACLE KEYWORD( FROM → WHERE → GROUP BY → HAVING → SELECT → ORDER BY ) ->	SYNTACTIC CHECKING.rb

STEP2: USER INFORMATION (TABLE NAME, COLUMN NAME)-> SEMANTIC CHECKING.
	
STEP3: IT WILL GO TO DATABASE -> TABLE FULL SCAN.

STEP4: COST & cordiality  	-> %CPU UTILIZATION.
```
	

## Important Notes:- 

•	JOINs: If multiple tables are involved, joins are resolved during the FROM clause. </br>
•	Subqueries: Subqueries are executed first, and their results are used in the main query. </br>
•	Aliases: Columns or expressions aliased in SELECT cannot be used in WHERE or GROUP BY but can be used in ORDER BY. </br>


## Cardinality: -

•	Definition: Cardinality is the estimated number of rows that the database expects to return. </br>
 
### Example:
For a table with 10,000 rows, if a query includes a filter (WHERE clause) that is expected to match 500 rows, the cardinality of that step would be 500.

###  Cost:-
Definition: Cost is a numerical estimate of the computational resources required to execute a query step

##  Types of SQL:-

DQL, DML, DDL, DCL, TCL : -  </br>
![image](https://github.com/user-attachments/assets/1d4fb2c4-b343-4ea4-82fb-a4b2fd6d1ad3)


###  DQL (Data query Language):-

•	DQL commands are basically SELECT statements.
•	SELECT statements let you query the database to find information in one or more tables, and return the query as a result set. </br>

###  Select how many tables in the database:
```
SELECT * FROM USER_TABLES
SELECT * FROM USER_TAB_COLUMNS
```
### Select all column in table :-
```
SELECT * FROM EMPLOYEES; 
```

### To see Description of the table:- 
```
DESC EMPLOYEES; 
```

### Select custom column in table:-
```
SELECT FIRST_NAME, LAST_NAME, EMP_ID FROM EMPLOYEES;
```

### Select Using where Condition (Selecting particular condition) :-
```
SELECT EMPLOYEE_ID, FIRST_NAME, SALARY, DEPARTMENT_ID FROM EMPLOYEES WHERE Employee_ID = 100;
```


### Select Using Order By function:-

 Order by clause always comes last only 

```
SELECT EMP_ID, FIRST_NAME, SALARY, DEPARTMENT_ID FROM EMPLOYEES WHERE EMP_ID 
order by SALARY DESC
FETCH FIRST 2 ROWS ONLY;	--- ITS fetch 2 row


SELECT EMP_ID, FIRST_NAME, SALARY, DEPARTMENT_ID 
FROM EMPLOYEES 
WHERE EMP_ID 
order by SALARY ASC
FETCH FIRST 1 ROWS ONLY;


SELECT EMPLOYEE_ID, FIRST_NAME, SALARY, DEPARTMENT_ID
FROM EMPLOYEES
OFFSET 2 ROWS FETCH NEXT 1 ROWS ONLY;
```


### OPERATORS:-
```
SELECT * FROM WORKER WHERE FIRST_NAME in ('Vipul', 'Satish');

SELECT * FROM WORKER WHERE FIRST_NAME NOT IN ('Vipul', 'Satish');


SELECT * FROM EMPLOYEES WHERE FIRST_NAME LIKE '%a';    --It finish with a


SELECT * FROM EMPLOYEES WHERE FIRST_NAME LIKE 'A%';    --It start with A

SELECT * FROM EMPLOYEES WHERE FIRST_NAME NOT LIKE 'A%';
```

### Null Operator :- 
```
SELECT * FROM EMPLOYEES WHERE COMMISSION_PCT IS NULL;

SELECT * FROM EMPLOYEES WHERE COMMISSION_PCT IS NOT NULL;
```

### Greater operator:-
```
SELECT * FROM EMPLOYEES WHERE SALARY >1000;
SELECT * FROM EMPLOYEES WHERE SALARY >=1000;
```

### Less than  operator:-
```
SELECT * FROM EMPLOYEES WHERE SALARY <1000;
SELECT * FROM EMPLOYEES WHERE SALARY <=1000;
```

### Between Operator:-
```
SELECT EMP_ID, FIRST_NAME, SALARY, DEPARTMENT_ID FROM EMPLOYEES WHERE EMP_ID between 100 AND 110;

SELECT EMP_ID, FIRST_NAME, SALARY, DEPARTMENT_ID FROM EMPLOYEES WHERE EMP_ID Not between 100 AND 110;
```


