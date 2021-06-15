# Assignment 5 -- Database: Add, Display, Delete records

In this assignment you will create three MySQL database tables and write php scripts to read, insert & delete data. You will be writing several SQL statements and you may find it useful to have a website or SQL notes near you.

The first database table will contain the names of your favorite four movies. The second table will be a list of actors who appear in the movies. The third table will be an associative table that describes the relationship between actors and movies (which actors appear in which movies). Actors and movies have a many-to-many relationship (an actor can be in multiple movies and a movie can have multiple actors).

The samples below use HTML5 validation which is optional.

1.  [DVDTitles.php](http://yorktown.cbe.wwu.edu/sandvig/mis314/assignments/a05/DVDTitles.php) - Create a MySQL database table named dvdtitles. You will be adding information about four (at least) of your favorite movies. It should have the following structure:

| Field Name | Type          | Attributes  |
|------------|---------------|-------------|
| asin       | varchar(15)   | primary key |
| title      | varchar(100)  |             |
| price      | doubles(5, 2) |             |


1.  ASIN is an acronym for "Amazon Standard Identification Number." It is a primary key that Amazon uses for all of its products. You can find ASINs on the product description page on Amazon's web site.

2.  Use [PhpMyAdmin](https://yorktown.cbe.wwu.edu/pma/) to create the table. 

3.  It will be helpful to have some data in the database while you are working on the php page. Add one or two records of data using phpMyAdmin.

4.  Database connection: You will use the same database connection function for all of your scripts. Copy databaseConnection.php [source](http://yorktown.cbe.wwu.edu/sandvig/mis314/lectures/L09/databaseConnection.php.txt) and create a new file named databaseConnection.php. Add your login information. Use your ATUS username for both username and database name. Password is the one you created for mySql.

5.  Modify the code in [mySQL.php](http://yorktown.cbe.wwu.edu/sandvig/mis314/lectures/L09/MySQL.php) ([source](http://yorktown.cbe.wwu.edu/sandvig/mis314/lectures/L09/MySQL.php.txt)) to insert, delete & display (in a table) records from the new table. You will need to modify the include statement to point to the database connection script that you created in the previous step.

6.  I suggest that you start with displaying records in the database and get it working properly before starting on the insert and delete features.

7.  String values in SQL statements are always enclosed within single quotes. ASIN and Title are both strings and require single quotes. For instance, your insert statement will look something like this:
```PHP
    $sql = "Insert into dvdtitles (asin, title, price) VALUES ('$asin', '$title', $price)";
```
8. SQL debugging tip: check your SQL statement before you execute it. Put the following line of code immediately before the mysql_query($strSQL) statement:
```PHP
    echo "SQL: $sql <br>";
```
    Format your page properly using tables or CSS. You may use the HTML from the sample.
9. The src of the images is:
`
    http://images.amazon.com/images/P/XXX.01.MZZZZZZZ.jpg
`
    where XXX is the item's ASIN. The sample source code illustrates image tags.

10. When retrieving ASIN from the querystring remember that ASIN is a string, not a number. Run it through the fCleanString() function rather than the fCleanNumber() function.

11. Once you get your php script working add the ASIN and title for four (or more) of your favorite movies. Go to Amazon's web site to find the ASIN for each.


2. [DVDActors.php](http://yorktown.cbe.wwu.edu/sandvig/mis314/assignments/a05/DVDActors.php) - Add another table to your database named dvdActors. It should have the following structure:

| Field Name | Type        | Attributes                  |
|------------|-------------|-----------------------------|
| actor      | int(5)      | auto_increment, primary key |
| fname      | varchar(20) |                             |
| lname      | varchar(20  |                             |

1.  Copy & modify the previous example to allow adding, deleting and reading of actors.

2.  Add at least two actors for each of your movies.

3.  [DVDActorsTitles.php](http://yorktown.cbe.wwu.edu/sandvig/mis314/assignments/a05/DVDActorsTitles.php) - Create a table of relationships between actors and movie titles. It should have the following structure:

| Field   | Type        | Attributes              |
|---------|-------------|-------------------------|
| asin    | varchar(15) | primary key (composite) |
| actorID | int(5)      | primary key (composite) |


1.  Because this table uses a composite key, the delete statement must reference both the asin and actorID fields. Click "delete" in the sample to see the syntax.

2.  Add data that describes the relationship between your movies and actors.

2.  [DVDListing.php](http://yorktown.cbe.wwu.edu/sandvig/mis314/assignments/a05/DVDListing.php) - Create a join statement that joins data from all three tables. Remember, that field names that are used in more than one table (ASIN, ActorID) must be fully qualified (i.e. dvdtitle.ASIN).

3.  [DVDListingImproved.php](http://yorktown.cbe.wwu.edu/sandvig/mis314/assignments/a05/DVDListingImproved.php) - The previous sql query returns a separate record for each actor. We often want to group results from several records into a single row. There are several way we can achieve this:

    -   Write PHP code to combine artists from multiple database records,
    -   using sql's GROUP BY clause combined with the GROUP_CONCAT() function
    -   executing a separate SQL statement to retrieve the actors for each ASIN
    -   create a mySQL function that returns the actors associated with a given ASIN in a single string and call the function from the SQL statement that retrieves the DVD titles.\
    The easiest and most efficient is the GROUP BY clause combined with the GROUP_CONCAT() function. [Group_Concat()](http://dev.mysql.com/doc/refman/5.0/en/group-by-functions.html#function_group-concat) is a mySQL extension to the SQL standard that concatenates all the values within each group into a single string.

    SQL provides several functions that work in conjunction with GROUP BY. These functions allow us to get information about the grouped records. For instance, the AVG(price) function calculates an average value for a specific field for each grouping, and COUNT(*) returns of the number of records in each group. The GROUP BY clause retrieves the text from grouped fields. For instance, suppose we had three records with the same ASIN and different values for FName (Ann, Barbara, Mary). We could use GROUP BY ASIN to combine these three records into one record and "Select GROUP_CONCAT(FName SEPARATOR ", ") as Names" to return the three names in a new field called "Names." Here is another [example of GROUP_CONCAT()](http://www.zen-cart.com/forum/showthread.php?t=35941).

    In this exercise we are grouping records by ASIN and using GROUP_CONCAT to list in a single field the actor names in each group. Modify the previous exercise to list all the actors for each movie title in one table cell using GROUP BY and Group_Concat.\
    **Steps:**
    -   Copy the SQL statement from the previous exercise and paste it into PHPMYAdmin (under the SQL tab).
    -   At the end of the SQL statement add:\
           GROUP BY DvdActorsTitles.ASIN;
    -   Test the query. It should work but will return only one actor name per ASIN.
    -   In the SELECT clause replace "FName, LName" with:\
           GROUP_CONCAT( Concat( FName, " ", LName ) SEPARATOR ", " ) AS Name
    -   Test the query in PHPMyAdmin. It should return results similar these:

        | ASIN | Title | Price | Name |
        | --- | --- | --- | --- |
        | 6305210411 | Sliding Doors | 9.98 | Gwyneth Paltrow, John Hannah |
        | B00005BKZS | Black Robe | 10.99 | Cate Blanchett, Leonardo DeCaprio |
        | B00080ZG1A | The Aviator | 12.99 | Aden Young, Lothaire Bluteau |
        | B000BSM26Q | Wedding Crashers | 13.99 | Owen Wilson, Vince Vaughn |