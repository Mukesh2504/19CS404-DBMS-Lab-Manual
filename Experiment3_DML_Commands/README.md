# Experiment 3: DML Commands

## AIM
To study and implement DML (Data Manipulation Language) commands.

## THEORY

### 1. INSERT INTO
Used to add records into a relation.
These are three type of INSERT INTO queries which are as
A)Inserting a single record
**Syntax (Single Row):**
```sql
INSERT INTO table_name (field_1, field_2, ...) VALUES (value_1, value_2, ...);
```
**Syntax (Multiple Rows):**
```sql
INSERT INTO table_name (field_1, field_2, ...) VALUES
(value_1, value_2, ...),
(value_3, value_4, ...);
```
**Syntax (Insert from another table):**
```sql
INSERT INTO table_name SELECT * FROM other_table WHERE condition;
```
### 2. UPDATE
Used to modify records in a relation.
Syntax:
```sql
UPDATE table_name SET column1 = value1, column2 = value2 WHERE condition;
```
### 3. DELETE
Used to delete records from a relation.
**Syntax (All rows):**
```sql
DELETE FROM table_name;
```
**Syntax (Specific condition):**
```sql
DELETE FROM table_name WHERE condition;
```
### 4. SELECT
Used to retrieve records from a table.
**Syntax:**
```sql
SELECT column1, column2 FROM table_name WHERE condition;
```
**Question 1**
--
Increase the reorder level by 30% for products from 'Food' category having quantity in stock less than 50% of existing reorder level in the products table
name               type
--------------  ----------
product_id         INT
product_name       VARCHAR(10)
category           VARCHAR(50)
cost_price         DECIMAL(10)
sell_price         DECIMAL(10)
reorder_lvl        INT
quantity              INT
supplier_id           INT
For example:

Test	Result
select changes();
changes()
----------
4


```sql
UPDATE products
SET reorder_lvl = reorder_lvl * 1.30
WHERE category = 'Food'
  AND quantity < reorder_lvl * 0.50;
```

**Output:**

<img width="1483" height="286" alt="image" src="https://github.com/user-attachments/assets/0006f0d2-2f77-48cd-9311-2dfc1ee93f9e" />


**Question 2**
---
<img width="1188" height="526" alt="image" src="https://github.com/user-attachments/assets/b2af5de5-5fdc-48ad-978e-eee96dfe9209" />

```sql
UPDATE purchases
SET
    per_unit_price = 25,
    total_price = 25 * quantity
WHERE
    purchase_date = '2022-08-15'
    AND product_id = 12;
```

**Output:**

<img width="1900" height="425" alt="image" src="https://github.com/user-attachments/assets/387a5e3d-a797-4f96-9768-9e0a4df4ac46" />


**Question 3**
---
Write a SQL statement to change the first_name column of employees table with 'John' for those employees whose department_id is 80 and gets a commission_pct below 0.35.

Employees table

---------------
employee_id
first_name
last_name
email
phone_number
hire_date
job_id
salary
commission_pct
manager_id
department_id
For example:

Test	Result
SELECT * FROM EMPLOYEES WHERE DEPARTMENT_ID=80 AND COMMISSION_PCT=.25;
EMPLOYEE_ID  FIRST_NAME  LAST_NAME   EMAIL       PHONE_NUMBER        HIRE_DATE   JOB_ID      SALARY      COMMISSION_PCT  MANAGER_ID  DEPARTMENT_ID
-----------  ----------  ----------  ----------  ------------------  ----------  ----------  ----------  --------------  ----------  -------------
151          John        Bernstein   DBERNSTE    011.44.1344.345268  8/7/87      SA_REP      9500        0.25            145         80
152          John        Hall        PHALL       011.44.1344.478968  8/8/87      SA_REP      9000        0.25            145         80
161          John        Sewall      SSEWALL     011.44.1345.529268  8/17/87     SA_REP      7000        0.25            146         80
162          John        Vishney     CVISHNEY    011.44.1346.129268  8/18/87     SA_REP      10500       0.25            147         80
168          John        Ozer        LOZER       011.44.1343.929268  8/24/87     SA_REP      11500       0.25            148         80
175          John        Hutton      AHUTTON     011.44.1644.429266  8/31/87     SA_REP      8800        0.25            149         80



```sql
UPDATE employees
SET first_name = 'John'
WHERE department_id = 80
AND commission_pct < 0.35;
```

**Output:**

<img width="1899" height="335" alt="image" src="https://github.com/user-attachments/assets/167626af-c558-411f-bf07-53bc7db51870" />


**Question 4**
---
Write a SQL statement to Update the hire_date of employees in department 50 to 2024-01-24.

Employees table

---------------
employee_id
first_name
last_name
email
phone_number
hire_date
job_id
salary
commission_pct
manager_id
department_id
For example:

