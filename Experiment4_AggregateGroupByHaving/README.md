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
--
<img width="1231" height="696" alt="image" src="https://github.com/user-attachments/assets/b067d17a-912a-44f5-87ae-197f90a0a75e" />


```sql
SELECT 
    PatientID,
    COUNT(PrescriptionID) AS TotalMedications
FROM 
    Prescriptions
GROUP BY 
    PatientID;
```

**Output:**

<img width="1240" height="845" alt="image" src="https://github.com/user-attachments/assets/50b8955b-130b-4b4f-9eec-9c58d44da68d" />


**Question 2**
---
<img width="1216" height="669" alt="image" src="https://github.com/user-attachments/assets/1535acd8-d0e5-4734-b424-e5c0c6332379" />


```sql
SELECT 
    PatientID,
    COUNT(*) AS TotalAppointments
FROM 
    Appointments
GROUP BY 
    PatientID;
```

**Output:**

<img width="1023" height="691" alt="image" src="https://github.com/user-attachments/assets/bd822661-42da-40ea-81bb-4806faeb35e0" />


**Question 3**
---
<img width="1163" height="624" alt="image" src="https://github.com/user-attachments/assets/9617d181-671f-47af-8f7c-803f26917e2a" />

```sql
SELECT 
    Specialty,
    Gender,
    COUNT(*) AS TotalDoctors
FROM 
    Doctors
GROUP BY 
    Specialty, Gender
ORDER BY 
    Specialty, Gender;
```

**Output:**

<img width="1126" height="757" alt="image" src="https://github.com/user-attachments/assets/2dc82c11-9213-4645-a8ea-bac83a862804" />


**Question 4**
---
<img width="1213" height="427" alt="image" src="https://github.com/user-attachments/assets/d2d29c4a-22f4-44ac-9679-e07f3c1ff67d" />

```sql
SELECT 
    SUM(inventory) AS total_available_amount
FROM 
    fruits
WHERE 
    price > 0.5;
```

**Output:**
<img width="1222" height="624" alt="image" src="https://github.com/user-attachments/assets/69b10bd5-1e12-4a17-81f3-1c61ea2bdb20" />


**Question 5**
---
<img width="964" height="627" alt="image" src="https://github.com/user-attachments/assets/680dcb7b-b1e7-4ff4-af50-b091b05c02e4" />


```sql
SELECT 
    name AS fruit_name,
    inventory AS lowest_quantity
FROM 
    fruits
ORDER BY 
    inventory ASC
LIMIT 1;
```

**Output:**

<img width="1105" height="421" alt="image" src="https://github.com/user-attachments/assets/8cf1dcf2-fe85-4c11-8f0d-0ded5a8142e1" />

**Question 6**
---
<img width="1087" height="590" alt="image" src="https://github.com/user-attachments/assets/4cdb78dd-ee13-4d2d-9cf9-bf4a1d9b6d45" />

```sql
SELECT 
    AVG(income) AS Average_Salary
FROM 
    employee;
```

**Output:**

<img width="1014" height="425" alt="image" src="https://github.com/user-attachments/assets/3babf02f-4a5d-43a6-aeaa-f378739b1daf" />


**Question 7**
---
<img width="1143" height="542" alt="image" src="https://github.com/user-attachments/assets/f438de0e-f0ee-4ffa-85b4-8770c03c36c7" />

```sql
SELECT 
    AVG(LENGTH(email)) AS avg_email_length_below_30
FROM 
    customer
WHERE 
    city = 'Mumbai';
```

**Output:**

<img width="1093" height="405" alt="image" src="https://github.com/user-attachments/assets/b77731a6-e0ea-465f-a049-d9f8f6f6be44" />


**Question 8**
---
<img width="1233" height="666" alt="image" src="https://github.com/user-attachments/assets/3b265bd0-3c25-4f59-b935-c734452483ba" />


```sql
SELECT 
    city,
    SUM(income) AS Income
FROM 
    employee
GROUP BY 
    city
HAVING 
    SUM(income) > 200000;
```

**Output:**

<img width="1100" height="646" alt="image" src="https://github.com/user-attachments/assets/06bdf29d-d5bf-4e38-88d8-d8df2b369031" />

**Question 9**
---
<img width="1218" height="572" alt="image" src="https://github.com/user-attachments/assets/55cb81bc-e1b6-4beb-9959-f8131f2a3667" />


```sql
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

<img width="1026" height="497" alt="image" src="https://github.com/user-attachments/assets/ea10a262-4597-4090-aefc-5ff1cca5b0ba" />

**Question 10**
---
<img width="1216" height="600" alt="image" src="https://github.com/user-attachments/assets/1a2d7437-5207-49e7-8ae8-89e4db53e934" />

```sql
SELECT 
    category_id,
    COUNT(product_name) AS "count(product_name)"
FROM 
    products
GROUP BY 
    category_id
HAVING 
    MIN(category_id) < 3;
```

**Output:**

<img width="1212" height="480" alt="image" src="https://github.com/user-attachments/assets/5ab7e4c4-7a50-445c-86cf-b65b17ee3eb9" />


## RESULT
Thus, the SQL queries to implement aggregate functions, GROUP BY, and HAVING clause have been executed successfully.
