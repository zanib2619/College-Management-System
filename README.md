# College-Management-System
# College Management System Database

This project is a basic implementation of a relational database schema for a College Management System using SQL. It covers the creation of tables for students, courses, and enrollments, along with appropriate keys and relationships.

## 📚 Project Overview

The main goal of this project is to design a well-structured schema that demonstrates:

* Creating a database and tables
* Using primary and foreign keys
* Establishing relationships between entities


This project is part of my learning and internship submission, aimed at demonstrating my understanding of database design concepts.

---

## 📌 Domain: College Management

### Entities:

* **Students**: Stores student details
* **Courses**: Contains course information
* **Enrollments**: Records which students are enrolled in which courses

---

## 💻 SQL Script

```sql
-- Create the database
CREATE DATABASE College;
USE College;

-- Create Students table
CREATE TABLE Students (
    StudentID INT PRIMARY KEY,
    Name VARCHAR(50) NOT NULL,
    Email VARCHAR(60) UNIQUE,
    DOB DATE
);

-- Create Courses table
CREATE TABLE Courses (
    CourseID INT PRIMARY KEY,
    CourseName VARCHAR(50) NOT NULL,
    Credits INT CHECK (Credits > 0)
);

-- Create Enrollments table
CREATE TABLE Enrollments (
    EnrollmentID INT PRIMARY KEY,
    StudentID INT,
    CourseID INT,
    EnrollmentDate DATE,
    FOREIGN KEY (StudentID) REFERENCES Students(StudentID),
    FOREIGN KEY (CourseID) REFERENCES Courses(CourseID)
);

📊 ER Diagram
[Students]
+-------------+
| StudentID PK|
| Name        |
| Email       |
| DOB         |
+-------------+

          |
          | 1
          |--------< Enrolls >--------|
                       *             |
                       |             |
                       v             v

[Enrollments]
+------------------+
| EnrollmentID PK  |
| StudentID FK     |
| CourseID  FK     |
| EnrollmentDate   |
+------------------+

          ^
          |
          | *
          | 1
      [Courses]
+----------------+
| CourseID   PK  |
| CourseName     |
| Credits        |
+----------------+




```
