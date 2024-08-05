CREATE DATABASE LibraryDB;
USE LibraryDB;

CREATE TABLE Student (
    StudentID INT AUTO_INCREMENT PRIMARY KEY,
    FirstName VARCHAR(50),
    LastName VARCHAR(50),
    Email VARCHAR(100),
    PhoneNumber VARCHAR(20),
    Address TEXT,
    RegistrationDate DATE
);

CREATE TABLE Teacher (
    TeacherID INT AUTO_INCREMENT PRIMARY KEY,
    FirstName VARCHAR(50),
    LastName VARCHAR(50),
    Email VARCHAR(100),
    PhoneNumber VARCHAR(20),
    Department VARCHAR(50),
    RegistrationDate DATE
);

CREATE TABLE Book (
    BookID INT AUTO_INCREMENT PRIMARY KEY,
    Title VARCHAR(100),
    Author VARCHAR(100),
    ISBN VARCHAR(20),
    PublicationYear YEAR,
    Category VARCHAR(50),
    TotalCopies INT,
    AvailableCopies INT
);

CREATE TABLE IssueRecord (
    IssueID INT AUTO_INCREMENT PRIMARY KEY,
    BookID INT,
    UserID INT,
    UserType ENUM('Student', 'Teacher'),
    IssueDate DATE,
    DueDate DATE,
    ReturnDate DATE,
    FineAmount DECIMAL(10, 2),
    FOREIGN KEY (BookID) REFERENCES Book(BookID)
    -- Note: UserID is a bit complex due to mixed UserType, needs application logic for enforcement
);
