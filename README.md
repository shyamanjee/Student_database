# Student Database App (Console-Based, JDBC + MySQL)

This project is a simple **console-based Java application** that demonstrates how to integrate **JDBC (Java Database Connectivity)** with a **MySQL** database. It provides a basic student management system, allowing users to:

* Add a student
* View all students
* Delete a student

This project is a great resource for learning the fundamentals of Java and database programming.

---

## Requirements

* **Java 8** or later
* **MySQL** installed and running
* **JDBC Connector** (`mysql-connector-j-9.4.0.jar`) added to the classpath
* **Ubuntu** (or any other OS with Java and MySQL installed)

---

## Setup Instructions

1.  **Install MySQL** On Ubuntu, you can install the MySQL server by running the following commands:
    ```bash
    sudo apt update
    sudo apt install mysql-server
    ```

2.  **Create the Database and Table** Log in to your MySQL server and create the `studentdb` database and the `students` table using the following SQL commands:
    ```sql
    CREATE DATABASE studentdb;
    USE studentdb;

    CREATE TABLE students (
        id INT PRIMARY KEY,
        name VARCHAR(100),
        age INT,
        course VARCHAR(100)
    );
    ```

3.  **Compile and Run the Application** Assuming you are in the project's root directory (`Student_database/`), compile and run the application from the terminal. Be sure to include the JDBC connector JAR in your classpath.
    ```bash
    javac -cp .:mysql-connector-j-9.4.0.jar *.java
    java -cp .:mysql-connector-j-9.4.0.jar StudentApp
    ```

---

## Project Structure
Student_database/
│
├── DatabaseConnection.java   # Java Class (Utility)
├── Student.java              # Java Class (POJO - Model)
├── StudentDAO.java           # Java Class (DAO - Data Access)
├── StudentApp.java           # Java Class (Main Application)
├── README.md                 # Documentation

---

## File Details

### `DatabaseConnection.java` (Utility Class)

* **Purpose:** Handles the connection to the MySQL database.
* **Key Features:** Provides a static `getConnection()` method used by other classes to establish a database connection. It uses the JDBC `DriverManager` to connect with the specified URL, username, and password. This design centralizes database configuration, making it easy to maintain.

### `Student.java` (Model / POJO)

* **Purpose:** Represents a single student object.
* **Fields:** `id` (unique integer), `name` (student’s name), `age` (student’s age), and `course` (enrolled course).
* **Key Features:** This is a Plain Old Java Object (POJO) with constructors, getters, and setters. It's used as a data structure when interacting with the database.

### `StudentDAO.java` (Data Access Object)

* **Purpose:** Contains methods to perform CRUD (Create, Read, Update, Delete) operations on the `students` table.
* **Key Features:** Includes methods like `addStudent(Student s)` to insert a new student, `getAllStudents()` to fetch all students, and `deleteStudent(int id)` to remove a student by their ID. This class's role is to keep database-specific logic separate from the main application logic, promoting a clean design.

### `StudentApp.java` (Main Console App)

* **Purpose:** The entry point of the program, providing a menu-driven interface.
* **Features:** Displays menu options (Add, View, Delete, Exit) to the user, takes input from the console, and calls the appropriate methods in the `StudentDAO` class to perform database operations.
* **Example Menu:**
    ```
    === Student Database App ===
    1. Add Student
    2. View All Students
    3. Delete Student
    4. Exit
    ```