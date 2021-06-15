# Assignment 6 -- SQL: Queries & Updating

This first part of this assignment uses three tables: geekProducts, geekCategories and geekProductCategories. The tables have the fields shown below.

To add these tables to your mySQL database, login into phpMyAdmin, click the "SQL" tab, paste this [phpMyAdmin SQL dump](http://yorktown.cbe.wwu.edu/sandvig/mis314/assignments/a06/geekProductsSQLDump.txt) into the query field and click the Go button.

The first five exercises all use the same the same database. It would be a good idea to put the connection information into a separate file and use an include statement to import it into each php script. This eliminates duplicate connection information.

![ER Diagram](https://yorktown.cbe.wwu.edu/sandvig/imagesNewer/GeekProducts.jpg)

Product images are available in three sizes. The size is specified by the image prefix: t_, m_, and L_. For instance the three sizes for the caffeine mug are: t_caffeine-mug.jpg, m_caffeine-mug.jpg, and L_caffeine-mug.jpg.

All of your php pages should initially display neatly (no partial tables or incorrect query results), respond gracefully when no records are found, and handle incorrect user entries. You may add additional features, but your pages should have at least as much functionality as the examples.

**Debugging Tip**: If you have problems debugging a SQL statement try running it directly in phpMyAdmin. Echo the SQL to the browser, copy it, and paste into phpMyAdmin under the SQL tab. Once you get it working inside phpMyAdmin then return it to the PHP script. This approach simplifies the debugging process by separating SQL problems from PHP problems.

1.  [ProductsByPrice.php](http://yorktown.cbe.wwu.edu/sandvig/mis314/assignments/a06/ProductsByPrice.php) - List all products under a specific price, sorted by price (primary) and name (secondary). You may wish to use [mySQL.php](http://yorktown.cbe.wwu.edu/sandvig/mis314/lectures/L09/MySQL.php) ([source](http://yorktown.cbe.wwu.edu/sandvig/mis314/lectures/L09/MySQL.php.txt)) as a template. Look in the sample's source code to see the images URLs.

2.  [ProductSearch.php](http://yorktown.cbe.wwu.edu/sandvig/mis314/assignments/a06/ProductSearch.php) - This page searches the Name field and returns all records that contain any part of the query in the product name. For instance, a search for "ff" would return "coffee" and "caffeine." The SQL statement uses wildcards with the syntax:
`
    "WHERE Name LIKE '%$query%' "
`
    where $query is the string entered by the user.

3.  [RandomProduct.php](http://yorktown.cbe.wwu.edu/sandvig/mis314/assignments/a06/RandomProduct.php) - Display a random selected product from the database. Use the long product description and the medium size images. The following SQL statement randomly orders the records in the database and returns the first record:
`
    select ItemID, Name, LongDesc, Image, price from geekproducts order by rand() limit 1;
`

4.  [ListCategories.php](http://yorktown.cbe.wwu.edu/sandvig/MIS314/Assignments/A06/ListCategories.php) - List the product categories as hyperlinks and display the name of the selected category. The SQL query uses the "DISTINCT" keyword to sort the items and remove any duplicate category names.

-   Optional: Improve the menu by using "group by" to list the number of items in each category ([sample](http://yorktown.cbe.wwu.edu/sandvig/MIS314/Assignments/A06/ProductCategoriesCount.php?))

6.  **[CategoryItems.php](http://yorktown.cbe.wwu.edu/sandvig/MIS314/Assignments/A06/CategoryItems.php)** - Display the items in each product category.  Copy the previous exercise and add a second query to retrieve the items in the selected category. The SQL statement joins the tables geekProducts and geekProductCategories on the field ItemID. Display the Name, price, thumbnail image and short product description.

7.  [CRUD.php](http://yorktown.cbe.wwu.edu/sandvig/mis314/assignments/a06/CRUD.php) - In this exercise you will add update capability to the basic mySQL script demonstrated in class: [mySQL.php](http://yorktown.cbe.wwu.edu/sandvig/MIS314/lectures/L09/mySQL.php) ([source](http://yorktown.cbe.wwu.edu/sandvig/MIS314/lectures/L09/mySQL.php.txt)). Steps:
    1.  Create a new database table using phpMyAdmin. Name the table tblCustomers and give it three fields:

| Field Name | Type    | Length/Values | Index   | Auto_Increment |
|------------|---------|---------------|---------|----------------|
| custID     | INT     | -             | Primary | yes            |
| nameL      | varchar | 50            | -       | -              |
| nameF      | varchar | 50            | -       | -              |


    2.  Copy and paste the basic mySQL script into a file named CRUD.php and get it working.
    3.  Updating database records is a two step process. The first step retrieves the existing information and populates the textboxs. The second step writes the updated information back to the database.

        **Step 1: Populating the textboxes:**

        1.  Add an update link (similar to the delete link) that passes a parameter named "updateID".
        2.  The customer data must be retrieved from the database before the textboxes are rendered. Move the code for connecting and selecting the database to a location above the form.
        3.  Write code to retrieve the customer data and assign the data to local variables named $nameL2 and $nameF2 (using slightly different variable names than those used to get nameL and NameF from the querystring).
        4.  Populate the textboxes using the syntax:\
            <input type="text" name="nameF" value="<?php echo $nameF2; ?>">
        5.  Test your code to make sure it is populating the textboxes.

        **Step 2: Updating the database.**

        1.  A flag is needed to indicate that the page is in the update step of the process. The updateID also needs be be saved. Both issues can be solved by storing the updateID in a hidden form field. Add a hidden field named updateID2 and populate it with $updateID (which is custID).
        2.  Write an if statement that checks for updateID2 in the querystring and executes an UPDATE SQL statement.
        3.  Fix: the Insert code will be triggered by the update because the textboxes contain data. Modify the if statement that triggers the insert to check that $updateID2 is empty.