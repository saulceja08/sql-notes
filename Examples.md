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

### 7. **Show first name, last name, and the full province name of each patient. Example: 'Ontario' instead of 'ON'**

**Query:**
```sql
SELECT p1.first_name, p1.last_name, p2.province_name
FROM patients p1
LEFT JOIN province_names p2
ON p1.province_id = p2.province_id;
``` 

### 8. **Show how many patients have a birth_date with 2010 as the birth year.**

**Query:**
```sql
SELECT COUNT(*) AS number_of_patients
FROM patients
WHERE YEAR(birth_date) = 2010;
``` 

### 9. **Show the first_name, last_name, and height of the patient with the greatest height.**

**Query:**
```sql
SELECT first_name, last_name, height
FROM patients
WHERE height = (SELECT MAX(height) FROM patients);
``` 

### 10. **Show all columns for patients who have one of the following patient_ids: 1,45,534,879,1000**

**Query:**
```sql
SELECT * FROM patients
WHERE patient_id IN (1,45,534,879,1000);
``` 

### 11. **Show the total number of admissions**

**Query:**
```sql
SELECT COUNT(*) AS total_admissions
FROM admissions;
``` 

### 12. **Show all the columns from admissions where the patient was admitted and discharged on the same day.**

**Query:**
```sql
SELECT *
FROM admissions
WHERE admission_date = discharge_date;
``` 

### 13. **Show the patient id and the total number of admissions for patient_id 579.**

**Query:**
```sql
SELECT patient_id, count(*) AS total_admissions
FROM admissions
WHERE patient_id = 579;
``` 

### 14. **Based on the cities that our patients live in, show unique cities that are in province_id 'NS'?**

**Query:**
```sql
SELECT DISTINCT(city)
FROM patients
WHERE province_id = 'NS';
``` 

### 15. **Show first name and last name of patients that weight within the range of 100 to 120 (inclusive)**

**Query:**
```sql
SELECT first_name, last_name
FROM patients
WHERE weight BETWEEN 100 and 120;
``` 

### 16. **Update the patients table for the allergies column. If the patient's allergies is null then replace it with 'NKA'**

**Query:**
```sql
UPDATE patients
SET allergies = 'NKA'
WHERE allergies IS NULL;
``` 

### 17. ****

**Query:**
```sql
;
``` 

### 18. ****

**Query:**
```sql
;
``` 

### 19. ****

**Query:**
```sql
;
``` 

### 20. ****

**Query:**
```sql
;
``` 