-- ============================================
-- STUDENT CRUD APPLICATION
-- ============================================

-- 1. CREATE DATABASE
CREATE DATABASE IF NOT EXISTS student_db;

USE student_db;


-- 2. CREATE STUDENT TABLE
CREATE TABLE student (
    std_id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(50) NOT NULL,
    email VARCHAR(100) NOT NULL UNIQUE,
    age INT CHECK (age >= 18 AND age <= 60),
    branch VARCHAR(20) DEFAULT 'CSE',
    marks INT CHECK (marks >= 0 AND marks <= 100)
);


-- 3. INSERT 5 STUDENTS
INSERT INTO student (name, email, age, branch, marks)
VALUES
('Ravi', 'ravi@gmail.com', 20, 'CSE', 85),
('Kiran', 'kiran@gmail.com', 21, 'ECE', 78),
('Suresh', 'suresh@gmail.com', 22, 'MECH', 72),
('Priya', 'priya@gmail.com', 20, 'CSE', 91),
('Anu', 'anu@gmail.com', 23, 'IT', 88);


-- 4. DISPLAY ALL STUDENTS
SELECT * FROM student;


-- 5. UPDATE STUDENT MARKS
UPDATE student
SET marks = 95
WHERE std_id = 1;


-- DISPLAY AFTER UPDATE
SELECT * FROM student;


-- 6. DELETE ONE STUDENT
DELETE FROM student
WHERE std_id = 5;


-- DISPLAY AFTER DELETE
SELECT * FROM student;


-- ============================================
-- 7. TEST NOT NULL CONSTRAINT
-- ============================================

-- This should give an error
INSERT INTO student (name, email, age, branch, marks)
VALUES (NULL, 'test@gmail.com', 20, 'CSE', 80);


-- ============================================
-- 8. TEST UNIQUE CONSTRAINT
-- ============================================

-- ravi@gmail.com already exists
-- This should give a duplicate email error
INSERT INTO student (name, email, age, branch, marks)
VALUES ('Test', 'ravi@gmail.com', 20, 'CSE', 80);


-- ============================================
-- 9. TEST AGE CHECK CONSTRAINT
-- ============================================

-- Age 15 is invalid
-- This should give a CHECK constraint error
INSERT INTO student (name, email, age, branch, marks)
VALUES ('Test', 'test2@gmail.com', 15, 'CSE', 80);


-- ============================================
-- 10. TEST MARKS CHECK CONSTRAINT
-- ============================================

-- Marks 120 is invalid
-- This should give a CHECK constraint error
INSERT INTO student (name, email, age, branch, marks)
VALUES ('Test', 'test3@gmail.com', 20, 'CSE', 120);


-- ============================================
-- 11. TEST DEFAULT CONSTRAINT
-- ============================================

-- Branch is not provided
-- Therefore branch will automatically become CSE
INSERT INTO student (name, email, age, marks)
VALUES ('Arjun', 'arjun@gmail.com', 21, 85);


-- 12. FINAL DISPLAY
SELECT * FROM student;



Table structure
student
--------------------------------
std_id    → PRIMARY KEY + AUTO_INCREMENT
name      → NOT NULL
email     → NOT NULL + UNIQUE
age       → CHECK (18–60)
branch    → DEFAULT 'CSE'
marks     → CHECK (0–100)
