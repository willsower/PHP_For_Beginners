# Assignment 2 -- Variables

Create a new directory called A02 for these assignments.

This assignment requires the use of simple HTML forms. Please use the following code as a template for exercises 1-4. You may cut-and-paste it into your php script.

```HTML
 <html>
   <head>
      <title>Sample web form</title>
      <link href="/sandvig/mis314/assignments/style.css" rel="stylesheet" type="text/css">
   </head>
   <body>
      <div class="pageContainer centerText">

         <h2>Hello Form</h2>
         <hr />

         <form>
            <p>Please enter your name:</p>
            <input type="text" name="fname" autofocus>
            <input type="submit" value="Submit Name">
         </form>

         <?php
         //Retrieve name from querystring. Check that parameter
         //is in querystring or may get "Undefined index" error
         if (isset($_GET['fname']))
         {
            $fname = $_GET['fname'];
            echo "<h1> Hello $fname";
         }
         ?>
      </div>
   </body>
</html>
```
**1\. [HelloForm.php](https://yorktown.cbe.wwu.edu/sandvig/mis314/assignments/A02/HelloForm.php) - **Paste the code above into a file and name it HelloForm.php.  This file is a template for the other parts of the exercise.

**2\. [GuessGame.php](https://yorktown.cbe.wwu.edu/sandvig/mis314/assignments/A02/GuessGame.php)**

1.  The user needs to enter a number for this exercise to work. Validate the user's input by replacing the isset() function with the is_numeric() function.
2.  For code readability, change the name of the input parameter from fname to something more appropriate, like "guessValue".
3.  Use an if statement similar to the one in [time greeting](https://yorktown.cbe.wwu.edu/sandvig/mis314/lectures/L01/timeGreeting.php) [(source)](https://yorktown.cbe.wwu.edu/sandvig/mis314/lectures/L01/timeGreeting.php.txt) to give the user hints as they try to guess a number. The if statement compares the user's input to the values shown in the following table and displays an appropriate message. The statements look something like:

```PHP
elseif ($intGuess < 7)\
    echo 'low.';
```

| Guess  | Response  |
|--------|-----------|
| < 4    | Very Low  |
| 4 - 6  | Low       |
| 7      | Correct!  |
| 8 - 10 | High      |
| > 10   | Very High |


**3\. [SimpleCalculator.php](https://yorktown.cbe.wwu.edu/sandvig/mis314/assignments/A02/SimpleCalculator.php)** - Write a script that retrieves two values from the querystring, adds them together and displays the results. Steps:

1.  Copy the code from HelloForm.php and modify it to display two text boxes. Assign the values entered to variables named value1 and value2 (tip: look at the source code for the example).
2.  In your php code assign the parameters from the querystring to local variables named $value1 and $value2. Use the is_numeric() function to check that the user entered numbers.
3.  Echo the variables to the browser to make sure they have been retrieved correctly.
4.  Add and print the values with the statement:
```PHP
    echo 'Sum is: ' . ($Value1 + $Value2);
```
**4\. [DisplayImage.php](https://yorktown.cbe.wwu.edu/sandvig/mis314/assignments/A02/DisplayImage.php)** - It is quite common to display images by concatenating dynamic information into the image path. For instance, Amazon.com concatenates book ISBNs into its image paths to display specific book images. In this exercise you will display an image of a die by concatenating a value from a textbox into the image path. Steps:

1.  Look at the source code for the sample to see the image path for the die.
2.  Put the html for the image into the echo statement. The statement starts like this:
```PHP
    echo "<img src='/images/...
```
**5\. [RandomImage.php](https://yorktown.cbe.wwu.edu/sandvig/mis314/assignments/A02/RandomImage.php)** - It is easy to generate random numbers in PHP. Display two die and their sum. Steps:

1.  Generate two random numbers between 1 and 6 using the rand() function. Google "php rand" for the documentation. Assign each random number to a variable.
2.  Concatenate the values into the image paths for the two dice.
3.  Add the values together and display the sum.