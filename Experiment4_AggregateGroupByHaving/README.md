# Experiment 4: Aggregate Functions, Group By and Having Clause

## AIM
To study and implement aggregate functions, GROUP BY, and HAVING clause with suitable examples.

## THEORY

### Aggregate Functions
These perform calculations on a set of values and return a single value.

- **MIN()** – Smallest value  
- **MAX()** – Largest value  
- **COUNT()** – Number of rows  
- **SUM()** – Total of values  
- **AVG()** – Average of values

**Syntax:**
```sql
SELECT AGG_FUNC(column_name) FROM table_name WHERE condition;
```
### GROUP BY
Groups records with the same values in specified columns.
**Syntax:**
```sql
SELECT column_name, AGG_FUNC(column_name)
FROM table_name
GROUP BY column_name;
```
### HAVING
Filters the grouped records based on aggregate conditions.
**Syntax:**
```sql
SELECT column_name, AGG_FUNC(column_name)
FROM table_name
GROUP BY column_name
HAVING condition;
```

**Question 1**
```
What is the average dosage prescribed for each medication?

Sample tablePrescriptions Table

Medication     AvgDosage
-------------  ----------
Ciprofloxacin  500.0
Doxorubicin    60.0
Ibuprofen      400.0
Levothyroxine  50.0
Lisinopril     10.0
MMR            0.5
Pending        0.0
Prenatal vita  1.0
Sertraline     50.0
Topiramate     25.0
```

```
SELECT
  Medication,
  AVG(Dosage) AS AvgDosage
FROM
  Prescriptions
GROUP BY
  Medication;

```

**Output:**


![image](https://github.com/user-attachments/assets/00d64b6f-75de-41bf-89ec-3c22e2ce3377)

**Question 2**
---
How many patients are there in each city?

Sample table: Patients Table
```
Address     TotalPatients
----------  -------------
Berlin      3
Chicago     4
Mexico      3
```
```
select Address,count(*)
as TotalPatients
from Patients
group by Address
```

**Output:**


![image](https://github.com/user-attachments/assets/2faa2ccd-b632-44fa-99e8-a93ece9a6901)



**Question 3**
---
Write a SQL Query to find how many medications are prescribed for each patient?

Sample table:MedicalRecords Table
```
PatientID   AvgMedications
----------  --------------
4           5
6           1
7           1
8           3
```
```
SELECT PatientID,COUNT(*) AS 
AvgMedications
FROM MedicalRecords
GROUP BY PatientID;
```

**Output:**


![image](https://github.com/user-attachments/assets/6d2109cb-841e-45ff-b522-84899ec7db53)


**Question 4**
---
Write a SQL query to find the maximum purchase amount.

Sample table: orders
```
ord_no      purch_amt   ord_date    customer_id  salesman_id

----------  ----------  ----------  -----------  -----------

70001       150.5       2012-10-05  3005         5002

70009       270.65      2012-09-10  3001         5005

70002       65.26       2012-10-05  3002         5001
```
```
SELECT
  MAX(purch_amt) AS MAXIMUM
FROM
  orders;
```

**Output:**


![image](https://github.com/user-attachments/assets/cd12696e-044f-447a-83a6-c2137711914f)



**Question 5**
---
Write a SQL query to find the total income of employees aged 40 or above.

Table: employee
```
name        type
----------  ----------
id          INTEGER
name        TEXT
age         INTEGER
city        TEXT
income      INTEGER
```
```
SELECT
  SUM(income) AS total_income
FROM
  employee
WHERE
  age >= 40;
```

**Output:**


![image](https://github.com/user-attachments/assets/2027b827-a195-4462-ac63-3a4417c3a832)


**Question 6**
---
Write a SQL query to find the number of employees whose age is greater than 32.

Sample table: employee

```
SELECT
  COUNT(*) AS COUNT
FROM
  employee
WHERE
  age > 32;
```

**Output:**


![image](https://github.com/user-attachments/assets/ca36d365-20b2-4332-ba6e-ec09c7263473)

**Question 7**
---
Write a SQL query to find the average length of names for people living in Chennai?

Table: customer
```
name        type
----------  ----------
id          INTEGER
name        TEXT   
city        TEXT
email       TEXT
phone       INTEGER
```
```
SELECT
  AVG(LENGTH(name)) AS avg_name_length
FROM
  customer
WHERE
  city = 'Chennai';
```

**Output:**


![image](https://github.com/user-attachments/assets/47345d5e-3e6b-406f-b1be-09adeb706616)


**Question 8**
---
Write the SQL query that accomplishes the grouping of data by joining date (jdate), calculates the maximum work hours for each date, and excludes dates where the maximum work hour is not greater than 12.

Sample table: employee1
```
jdate       MAX(workhour)
----------  -------------
2004.0      15
2006.0      15
```
```
SELECT
  jdate,
  MAX(workhour) AS "MAX(workhour)"
FROM
  employee1
GROUP BY
  jdate
HAVING
  MAX(workhour) > 12;
```

**Output:**


![image](https://github.com/user-attachments/assets/23997459-e621-4df3-a43d-8a91e46850e2)


**Question 9**
---
Write the SQL query that achieves the grouping of data by occupation, calculates the total work hours for each occupation, and excludes occupations where the total work hour sum is not greater than 20.

Sample table: employee1
```
occupation  SUM(workhour)
----------  -------------
Business    30
Doctor      30
Engineer    24
Teacher     27
```
```
SELECT
  occupation,
  SUM(workhour) AS "SUM(workhour)"
FROM
  employee1
GROUP BY
  occupation
HAVING
  SUM(workhour) > 20;
```

**Output:**


![image](https://github.com/user-attachments/assets/58f7530d-2e34-499d-8bb3-fdacc54b271a)


**Question 10**
---
Write the SQL query that achieves the grouping of data by occupation, calculates the average work hours for each occupation, and includes only those occupations where the average work hour falls between 10 and 12.

Sample table: employee1
```
Result
occupation  AVG(workhour)
----------  -------------
Business    10.0
Engineer    12.0
```
```
SELECT
  occupation,
  AVG(workhour) AS "AVG(workhour)"
FROM
  employee1
GROUP BY
  occupation
HAVING
  AVG(workhour) BETWEEN 10 AND 12;
```

**Output:**


![image](https://github.com/user-attachments/assets/9bebc555-de90-463e-ae8c-6277bc2fb678)




## RESULT
Thus, the SQL queries to implement aggregate functions, GROUP BY, and HAVING clause have been executed successfully.

