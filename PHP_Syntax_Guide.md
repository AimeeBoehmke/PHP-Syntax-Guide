# PHP Syntax Guide

The following guide will cover some basic PHP fundamentals.

## PHP Script Tag
Below is an example of PHP script tags inserted into an HTML document. Everything outside of the PHP tags is treated as HTML, and the PHP code is embedded within it's tags.

```
<!DOCTYPE html>
<html>
<head>
    <title>Example</title>
</head>
<body>

    <h1>PHP Script Example</h1>

    <?php
        // Your PHP code goes here
    ?>

</body>
</html>
```

## Commenting
A comment in PHP is used to leave a message in the code without it interfering with the operational code or execution of the program.

Likewise, they can be used to leave reminders for yourself, or to cancel out part of your code (if you want to keep it handy in the file but not execute).

```
-- A single line comment starts with two backslashes.
// This is a single-line comment.

-- A '#' can also be used for a single-line comment.
# This is also a single-line comment.

-- A multi-line comment is formatted like this...
/* This is a
multi-line comment */
```

## Defining Variables

Variables are containers for storing values. They allow you to assign a name to a particular value, making it easier to reference throughout your code.

A PHP variable starts with a '$' symbol, followed by the name of the variable.

```
// A PHP variable holding a string value.
$city = "Vancouver";

// A PHP variable holding an integer value.
$salary = 5000; 
```
**Variable Rules**

- A variable name cannot start with a number
- A variable must start with a letter or underscore
- A variable name can only contain alpha-numer characters and underscores
- Variable names are case sensitive and cannot contain spaces

#### Variable Scope

PHP variable can be declared anywhere in the script. However, the scope of a variable determines where the variable can be referenced or used.

PHP has three variable scopes:
- local
- global
- static

#### Local Scope

This a variable that is declared within a function and can only be accessed within that function.

```
function myFunction() {
    $myVariable = "Aimee."; // local scope
    echo "<p>Hi, my name is $myVariable</p>";
}

myFunction(); // Will display "Hi, my name is Aimee."

echo $myVariable; // Will generate an error.
```

**Static**

When a function is completed/executed, all of it's contained variables are deleted. However, you can save the local variable within the function if you use the **static** keyword before the variable name.

```
function myFunction() {
    static $myVariable = "Aimee."; // using the static keyword before the variable
    echo "<p>Hi, my name is $myVariable</p>";
}
```

#### Global Scope

This is a variable defined outside of a function and can be accessed anywhere outside of functions. They're not limited to a specific function and can be used throughout an entire script.

```
$myVariable = "Aimee."; // global scope

function myFunction() {
    echo "<p>Hi, my name is $myVariable</p>";
}

myFunction(); // Displays "Hi, my name is Aimee." because the function accesses the global variable.

echo "<p>Hi, my name is $myVariable</p>"; // Also displays "Hi, my name is Aimee."
```

## Echo/Print Statements

Echo and Print are both methods of getting data to output to the browser.

**Echo** accepts multiple parameters, does not have a return value, and is slightly faster.

**Print** can only accept one parameter, has a return value of 1, and is slightly slower than echo.

**The return value of 1 from using **print** is seldom needed in practical programming, so most programmers use echo.*

### Echo

```
$someVariable = "Hello World!";

echo $someVariable; // Output is "Hello World!"
echo "Hello World!"; // Output is "Hello World!"
echo "<h1>Hello World!</h1>"; Will output Hello World as an HTML header.
```

### Print

```
$anotherVariable = "Welcome to my page.";

print $anotherVariable; // Output is "Welcome to my page."
print "Welcome to my page."; // Output is "Welcome to my page."
print "<p>Welcome to my page.<p>"; Will output "Welcome to my page." as an HTML paragraph.
```

## Data Types

Variables store different types of data; these are the data types that are supported in PHP.

- String
- Integer
- Float (floating point numbers)
- Boolean 
- Array
- Object
- Null

If you're unsure of tha value or data type of one or more variables, you can preform the **var_dump()** function. It will reveal the type and value of the variable(s).

```
// Syntax
var_dump(var1, var2, ...);
```
```
// Example
$number = 1.23;
var_dump($number); // Output: float(1.23)
```

### Strings

