## Objective
Create an RDS database instance, connect using SQL Workbench, and execute basic SQL queries.

## Steps

1. Create RDS instance
   - Go to RDS → Create database
   - Engine: MySQL
   - Template: Free tier
   - DB instance identifier: mydb
   - Master username: admin
   - Set password

2. Configure connectivity
   - Public access: Yes
   - Select default VPC
   - Create new security group
   - Allow inbound rule: MySQL/Aurora (Port 3306) from your IP

3. Launch database and wait until status becomes Available.

4. Note the endpoint
   - RDS → Connectivity & security → Endpoint

5. Open SQL Workbench
   - Create new connection
   - Hostname: RDS endpoint
   - Port: 3306
   - Username: admin
   - Password: configured password

6. Connect to database

7. Create database
   CREATE DATABASE testdb;

8. Use database
   USE testdb;

9. Create table
   CREATE TABLE students (
       id INT PRIMARY KEY,
       name VARCHAR(50),
       age INT
   );

10. Insert records
    INSERT INTO students VALUES (1,'John',22);
    INSERT INTO students VALUES (2,'Alice',21);

11. Retrieve data
    SELECT * FROM students;

## Result
Successfully connected to the RDS database and executed SQL queries with data stored and retrieved.