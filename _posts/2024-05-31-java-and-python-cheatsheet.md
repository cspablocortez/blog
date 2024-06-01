---
title: Java and Python Cheatsheet
date: 2024-05-31
layout: post
published: true
---

# Variables and Data Types

- **Java**
  - Declaring variables

```java
String name = "Pablo";
int day = 31;
double degrees = 98.9;
char grade = 'A';
boolean passedAPExam = true;
```
  
  - Types of variables: int, double, char, boolean, etc.
  - Type casting: converting from one primitive type to another

```java
double myDouble = 9.78d;
int myInt = (int) myDouble; // Manual casting: double to int
```
  
- **Python**
  - Variables and dynamic typing 
  - Basic data types: int, float, str, bool
  - Type conversion

# Control Structures

- **Java**
  - Conditional Statements: if, if-else, switch

```java
int age = 16;
bool hasLicense = true;

if (age >= 16 && hasLicense) {
  System.out.println("You can drive!");
} else {
  System.out.println("Ride the bus lol");
}

```
  
  - Loops: for, while, do-while
  
```java

for (int i = 0; i < VALUE; i++) {
  // DO SOMETHING
}


while (!gameOver) {
  keepPlaying();
}

int i = 0;
do {
  System.out.println(i);
  i++;
} 

while (i <= 5);
```
  
  
- **Python**
  - Conditional Statements: if, elif, else
  - Loops: for, while



# Functions and Methods

- **Java**
  - Defining methods
  
```java
[access modifier] [return type] [name]([parameters]) {
  // TO DO...
}

public int square(int n) {
  return n * n;
}
```
  
  - Method calling

`obj.methodName();`

  - Return types and parameters
  
- **Python**
  - Defining functions
  - Function calling
  - Return values and parameters

---

# Data Structures

- **Java**
  - Arrays
  - ArrayLists
  - HashMaps
  
- **Python**
  - Lists
  - Dictionaries
  - Sets

---

# Object-Oriented Programming

- **Java**
  - Understanding classes and objects
  - Constructors
  - Encapsulation, Inheritance, and Polymorphism
  
- **Python**
  - Classes and objects
  - Constructors
  - Inheritance and method overriding

---

# Error Handling

- **Java**
  - Try-catch blocks
  - Finally block
  - Creating custom exceptions
  
- **Python**
  - Try-except block
  - Finally and else clauses
  - Raising exceptions

--- 

# Libraries and APIs
- **Java**
  - Using standard libraries (e.g., java.util)
  - Reading from and writing to files
  
- **Python**
  - Using standard libraries (e.g., sys, os)
  - File handling (open, read, write, close)


# Choosing your assignments

- **Java**
  - One USACO problem (Bronze Level)
  - One USACO problem (Silver Level)
  - One USACO problem (Gold Level)
  
- **Python**
  - One USACO problem (Bronze Level)
  - One USACO problem (Silver Level)
  - One USACO problem (Gold Level)


