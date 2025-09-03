# Student Database App (Console-Based, JDBC + MySQL)

## 📌 Requirements
- Java 8 or later
- MySQL installed
- JDBC Connector (add `mysql-connector-java.jar` to classpath)

## ⚙️ Setup Instructions
1. Create database in MySQL:
   ```sql
   CREATE DATABASE studentdb;
   USE studentdb;
   CREATE TABLE students (
       id INT PRIMARY KEY,
       name VARCHAR(100),
       age INT,
       course VARCHAR(100)
   );
