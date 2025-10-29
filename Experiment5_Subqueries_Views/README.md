# Experiment 5: Subqueries and Views

## AIM
To study and implement subqueries and views.

## THEORY

### Subqueries
A subquery is a query inside another SQL query and is embedded in:
- WHERE clause
- HAVING clause
- FROM clause

**Types:**
- **Single-row subquery**:
  Sub queries can also return more than one value. Such results should be made use along with the operators in and any.
- **Multiple-row subquery**:
  Here more than one subquery is used. These multiple sub queries are combined by means of ‘and’ & ‘or’ keywords.
- **Correlated subquery**:
  A subquery is evaluated once for the entire parent statement whereas a correlated Sub query is evaluated once per row processed by the parent statement.

**Example:**
```sql
SELECT * FROM employees
WHERE salary > (SELECT AVG(salary) FROM employees);
```
### Views
A view is a virtual table based on the result of an SQL SELECT query.
**Create View:**
```sql
CREATE VIEW view_name AS
SELECT column1, column2 FROM table_name WHERE condition;
```
**Drop View:**
```sql
DROP VIEW view_name;
```

**Question 1**
--
-<img width="1243" height="901" alt="image" src="https://github.com/user-attachments/assets/9d61af39-9eee-44b8-9f26-d8ac4e217496" />


```sql
SELECT 
    o.ord_no, 
    o.purch_amt, 
    o.ord_date, 
    o.customer_id, 
    o.salesman_id
FROM 
    orders o
JOIN 
    salesman s 
ON 
    o.salesman_id = s.salesman_id
WHERE 
    s.city = 'New York';

```

**Output:**

<img width="1288" height="563" alt="image" src="https://github.com/user-attachments/assets/7ea0d21f-5465-4be2-ba82-7d6359078337" />


**Question 2**
---
<img width="1267" height="526" alt="image" src="https://github.com/user-attachments/assets/7144b9a0-12a5-4483-8595-c18b01d79a2d" />

```sql
SELECT 
    department_id AS depar,
    department_name
FROM 
    departments
WHERE 
    LENGTH(department_name) > (
        SELECT AVG(LENGTH(department_name)) 
        FROM departments
    );

```

**Output:**

<img width="1278" height="802" alt="image" src="https://github.com/user-attachments/assets/b264eb75-a380-4ef6-824b-1f134a9a0fc1" />


**Question 3**
---
<img width="1282" height="493" alt="image" src="https://github.com/user-attachments/assets/53c05d2e-a023-4621-be6f-90eb38349999" />


```sql
SELECT 
    s.salesman_id, 
    s.name
FROM 
    salesman s
JOIN 
    customer c 
ON 
    s.salesman_id = c.salesman_id
GROUP BY 
    s.salesman_id, s.name
HAVING 
    COUNT(c.customer_id) > 1;

```

**Output:**

<img width="1236" height="571" alt="image" src="https://github.com/user-attachments/assets/abce9fcf-8dd4-4013-beb6-dbe01b72df61" />


**Question 4**
---
<img width="1269" height="678" alt="image" src="https://github.com/user-attachments/assets/9a58a481-4050-4f1b-91d1-cbb597180b54" />

```sql
SELECT 
    student_id,
    student_name,
    subject,
    grade
FROM 
    Grades g
WHERE 
    grade = (
        SELECT MAX(grade)
        FROM Grades
        WHERE subject = g.subject
    );

```

**Output:**

<img width="1292" height="555" alt="image" src="https://github.com/user-attachments/assets/17caf0a9-3a05-4312-aa0c-1a5961019224" />


**Question 5**
---
<img width="1225" height="688" alt="image" src="https://github.com/user-attachments/assets/806b661d-aaed-4e77-84fa-6d36ac667aaf" />


```sql
SELECT 
    *
FROM 
    CUSTOMERS
WHERE 
    SALARY = 1500;

```

**Output:**

<img width="1293" height="456" alt="image" src="https://github.com/user-attachments/assets/30bee5e6-f639-40b0-82c4-e18ee217cb4d" />


**Question 6**
---
<img width="1234" height="564" alt="image" src="https://github.com/user-attachments/assets/60bb2bc7-1d6d-4b24-addf-c1d72d26bb83" />


```sql
SELECT 
    medication_id AS medic, 
    medication_name, 
    dosage
FROM 
    Medications
WHERE 
    dosage = (
        SELECT MAX(dosage) 
        FROM Medications
    );

```

**Output:**

<img width="1225" height="501" alt="image" src="https://github.com/user-attachments/assets/2578332a-7f17-493a-8ad5-6ae9a0ea142f" />


**Question 7**
---
<img width="1288" height="881" alt="image" src="https://github.com/user-attachments/assets/242e6a9e-fc06-4090-b68d-2e77e2e78485" />


```sql
SELECT 
    o.ord_no, 
    o.purch_amt, 
    o.ord_date, 
    o.customer_id, 
    o.salesman_id
FROM 
    orders o
JOIN 
    salesman s 
ON 
    o.salesman_id = s.salesman_id
WHERE 
    s.city = 'New York';

```

**Output:**

<img width="1282" height="592" alt="image" src="https://github.com/user-attachments/assets/fd34638d-b24f-46fd-a484-c54b059bd403" />


**Question 8**
---
<img width="1274" height="896" alt="image" src="https://github.com/user-attachments/assets/66960c52-272d-4190-bb88-6282a67d36f2" />


```sql
SELECT 
    o.ord_no, 
    o.purch_amt, 
    o.ord_date, 
    o.salesman_id
FROM 
    orders o
JOIN 
    salesman s 
ON 
    o.salesman_id = s.salesman_id
WHERE 
    s.commission = (
        SELECT MAX(commission) 
        FROM salesman
    );

```

**Output:**

<img width="1274" height="583" alt="image" src="https://github.com/user-attachments/assets/aeadf2f3-565e-4a5f-8046-cb29b035af4e" />


**Question 9**
---
<img width="1287" height="664" alt="image" src="https://github.com/user-attachments/assets/3e37ae9f-284e-4897-a12b-5ac7ea6246df" />


```sql
SELECT 
    student_id, 
    student_name, 
    subject, 
    grade
FROM 
    Grades g
WHERE 
    grade = (
        SELECT MIN(grade)
        FROM Grades
        WHERE subject = g.subject
    );

```

**Output:**

<img width="1304" height="551" alt="image" src="https://github.com/user-attachments/assets/6487b101-471b-411e-8ea6-09c35802eeb0" />

**Question 10**
---
<img width="1278" height="815" alt="image" src="https://github.com/user-attachments/assets/cb2c494b-f425-429e-a6ab-29d93929530e" />


```sql
SELECT 
    *
FROM 
    CUSTOMERS
WHERE 
    AGE < 30;

```

**Output:**

<img width="1281" height="672" alt="image" src="https://github.com/user-attachments/assets/2a215cf2-4525-4792-a3b3-3add264af7c7" />



## RESULT
Thus, the SQL queries to implement subqueries and views have been executed successfully.
