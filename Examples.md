# SQL Query Examples 📊

This page provides practical examples of common SQL queries, with questions and their corresponding solutions.
Note: Reference the Database Schema Diagram. Multiple solutions accepted

## 🔍 Basic Query solutions

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

### 15. **Write a query to find the first_name, last name and birth date of patients who has height greater than 160 and weight greater than 70**

**Query:**
```sql
SELECT first_name, last_name, birth_date
FROM patients
WHERE height > 160 AND weight > 70;
``` 

### 16. **Write a query to find list of patients first_name, last_name, and allergies where allergies are not null and are from the city of 'Hamilton'**

**Query:**
```sql
SELECT first_name, last_name, allergies
FROM patients
WHERE allergies not null
and city = 'Hamilton';
``` 

### 17. **Show unique birth years from patients and order them by ascending.**

**Query:**
```sql
SELECT DISTINCT YEAR(birth_date) AS birth_year
FROM patients
ORDER BY birth_year ASC;
``` 

### 18. **Show unique first names from the patients table which only occurs once in the list.**

**Query:**
```sql
SELECT first_name 
FROM patients
GROUP BY first_name
HAVING COUNT(first_name) = 1;
``` 

### 19. **Show patient_id and first_name from patients where their first_name start and ends with 's' and is at least 6 characters long.**

**Query:**
```sql
SELECT patient_id, first_name
FROM patients
WHERE first_name LIKE 's%s'
AND LEN(first_name) >= 6;
``` 

### 20. **Show patient_id, first_name, last_name from patients whos diagnosis is 'Dementia'.**

**Query:**
```sql
SELECT p.patient_id, p.first_name, p.last_name
FROM patients p
LEFT JOIN admissions a
On p.patient_id = a.patient_id
Where a.diagnosis = 'Dementia';
``` 

### 21. **Display every patient's first_name. Order the list by the length of each name and then by alphabetically.**

**Query:**
```sql
SELECT first_name
FROM patients
ORDER BY LEN(first_name), first_name;
``` 

### 22. **Show the total amount of male patients and the total amount of female patients in the patients table. Display the two results in the same row.**

**Query:**
```sql
SELECT
	Sum(CASE WHEN gender='M' THEN 1 ELSE 0 END) AS "male_patients",
	Sum(CASE WHEN gender='F' THEN 1 ELSE 0 end) AS "female_patients"
FROM patients;
``` 

### 23. **Show first and last name, allergies from patients which have allergies to either 'Penicillin' or 'Morphine'. Show results ordered ascending by allergies then by first_name then by last_name.**

**Query:**
```sql
SELECT first_name, last_name, allergies
FROM patients
WHERE allergies = "Penicillin" OR allergies = "Morphine"
ORDER BY allergies ASC, first_name, last_name;
``` 

### 24. **Show patient_id, diagnosis from admissions. Find patients admitted multiple times for the same diagnosis.**

**Query:**
```sql
SELECT patient_id, diagnosis
FROM admissions
Group BY patient_id,diagnosis
HAVING count(*) > 1;
``` 

### 25. **Show the city and the total number of patients in the city. Order from most to least patients and then by city name ascending.**

**Query:**
```sql
SELECT city, COUNT(*) AS num_patients
FROM patients
GROUP BY city
ORDER BY num_patients DESC, city asc;;
``` 

### 26. **Show first name, last name and role of every person that is either patient or doctor. The roles are either "Patient" or "Doctor"**

**Query:**
```sql
SELECT first_name,last_name, "Doctor" AS role
FROM doctors
UNION ALL
SELECT first_name, last_name, "Patient" AS role
FROM patients;
``` 

### 27. **Show all allergies ordered by popularity. Remove NULL values from query.**

**Query:**
```sql
SELECT allergies, COUNT(*) AS total_diagnosis
FROM patients
WHERE allergies IS NOT NULL
GROUP BY allergies
ORDER BY total_diagnosis DESC;
``` 

### 28. **Show all patient's first_name, last_name, and birth_date who were born in the 1970s decade. Sort the list starting from the earliest birth_date.**

**Query:**
```sql
SELECT first_name, last_name, birth_date
FROM patients
WHERE birth_date BETWEEN "1970-01-01" AND "1979-12-31"
ORDER BY birth_date ASC;
``` 

### 29. **We want to display each patient's full name in a single column. Their last_name in all upper letters must appear first, then first_name in all lower case letters. Separate the last_name and first_name with a comma. Order the list by the first_name in decending order. EX: SMITH,jane**

**Query:**
```sql
SELECT CONCAT(UPPER(last_name), ",", LOWER(first_name)) AS full_name
FROM patients
ORDER BY first_name DESC;
``` 

### 30. **Show the province_id(s), sum of height; where the total sum of its patient's height is greater than or equal to 7,000.**

**Query:**
```sql
SELECT province_id, SUM(height) AS total_heights
FROM patients
GROUP BY province_id
HAVING sum(height) >= 7000;
``` 