Strings are a sequence of characters, for example "My name is Aimee". PHP strings *must* be enclosed in either single, or double quotation marks.

```
echo 'My name is Aimee';
echo "Myname is Aimee";
```

***Note**: There is a a difference between double and single quotes in PHP. Double quotes process special characters, single quotes do not.

```
$variable = "World";

// Using double quotes
echo "Hello $variable!";  // Output: Hello World!

// Using single quotes
echo 'Hello $variable!';  // Output: Hello $variable!
```

## PHP Numbers

There are three main numeric types in PHP:

```
$x = 10; // Integer
$y = 10.2; // Float
$z = "102"; // Number Strings
```

In addition, PHP has two more data types used for numbers:

**Infinity**: A special numeric value that represent positive infinty. Its used to denote a value that exceeds the maximum possible numeric value

**NaN**: Stands for "Not a Number". A special numeric value representing an undefined or unrepresentable value resulting from an impossible arithmetic operation.

### Integers

An integer is a whole number without a decimal point. An integer can range between -2147483648 and 2147483647 in 32 bit systems, and between -9223372036854775808 and 9223372036854775807 in 64 bit systems. Any value greater or lower than the defined range is stored as a *float*.

Rules for integers:
- An integer must have at least one digit
- An integer must NOT have a decimal point
- An integer can be a positive or negative number
- Integers can be in decimal, hexadecimal, or octal formats.

```
echo 1234;
```

### Floats

A float is a number with a decimal point or in exponential form. It allows for the representation of both fractional and very large or very small numbers. Floats are useful for handling values that require more precision than integers, such as monetary values or scientific calculations.

```
$number = 1.23;
```

### Number Strings

A PHP number string is a string that represents a numeric value. It can contain numerical characters, along with optional symbols like a minus sign for negative numbers, a decimal point for floating-point numbers, or scientific notation for expressing very large or very small numbers. These strings can be converted into numeric values for mathematical operations using PHP functions like intval() or floatval().

```
$numberString = "123.45";

// intval() example
$intValue = intval("123"); // $intValue will be an integer value of 123

// floatval() example
$floatValue = floatval("123.45"); // $floatValue will be a float value of 123.45
```

### Booleans

The boolean data type represents one of two possible states: true or false (where 1 = true and 0 = false). Booleans are used to evaluate conditions and control the flow of programs.

```
$z = false;
var_dump($z); // Output: bool(false)
```

### Arrays

Arrays are used to store multiple values in a single variable.

In PHP, there are three types of arrays:

**Indexed arrays** - Arrays with a numeric index
**Associative arrays** - Arrays with named keys
**Multidimensional arrays** - Arrays containing one or more arrays

**Example Arrays**

**Indexed Array**

```
$animals = array("cat", "dog", "fish", "snake");
var_dump($animals); 
```

**Associative Array**

```
$phone = array(
    "make" => "Apple",
    "model" => "iPhone 15 Pro",
    "refurbished" => true
);
var_dump($phone);
```


**Multidimensional Array**

```
$people = array(
    array("Aimee", 40, "Gardener"),
    array("Jesse", 47, "Musician"),
    array("Sara", 48, "Producer")
);
var_dump($people);
```

#### Accessing Array Values

Here are examples of how to access array items based on array types:

**Indexed Array**

```
echo $animals[1]; // Output: dog
```

**Associative Array**

```
echo $phone["model"]; // Output: iPhone 15 Pro
```

**Multidimensional Array**

```
echo $people[0][0]; // Output: Aimee
echo $people[0][0] . " - " . $people[0][2]; // Output: Aimee - Gardener
```
#### Updating Array Values

Here are examples of how to update array items based on array types:

**Indexed Array**

```
$animals[1] = "horse"; // Update element
$animals[] = "sloth"; // Add new element
```

**Associative Array**

```
$phone["refurbished"] = false; // Update value
$phone["warranty"] = "3 year"; // Add new key-value pair
```
**Multidimensional Array**

```
$people[1][1] = 50; // Update Jesse's age
$newPerson = array("Mike", 40, "DJ"); // Define new person
$people[] = $newPerson; // Add new person to the array
```

### Classes & Objects

A PHP class is like a template, and an object is what you create from that template to use in your code. The two work together because the class provides the instructions for creating and working with objects, helping to organize and structure your code. They're used to model real-world entities, organize data, and perform actions in PHP programs.

