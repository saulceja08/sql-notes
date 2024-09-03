# SQL Query Examples 📊

This page provides practical examples of common SQL queries, with questions and their corresponding solutions.

## 🔍 Basic Queries

### 1. **Show first name, last name, and gender of patients whose gender is 'M'**

**Query:**
```sql
SELECT first_name, last_name, gender
FROM patients
WHERE gender = 'M';
```

### 2. **Show first name and last name of patients who does not have allergies. (null)**

**Query:**
```sql
SELECT 	first_name, last_name
FROM patients
WHERE allergies IS null;
```

### 3. **Show first name of patients that start with the letter 'C'**

**Query:**
```sql
SELECT first_name 
FROM patients
WHERE first_name like 'C%';
``` 

### 4. **Show first name and last name of patients that weight within the range of 100 to 120 (inclusive)**

**Query:**
```sql
SELECT first_name, last_name
FROM patients
WHERE weight between 100 AND 120;
``` 

### 5. **Update the patients table for the allergies column. If the patient's allergies is null then replace it with 'NKA'**

**Query:**
```sql
UPDATE patients

SET allergies = 'NKA'
WHERE allergies is null;
``` 

### 6. **Show first name and last name concatinated into one column to show their full name.**

**Query:**
```sql
SELECT CONCAT(first_name, " ", last_name) 
FROM patients;
``` 