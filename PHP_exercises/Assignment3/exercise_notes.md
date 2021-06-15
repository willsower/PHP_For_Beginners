# Assignment 3 -- Control structures, Functions

You may use the HTML from the samples.

1.  [ForLoop.php](http://yorktown.cbe.wwu.edu/sandvig/mis314/assignments/a03/ForLoop.php) -- Use a for loop ([w3Schools example](http://www.w3schools.com/php/php_looping_for.asp)) that iterates the number of times specified by the user.

2.  [ForLoopTable.php](http://yorktown.cbe.wwu.edu/sandvig/mis314/assignments/A03/ForLoopTable.php) --Row data is usually displayed in a table. Modify the previous exercise to write your script output to a table.

3.  [ForLoopNested.php](http://yorktown.cbe.wwu.edu/sandvig/mis314/assignments/a03/ForLoopNested.php) -- Add some columns to your table. Copy the previous exercise and modify it to write a table with multiple rows and columns. Write the row and column number in each cell. 

-   Tip: Modify the previous exercise by nesting a for{} loop inside the existing for{} loop . The inner loop will produce the columns.

5.  [ValidInput.php](http://yorktown.cbe.wwu.edu/sandvig/mis314/assignments/a03/ValidInput.php) -- It is important to validate all user entries so that invalid data does not cause our script to crash or misbehave. Modify this script to alert the user if they input a non-numeric input or a value greater than 10. Use the [is_numeric()](http://us2.php.net/is_numeric) function to check for numeric data. Us an if statement to check for numeric and to check that the values are within the range 1 to 10 (inclusive). It will look something like this:
```PHP
$rows = $_GET['rows'];
if (!empty($rows)) {
        //validate with is_numeric and < > tests
        if(test1 && test2 && test3){
        //valid entry
        //use the value
        }
        else {
        //invalid entry
        echo "Please enter a number 1-10";
        }
}
```
6.  [SalesCalc.php](http://yorktown.cbe.wwu.edu/sandvig/mis314/assignments/a03/SalesCalc.php) -- Write a script that computes the sales information shown in the example. Validate the form input data to make sure it is numeric. Do not show a warning when the page initially loads. Tips:
    -   Use two nested if statements to validate the data as in the previous exercise. The first checks to see if anything has been entered and does not produce a warning if empty (for when the page initially loads). The second checks the datatype and produces a warning if not numeric. The HTML table that displays the calculations is inside the code block for the if statements.
    -   Use the number_format() function to format the numeric output in a currency format. Google "php number_format" for documentation.

7.  [FontPicker.php](http://yorktown.cbe.wwu.edu/sandvig/mis314/Assignments/A03/FontPicker.php) -- Modify the class example [FunkyFont.php](http://yorktown.cbe.wwu.edu/sandvig/mis314/lectures/L03/FunkyFont.php) ([source](http://yorktown.cbe.wwu.edu/sandvig/mis314/lectures/L03/FunkyFont.php.txt)) to use five additional fonts. Steps:
    -   All the images are stored on Yorktown and may be referenced from their current location (no need to copy the images). The common portion of each path is:

        "<img src='/sandvig/images/alphabet/"

    -   The images for each font is stored in a separate folder. Each font uses a slightly different naming convention. The naming convention for each font is (where x is the character desired) is shown in the table below. Look at the image tags in the sample to see a complete image path.

| Font        | Directory & File   |
|-------------|--------------------|
| Chunk Red   | chunk/red/x9.jpg   |
| Deco Blue   | deco/blue/x1.gif   |
| Animals     | animals/x4.gif     |
| Elegant Red | elegant/red/4x.gif |
| Funky       | funky/x3.jpg       |
| Tape        | punch/black/x7.gif |


-   You may copy the HTML for the radio buttons from the sample.
-   Use a series of "if" "elseif" statements or a switch statement to display the appropriate font.
-   The readability of your code can be improved significantly by using a function to break out the code that selects & writes the image tags. For instance, the sample script uses a function `fWriteChar($char, $font)`. It accepts a single character and the name of the font and writes the appropriate image tag.
-   Replace spaces in the message with <br /> tags.
-   Optional: For code beautification include line breaks (\n) in your echo statements.
-   Optional: The sample includes a snippet of JavaScript that resets the radio buttons to the selected item after each page postback. Copy this JavaScript or write your own and add it to the page. The sample JavaScript requires that the radio buttons have the name "font." Execution of the JavaScript is initialized with onload="selectRadioButton()" in the body tag.