In PHP, an object is an instance of a class. Objects allow you to organize and encapsulate related data and functionality into a single entity.

Classes define the structure and behavior of objects, while objects are the actual instances created from those classes.

```
// Define a class
class Person {
    // Properties
    public $name;
    public $age;
    
    // Constructor
    public function __construct($name, $age) {
        $this->name = $name;
        $this->age = $age;
    }
    
    // Method
    public function greet() {
        return "Hello, my name is $this->name and I am $this->age years old.";
    }
}

// Create an object (instance) of the class
$person1 = new Person("Aimee", 40);

// Access properties and methods of the object
echo $person1->greet(); // Output: Hello, my name is Aimee and I am 40 years old.
```

A common access modifier, "**public**", is often used in classes in order to declare the visibility of properties and methods within a class. When a property or method is decalred public, it means that it can be accessed from outside the class.

The **__construct** method in PHP is a special method that gets called automatically when you create a new object. It is used to initialize object properties or perform any setup tasks that need to be done when the object is created.

In PHP, the **$this** keyword refers to the current object. It allows you to access properties and methods of the current object.

## PHP Constants

Constants are identifiers that represent fixed values and remain unchangeable throughout the script's execution. Unlike variables, constants cannot be altered once defined, and they are globally scoped.

Constant names must start with a letter or underscore, and they do not require a dollar sign at the beginning.

**Defining a Constant** 
Use the **define()** function followed by the constant's name and value:

```
// Syntax
define("constantName", "constantValue");
```

```
// Example  
define("kingOfPop", "Michael Jackson");
echo kingOfPop; // Output: Michael Jackson
```

## PHP Operators

### Arithmetic Operator

Used to preform arithmetical operations with numeric values:

| Operator | Name           |   Example   |
| -------- | -------        |   -------   |
| +        | Addition       |  \$a + $b   |
| -        | Subtraction    |  \$a - $b   |
| *        | Multiplication |  \$a * $b   |
| /        | Division       |  \$a / $b   |
| %        | Modulo         |  \$a % $b   |
| **       | Exponentiation |  \$a ** $b  |  

### Assignement Operators

Used to write a value to a variable:

| Assignment | Same as |   
| -------- | -------   |  
| a = b    | a = b     |             
| a += b   | a = a + b |             
| a -= b   | a = a - b |
| a *= b   | a = a * b | 
| a /= b   | a = a / b | 
| a %= b   | a = a & b |           

### Comparison Operators

Used to compare two values (number or string):

| Operator | Name                           |  
| -------- | ---------------------------    |  
| ==  | Equal                               |             
| === | Identical                           |             
| !=  | Not equal                           |             
| <>  | Not equal                           |              
| !== | Not identical                       |             
| >   | Greater than                        |              
| <   | Less than                           |              
| >=  | Greater than or equal to            |              
| <=  | Less than or equal to               |              
| <=> | Less than, equal to, or greater than|              

### Increment/Decrement Operators

Increment operators are used to increment a variable's value.
Decrement operators are used to decrement a variable's value.

| Operator | Description                       |
| -------- | --------------------------------  |  
| ++$a | Increments \$a by one, then returns $a|             
| $a++ | Returns \$a, then increments $a by one|             
| --$a | Decrements \$a by one, then returns $a|
| $a-- | Returns \$a, then decrements $a by one|                

### Logical Operators

Used to combine conditional statements:

| Operator | Name | Example   |     Result                       |
| -------- | ---- | --------- | -------------------------------  |
| and      | And  | \$a and $b | True if both \$a and $b are true |
| or       | Or   | \$a or $b  | True if either \$a or $b is true |
| xor      | Xor  | \$a xor $b | True if either \$a or $b is true, but not both |
| &&       | And  | \$a && $b  | True if both \$a and $b are true |
| \|\|       | Or   | $a \|\| \$b  | True if either \$a or $b is true |
| !        | Not  | !$a       | True if $a is not true           |


### String Operators

| Operator | Result          |
| -------- | ----------- |
| .        | Used to concatenate arguments |
| .=       | Used to append the argument on the right to the left argument      |


## Conditional Statements

Conditional statements are used to perform different actions based on different conditions.

In PHP these are some of the conditional statements used:


### If Statement

