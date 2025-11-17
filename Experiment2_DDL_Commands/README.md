# Experiment 2: DDL Commands

# NAME : B SRI RAM
## Register number : 212223040203


## AIM
To study and implement DDL commands and different types of constraints.

## THEORY

### 1. CREATE
Used to create a new relation (table).

**Syntax:**
```sql
CREATE TABLE (
  field_1 data_type(size),
  field_2 data_type(size),
  ...
);
```
### 2. ALTER
Used to add, modify, drop, or rename fields in an existing relation.
(a) ADD
```sql
ALTER TABLE std ADD (Address CHAR(10));
```
(b) MODIFY
```sql
ALTER TABLE relation_name MODIFY (field_1 new_data_type(size));
```
(c) DROP
```sql
ALTER TABLE relation_name DROP COLUMN field_name;
```
(d) RENAME
```sql
ALTER TABLE relation_name RENAME COLUMN old_field_name TO new_field_name;
```
### 3. DROP TABLE
Used to permanently delete the structure and data of a table.
```sql
DROP TABLE relation_name;
```
### 4. RENAME
Used to rename an existing database object.
```sql
RENAME TABLE old_relation_name TO new_relation_name;
```
### CONSTRAINTS
Constraints are used to specify rules for the data in a table. If there is any violation between the constraint and the data action, the action is aborted by the constraint. It can be specified when the table is created (using CREATE TABLE) or after it is created (using ALTER TABLE).
### 1. NOT NULL
When a column is defined as NOT NULL, it becomes mandatory to enter a value in that column.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) NOT NULL
);
```
### 2. UNIQUE
Ensures that values in a column are unique.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) UNIQUE
);
```
### 3. CHECK
Specifies a condition that each row must satisfy.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) CHECK (logical_expression)
);
```
### 4. PRIMARY KEY
Used to uniquely identify each record in a table.
Properties:
Must contain unique values.
Cannot be null.
Should contain minimal fields.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) PRIMARY KEY
);
```
### 5. FOREIGN KEY
Used to reference the primary key of another table.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size),
  FOREIGN KEY (column_name) REFERENCES other_table(column)
);
```
### 6. DEFAULT
Used to insert a default value into a column if no value is specified.

Syntax:
```sql
CREATE TABLE Table_Name (
  col_name1 data_type,
  col_name2 data_type,
  col_name3 data_type DEFAULT 'default_value'
);
```

**Question 1**
--

![image](https://github.com/user-attachments/assets/76739947-13b2-443d-907c-103224fdb6a9)


```sql
ALTER TABLE student_details
ADD column Date_of_birth Date;
```

**Output:**

![image](https://github.com/user-attachments/assets/01ff9148-eb93-4876-9957-a0093f02d9dd)


**Question 2**
---
![image](https://github.com/user-attachments/assets/0b9ebbcf-27e1-414a-bb8f-da8dde2fcc2b)


```sql
create table Department(
    DepartmentID integer PRIMARY KEY,DepartmentName TEXT UNIQUE NOT NULL,
    Location text );

```

**Output:**
![image](https://github.com/user-attachments/assets/0b83479a-0e7a-4b6a-b624-5769b10e08c0)


**Question 3**
---
![image](https://github.com/user-attachments/assets/d4832cd6-e65b-45f4-87a8-fa9ca439f974)



```sqldelete from customer where cust_city LIKE 'L%';
```

**Output:**
![image](https://github.com/user-attachments/assets/baa0b55f-d35f-432c-88b1-0f4126c21b4b)



**Question 4**
---
![image](https://github.com/user-attachments/assets/e50a280d-8dd2-4e75-989c-55dfdecba71b)


```sql
create table item(item_id text primary key,item_desc text not null,rate integer not null,
icom_id text(4),foreign key (icom_id)references company(com_id) on update cascade on delete cascade);
```

**Output:**

![image](https://github.com/user-attachments/assets/213c992d-c984-4eff-aef6-5544fff25053)


**Question 5**
---
![image](https://github.com/user-attachments/assets/07adf473-0469-4bb9-8448-8d002d14244f)


```sql
create table item(item_id text primary key,item_desc text not null,rate integer not null,icom_id text(4),foreign key (icom_id)references company(com_id) on update set null on delete set null);
```

**Output:**
![image](https://github.com/user-attachments/assets/2adca52a-898e-4d6f-9b82-251d0785c2d3)


**Question 6**
---
![image](https://github.com/user-attachments/assets/dba29aa5-566b-4aad-92f4-201915ea959a)


```sql
CREATE TABLE Attendance(
AttendanceID  INTEGER  primary key,
EmployeeID INTEGER , 
AttendanceDate  DATE,
Status  TEXT check (status in( 'Present', 'Absent', 'Leave')),
foreign key (EmployeeID) references Employees(EmployeeID)
);
```

**Output:**

![image](https://github.com/user-attachments/assets/61f34bdf-c900-44ce-bbc1-1418dcba50e8)


**Question 7**
---
![image](https://github.com/user-attachments/assets/f7b81bf5-5415-4f81-a45d-1cfd039ba3ef)


```sql
ALTER TABLE Companies 
ADD COLUMN designation varchar(50);
ALTER TABLE Companies 
ADD COLUMN net_salary number;
```

**Output:**

![image](https://github.com/user-attachments/assets/0d5737b3-081b-432f-baa0-3f5a1d16fd7d)


**Question 8**
---
![image](https://github.com/user-attachments/assets/917cf486-76e0-4e5a-9f63-0da563549c44)




```sql
delete from customer where cust_city <> 'New York' and OUTSTANDING_AMT>5000;

```

**Output:**

![image](https://github.com/user-attachments/assets/f062251b-acd9-4551-af56-5474b6d8e7a8)



**Question 9**
---
![image](https://github.com/user-attachments/assets/843b2831-bf7b-4f03-800e-5715d8477828)


```sql
create table orders (OrderID INTEGER,OrderDate TEXT,CustomerID INTEGER);
```

**Output:**

![image](https://github.com/user-attachments/assets/18fe1794-e75c-42c1-9e4c-07042cf32382)


**Question 10**
---
![image](https://github.com/user-attachments/assets/60b18da4-7a37-4ad4-bd47-8d4f30046579)



```sql
delete from doctors where doctor_id between 2 and 4;

```

**Output:**

![image](https://github.com/user-attachments/assets/f843842b-b101-4c6d-940f-5e618739eb35)



## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
