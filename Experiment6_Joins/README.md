# Experiment 6: Joins

## AIM
To study and implement different types of joins.

## THEORY

SQL Joins are used to combine records from two or more tables based on a related column.

### 1. INNER JOIN
Returns records with matching values in both tables.

**Syntax:**
```sql
SELECT columns
FROM table1
INNER JOIN table2
ON table1.column = table2.column;
```

### 2. LEFT JOIN
Returns all records from the left table, and matched records from the right.

**Syntax:**

```sql
SELECT columns
FROM table1
LEFT JOIN table2
ON table1.column = table2.column;
```
### 3. RIGHT JOIN
Returns all records from the right table, and matched records from the left.

**Syntax:**

```sql
SELECT columns
FROM table1
RIGHT JOIN table2
ON table1.column = table2.column;
```
### 4. FULL OUTER JOIN
Returns all records when there is a match in either left or right table.

**Syntax:**

```sql
SELECT columns
FROM table1
FULL OUTER JOIN table2
ON table1.column = table2.column;
```

**Question 1**
--
<img width="1289" height="751" alt="image" src="https://github.com/user-attachments/assets/b0ffdd7e-f41d-41b6-ba6b-fb5bb1ab0299" />


```sql
SELECT 
    p.first_name AS patient_name
FROM 
    patients p
INNER JOIN 
    doctors d 
ON 
    p.doctor_id = d.doctor_id
WHERE 
    d.first_name = 'Emily'
    AND d.last_name = 'Johnson'
    AND p.discharge_date IS NOT NULL;

```

**Output:**

<img width="1173" height="498" alt="image" src="https://github.com/user-attachments/assets/26e5dda6-7c68-4a0d-8e5b-3e8f1db920fc" />

**Question 2**
---
<img width="1292" height="817" alt="image" src="https://github.com/user-attachments/assets/210a1ded-686d-4a82-b479-68155e87f3e6" />


```sql
SELECT 
    p.first_name AS patient_name, 
    a.*
FROM 
    patients p
INNER JOIN 
    appointments a 
ON 
    p.patient_id = a.patient_id;

```

**Output:**

<img width="1303" height="672" alt="image" src="https://github.com/user-attachments/assets/1562a171-9b7f-453e-a441-3098de47aaa2" />

**Question 3**
---
<img width="1283" height="863" alt="image" src="https://github.com/user-attachments/assets/a8aad79c-480b-4a46-9222-c95b10a4e6d2" />


```sql
SELECT 
    p.first_name, 
    s.*
FROM 
    patients p
INNER JOIN 
    surgeries s 
ON 
    p.patient_id = s.patient_id
WHERE 
    p.date_of_birth > '1990-01-01';

```

**Output:**

<img width="1282" height="498" alt="image" src="https://github.com/user-attachments/assets/2ccee66b-4161-4c0c-a863-b9800f4b1c80" />


**Question 4**
---
<img width="1277" height="560" alt="image" src="https://github.com/user-attachments/assets/f104bc1f-1053-4cf0-bc6e-60df89741f76" />


```sql
SELECT 
    c.cust_name, 
    s.commission
FROM 
    customer c
LEFT JOIN 
    salesman s 
ON 
    c.salesman_id = s.salesman_id;

```

**Output:**

<img width="975" height="944" alt="image" src="https://github.com/user-attachments/assets/264b67b2-4a8e-45f4-b4f9-8be2ca956d18" />


**Question 5**
---
<img width="1263" height="393" alt="image" src="https://github.com/user-attachments/assets/788ec24d-ec47-42ef-baf2-7d3023db5524" />


```sql
SELECT 
    s.name
FROM 
    salesman s
LEFT JOIN 
    customer c 
ON 
    s.salesman_id = c.salesman_id
WHERE 
    c.city = 'New York';

```

**Output:**

<img width="986" height="498" alt="image" src="https://github.com/user-attachments/assets/7924b084-030a-4753-b6d9-a24185a5097a" />


**Question 6**
---
<img width="1333" height="783" alt="image" src="https://github.com/user-attachments/assets/37e9e9d2-60a8-4510-90e6-f045ac389217" />


```sql
SELECT 
    c.cust_name AS "Customer Name",
    c.city AS "city",
    s.name AS "Salesman",
    s.city AS "city",
    s.commission
FROM 
    customer c
JOIN 
    salesman s
ON 
    c.salesman_id = s.salesman_id
WHERE 
    c.city <> s.city
    AND s.commission > 0.12;

```

**Output:**

<img width="1294" height="737" alt="image" src="https://github.com/user-attachments/assets/2cf2ebca-156d-4185-aeed-8062b01b118c" />


**Question 7**
---
<img width="1315" height="974" alt="image" src="https://github.com/user-attachments/assets/ccd40444-0abf-44c5-9ece-829781b040e3" />



```sql
SELECT 
    c.cust_name AS "Customer Name",
    c.city,
    s.name AS "Salesman",
    s.commission
FROM 
    customer c
INNER JOIN 
    salesman s ON c.salesman_id = s.salesman_id
WHERE 
    s.commission > 0.12;
```

**Output:**

<img width="1289" height="862" alt="image" src="https://github.com/user-attachments/assets/abe387b9-3d85-464d-acf7-a7fe98960d5d" />


**Question 8**
---

```sql
SELECT 
    c.cust_name AS "Customer Name",
    c.city AS "city",
    s.name AS "Salesman",
    s.commission AS "commission"
FROM 
    customer c
INNER JOIN 
    salesman s
ON 
    c.salesman_id = s.salesman_id
WHERE 
    s.commission > 0.12;

```

**Output:**

<img width="1307" height="895" alt="image" src="https://github.com/user-attachments/assets/9ed27ded-6ed7-4165-a125-f53de800277a" />


**Question 9**
---
<img width="1298" height="936" alt="image" src="https://github.com/user-attachments/assets/da5f9457-5984-4b59-835b-92afb3481c23" />


```sql
SELECT 
    c.cust_name AS "cust_name",
    c.city AS "city",
    c.grade AS "grade",
    s.name AS "Salesman",
    s.city AS "city"
FROM 
    customer c
JOIN 
    salesman s
ON 
    c.salesman_id = s.salesman_id
ORDER BY 
    c.customer_id ASC;

```

**Output:**

<img width="1321" height="906" alt="image" src="https://github.com/user-attachments/assets/3ac37dba-d345-40f4-8b55-5704246071dd" />


**Question 10**
---
<img width="1324" height="912" alt="image" src="https://github.com/user-attachments/assets/2f42479d-da36-4864-9e20-a7762f1e9637" />


```sql
SELECT 
    c.cust_name AS "cust_name",
    c.city AS "city",
    c.grade AS "grade",
    s.name AS "Salesman",
    s.city AS "city"
FROM 
    customer c
JOIN 
    salesman s
ON 
    c.salesman_id = s.salesman_id
WHERE 
    c.grade < 300
ORDER BY 
    c.customer_id ASC;

```

**Output:**

<img width="1306" height="823" alt="image" src="https://github.com/user-attachments/assets/690f4630-5fe9-4ab3-b024-8ae3f8cca3ab" />



## RESULT
Thus, the SQL queries to implement different types of joins have been executed successfully.
