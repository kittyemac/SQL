-- Create table about authors and your favourite book of theirs 
```sql
CREATE TABLE authors (id INTEGER PRIMARY KEY, name TEXT, country_of_origin TEXT, favourite_book TEXT, original_language TEXT, favourite_book_length INTEGER);

INSERT INTO authors VALUES (1, "Elena Ferrante", "Italy", "My Brilliant Friend","Italian", 311);
INSERT INTO authors VALUES (2, "Herman Melville", "America", "Moby Dick", "English", 427);
INSERT INTO authors VALUES (3, "Haruki Murakami", "Japan", "Kafka on the Shore", "Japanese", 448);
INSERT INTO authors VALUES (4, "L. P. Hartley", "England", "The Go-Between", "English", 237);
INSERT INTO authors VALUES (5, "Jane Austen", "England", "Persuasian", "English", 272);
INSERT INTO authors VALUES (6, "Jane Austen", "England", "Sense and Sensibility","English", 360);
INSERT INTO authors VALUES (7, "Chimamanda Ngozi Adichie", "Nigeria", "Half of a Yellow Sun", "English", 448);
INSERT INTO authors VALUES (8, "Robert Graves", "England", "I, Claudius", "English", 416);
INSERT INTO authors VALUES (9, "Ryu Murakami", "Japan", "In the Miso Soup", "Japanese", 217);
INSERT INTO authors VALUES (10, "J. M. Coetzee", "South Africa", "Disgrace", "English", 220);
INSERT INTO authors VALUES (11, "Oyinkan Braithwaite", "Nigeria", "My Sister the Serial Killer", "English", 226);
```
CREATE TABLE continents (id INTEGER PRIMARY KEY, country TEXT, language TEXT, continent TEXT);

INSERT INTO continents VALUES (1, "England", "English", "Europe");
INSERT INTO continents VALUES (2, "Nigeria", "English", "Africa");
INSERT INTO continents VALUES (3, "Japan", "Japanese", "Asia");
INSERT INTO continents VALUES (4, "Italy", "Italian", "Europe");
INSERT INTO continents VALUES (5, "South Africa", "English", "Africa");
INSERT INTO continents VALUES (6, "America", "English", "North America");

-- create a database with a new colomn describing if the books are novels or novellas based on their length, and join with continents to show the author's continent of origin

SELECT authors.name, authors.favourite_book,continents.continent,
    CASE
        WHEN favourite_book_length > 250 THEN "Novel"
        WHEN favourite_book_length < 250 THEN "Novella"
    END as "type"
    FROM authors
    JOIN continents
    ON authors.country_of_origin = continents.country;
