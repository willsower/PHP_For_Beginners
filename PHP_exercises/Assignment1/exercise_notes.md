# Assignment 1 - Server Side Includes & PHP

You may copy the HTML/CSS from the working samples to use in your assignments. You will be the one developing all server-side code, this is your own work for these exercises.

**1\. [HelloWorld.php](http://yorktown.cbe.wwu.edu/sandvig/mis314/assignments/A01/Hello.php)** -- This exercise will familiarize you with the Netbeans IDE. You may look at and modify the HTML and CSS used in the samples on any assignments.

1. **Open Netbeans project:** Create a new Netbeans project as described in [First-time Netbeans Setup](../../environment_setup.md) if you have not already done so.

2. **Create assignment folder:** Under the Projects tab, right-click on Source Files, and create a new folder named A01 for assignment 1 files (web folder and file names should not contain spaces).

    If you do not see a "new folder" option in Netbeans create a new file and in the dialog box specify a new folder name (click image on right for example). Netbeans will then create both the file and folder.

3.  **Create PHP web page:** Right-click on the A01 folder and select new PHP web page.

4.  Name the page "Hello". Note that Netbeans adds the .php extension automatically. Click finish.

5.  **Create an external CSS file**: Right-click on A01 and select new Cascading Style Sheet.

6.  **Link CSS to php page**: Add a link tag to the php page that links to your style sheet (look at the code in the sample if you are unsure of the syntax).

7.  **Define styles:** Define at least two styles in the CSS stylesheet. Netbeans should be providing smart-code completion.  Save the css file (Ctrl-S).

8.  **Write HTML:** Add some HTML and text to the php file that utilizes your styles. Netbean's smart-code completion should be able to see the styles in your style sheet.

9.  **Format**: When your HTML and php code is getting messy right-click in the editor and select "Format" for auto-formatting.

10. **Add PHP**: Add the following snippet to your php page:

    ```PHP
    <?php
        for ($i = 0; $i <= 10; $i++) {
            echo "Hello world. Value of i is $i <br />";
        }
    ?>
    ```

**2\.** **[Lion.php](https://yorktown.cbe.wwu.edu/sandvig/mis314/assignments/A01/Lion.php)** -- This assignment uses PHP's include statement to insert one file into another file. The include statement is useful for reusing both HTML and PHP code and are used extensively with PHP. Please read the short tutorial [PHP Include Files](https://www.w3schools.com/php/php_includes.asp%20target=) on w3schools.com prior to starting the assignment. The syntax is:

```PHP
<?php include 'header.html';  ?>
```

where 'header.html' is a separate file. The included file will be inserted at the location of the include statement.

The exercise uses include files for the header, footer and left menu. The body of each page should have a different picture (you can use the photos in the example or your own pictures).

**Tips**:

-   You will create six files for this assignment: Lion.php, Giraffe.php, monkey.php are content pages. They will use include statements to insert the header, footer and menu.

-   header.html, footer.html and menu.html contain only HTML. These files should not contain page-level tags <head> <body> <title> etc. since these are in the parent php file. Use your browser's "view source" to see the HTML in the sample.  You may copy the HTML from the example or create your own.![Restore Files](https://yorktown.cbe.wwu.edu/sandvig/mis314/images/RestoreFolder.png)

**3\. [ClockLoop.php](http://yorktown.cbe.wwu.edu/sandvig/mis314/lectures/L01/ClockLoop.php)** -- Add a [for loop](https://www.w3schools.com/php/php_looping_for.asp) to the example [Clock.php](http://yorktown.cbe.wwu.edu/sandvig/mis314/lectures/L01/Clock.php) ([ source](http://yorktown.cbe.wwu.edu/sandvig/mis314/lectures/L01/Clock.php.txt)) to display the date 10 times. To add line breaks between iterations the echo statement will need to include paragraph, div, or br tags.