### 31. **Show the difference between the largest weight and smallest weight for patients with the last name 'Maroni'**

**Query:**
```sql
SELECT MAX(weight) - MIN(weight) AS weight_difference
FROM patients
WHERE last_name = 'Maroni';
``` 

### 32. **Show all of the days of the month (1-31) and how many admission_dates occurred on that day. Sort by the day with most admissions to least admissions.**

**Query:**
```sql
SELECT DAY(admission_date) AS day_of_month, COUNT(admission_date) AS total_admissions
FROM admissions
GROUP BY day(admission_date)
ORDER BY total_admissions DESC;
``` 

### 33. **Show all columns for patient_id 542's most recent admission_date.**

**Query:**
```sql
SELECT * 
FROM admissions
WHERE patient_id = 542
ORDER BY admission_date DESC
LIMIT 1;
``` 

### 34. **Show patient_id, attending_doctor_id, and diagnosis for admissions that match one of the two criteria: 1. patient_id is an odd number and attending_doctor_id is either 1, 5, or 19. 2. attending_doctor_id contains a 2 and the length of patient_id is 3 characters.**

**Query:**
```sql
SELECT patient_id, attending_doctor_id, diagnosis
FROM admissions
WHERE 
(patient_id % 2 = 1 AND attending_doctor_id IN (1,5,19))
OR 
(attending_doctor_id LIKE "%2%" AND LEN(patient_id) = 3);
``` 

### 35. ****

**Query:**
```sql
SELECT d.first_name, d.last_name, COUNT(*) AS admissions_total
FROM admissions a
JOIN doctors d
ON a.attending_doctor_id = d.doctor_id
GROUP BY a.attending_doctor_id;
``` 

### 36. **For each doctor, display their id, full name, and the first and last admission date they attended.**

**Query:**
```sql
SELECT 
	doctor_id, 
	first_name || ' ' || last_name AS full_name, 
	MIN(admission_date) AS first_admission_date, 
	MAX(admission_date) AS last_admission_date
FROM admissions a
JOIN doctors ph ON a.attending_doctor_id = ph.doctor_id
GROUP BY doctor_id;;
``` 

### 37. **Display the total amount of patients for each province. Order by descending.**

**Query:**
```sql
SELECT pv.province_name, COUNT(*) AS patient_count
FROM patients p
JOIN province_names pv
ON p.province_id = pv.province_id
GROUP BY pv.province_id
ORDER BY patient_count DESC;
``` 

### 38. **For every admission, display the patient's full name, their admission diagnosis, and their doctor's full name who diagnosed their problem.**

**Query:**
```sql
SELECT
  CONCAT(patients.first_name, ' ', patients.last_name) AS patient_name,
  diagnosis,
  CONCAT(doctors.first_name,' ',doctors.last_name) AS doctor_name
FROM patients
  JOIN admissions ON admissions.patient_id = patients.patient_id
  JOIN doctors ON doctors.doctor_id = admissions.attending_doctor_id;;
``` 

### 39. **display the first name, last name and number of duplicate patients based on their first name and last name. Ex: A patient with an identical name can be considered a duplicate.**

**Query:**
```sql
SELECT first_name, last_name, count(*) AS num_of_duplicates
FROM patients
GROUP BY
  first_name,
  last_name
HAVING COUNT(*) > 1;
``` 

### 40. **Display patient's full name, height in the units feet rounded to 1 decimal, weight in the unit pounds rounded to 0 decimals, birth_date, gender non abbreviated. Convert CM to feet by dividing by 30.48. Convert KG to pounds by multiplying by 2.205.**

**Query:**
```sql
SELECT
    CONCAT(first_name, ' ', last_name) AS 'patient_name', 
    ROUND(height / 30.48, 1) AS 'height "Feet"', 
    ROUND(weight * 2.205, 0) AS 'weight "Pounds"', birth_date,
CASE
	WHEN gender = 'M' THEN 'MALE' ELSE 'FEMALE' 
	END AS 'gender_type'
FROM patients;
``` 

### 41. ****

**Query:**
```sql
SELECT p.patient_id, p.first_name, p.last_name
FROM patients p
LEFT JOIN admissions a
ON p.patient_id = a.patient_id
WHERE a.patient_id IS NULL;
``` 

### 42. ****

**Query:**7
```sql
;
``` 

### 43. ****

**Query:**
```sql
;
``` 

### 44. ****

**Query:**
```sql
;
``` 

### 45. ****

**Query:**
```sql
;
``` 

### 46. ****

**Query:**
```sql
;
``` 

### 47. ****

**Query:**
```sql
;
``` 

### 48. ****

**Query:**
```sql
;
``` 

### 49. ****

**Query:**
```sql
;
``` 

### 50. ****

**Query:**
```sql
;
``` 

### 51. ****

**Query:**
```sql
;
``` 

### 52. ****

**Query:**
```sql
;
``` 