# Variables
- Variables are named containers for holding data
- PHP variables start with $
- Variable names are case sensitive
- A valid variable name starts with a letter or underscore

```PHP
$variable
$thisIsAVariable
```

###### Assigning a value is similiar to other languages

```PHP
$fName = "Taichen"; //string
$favNumber = 25; //int
$price = 4.99; //float
$skyIsBlue = True; //boolean
```

- You can reassign a variable at any time
- You can assign a variable to another variable

```PHP
$food = "Spaghetti";

echo $food; //Output: Spaghetti

$food = "Pizza";

echo $food; //Output: Pizza

$drink = "Lemonade";
$drink2 = $drink;

echo $drink; // Output: Lemonade
echo $drink2; //Output: Lemonade
```

###### Retrieving a Value

```PHP
$fName = "Taichen";

echo "Hi " . $fName; //Outputs: Hi Taichen

$number = 35;
$price = 2.99;

echo "I just bought " . $number . " cakes for $" . $price ". What a deal!";
//Above output: I just bought 35 cakes for $2.99. What a deal!
```