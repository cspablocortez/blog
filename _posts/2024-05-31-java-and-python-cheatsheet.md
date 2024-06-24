---
title: Java and Python Cheatsheet
date: 2024-05-31
layout: post
published: true
---

Last updated: Sun Jun 16 at 6:41:46 PM PST

# Variables and Data Types

- **Java**
  - Declaring variables

```java
String city  = "Las Vegas";
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

```java
String[] cars = {"Volvo", "BMW", "Ford", "Mazda"};
int[] myNum - {10, 20, 30, 40};
```

  - ArrayLists

First you'll import the `ArrayList` class from the `java.util` package.

```java
import java.util.ArrayList;
```

```java
ArrayList<String> cars = new ArrayList<String>(); 
cars.add("Volvo");
cars.add("BMW");
cars.add("Ford");
cars.add(0, "Mazda"); // Insert element at the beginning of the list (0)
System.out.println(cars);
```

  - HashMaps

HashMaps in Java are similar to dictionaries in Python &mdash;they're for storing items in key - value pairs.

```java
import java.util.HashMap; // import the HashMap class

HashMap<String, String> capitalCities = new HashMap<String, String>();
// Add keys and values (Country, City)
capitalCities.put("England", "London");
capitalCities.put("Germany", "Berlin");
capitalCities.put("Norway", "Oslo");
capitalCities.put("USA", "Washington DC");
System.out.println(capitalCities);
```

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

## Classes

A class called `Main` in a file called `Main.java` with a `main` method.

```java

public Class Main {
	public static void main(String[] args) {
		
	}
}
```
  
- **Python**
  - Classes and objects
  - Constructors
  - Inheritance and method overriding

---

# Error Handling

- **Java**
  - Try-catch blocks

```java
public class Main {
  public static void main(String[ ] args) {
    try {
      int[] myNumbers = {1, 2, 3};
      System.out.println(myNumbers[10]);
    } catch (Exception e) {
      System.out.println("Something went wrong.");
    }
  }
}
```
  - Finally block
  - Creating custom exceptions

```java
try {
    System.out.println("The count is " + Integer.parseInt(count));
} catch (NumberFormatException e) {
    System.out.println("No count");
} finally {
    System.out.println("In finally");
}
```
  
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

## Recommendations:

I recommend you solve at least *one* of the following problems using *both* languages. If you visit the [USACO Guide problems page](https://usaco.guide/problems/), you should be able to find solutions for these problems. Only use them to go over your work!

[USACO 2016 January Contest, Bronze - Problem 1. Promotion Counting](https://usaco.org/index.php?page=viewproblem2&cpid=591)

[USACO 2020 January Contest, Bronze - Problem 1. Word Processor](https://usaco.org/index.php?page=viewproblem2&cpid=987)

[USACO 2016 December Contest, Silver - Problem 1. Counting Haybales](https://usaco.org/index.php?page=viewproblem2&cpid=666)

## Assignment

### BRONZE

	Hungry Cow Feb 2023
	

### SILVER 
	Bakery Feb 23

### GOLD

	Piling Papers Feb 23
	

TEMPLATE for USACO problems