Test	Result
SELECT EMPLOYEE_ID, FIRST_NAME, HIRE_DATE FROM EMPLOYEES 
WHERE DEPARTMENT_ID=50 LIMIT 3;
EMPLOYEE_ID  FIRST_NAME  HIRE_DATE
-----------  ----------  ----------
120          Matthew     2024-01-24
121          Adam        2024-01-24
122          Payam       2024-01-24


```sql
UPDATE employees
SET hire_date = '2024-01-24'
WHERE department_id = 50;
```

**Output:**

<img width="1227" height="304" alt="image" src="https://github.com/user-attachments/assets/51038402-bc55-4579-a18c-e7f1d757f7a1" />


**Question 5**
---
Write a SQL statement to change the email column of employees table with 'Unavailable' for all employees in employees table.

Employees table

---------------
employee_id
first_name
last_name
email
phone_number
hire_date
job_id
salary
commission_pct
manager_id
department_id
 

For example:

Test	Result
SELECT EMPLOYEE_ID,FIRST_NAME,EMAIL FROM EMPLOYEES LIMIT 2;
EMPLOYEE_ID  FIRST_NAME  EMAIL
-----------  ----------  -----------
100          Steven      Unavailable
101          Neena       Unavailable


```sql
UPDATE employees
SET email = 'Unavailable';
```

**Output:**

<img width="1366" height="486" alt="image" src="https://github.com/user-attachments/assets/b6a42d04-8f9c-4fb9-a953-e34ab0813a86" />


**Question 6**
---
Write a SQL query to Delete a Specific Surgery whose ID is 3

Sample table: Surgeries

attributes: surgery_id, patient_id, surgeon_id, surgery_date
For example:

Test	Result
SELECT * FROM surgeries;
surgery_id  patient_id  surgeon_id  surgery_date
----------  ----------  ----------  ------------
1           1           1           2024-01-15
2           2           2           2024-02-28
3           3           3           2024-03-25
surgery_id  patient_id  surgeon_id  surgery_date
----------  ----------  ----------  ------------
1           1           1           2024-01-15
2           2           2           2024-02-28

```sql
DELETE FROM Surgeries
WHERE surgery_id = 3;
```

**Output:**

<img width="1396" height="465" alt="image" src="https://github.com/user-attachments/assets/7b69056d-3178-42d8-85e8-4a74144bfc08" />


**Question 7**
---
Write a SQL query to Delete customers from 'customer' table where 'OPENING_AMT' is between 4000 and 6000.

Sample table: Customer

+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+  
|CUST_CODE  | CUST_NAME   | CUST_CITY   | WORKING_AREA | CUST_COUNTRY | GRADE | OPENING_AMT | RECEIVE_AMT | PAYMENT_AMT |OUTSTANDING_AMT| PHONE_NO     | AGENT_CODE |
+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+
| C00013    | Holmes      | London      | London       | UK           |     2 |     6000.00 |     5000.00 |     7000.00 |       4000.00 | BBBBBBB      | A003       |
| C00001    | Micheal     | New York    | New York     | USA          |     2 |     3000.00 |     5000.00 |     2000.00 |       6000.00 | CCCCCCC      | A008       |
| C00020    | Albert      | New York    | New York     | USA          |     3 |     5000.00 |     7000.00 |     6000.00 |       6000.00 | BBBBSBB      | A008       |
For example:

Test	Result
SELECT * FROM customer
WHERE OPENING_AMT BETWEEN 4000 AND 6000;
CUST_CODE   CUST_NAME   CUST_CITY   WORKING_AREA  CUST_COUNTRY  GRADE       OPENING_AMT  RECEIVE_AMT  PAYMENT_AMT  OUTSTANDING_AMT  PHONE_NO    AGENT_CODE
----------  ----------  ----------  ------------  ------------  ----------  -----------  -----------  -----------  ---------------  ----------  ----------
C00013      Holmes      London      London        UK            2           6000         5000         7000         4000             BBBBBBB     A003
C00020      Albert      New York    New York      USA           3           5000         7000         6000         6000             BBBBSBB     A008
C00025      Ravindran   Bangalore   Bangalore     India         2           5000         7000         4000         8000             AVAVAVA     A011
C00024      Cook        London      London        UK            2           4000         9000         7000         6000             FSDDSDF     A006
C00015      Stuart      London      London        UK            1           6000         8000         3000         11000            GFSGERS     A003
C00002      Bolt        New York    New York      USA           3           5000         7000         9000         3000             DDNRDRH     A008
C00004      Winston     Brisban     Brisban       Australia     1           5000         8000         7000         6000             AAAAAAA     A005
C00023      Karl        London      London        UK            0           4000         6000         7000         3000             AAAABAA     A006
C00010      Charles     Hampshair   Hampshair     UK            3           6000         4000         5000         5000             MMMMMMM     A009
C00012      Steven      San Jose    San Jose      USA           1           5000         7000         9000         3000             KRFYGJK     A012


```sql
DELETE FROM customer
WHERE OPENING_AMT BETWEEN 4000 AND 6000;
```