This conditional statement executes some code if *one* condition is met.

```
<?php
// Syntax
if (condition) {
  // code to be executed if condition is true;
}
```
```
// Example
if (10 < 20) {
    echo "I'm the king of the universe!";
}
// Output: I'm the king of the universe!
```

### If... Else Statement

This conditional statement executes one piece of code if a condition is met and another sequence of code if not.

```
// Syntax
if (condition) {
 // code to execute if condition is met
} else {
 // code to execute if condition is not met
} 
```
```
// Example
if (20 < 10) {
  echo "I'm the king of the universe!";
} else {
  echo "20 is not less than 10, dumb-dumb.";
}
// Output: 20 is not less than 10, dumb-dumb.
?>
```

### If... Elseif... Else Statement

This conditional statement executes different codes for more than two conditions.

```
// Syntax
if (condition) {
 // code to execute if condition is met
} elseif (condition) {
 // code to execute if this condition is met
} else {
 // code to execute if none of the conditions are met
} 
```
```
// Example
$hour = 14;

if ($hour < 12) {
    echo "Good morning!";
} elseif ($hour < 18) {
    echo "Good afternoon!";
} else {
    echo "Good evening!";
}

// If the $hour is less than 12, it will output "Good morning!".
// If the $hour is between 12 and 17, it will output "Good afternoon!".
// If the $hour is 18 or greater, it will output "Good evening!".
```

## Functions

### Built-In Functions

PHP has a ton of built-in functions that can be called directly, from within a script, and perform specific tasks. Here are some examples of built-in PHP functions that are handy to know.

| Function     | Description          |
| ------------ | -------------------- |
| json_decode()| Decodes a JSON string |
| json_encode()| Encode a value to JSON format |
| isset()      | Checks whether a variable is set and returns true if the variable exists, and false otherwise |
| setcookie()  | Defines a cookie to be sent along with the rest of the HTTP headers |
| count()| Counts the number of elements in an array or the number of properties in an object |
| implode()| Joins array elements into a single string, using a specified separator between each element |
| explode()| Splits a string into an array of substrings based on a specified delimiter |

There are many resources on the internet that will provide a list of other built in functions.

### User-Defined Functions

These are functions created by the user that can be re-used throughout a script. These functions are declared using the '**function**' keyword followed by a name, optional parameters, and the code block to execute.

```
// Syntax
function functionName(parameters) {
  // code to be executed
}
```
```
// Example
function greet($name) {
  echo "Hello, $name!";
}

// Calling the function
greet("Aimee"); // Output: Hello, Aimee!
```

## Loops

PHP loops are used to run the same block of code over and over until a certain condition is met.

The following are the different PHP loop types:

### While Loop

Loops through a block of code as long as the specified condition is true.

```
// Syntax
while (condition that must apply) {
 // code to execute goes here
} 
```
```
// Example
$num = 10;

while ($num >= 0) {  
    echo "$num seconds remaining <br>";
    $num--;
} // Loop counts down from 10

echo "Blast off!"; // Executes when the loop completes
```

### Do While Loop

Loops through a block of code once, and then repeats the loop as long as the specified condition is true.

```
// Syntax
do {
 // code to execute goes here;
} while (condition that must apply); 
```
```
// Example
do {
    $password = readline("Enter your password: "); // Prompts user to enter a password
} while (strlen($password) < 8); 
/* Password must be 8 or more characters. 
If password is over 8 characters the loop terminates */

echo "Password is valid!"; // Executes when the loop completes
```

### For Loop

Loops through a block of code a specified number of times.

```
// Syntax
for (starting value; ending value; increment/decrement) {
    // Code to be executed
}
```
```
// Example
for ($i = 0; $i < 5; $i++) {
    echo "Number $i <br>";
}

// Output:
   Number 0
   Number 1
   Number 2
   Number 3
   Number 4
```

### For Each Loop

Loops through a block of code for each element in an array.

```
// Syntax
foreach ($array as $value) {
    // Code to be executed for each element in the array
}
```
```
// Example
$animals = array("Cat", "Dog", "Horse", "Snake" );

foreach ($animals as $animal) {
    echo "Animal: $color <br>";
}

// Output:
   Animal: Cat
   Animal: Dog
   Animal: Horse
   Animal: Snake
```