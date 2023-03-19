# MORE  JOIN

1.

```sql
SELECT 
	id, 
	title
FROM movie
WHERE yr=1962
```

2.

```sql
SELECT yr
FROM movie
WHERE title='Citizen Kane'

```

3.

```sql
SELECT 
	id, 
	title, 
	yr
FROM movie
WHERE title LIKE 'Star Trek%'
ORDER BY yr

```

4.

```sql
SELECT id
FROM actor
WHERE name='Glenn Close'
```

5.

```sql
SELECT id
FROM movie
WHERE title = 'Casablanca'
```

6.

```sql
SELECT name
FROM actor a
LEFT JOIN casting c ON (a.id=c.actorid)
WHERE c.movieid = 11768

```

7.

```sql
SELECT name
FROM casting c
LEFT JOIN movie m ON c.movieid=m.id
LEFT JOIN actor a ON c.actorid=a.id
WHERE m.title = 'Alien'
```

8.

```sql
SELECT title
FROM casting c
LEFT JOIN movie m ON c.movieid=m.id
LEFT JOIN actor a ON c.actorid=a.id
WHERE a.name = 'Harrison Ford'
```

9.

```sql
SELECT  
	title
FROM casting c
LEFT JOIN movie m ON c.movieid=m.id
LEFT JOIN actor a ON c.actorid=a.id
WHERE (a.name = 'Harrison Ford') AND (c.ord <> 1)
```

10.

```sql
SELECT  
	m.title, 
	a.name
FROM casting c
LEFT JOIN movie m ON c.movieid=m.id
LEFT JOIN actor a ON c.actorid=a.id
WHERE m.yr=1962 AND c.ord=1

```

11.

```sql
SELECT 
	yr,
	COUNT(title) 
FROM movie 
JOIN casting ON movie.id=movieid
JOIN actor   ON actorid=actor.id
WHERE name='Rock Hudson'
GROUP BY yr
HAVING COUNT(title) > 2
```

12.

```sql
SELECT 
	m.title, 
	a.name 
FROM casting c
JOIN movie m ON c.movieid=m.id
JOIN actor a ON c.actorid=a.id
WHERE movieid IN (
  SELECT movieid FROM actor a JOIN casting c ON a.id=c.actorid
  WHERE name='Julie Andrews')
AND c.ord = 1

```

13.

```sql
SELECT 
	name 
FROM actor 
JOIN casting ON actorid=actor.id
WHERE ord = 1
GROUP BY name
HAVING COUNT(name) >= 15
```



14.

```sql
SELECT 
	title, 
	COUNT(actorid)  
FROMmovie 
JOIN casting ON movie.id=movieid
JOIN actor   ON actorid=actor.id
WHERE yr = 1978
GROUP BY title
ORDER BY COUNT(actorid) DESC, title
```



15.

```sql
SELECT 
	a.name 
FROM casting c
LEFT JOIN movie m ON c.movieid=m.id
LEFT JOIN actor a ON c.actorid=a.id
WHERE movieid IN (
  	SELECT movieid 
    FROM actor a 
    JOIN casting c ON a.id=c.actorid
 	WHERE name='Art Garfunkel') AND a.name <> 'Art Garfunkel'
```

