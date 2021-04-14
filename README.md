# SQL-FINAL-PROJECT
SQL Final 
Directions
Welcome to the Final Project for the SQL course! Great job making it this far! This Final Project will be different from the Hands-On projects you have previously seen in a couple of different ways. For the Final Project, you will be putting together the numerous topics you have learned into one large project. It is designed to mimic real problems which you may face in your career, so it may be a challenge for you and will also take several hours. Take this project step-by-step and be aware that the project description below is written to be a bit less specific than previous Hands-Ons. The Final Project is supposed to challenge you to do some problem solving to figure out how to accomplish a task. You can always review past lessons or use a Google search if needed. Please read through the following setup instructions before you start the project. Good luck!

Setup
This Final Project is structured into three parts, and each part may ask you to run multiple queries. After each query, please take a screenshot of the MySQL Workbench output and add it to a Word document (or an equivalent) and name this file SQL-FinalProject. This way, you will be able to submit your answers to each part all at once.

For this project, you will be working with the same database you have been using throughout this course.

Good luck!

Part 1
Run a query that creates a viewer table that has the following columns: viewer_id, first_name, last_name, email. Make sure the viewer_id is the primary key and auto increments.
Add the following customers:
Name	Email
Kenneth Davis	kenneth.davis@gmail.com
David Shirley	david.shirley@gmail.com
Gaby Garcia	gaby.garcia@gmail.com
Donna Bumbleton	donna.bumbleton@gmail.com
Run a query to see all of the new customers within the database.
Additional Info!
For an example of creating views, watch this workshop: Views.

Part 2
Run the following SQL query to add a new table into the database:
CREATE TABLE sakila.StreamingServiceQueue(
    queue_id INTEGER PRIMARY KEY AUTO_INCREMENT,
    genre NVARCHAR(50) NOT NULL,
    filmTitle NVARCHAR(50) NOT NULL,
    streamAvailable BOOLEAN CHECK(streamAvailable IN (true, false))
)
Next, run the following insert statements to add some data to the Products table:
-- query 1
INSERT INTO sakila.StreamingServiceQueue (genre, filmTitle, streamAvailable)
VALUES ("Movies based on books","The Breadwinner", true)

-- query 2
INSERT INTO sakila.StreamingServiceQueue (genre, filmTitle, streamAvailable)
VALUES ("Emotional","Roma", false)

-- query 3
INSERT INTO sakila.StreamingServiceQueue (genre, filmTitle, streamAvailable)
VALUES ("Campy","To Wong Foo, Thanks for Everything Julie Newmar", true)

-- query 4
INSERT INTO sakila.StreamingServiceQueue (genre, filmTitle, streamAvailable)
VALUES ("Critically Acclaimed","A Single Man", true)
Run a query to see all of the films in your Streaming Service queue.
Part 3
Run the following SQL query to add a new table into the database:
CREATE TABLE sakila.WatchedList(
    watch_id INTEGER PRIMARY KEY AUTO_INCREMENT,
    queue_id INTEGER NOT NULL,
    viewer_id INTEGER NOT NULL,
    FOREIGN KEY(viewer_id) REFERENCES sakila.viewer(viewer_id),
    FOREIGN KEY(queue_id) REFERENCES sakila.StreamingServiceQueue(queue_id)
)
Next, run the following insert statements to add some data to the WatchedList table:
-- query 1
INSERT INTO sakila.WatchedList (viewer_id, queue_id)
VALUES (1, 2)

-- query 2
INSERT INTO sakila.WatchedList (viewer_id, queue_id)
VALUES (2, 1)

-- query 3
INSERT INTO sakila.WatchedList (viewer_id, queue_id)
VALUES (3, 2)

-- query 4
INSERT INTO sakila.WatchedList (viewer_id, queue_id)
VALUES (4, 1)
Lastly, run a query to see the customer's full name, their email address, and their watch_id as well as the genre and title of the film they watched. The list of customers should be ordered in alphabetical order by their last name.
