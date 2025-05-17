# <div align="center">  Basic Topic for SQL </div>
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
 
## Example:
For a table with 10,000 rows, if a query includes a filter (WHERE clause) that is expected to match 500 rows, the cardinality of that step would be 500.

##  Cost:-
Definition: Cost is a numerical estimate of the computational resources required to execute a query step

##  Types of SQL:-

DQL, DML, DDL, DCL, TCL : -  </br>
![image](https://github.com/user-attachments/assets/1d4fb2c4-b343-4ea4-82fb-a4b2fd6d1ad3)


##  DQL (Data query Language):-

•	DQL commands are basically SELECT statements.
•	SELECT statements let you query the database to find information in one or more tables, and return the query as a result set. </br>

##  Select how many tables in the database:
```
SELECT * FROM USER_TABLES
SELECT * FROM USER_TAB_COLUMNS
```
DB2 Equivalent
```
sql
SELECT * FROM SYSCAT.TABLES WHERE TABSCHEMA = CURRENT_SCHEMA;

```
## Select all column in table :-
```
SELECT * FROM EMPLOYEES; 
```

## To see Description of the table:- 
```
DESC EMPLOYEES; 
```
DB2 
```
SELECT COLNAME, TYPENAME, LENGTH, SCALE, NULLS
FROM SYSCAT.COLUMNS
WHERE TABNAME = 'EMPLOYEES' AND TABSCHEMA = CURRENT_SCHEMA;
```
## Select custom column in table:-
```
SELECT FIRST_NAME, LAST_NAME, EMP_ID FROM EMPLOYEES;
```

## Select Using where Condition (Selecting particular condition) :-
```
SELECT EMPLOYEE_ID, FIRST_NAME, SALARY, DEPARTMENT_ID FROM EMPLOYEES WHERE Employee_ID = 100;
```


## Select Using Order By function:-

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


## OPERATORS:-
```
SELECT * FROM WORKER WHERE FIRST_NAME in ('Vipul', 'Satish');

SELECT * FROM WORKER WHERE FIRST_NAME NOT IN ('Vipul', 'Satish');


SELECT * FROM EMPLOYEES WHERE FIRST_NAME LIKE '%a';    --It finish with a


SELECT * FROM EMPLOYEES WHERE FIRST_NAME LIKE 'A%';    --It start with A

SELECT * FROM EMPLOYEES WHERE FIRST_NAME NOT LIKE 'A%';
```

## Null Operator :- 
```
SELECT * FROM EMPLOYEES WHERE COMMISSION_PCT IS NULL;

SELECT * FROM EMPLOYEES WHERE COMMISSION_PCT IS NOT NULL;
```

## Greater operator:-
```
SELECT * FROM EMPLOYEES WHERE SALARY >1000;
SELECT * FROM EMPLOYEES WHERE SALARY >=1000;
```

## Less than  operator:-
```
SELECT * FROM EMPLOYEES WHERE SALARY <1000;
SELECT * FROM EMPLOYEES WHERE SALARY <=1000;
```

## Between Operator:-
```
SELECT EMP_ID, FIRST_NAME, SALARY, DEPARTMENT_ID FROM EMPLOYEES WHERE EMP_ID between 100 AND 110;

SELECT EMP_ID, FIRST_NAME, SALARY, DEPARTMENT_ID FROM EMPLOYEES WHERE EMP_ID Not between 100 AND 110;
```



#  DDL (Data Definition Language) :-

## CREATE TABLE :-

We know that a table comprises of rows and columns. 
So while creating tables we have to provide all the information to SQL about the names of the columns, 
type of data to be stored in columns, size of the data etc. Let us now dive into details on how to use CREATE TABLE statement to create tables in SQL.

```
CREATE DATABASE DATABASE_NAME;

CREATE TABLE TABLE1(ID NUMBER(10), NAME VARCHAR2(20), DOB DATE);
```







## ALTER TABLE:-

	 Multiple columns can also be modified at once.

	We cannot modify number to varchar & varchar to number, only size of the variable can change that too increase not decrease.

```
ALTER TABLE T1 ADD(MOBILE NUMBER(10));

ALTER TABLE T1 DROP(DOB);

ALTER TABLE T1 MODIFY (MOBILE VARCHAR2(20));

ALTER TABLE T1 RENAME COLUMN MOBILE TO EMAIL;
```

## RENAME TABLE:-

```
RENAME T1 TO TABLE1;
```

## TRUNCATE TABLE:-
```
TRUNCATE TABLE TABLE1;
```

## DROP TABLE:-
```
DROP TABLE TABLE1;
```
# Difference Between DELETE, TRUNCATE, and DROP  

| Feature | DELETE | TRUNCATE | DROP |
|---------|--------|----------|------|
| **Type** | DML command | DDL command | DDL command |
| **Functionality** | Deletes some or all rows from the table | Deletes all rows from the table | Removes all indexes, privileges, rows, and frees the memory space for other objects |
| **UNDO Space Usage** | Uses UNDO space | Does not use UNDO space | Does not use UNDO space |
| **Space Management** | Released blocks go to the freelist for reuse; does not deallocate space | Deallocates all space used by the table except MINEXTENTS | Unless `PURGE` is specified, does not release space |
| **Foreign Key Constraints** | Can delete data even if FKs are enabled | Cannot TRUNCATE data if FK is enabled; FK needs to be disabled or dropped | Can drop the table using `CASCADE CONSTRAINTS`, which removes associated FKs |
| **Rollback** | Uncommitted DELETE can be rolled back | Cannot be rolled back | Can be rolled back |
| **Commit Requirement** | Requires a commit | No commit needed after execution | No commit required |
| **Trigger Behavior** | Can use with triggers | No trigger fired | No trigger fired |
| **Privilege Granting** | `DELETE` privilege on a table can be granted to another user/role | `TRUNCATE` privilege on a table **cannot** be granted to another user/role | `DROP` privilege on a table **cannot** be granted to another user/role |
| **Execution Permission** | Can be executed if the user has the `DELETE` privilege on the table | Cannot be executed on another user’s schema | Cannot be executed on another user’s schema |
| **Clustered Table Support** | Can work on a table that is part of a cluster | No, must truncate the whole cluster or use `DELETE` or `DROP` | Can work on a table that is part of a cluster |


# DML (DATA MANAPULATION LANGUAGE) :-

## INSERT :-

 ```
------TYPE 1:-
INSERT INTO 
T1(ID, NAME, ADDRESS) 
VALUES(1,’RAMESH’, ‘CHENNAI’);

------TYPE 2:-
INSERT INTO T1 VALUES(1,’RAMESH’,‘CHENNAI’);

-----TYPE 3:-
INSERT ALL
INTO T1(ID,NAME,ADDRESS) VALUES(1,'K','AV')
INTO T1(ID,NAME,ADDRESS) VALUES(2,'M','AT')
INTO T1(ID,NAME,ADDRESS) VALUES(3,'R','AVT')
SELECT * FROM DUAL;
```

## UPDATE VALUES :-
```
UPDATE T1 
SET DEPARTMENT=’NON TRADE’ 
WHERE EMPID = 5986;


MULTIPLE COLUMN UPDATE:-
UPDATE STUDENTS SET 
student_name = 'kumar',
date_of_birth = TO_DATE('11-December-1992', 'DD-MON-YY'), 
email = 'scott@tiger.com',
city = 'Chennai'
WHERE STUDENT_ID = 100;
```


## DELETE VALUES :-

```
DELETE FROM EMP WHERE EMP_ID=1265;
```


## MERGE TABLE:-

•	The merge statement selects data from one or more source tables and updates or inserts it into a target table.

•	It will copy the master to the temp table.

```
MERGE INTO TEMP_TABLE		/*TARGET TABLE*/
USING MASTER_TABLE		/*SOURCE TABLE*/

ON (TEMP.ID=MASTER.ID)

WHEN MATCHED THEN
UPDATE SET TEMP.DEPARTMENT=MASTER.DEPARTMENT, TEMP.LOCATION=MASTER.LOCATION

WHEN NOT MATCHED THEN
INSERT VALUES (TEMP.ID, TEMP.DEPART, TEMP.LOCATION);
```



## TCL (Transaction Control Language):-

```
Commit;->  save the transaction into data file from buffer cache.

SAVEPOINT A -> Temporarily save the transaction that you can roll back to that point whenever you want before commit. 

ROLL BACK A; -> This command restores the database to last committed state.
```
      
It is also used with savepoint command to jump to a savepoint in a transaction.




# SINGLE ROW FUNCTION:-
These functions require one or more input arguments and operate on each row, thereby returning one output value for each row. Argument can be a column, literal or an expression. Single row functions can be used in SELECT statement, WHERE and ORDER BY clause.


## Character Function:-
Handling string function in the query.

## SUBSTR:-
Example: Find Print The First Three Characters Of FIRST_NAME From Worker Table
```
Select SUBSTR(first_name, 1,3) from EMPLOYEES;

SELECT 
FIRST_NAME, 
SUBSTR(FIRST_NAME,-2) 
FROM EMPLOYEES
WHERE ROWNUM <10;
```

The result will be from 2 characters.
FIRST_NAME           SU
-------------------- --
Ellen                en
Sundar               ar
Mozhe                he
David                id
Hermann              nn
Shelli               li
Amit                 it
Elizabeth            th
Sarah                ah

## INSTR:-
Example:-v Find The Position Of The Alphabet (‘A’) In The First Name
```
SELECT INSTR(FIRST_NAME, ‘a’) from EMPLOYEES;
```

FIND how many ‘A’ is in first_name:-
```
SELECT 
FIRST_NAME, 
(length(FIRST_NAME) - LENGTH(replace(HIGHER(first_NAME),'A',''))) HOW_MANY_L
FROM EMPLOYEES;
```

## TRIM:- 
•	To remove BOTH side SPACE values.
```
SELECT TRIM(FIRST_NAME) FROM EMPLOYEES;
```

### Trim only remove first and last character
```
select 
FIRST_NAME, 
TRIM('a' FROM FIRST_NAME) 
FROM EMPLOYEES;
```

Output:-
FIRST_NAME           TRIM('A'FROMFIRST_NA
-------------------- --------------------
Jose Manuel          Jose Manuel         
Peter                Peter               
Clara                Clar                
Shanta               Shant               
Alana                Alan                
Matthew              Matthew             
Jennifer             Jennifer            
Eleni                Eleni

## RTRIM:-   
•	To remove right side arguments values.
Example:- To remove N in first name column in right side.

```
SELECT RTRIM(FIRST_NAME, 'N') from WORKER;
```

## LTRIM:-   
•	To remove LEFT side given arguments values.
Example:- To remove N in first name column in right side.
```
SELECT LTRIM(FIRST_NAME, 'A') from WORKER;

SELECT LTRIM('**RA**JE**SH**','*'), RTRIM('**RA**JE**SH**','*') FROM DUAL;
```
L_TRIM       R_TRIM      
------------ ------------
RA**JE**SH** **RA**JE**SH


Below statement is wrong 
```
SELECT TRIM('**RA**JE**SH**','*') FROM DUAL;
```

## LPAD:-   
•	To Add Left side arguments values.
Example:- To add N in first name column in right side.
```
SELECT LPAD(FIRST_NAME, '10', '0') from EMPLOYEES;
```


## LENGTH:-
•	Find length of the string.
Example:- find the unique value of the department & there lengths
```
SELECT LENGTH(DEPARTMENT), department FROM WORKER;
```

### Find how many A or a letters are there in the columns:-
```
SELECT FIRST_NAME,
  (LENGTH(UPPER(FIRST_NAME)) - LENGTH(REPLACE(UPPER(FIRST_NAME), 'A', ''))) AS count_of_A
FROM EMPLOYEES;
```


## CONCAT:-
•	combain two words or string.
```
SELECT CONCAT(FIRST_NAME,LAST_NAME) FROM EMPLOYEES;
SELECT FIRST_NAME||'SENTHIL'|| PHONE_NUMBER||SALARY FROM EMPLOYEES;
```

## CASE MANIPULULICATION:-
```
-----UPPER 
SELECT UPPER(FIRST_NAME) FROM EMPLOYEES;

----- LOWER
SELECT LOWER(FIRST_NAME) FROM EMPLOYEES;

----- INITCAP
SELECT INITCAP(FIRST_NAME) FROM EMPLOYEES;

```


## TRANSLATE & REPLACE:-
•	Translate will change each & every variable.
•	Replace will only change given EXACT variable.
```
SELECT 
REPLACE ('INDIA', 'IN','XY'), TRANSLATE('INDIA', 'IN','XY')
FROM DUAL;


SELECT REPLACE(FIRST_NAME, 'a', 'A') FROM WORKER;
```
In above query all small a will replace A 

TRANSLATE('INDIA','IN','XY')	REPLACE('INDIA','IN','XY')
XYDXA	XYDIA

```
SELECT 
TRANSLATE('INDIA', 'I','XY'), 
REPLACE ('INDIA', 'I','XY') 
FROM DUAL;
```

TRANS REPLACE
----- -------
XNDXA XYNDXYA

```
SELECT TRANSLATE('123456789', '598','#@'), 
REPLACE ('123456789', '54','@@') FROM DUAL;
TRANSLATE('123456789','59','#@')	REPLACE('123456789','54','@@')
1234#67@	123456789


SELECT REPLACE('INDIA','I','57'), TRANSLATE('INDIA','IN','57') FROM DUAL;
```

 
# Regular Expression :-

Key Features of Regular Expressions in Oracle
1.	Pattern Matching: Search for strings matching a specific pattern.
2.	Extracting Substrings: Extract specific parts of a string that match a pattern.
3.	Replacing Strings: Replace parts of a string based on a pattern.
4.	Splitting Strings: Break strings into parts using a pattern as the delimiter.

   
## 1. REGEXP_LIKE:-
Purpose: Matches a string against a regular expression pattern (similar to LIKE, but more powerful).
Example: Find employees whose names start with J and end with n:

```
SELECT *
FROM EMPLOYEES
WHERE REGEXP_LIKE(NAME, '^J.*n$');
```
## 2. REGEXP_SUBSTR:-

Purpose: Extracts the substring that matches a regular expression.
```
SELECT REGEXP_SUBSTR('Address 123 Main St.', '\d+', 1, 1) AS first_number
FROM DUAL;
```
Extract the domain (e.g., gmail.com) from an email address:
```
SELECT REGEXP_SUBSTR(EMAIL, '@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}', 1, 1) AS domain
FROM USERS;
```

## 3. REGEXP_REPLACE:-

•  Purpose: Replaces substrings matching a pattern with another string.

Example: Replace all non-numeric characters in a string with an empty string
```
SELECT REGEXP_REPLACE('Phone: (123) 456-7890', '[^0-9]', '') AS digits_only
FROM DUAL;
```
Replace Multiple Spaces with a Single Space
```
SELECT REGEXP_REPLACE('This   is   a   test.', '\s+', ' ') AS normalized_text
FROM DUAL;
```



## 4. REGEXP_INSTR:-
Purpose: Returns the starting position of a substring that matches a pattern.
Example: Find the starting position of the first numeric sequence in a string
```
SELECT REGEXP_INSTR('ID: ABC123XYZ', '\d+', 1, 1) AS position
FROM DUAL;
```

# Regex Patterns and Metacharacters  

Regular expressions use special characters (metacharacters) to define patterns.  


| Metacharacter | Description | Example |
|--------------|-------------|---------|
| `.` | Matches any single character. | `A.B` matches `ACB`, `A9B`. |
| `*` | Matches 0 or more occurrences of the preceding character. | `A*` matches `A`, `AA`, `AAA`. |
| `+` | Matches 1 or more occurrences of the preceding character. | `A+` matches `A`, `AA`, `AAA`. |
| `?` | Matches 0 or 1 occurrence of the preceding character. | `AB?C` matches `AC`, `ABC`. |
| `^` | Matches the beginning of the string. | `^A` matches strings starting with `A`. |
| `$` | Matches the end of the string. | `Z$` matches strings ending with `Z`. |
| `[ ]` | Matches any one character in the set. | `[A-Z]` matches any uppercase letter. |
| `[^ ]` | Matches any character not in the set. | `[^0-9]` matches non-numeric characters. |
| `{n,m}` | Matches between `n` and `m` occurrences. | `A{2,4}` matches `AA`, `AAA`, `AAAA`. |
| `\d` | Matches any digit (equivalent to `[0-9]`). | `\d+` matches `123`. |
| `\w` | Matches any word character (letters, digits, or `_`). | `\w+` matches `hello123`. |
| `\s` | Matches any whitespace character. | `\s` matches spaces, tabs, etc. |



### To saprate alpha and numeric :- 
```
SELECT HIRE_DATE, TRANSLATE(HIRE_DATE,'-0123456789', ' ')AS ALPHA, TRANSLATE(HIRE_DATE,'ABCDEFGHIJKLMNOPQRSTUVWXYZ-', ' ')AS "NUMBER" FROM EMPLOYEES;

SELECT  HIRE_DATE, REGEXP_REPLACE(HIRE_DATE, '[^A-Z]', '') ALPHA from EMPLOYEES;
```

HIRE_DATE	ALPHA
17-JUN-87	JUN
21-SEP-89	SEP
13-JAN-93	JAN
03-JAN-90	JAN
21-MAY-91	MAY

To separate each character:-  

select  country_name, REGEXP_REPLACE(country_name, '(.)', '\1 ') from countries
COUNTRY_NAME	REGEXP_REPLACE(COUNTRY_NAME,'(.)','\1')
Argentina	A r g e n t i n a
Australia	A u s t r a l i a
Belgium	B e l g i u m
Brazil	B r a z i l


### To Remove 2 or more space from the gap :-
```
SELECT REGEXP_REPLACE('the web development tutorial w3resource.com', '( ){2,}', ' ') "REGEXP_REPLACE" FROM DUAL;
```




### SPECIAL CHAR REMOVE:-
^ in this setup it allows only numeric and character other then that it will skip.
```
REGEXP_REPLACE(TAC_RTA_CODE, '[^0-9A-Za-z]', '')
```
