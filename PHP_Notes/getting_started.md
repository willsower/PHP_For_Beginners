# Getting Started with PHP

PHP was originally named **P**ersonal **H**ome **P**age, but was then later renamed to **P**HP: **H**ypertext **P**rocessor which sounds more powerful.

###### PHP Server Tags
- Code inside tags is executed
- Only output sent to browser
- Client will never see the PHP code (when they click view source on a page for example)
- Syntax
    - Three variations but all the same (gives same result)
        - `<?php ... ?>`
        - `<? ... ?>`
        - `<script language = "php"> ... </script>`

###### Other

- PHP requires a semi colon at the end of each sentence `;`
- We use `echo` to print out to the screen. This is the equivalent to `print()` in for example Python or `System.out.println` in Java.
- To concatenate PHP uses `.` This is the equivalent of using a `+` for other languages such as Java/Python.
- To comment in PHP use `//` or `#` for single line comments. A block comment is `/* ... */`

```PHP
echo "Hello " . "World!"; //Will output Hello World!
```