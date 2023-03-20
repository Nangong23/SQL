# NULL

[toc]



## 1

```sql
SELECT 
	teacher.name
FROM teacher
LEFT JOIN dept ON teacher.dept = dept.id
WHERE dept IS NULL
```



## 2

```sql
SELECT 
	teacher.name
FROM teacher
LEFT JOIN dept ON teacher.dept = dept.id
WHERE dept IS NULL
```



## 3

```sql
SELECT 
	teacher.name, 
	dept.name
FROM teacher
LEFT JOIN dept ON teacher.dept = dept.id

```



## 4

```sql
SELECT 
	teacher.name, 
	dept.name
FROM teacher
RIGHT JOIN dept ON teacher.dept = dept.id

```



## 5

```sql
SELECT 
	name, 
	COALESCE(mobile, '07986 444 2266')
FROM teacher
```



## 6

```SQL
SELECT 
	teacher.name, 
	COALESCE(dept.name, 'None')
FROM teacher
LEFT JOIN dept ON teacher.dept = dept.id

```



## 7

```sql
SELECT 
	COUNT(name), 
	COUNT(mobile)
FROM teacher
```



## 8

```sql
SELECT  
	dept.name, 
	COUNT(teacher.name)
FROM teacher
RIGHT JOIN dept ON teacher.dept = dept.id
GROUP BY dept.name

```



## 9

```sql
SELECT  
	teacher.name,
   	CASE WHEN dept.id = 1 OR dept.id = 2 THEN 'Sci'
    	 ELSE 'Art'
    END
FROM teacher
LEFT JOIN dept ON teacher.dept = dept.id

```



## 10

```sql
SELECT  
	teacher.name,
  	CASE WHEN dept.id IN (1, 2) THEN 'Sci'
         WHEN dept.id = 3  THEN 'Art'
         ELSE 'None'
 	END
FROM teacher
LEFT JOIN dept ON teacher.dept = dept.id


```

