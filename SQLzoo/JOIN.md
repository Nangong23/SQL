JOIN

10.

```SQL
SELECT 
	stadium, 
	COUNT(player)
FROM game 
JOIN goal ON id = matchid
GROUP BY stadium
```

11.

```sql
SELECT 
	matchid,
	mdate, 
	COUNT(player)
FROM game JOIN goal ON matchid = id 
WHERE (team1 = 'POL' OR team2 = 'POL')
GROUP BY matchid, mdate
```

12.

```sql
SELECT 
	matchid,
	mdate, 
	COUNT(player)
FROM game
JOIN goal ON id=matchid
WHERE teamid='GER'
GROUP BY matchid, mdate
```

13.

```SQL
SELECT 
	mdate,
  	team1,
  	SUM(CASE WHEN teamid=team1 THEN 1 ELSE 0 END) score1,
  	team2,
  	SUM(CASE WHEN teamid=team2 THEN 1 ELSE 0 END) score2
FROM game 
LEFT JOIN goal ON matchid = id 
GROUP BY mdate, matchid, team1, team2
```

