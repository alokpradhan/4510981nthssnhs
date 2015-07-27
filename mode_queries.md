Run queries on the `tutorial.billboard_top_100_year_end` database on the [Mode Analytics editor](https://modeanalytics.com/editor).

1. How many years did Mariah Carey have a song in the Top 10?
SELECT year
FROM tutorial.billboard_top_100_year_end
WHERE "group" LIKE 'Mariah Carey' OR "group" ILIKE '% Mariah Carey %'
AND year_rank <= 10

2. A list of all Whitney Houston song titles that didn't rank higher than 20th, in chronological order.
SELECT song_name
FROM tutorial.billboard_top_100_year_end
WHERE "group" LIKE 'Whitney Houston' OR "group" ILIKE '% Whitney Houston %'
AND year_rank >= 20
ORDER BY year asc


3. How many artists have finished a year with the number 1 song?
SELECT COUNT(DISTINCT artist)
FROM tutorial.billboard_top_100_year_end
WHERE year_rank = 1

4. In which year did Ke$ha have the most charted hits, and how many did she have that year? (Just one query...)
SELECT year, COUNT(song_name) AS count
FROM tutorial.billboard_top_100_year_end
WHERE "group" ILIKE 'Ke$ha' OR "group" ILIKE 'Ke$ha %'
GROUP BY year
ORDER BY count DESC
LIMIT 1

5. What is the highest chart position ever reached by Ke$ha's sometime collaborators, the strangely-named "3OH!3"?
SELECT MIN(year_rank)
FROM tutorial.billboard_top_100_year_end
WHERE "group" ILIKE '% 3OH!3' OR "group" ILIKE '3OH!3'


6. "A list of years that had a charted song containing the word "heaven" and a count of the number."
SELECT year, COUNT(song_name)
FROM tutorial.billboard_top_100_year_end
WHERE song_name ILIKE 'heaven %'
OR song_name ILIKE '% heaven'
GROUP BY year







