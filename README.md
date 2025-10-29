# AWS RDS MySQL Database Setup using MySQL Workbench

## 🎯 Objective
To create and manage a MySQL database on Amazon RDS, connect to it using MySQL Workbench, and perform basic SQL operations such as creating tables and inserting records.

---

## 🛠️ Tools Used
- **Amazon RDS** – Managed MySQL Database Service  
- **MySQL Workbench** – GUI client for connecting and managing MySQL databases  
- **AWS Console** – For creating and configuring the RDS instance  

---

## 🚀 Steps Performed

### 1. Create a MySQL Database on AWS RDS
1. Open the **AWS Management Console** → Go to **RDS**.
2. Click **Create database** → Choose **Standard Create**.
3. Select **MySQL** as the engine type.
4. Under **Templates**, choose **Free Tier**.
5. Set:
   - DB instance identifier: `intern-demo-db`
   - Master username: `admin`
  
6. In **Connectivity**:
   - Enable **Public Access**
   - Select or create a **VPC Security Group** that allows **port 3306**
7. Create the database and wait for the status to become **Available**.

---

### 2. Connect Using MySQL Workbench
1. Open **MySQL Workbench**.
2. Click **+** to add a new connection.
3. Fill in:
   - Connection Name: `aws-rds-sql`
   - Hostname: `intern-demo-db.ccz0agm4qj3n.us-east-1.rds.amazonaws.com`
   - Port: `3306`
   - Username: `admin`
4. Click **Store in Vault...** and enter your password.
5. Click **Test Connection** → It should show *"Successfully connected"* ✅.

---

### 3. Create Database and Table
Run the following commands in a new SQL tab:

```sql

CREATE DATABASE my_aws_demo;
USE my_aws_demo;


CREATE TABLE employees (
  id INT AUTO_INCREMENT PRIMARY KEY,
  name VARCHAR(100),
  role VARCHAR(50),
  salary DECIMAL(10,2)
);


-- Create the students table
CREATE TABLE students (
  id INT AUTO_INCREMENT PRIMARY KEY,
  name VARCHAR(50),
  domain VARCHAR(50),
  score INT
);

-- Insert data into students table
INSERT INTO students (name, domain, score)
VALUES ('Aarav', 'Cloud', 95),
       ('Diya', 'DevOps', 89);


SELECT * FROM students;


SELECT * FROM employees;

