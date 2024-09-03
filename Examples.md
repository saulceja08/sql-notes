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
select first_name 
FROM patients
where first_name like 'C%';
``` 
