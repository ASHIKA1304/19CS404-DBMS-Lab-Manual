## Experiment 2 : DDL Commands

## AIM

To study and implement DDL commands and different types of constraints.

## THEORY

## 1. CREATE
Used to create a new relation (table).

## Syntax:

CREATE TABLE (
  field_1 data_type(size),
  field_2 data_type(size),
  ...
);
## 2. ALTER
Used to add, modify, drop, or rename fields in an existing relation. 

(a) ADD

```
ALTER TABLE std ADD (Address CHAR(10));
```
(b) MODIFY

```
ALTER TABLE relation_name MODIFY (field_1 new_data_type(size));
```
(c) DROP

```
ALTER TABLE relation_name DROP COLUMN field_name;
```
(d) RENAME

```
ALTER TABLE relation_name RENAME COLUMN old_field_name TO new_field_name;
```
## 3. DROP TABLE
Used to permanently delete the structure and data of a table.

```
DROP TABLE relation_name;
```

## 4. RENAME
Used to rename an existing database object.

```
RENAME TABLE old_relation_name TO new_relation_name;
```

## CONSTRAINTS

Constraints are used to specify rules for the data in a table. If there is any violation between the constraint and the data action, the action is aborted by the constraint. It can be specified when the table is created (using CREATE TABLE) or after it is created (using ALTER TABLE).

## 1. NOT NULL
When a column is defined as NOT NULL, it becomes mandatory to enter a value in that column. 
## Syntax:

```
CREATE TABLE Table_Name (
  column_name data_type(size) NOT NULL
);
```

## 2. UNIQUE

Ensures that values in a column are unique. 

## Syntax:

```
CREATE TABLE Table_Name (
  column_name data_type(size) UNIQUE
);
```

## 3. CHECK

Specifies a condition that each row must satisfy.

## Syntax:

```
CREATE TABLE Table_Name (
  column_name data_type(size) CHECK (logical_expression)
);
```

## 4. PRIMARY KEY
Used to uniquely identify each record in a table. Properties: Must contain unique values. Cannot be null. Should contain minimal fields.

## Syntax:

```
CREATE TABLE Table_Name (
  column_name data_type(size) PRIMARY KEY
);
```

## 5. FOREIGN KEY
Used to reference the primary key of another table. 

## Syntax:

```
CREATE TABLE Table_Name (
  column_name data_type(size),
  FOREIGN KEY (column_name) REFERENCES other_table(column)
);
```

## 6. DEFAULT
Used to insert a default value into a column if no value is specified.

## Syntax:

```
CREATE TABLE Table_Name (
  col_name1 data_type,
  col_name2 data_type,
  col_name3 data_type DEFAULT 'default_value'
);
```

## QUESTIONS:

## 1.

<img width="1246" height="265" alt="image" src="https://github.com/user-attachments/assets/b02aa367-2630-47c9-bcc4-28535d6a3c67" />

```
INSERT INTO Customers (CustomerID, Name, Address, City, ZipCode)
VALUES (301, 'Michael Jordan', '123 Maple St', 'Chicago', 60616);
```

## OUTPUT :

<img width="1242" height="341" alt="image" src="https://github.com/user-attachments/assets/c0e52cb7-0bca-4059-8b6d-13840f3f087b" />


## 2.
<img width="1230" height="535" alt="image" src="https://github.com/user-attachments/assets/b15686cf-b372-4a1c-b236-9ede6d7dec7a" />

```
INSERT INTO Books (ISBN, Title, Author)
VALUES ('978-1234567890', 'Introduction to AI', 'John Doe');

INSERT INTO Books (ISBN, Title, Author, Publisher, Year)
VALUES ('978-9876543210', 'Deep Learning', 'Jane Doe', 'TechPress', 2022);

INSERT INTO Books (ISBN, Title, Author, Year)
VALUES ('978-1122334455', 'Cybersecurity Essentials', 'Alice Smith', 2021);
```

## OUTPUT :

<img width="1253" height="393" alt="image" src="https://github.com/user-attachments/assets/3ad0d018-8519-4aed-a2eb-442b94f290ac" />

## 3. 

<img width="1254" height="445" alt="image" src="https://github.com/user-attachments/assets/12c0a71b-1a9b-45ec-b0b4-03e8af413d31" />

```
ALTER TABLE Employees ADD COLUMN Date_of_joining Date;

ALTER TABLE Employees RENAME COLUMN job_title TO Designation;
```

## OUTPUT :

