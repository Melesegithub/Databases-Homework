# Class Database

## Submission

Below you will find a set of tasks for you to complete to set up a databases of students and mentors.

To submit this homework write the correct commands for each question here:

```sql


```

When you have finished all of the questions - open a pull request with your answers to the `Databases-Homework` repository.

## Task

1. Create a new database called `cyf_classes` (hint: use `createdb` in the terminal)
   ` sudo -u postgres createdb cyf_classes`
2. Create a new table `mentors`, for each mentor we want to save their name, how many years they lived in Glasgow, their address and their favourite programming language.
   ` CREATE TABLE mentors ( id SERIAL PRIMARY KEY, name VARCHAR(255), number_of_years_in_Glasgow INTEGER, address VARCHAR(255), programming_language VARCHAR(255))`
3. Insert 5 mentors in the `mentors` table (you can make up the data, it doesn't need to be accurate ;-)).
   ` INSERT INTO mentors (name, number_of_years_in_Glasgow, address, programming_language) VALUES ('John',8,'20 High Street', 'Java')`

` INSERT INTO mentors (name, number_of_years_in_Glasgow, address, programming_language) VALUES ('Michel',2,'20 Low Street', 'C')`

` INSERT INTO mentors (name, number_of_years_in_Glasgow, address, programming_language) VALUES ('Aster',3,'20 Cresent Street', 'C#')`

` INSERT INTO mentors (name, number_of_years_in_Glasgow, address, programming_language) VALUES ('Melese',9,'20 kenni Street', 'Python')`

` INSERT INTO mentors (name, number_of_years_in_Glasgow, address, programming_language) VALUES ('Scot',22,'20 Argile Street', 'JavaScript')` 4. Create a new table `students`, for each student we want to save their name, address and if they have graduated from Code Your Future.
` CREATE TABLE students ( id SERIAL PRIMARY KEY, name VARCHAR(255), address VARCHAR(255), graduated_from_CYF VARCHAR(255))` 5. Insert 10 students in the `students` table.

` INSERT INTO students (name, address, graduated_from_CYF) VALUES ('Kalid','Hope Street','No')`
` INSERT INTO students (name, address, graduated_from_CYF) VALUES ('Daniel','Regen Street','Yes')`
` INSERT INTO students (name, address, graduated_from_CYF) VALUES ('Mohammed','Duke Street','Yes')`
` INSERT INTO students (name, address, graduated_from_CYF) VALUES ('Nasir','Argile Street','Yes')`
` INSERT INTO students (name, address, graduated_from_CYF) VALUES ('Christina','Jamaica Street','Yes')`
` INSERT INTO students (name, address, graduated_from_CYF) VALUES ('Tosin','Western Street','Yes')`
` INSERT INTO students (name, address, graduated_from_CYF) VALUES ('Joy','Bochanan Street','Yes')`
` INSERT INTO students (name, address, graduated_from_CYF) VALUES ('Melese','Kennishead Street','Yes')`
` INSERT INTO students (name, address, graduated_from_CYF) VALUES ('Robert','Hope Street','No')`
` INSERT INTO students (name, address, graduated_from_CYF) VALUES ('Scot','Hope Street','No')`

6. Verify that the data you created for mentors and students are correctly stored in their respective tables (hint: use a `select` SQL statement).
   ` SELECT * FROM mentors;`
   ` SELECT * FROM mentors WHERE name='Scot';`

` SELECT * FROM students;`
` SELECT * FROM students WHERE name='Tosin';` 7. Create a new `classes` table to record the following information:

- A class has a leading mentor
- A class has a topic (such as Javascript, NodeJS)
- A class is taught at a specific date and at a specific location
  ` CREATE TABLE classes ( id SERIAL PRIMARY KEY, mentor_name VARCHAR(255), topic VARCHAR(255), date DATE,location VARCHAR(255))`

8. Insert a few classes in the `classes` table
   ` INSERT INTO classes (mentor_name, topic, date, location) VALUES ('Doglas','Module Js','2023-05-23','KingsPark')`;
   ` INSERT INTO classes (mentor_name, topic, date, location) VALUES ('Michel','Responsive web design','2023-06-12','Mitchel Library')`;
   `INSERT INTO classes (mentor_name, topic, date, location) VALUES ('Dara','PD Module','2023-05-15','Glasgow caledonial')`;
9. We now want to store who among the students attends a specific class. How would you store that? Come up with a solution and insert some data if you model this as a new table.  
   ` ALTER TABLE students ADD COLUMN course VARCHAR(255)`
   `  UPDATE students SET course = 'Responsive web design' WHERE name = 'Melese';`
   `  UPDATE students SET course = 'Module JS' WHERE name = 'Daniel';`
   `  UPDATE students SET course = 'Module JS' WHERE name = 'Mohammed';`
   `  UPDATE students SET course = 'Module JS' WHERE name = 'Nasir';`
   `  UPDATE students SET course = 'PD Module' WHERE name = 'Tosin';`
   `  UPDATE students SET course = 'PD Module' WHERE name = 'Christina';`
   `  UPDATE students SET course = 'PD Module' WHERE name = 'Joy';`
10. Answer the following questions using a `select` SQL statement:
    - Retrieve all the mentors who lived more than 5 years in Glasgow
      `SELECT * FROM mentors WHERE number_of_years_in_Glasgow >5`
    - Retrieve all the mentors whose favourite language is Javascript
      `SELECT * FROM mentors WHERE programming_language='Javascript'`
    - Retrieve all the students who are CYF graduates
      `SELECT * FROM students WHERE graduated_from_CYF='Yes' `
    - Retrieve all the classes taught before June this year
      ` SELECT * FROM classes WHERE EXTRACT(MONTH FROM classes) < 6`
    - Retrieve all the students (retrieving student ids only is fine) who attended the Javascript class (or any other class that you have in the `classes` table).
      ` SELECT * FROM students WHERE course='Javascript'`
