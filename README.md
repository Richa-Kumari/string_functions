# string_functions
Part of UDEMY SQL course

-- create database bookshop
CREATE DATABASE bookshop;


-- use database
USE bookshop;


-- create table books
CREATE TABLE books 
	(
		book_id INT NOT NULL AUTO_INCREMENT,
		title VARCHAR(100),
		author_fname VARCHAR(100),
		author_lname VARCHAR(100),
		released_year INT,
		stock_quantity INT,
		pages INT,
		PRIMARY KEY(book_id)
	);


-- Insert values into the table "books"
INSERT INTO books (title, author_fname, author_lname, released_year, stock_quantity, pages)
VALUES
('The Namesake', 'Jhumpa', 'Lahiri', 2003, 32, 291),
('Norse Mythology', 'Neil', 'Gaiman',2016, 43, 304),
('American Gods', 'Neil', 'Gaiman', 2001, 12, 465),
('Interpreter of Maladies', 'Jhumpa', 'Lahiri', 1996, 97, 198),
('A Hologram for the King: A Novel', 'Dave', 'Eggers', 2012, 154, 352),
('The Circle', 'Dave', 'Eggers', 2013, 26, 504),
('The Amazing Adventures of Kavalier & Clay', 'Michael', 'Chabon', 2000, 68, 634),
('Just Kids', 'Patti', 'Smith', 2010, 55, 304),
('A Heartbreaking Work of Staggering Genius', 'Dave', 'Eggers', 2001, 104, 437),
('Coraline', 'Neil', 'Gaiman', 2003, 100, 208),
('What We Talk About When We Talk About Love: Stories', 'Raymond', 'Carver', 1981, 23, 176),
("Where I'm Calling From: Selected Stories", 'Raymond', 'Carver', 1989, 12, 526),
('White Noise', 'Don', 'DeLillo', 1985, 49, 320),
('Cannery Row', 'John', 'Steinbeck', 1945, 95, 181),
('Oblivion: Stories', 'David', 'Foster Wallace', 2004, 172, 329),
('Consider the Lobster', 'David', 'Foster Wallace', 2005, 92, 343);


-- Display table books
SELECT * FROM books;

-- Displays the structure of the table
DESC books;

-- CONCAT function
SELECT CONCAT(author_fname, ' ', author_lname) AS author_fullname FROM books;

-- CONCAT_WS (with separator) mention the separating character at first 
SELECT CONCAT_WS('-', title, author_fname, author_lname) FROM books;

-- SUBSTRING("Value", Starting character. no of characters)
SELECT SUBSTRING(title, 4,9) from books;

SELECT SUBSTRING(title, 4) FROM books;

-- Using CONCAT and SUBSTR togther
SELECT CONCAT(SUBSTR(title, 2,8), '....') AS short_name FROM books;

-- Get first words of author_fname and author_lname and separate them with a . 
SELECT 
  CONCAT(
    SUBSTR(author_fname, 1, 1), 
    '.', 
    SUBSTR(author_lname, 1, 1), 
    '.'
  ) AS short 
FROM 
  books;
 
 -- REPLACE( text to replace, og_text, replaced text)
 SELECT 
  REPLACE(title, " ", "-") 
from 
  books;

-- REVERSE(text)
SELECT 
 REVERSE(author_fname) 
FROM 
 books;

 -- Char_length
 SELECT 
  CONCAT(
    author_lname, 
    ' is ', 
    CHAR_LENGTH(author_lname), 
    ' characters long'
  ) 
FROM 
  books;

-- UPPER and LOWER (UCASE & LCASE)
SELECT 
 CONCAT('MY FAVORITE BOOK IS ', UPPER(title)) 
FROM
 books;
 
SELECT
 CONCAT('MY FAVORITE BOOK IS ', LOWER(title)) 
FROM
 books;

 -- INSERT(String, position where to insert, no of characters to replace, wat to insert)
 SELECT
  INSERT(title, 3, 3, " WTH ") 
from 
 books;

 -- String challenges
 -- REVERSE & UPPERCASE
 SELECT 
 REVERSE(
     UPPER("Why does my cat look at me with such hatred?")
     );

-- Guess the answer
 SELECT 
  REPLACE(
      CONCAT('I',' ','Like',' ','Cats'),
      ' ',
      '-'
      );

 -- REPLACE " " to "->"
 SELECT 
 REPLACE(title, ' ','->') AS title 
 from 
  books;

 -- Display last name as forward and reverse it as backward
 SELECT 
 author_lname AS Forward, 
  REVERSE(author_lname) AS Backward
FROM
 books;

 -- Display author's full name in uppercase AS full name in caps
 SELECT
  CONCAT(
      UPPER(author_fname), ' ', UPPER(author_lname)
  ) AS full_name_in_caps
FROM 
 books;

 -- CONCAT title and release date with a text in the middle
 SELECT
  CONCAT(
    title, ' was released in the year ', released_year
  ) AS blurb
  FROM
   books;

   --Display title and length of each title
   SELECT
    title,
    CHAR_LENGTH(title) AS character_count
  FROM
   books;

   -- Display three columns
   -- First: First ten char of title along with ...books as short_title
   -- Second: Author'last name, a comma, author's first name as author
   -- Third: quantity along with "in stock"
   SELECT
    CONCAT(
     SUBSTR(title, 1, 10), '...'
    ) AS short_title,
    CONCAT(
    author_lname, ', ', author_fname
    ) AS author,
    CONCAT(
      stock_quantity, " in stock"
    ) As quantity
  FROM
   books;