**Output:**

<img width="1884" height="389" alt="image" src="https://github.com/user-attachments/assets/4a6db529-bebc-45ea-92e5-201566aa3554" />


**Question 8**
---
Write a SQL query to Delete customers from 'customer' table where 'CUST_NAME' contains the substring 'Holmes'.

Sample table: Customer

+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+  
|CUST_CODE  | CUST_NAME   | CUST_CITY   | WORKING_AREA | CUST_COUNTRY | GRADE | OPENING_AMT | RECEIVE_AMT | PAYMENT_AMT |OUTSTANDING_AMT| PHONE_NO     | AGENT_CODE |
+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+
| C00013    | Holmes      | London      | London       | UK           |     2 |     6000.00 |     5000.00 |     7000.00 |       4000.00 | BBBBBBB      | A003       |
| C00001    | Micheal     | New York    | New York     | USA          |     2 |     3000.00 |     5000.00 |     2000.00 |       6000.00 | CCCCCCC      | A008       |
| C00020    | Albert      | New York    | New York     | USA          |     3 |     5000.00 |     7000.00 |     6000.00 |       6000.00 | BBBBSBB      | A008       |
For example:

Test	Result
select changes();
CUST_CODE   CUST_NAME   CUST_CITY   WORKING_AREA  CUST_COUNTRY  GRADE       OPENING_AMT  RECEIVE_AMT  PAYMENT_AMT  OUTSTANDING_AMT  PHONE_NO    AGENT_CODE
----------  ----------  ----------  ------------  ------------  ----------  -----------  -----------  -----------  ---------------  ----------  ----------
C00013      Holmes      London      London        UK            2           6000         5000         7000         4000             BBBBBBB     A003
changes()
----------
1

```sql
DELETE FROM customer
WHERE CUST_NAME LIKE '%Holmes%';
```

**Output:**

<img width="1862" height="351" alt="image" src="https://github.com/user-attachments/assets/0b68f8e0-5a76-4fc1-a63e-07d14bef8358" />


**Question 9**
---
Write a SQL query to Delete customers with 'GRADE' 3 or 'AGENT_CODE' 'A008' whose 'OUTSTANDING_AMT' is less than 5000

Sample table: Customer

+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+  
|CUST_CODE  | CUST_NAME   | CUST_CITY   | WORKING_AREA | CUST_COUNTRY | GRADE | OPENING_AMT | RECEIVE_AMT | PAYMENT_AMT |OUTSTANDING_AMT| PHONE_NO     | AGENT_CODE |
+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+
| C00013    | Holmes      | London      | London       | UK           |     2 |     6000.00 |     5000.00 |     7000.00 |       4000.00 | BBBBBBB      | A003       |
| C00001    | Micheal     | New York    | New York     | USA          |     2 |     3000.00 |     5000.00 |     2000.00 |       6000.00 | CCCCCCC      | A008       |
| C00020    | Albert      | New York    | New York     | USA          |     3 |     5000.00 |     7000.00 |     6000.00 |       6000.00 | BBBBSBB      | A008       |
For example:

Test	Result
select changes();
changes()
----------
1


```sql
DELETE FROM customer
WHERE (GRADE = 3 OR AGENT_CODE = 'A008')
AND OUTSTANDING_AMT < 5000;
```

**Output:**

<img width="1835" height="276" alt="image" src="https://github.com/user-attachments/assets/122ef9f1-fe8a-4e08-b8c0-c046fe176b73" />


**Question 10**
---
Write a SQL query to Delete customers from 'customer' table where 'GRADE' is not equal to 3.

 
Sample table: Customer

+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+  
|CUST_CODE  | CUST_NAME   | CUST_CITY   | WORKING_AREA | CUST_COUNTRY | GRADE | OPENING_AMT | RECEIVE_AMT | PAYMENT_AMT |OUTSTANDING_AMT| PHONE_NO     | AGENT_CODE |
+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+
| C00013    | Holmes      | London      | London       | UK           |     2 |     6000.00 |     5000.00 |     7000.00 |       4000.00 | BBBBBBB      | A003       |
| C00001    | Micheal     | New York    | New York     | USA          |     2 |     3000.00 |     5000.00 |     2000.00 |       6000.00 | CCCCCCC      | A008       |
| C00020    | Albert      | New York    | New York     | USA          |     3 |     5000.00 |     7000.00 |     6000.00 |       6000.00 | BBBBSBB      | A008       |
For example:

Test	Result
select distinct(grade)from customer;
GRADE
----------
2
3
1
0
GRADE
----------
3

```sql
DELETE FROM customer
WHERE GRADE <> 3;
```

**Output:**

<img width="774" height="591" alt="image" src="https://github.com/user-attachments/assets/5949a082-c4c5-486b-8636-3dee3764a131" />


## RESULT
Thus, the SQL queries to implement DML commands have been executed successfully.
