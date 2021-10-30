CREATE TABLE movies (
	movie_id INTEGER PRIMARY KEY,
	movie_name TEXT NOT NULL,
	actor_name TEXT NOT NULL,
	actress_name TEXT NOT NULL,
	release_year TEXT NOT NULL,
	director_name TEXT NOT NULL

);

CREATE TABLE groups (
   group_id INTEGER PRIMARY KEY,
   name TEXT NOT NULL
);

CREATE TABLE movie_groups(
   movie_id INTEGER,
   group_id INTEGER,
   PRIMARY KEY (movie_id, group_id),
   FOREIGN KEY (movie_id) 
      REFERENCES movies (movie_id) 
         ON DELETE CASCADE 
         ON UPDATE NO ACTION,
   FOREIGN KEY (group_id) 
      REFERENCES groups (group_id) 
         ON DELETE CASCADE 
         ON UPDATE NO ACTION
);

SELECT DISTINCT groups
FROM table
  JOIN table ON join_condition
WHERE row_filter
ORDER BY column
LIMIT count OFFSET offset
GROUP BY column
HAVING group_filter;

SELECT
	movie_id,
	movie_name,
	actor_name,
	actress_name
	release_year,
	director_name
FROM
	table;
