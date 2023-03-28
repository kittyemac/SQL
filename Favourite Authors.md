# Author Statistics
## I created a small table detailing a few of my favourite authors, including details about them and my favourite book of theirs. I then created a second table listing a few countries, the language of each country, and which continent it belongs to. 

### 1 Create the 'authors' table 
#### 1.1 Define the column headings
```sql
CREATE TABLE authors (id INTEGER PRIMARY KEY, name TEXT, country_of_origin TEXT, favourite_book TEXT, original_language TEXT, book_length INTEGER);
```
#### 1.2 Populate the 'authors' table with values
```sql
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
#### 1.3 A view of the populated 'authors' table
| ID    | name          | country_of_origin| favourite_book | original_language | book_length |
| :------:|:-------------:| :-----:|:-------------:|:-------------:|:-------------:|
|1| Elena Ferrante| Italy| My Brilliant Friend|Italian| 311|
|2| Herman Melville|America|Moby Dick|English|427|
|3| Haruki Murakami|Japan|Kafka on the Shore|Japanese|448|
|4| L. P. Hartley|England|The Go-Between|English|237|
|5| Jane Austen|England|Persuasian|English| 272|
|6| Jane Austen|England|Sense and Sensibility|English|360|
|7| Chimamanda Ngozi Adichie|Nigeria|Half of a Yellow Sun|English|448|
|8| Robert Graves|England|I, Claudius|English|416|
|9| Ryu Murakami|Japan|In the Miso Soup|Japanese|217|
|10| J. M. Coetzee|South Africa|Disgrace|English|220|
|11| Oyinkan Braithwaite|Nigeria|My Sister the Serial Killer|English|226|

### 2 Create the 'continents' table 
#### 2.1 Define the column headings
```sql
CREATE TABLE continents (id INTEGER PRIMARY KEY, country TEXT, language TEXT, continent TEXT);
```
#### 2.2 Populate the 'continents' table with values
```sql
INSERT INTO continents VALUES (1, "England", "English", "Europe");
INSERT INTO continents VALUES (2, "Nigeria", "English", "Africa");
INSERT INTO continents VALUES (3, "Japan", "Japanese", "Asia");
INSERT INTO continents VALUES (4, "Italy", "Italian", "Europe");
INSERT INTO continents VALUES (5, "South Africa", "English", "Africa");
INSERT INTO continents VALUES (6, "America", "English", "North America");
```
#### 2.3 A view of the populated 'continents' table
ID|country|language|continent
:---:|:---:|:---:|:---:
1|England|English|Europe
2|Nigeria|English|Africa
3|Japan|Japanese|Asia
4|Italy|Italian|Europe
5|South Africa|English|Africa
6|America|English|North America

### 3 Querying 

#### 3.1 Run a query 
In this query I wanted to create a new column using `CASE` to determine if my favourite books are novels or novellas based on their page count. I then used `JOIN` to see which continent the author is from. 

```sql
SELECT authors.name, authors.favourite_book,continents.continent,
    CASE
        WHEN book_length > 250 THEN "Novel"
        WHEN book_length < 250 THEN "Novella"
    END as "type"
    FROM authors
    JOIN continents
    ON authors.country_of_origin = continents.country;
```
#### 3.2 Query Results
name	|favourite_book|	continent	|type
:---:|:---:|:---:|:---:
Elena Ferrante	|My Brilliant Friend	|Europe|	Novel
Herman Melville|	Moby Dick|	North America|	Novel
Haruki Murakami|	Kafka on the Shore	|Asia|Novel
L. P. Hartley	|The Go-Between|	Europe	|Novella
Jane Austen|	Persuasian	|Europe|	Novel
Jane Austen	|Sense and Sensibility	|Europe|	Novel
Chimamanda Ngozi Adichie|	Half of a Yellow Sun|	Africa|	Novel
Robert Graves|	I, Claudius	|Europe	|Novel
Ryu Murakami|	In the Miso Soup	|Asia	|Novella
J. M. Coetzee	|Disgrace|	Africa	|Novella
Oyinkan Braithwaite	|My Sister the Serial Killer	|Africa	|Novella