<img width="1230" height="416" alt="image" src="https://github.com/user-attachments/assets/e6bf92be-55c8-46a0-ac30-979064d47403" />

## 4.

<img width="1234" height="374" alt="image" src="https://github.com/user-attachments/assets/78ac7d4e-6ab8-4940-b35b-29ec24dcd9cb" />

```
CREATE TABLE Invoices (
    InvoiceID INTEGER PRIMARY KEY,
    InvoiceDate DATE,
    DueDate DATE,
    Amount REAL CHECK (Amount > 0),
    CHECK (DueDate > InvoiceDate)
);
```

## OUTPUT :

<img width="1301" height="365" alt="image" src="https://github.com/user-attachments/assets/c755e7f2-1bf7-4193-b109-59a15c630437" />

## 5

<img width="1294" height="287" alt="image" src="https://github.com/user-attachments/assets/058e4669-db4c-4d9c-b086-3ae66694cba6" />

```

CREATE TABLE IF NOT EXISTS Orders (
    OrderID INTEGER PRIMARY KEY,
    OrderDate DATE,
    CustomerID INTEGER
);


CREATE TABLE Invoices (
    InvoiceID INTEGER PRIMARY KEY,
    InvoiceDate DATE,
    Amount REAL CHECK (Amount > 0),
    DueDate DATE,
    OrderID INTEGER,
    FOREIGN KEY (OrderID) REFERENCES Orders(OrderID),
    CHECK (DueDate > InvoiceDate)
);
```

## OUTPUT : 

<img width="1179" height="312" alt="image" src="https://github.com/user-attachments/assets/e02b734e-63d8-4262-a1bf-07ef6ca68dd2" />

## 6.

<img width="1303" height="297" alt="image" src="https://github.com/user-attachments/assets/b4ae334c-9785-461b-8e1a-ebeadbc5ac7f" />

```
CREATE TABLE Department (
    DepartmentID INTEGER PRIMARY KEY,
    DepartmentName TEXT UNIQUE NOT NULL,
    Location TEXT
);
```

## OUTPUT :

<img width="868" height="478" alt="image" src="https://github.com/user-attachments/assets/1d4a1a00-0c5b-403f-b8ed-190517ef4dd8" />

## 7.

<img width="1300" height="354" alt="image" src="https://github.com/user-attachments/assets/b3686784-2fa1-4b53-9587-facdbf68beb9" />

```
ALTER TABLE Student_details
ADD COLUMN mobilenumber number;
```

## OUTPUT :

<img width="1169" height="316" alt="image" src="https://github.com/user-attachments/assets/16da3746-eb15-47cb-8f12-5db0a1528d68" />

## 8.

<img width="1306" height="305" alt="image" src="https://github.com/user-attachments/assets/4bc7d914-73f7-449d-80f5-1f6ef81e4da4" />

```
INSERT INTO Books (ISBN, Title, Author, Publisher, YearPublished)
SELECT ISBN, Title, Author, Publisher, YearPublished
FROM Out_of_print_books;
```

## OUTPUT :


## 9.

<img width="1285" height="292" alt="image" src="https://github.com/user-attachments/assets/294b6321-5393-45d3-852e-8a4442e3bd1a" />

```
CREATE TABLE IF NOT EXISTS Suppliers (
    SupplierID INTEGER PRIMARY KEY,
    SupplierName TEXT
);

CREATE TABLE IF NOT EXISTS Orders (
    OrderID INTEGER PRIMARY KEY,
    OrderDate DATE,
    CustomerID INTEGER
);


CREATE TABLE Shipments (
    ShipmentID INTEGER PRIMARY KEY,
    ShipmentDate DATE,
    SupplierID INTEGER,
    OrderID INTEGER,
    FOREIGN KEY (SupplierID) REFERENCES Suppliers(SupplierID),
    FOREIGN KEY (OrderID) REFERENCES Orders(OrderID)
);
```

## OUTPUT :

<img width="1304" height="260" alt="image" src="https://github.com/user-attachments/assets/c55de0bd-2cc9-47a3-a97e-605086f08cb7" />

## 10.

<img width="1315" height="397" alt="image" src="https://github.com/user-attachments/assets/664a3b01-ec77-4c3e-a1e2-48dab1daf6e1" />

```
CREATE TABLE Products(
    ProductID INTEGER,
    ProductName TEXT,
    Price REAL,
    Stock INTEGER
);
```

## OUTPUT :

<img width="1310" height="301" alt="image" src="https://github.com/user-attachments/assets/da377e8f-b248-405c-8f2f-8f34bd0c90f9" />

