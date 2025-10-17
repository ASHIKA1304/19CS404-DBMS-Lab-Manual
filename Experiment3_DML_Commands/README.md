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
<img width="1235" height="647" alt="image" src="https://github.com/user-attachments/assets/52d3c317-5144-42b8-b9c1-618615fd8221" />

```
UPDATE EMPLOYEES
SET EMAIL = 'not available',
    COMMISSION_PCT = 0.55
WHERE DEPARTMENT_ID = 110;
```

**Output:**


<img width="1213" height="475" alt="image" src="https://github.com/user-attachments/assets/48e59efc-4300-4898-acb5-39531685b7cf" />

**Question 2**

<img width="1229" height="622" alt="image" src="https://github.com/user-attachments/assets/e720e8a8-a2f7-404e-a83b-8419747e9097" />

```
UPDATE PRODUCTS
SET sell_price = sell_price * 1.15
WHERE quantity < 50
  AND supplier_id = 10;
```
**Output:**

<img width="1243" height="590" alt="image" src="https://github.com/user-attachments/assets/a1db7f16-840c-4ecf-86f8-955fddb196ff" />

**Question 3**

<img width="1232" height="607" alt="image" src="https://github.com/user-attachments/assets/a7e31d3c-8c1a-4d2b-81f1-c652f2ecda32" />

```
UPDATE PRODUCTS
SET reorder_lvl = 40
WHERE category = 'Grocery';
```

**Output:**

<img width="1253" height="510" alt="image" src="https://github.com/user-attachments/assets/ab2ede1b-1bee-49c4-8d22-aeb1b66e3cad" />

**Question 4**

<img width="1228" height="700" alt="image" src="https://github.com/user-attachments/assets/1e2e90ff-b829-4143-aa59-88a50fac3bde" />

```
UPDATE PURCHASES
SET per_unit_price = 25,
    total_price = quantity * 25
WHERE purchase_date = '2022-08-15'
  AND product_id = 12;
```


**Output:**

<img width="1237" height="624" alt="image" src="https://github.com/user-attachments/assets/ffac239e-622a-49b5-b125-b1e25fb30e10" />

**Question 5**

<img width="1240" height="386" alt="image" src="https://github.com/user-attachments/assets/b99f068e-3e6d-4fce-b938-7653b8c156fc" />

```
UPDATE PRODUCTS
SET quantity = quantity * 1.10;
```

**Output:**

<img width="1234" height="663" alt="image" src="https://github.com/user-attachments/assets/0762360c-fe45-4b3d-9e76-faa94e0aba52" />


**Question 6**

<img width="1298" height="772" alt="image" src="https://github.com/user-attachments/assets/2ed36808-fce7-442f-aabb-ddc9576ddb12" />

```
DELETE FROM customer
WHERE cust_country = 'India'
  AND cust_city <> 'Chennai';
```

**Output:**

<img width="1216" height="916" alt="image" src="https://github.com/user-attachments/assets/be4cfd35-085c-4ce8-98e9-479b89339a1c" />

**Question 7**

<img width="1248" height="610" alt="image" src="https://github.com/user-attachments/assets/55276766-b2b3-4964-ba6e-9abc7653a51c" />

```
DELETE FROM doctors
WHERE last_name = 'Brown'
  AND specialization IN ('Pediatrics', 'Cardiology');
```


**Output:**

<img width="1316" height="841" alt="image" src="https://github.com/user-attachments/assets/760a0f37-e495-44e7-a0f3-80c04cc16c01" />

**Question 8**

<img width="1306" height="418" alt="image" src="https://github.com/user-attachments/assets/5afe7e2e-8040-4399-b499-a367c67df49f" />

```
DELETE FROM customer
WHERE GRADE = 2
  AND CUST_NAME LIKE 'M%'
  AND PAYMENT_AMT < 3000;
```


**Output:**

<img width="1293" height="414" alt="image" src="https://github.com/user-attachments/assets/04192997-5aba-42e6-ad65-19f8ed6495c4" />

**Question 9**

<img width="1285" height="595" alt="image" src="https://github.com/user-attachments/assets/44198fe9-ab90-4563-b9cd-76ea4f8a9169" />

```
DELETE FROM customer
WHERE GRADE >= 2;
```

**Output:**

<img width="1317" height="512" alt="image" src="https://github.com/user-attachments/assets/72023880-632a-4b28-8cfe-e84c01c6130b" />

**Question 10**

<img width="1267" height="441" alt="image" src="https://github.com/user-attachments/assets/de8a0af9-2268-4238-a91f-f4e279f6aa4f" />

```
DELETE FROM doctors
WHERE doctor_id BETWEEN 2 AND 4;
```

**Output:**

<img width="1319" height="766" alt="image" src="https://github.com/user-attachments/assets/83cc5f7b-3c6a-4fbe-b00a-87ffd99858cf" />


## RESULT
Thus, the SQL queries to implement DML commands have been executed successfully.
