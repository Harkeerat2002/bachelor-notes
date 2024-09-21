**Course:** Data Management**  
Name:** Harkeerat Singh Sawhney  
**Date:** 13/04/2022

```
CREATE TABLE Actor (
    A VARCHAR(20) NOT NULL,
    ActorName VARCHAR(20),
    Country VARCHAR(20),
    DBirth DATE,
    CONSTRAINT PK_Actor PRIMARY KEY (A)
);
```

1.   
    (a)
    
```sql
    INSERT INTO
        Actor
    VALUES
        (
            'A1',
            'Daniel Radcliffe',
            'Great Britain',
            '1989-07-02'
        );
    ```
    
    (b)
    
    ```
    INSERT INTO
        Actor
    VALUES
        (
            'A2',
            'Emma Watson',
            'Great Britain',
            '1990-04-15'
        );
    ```
    

  

```
CREATE TABLE Movie (
    M VARCHAR(20) NOT NULL,
    Title VARCHAR(20),
    Director VARCHAR(20),
    DirectorRegion VARCHAR(20) NOT NULL,
    MovieRegion VARCHAR(20) NOT NULL,
    CONSTRAINT PK_Movie PRIMARY KEY (M),
    CONSTRAINT UK_Movie UNIQUE (Title, MovieRegion),
    CONSTRAINT CK_Movie_DirectorRegion CHECK (
        DirectorRegion <> 'Europe'
        OR MovieRegion <> 'Europe'
        AND DirectorRegion <> 'America'
    )
);
```

1.   
    (a)  
    This query “CK_Movie_DirectorRegion is giving an error, because the DirectorRegion is “Europe” whereas the MovieRegion is “America. Hence either the DirectorRegion should be “America” or the MovieRegion should be Europe.
    
    (b)
    
    Again the query “CK_Movie_DirectorRegion” is giving an error, because MovieRegion is “America” while the DirectorRegion Europe. Hence either the DirectorRegion should be “America”, or MovieRegion should be “Europe”
    
    (c)  
    The record would be inserted in the table. Hence MovieRegion is “Europe”.
    
    (d)
    
    This is the same error as 4 (b). MovieRegion is not “Europe” and the DirectorRegion has to be “Europe”.
    
    (e)
    
    This the same error as 4 (b). MovieRegion is not “Europe” and the DirectorRegion has to be “Europe”
    

```
CREATE TABLE ActorMovie (
    A VARCHAR(20) NOT NULL,
    M VARCHAR(20) NOT NULL,
    Cachet DECIMAL(10, 2) NOT NULL,
    MainActor ENUM('Yes', 'No') NOT NULL,
    CONSTRAINT PK_ActorMovie PRIMARY KEY (A, M),
    CONSTRAINT FK_A_Delete FOREIGN KEY (A) REFERENCES Actor(A) ON DELETE CASCADE,
    CONSTRAINT FK_M_Delete FOREIGN KEY (M) REFERENCES Movie(M) ON DELETE CASCADE,
    CONSTRAINT CK_ActorMovie_Cachet CHECK (Cachet > 0.00)
);
```

```
SELECT
    COUNT(DISTINCT A)
FROM
    ActorMovie AS Number
FROM
    Actor,
    ActorMovie
WHERE
    ActorMovie.A = Actor.A
    AND MainActor = 'Yes';
```

```
SELECT
    Title
FROM
    Movie
WHERE
    Director = 'Yates';
```

```
CREATE VIEW GlobalView AS
SELECT
    Actor.A,
    Actor.ActorName,
    Actor.Country,
    ActorMovie.M,
    ActorMovie.Cachet,
    ActorMovie.MainActor,
    Movie.Title,
    Movie.Director,
    Movie.MovieRegion
FROM
    Actor,
    ActorMovie,
    Movie
WHERE
    ActorMovie.A = Actor.A
    AND ActorMovie.M = Movie.M
    AND ActorMovie.Cachet > 0.00
    AND ActorMovie.MainActor = 'Yes';
```

```
SELECT
    COUNTRY AS COUNTRY,
    COUNT(*) AS NUMBER_OF_ROLES
FROM
    Actor,
    ActorMovie,
    Movie
WHERE
    ActorMovie.A = Actor.A
    AND ActorMovie.M = Movie.M
    AND Movie.Title LIKE 'HP%'
    AND ActorMovie.Cachet > 0.00
    AND ActorMovie.MainActor = 'Yes'
GROUP BY
    COUNTRY
ORDER BY
    NUMBER_OF_ROLES DESC;
```

```
SELECT
    DISTINCT Title
FROM
    Movie,
    Actor,
    ActorMovie
WHERE
    ActorMovie.A = Actor.A
    AND ActorMovie.M = Movie.M
    AND Actor.Country = 'Great Britain'
    AND ActorMovie.MainActor = 'Yes';
```

```
SELECT
    Director,
    SUM(Cachet) AS TOTAL_CASH
FROM
    Actor,
    ActorMovie,
    Movie
WHERE
    ActorMovie.A = Actor.A
    AND ActorMovie.M = Movie.M
    AND Actor.ActorName = 'Emma Watson'
GROUP BY
    Actor.ActorName,
    Director;
```

```
SELECT
    Title
FROM
    Movie,
    Actor,
    ActorMovie
WHERE
    ActorMovie.A = Actor.A
    AND ActorMovie.M = Movie.M
    AND Actor.ActorName = 'Daniel Radcliffe'
    AND Movie.Title IN (
        SELECT
            Title
        FROM
            Movie,
            Actor,
            ActorMovie
        WHERE
            ActorMovie.A = Actor.A
            AND ActorMovie.M = Movie.M
            AND Actor.ActorName = 'Rupert Grint'
    );
```

```
UPDATE
    Movie
SET
    Director = 'Columbus EU'
WHERE
    Director = 'Columbus'
    AND DirectorRegion = 'Europe';

UPDATE
    Movie
SET
    Director = 'Columbus US'
WHERE
    Director = 'Columbus'
    AND DirectorRegion = 'America';
```

```
GRANT
SELECT
    ON Movie TO Ribo;
```

1.   
    **ON DELETE CASCADE:** This means that on the deletion, the tuples which is containing the key would also be deleted. The rows which are refereed by the keys would be removed, leading to the keys referring to the deleted rows.
    
    **ON DELETE SET NULL:** This means that when deleted, the tuples which is containing the key would have the foreign key replaced by null.