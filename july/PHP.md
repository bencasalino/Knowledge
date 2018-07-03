#PHP

- Open Source Server Side Scripting Language

- Hypertext Preprocessor

- scripts are executed on the server and returned to the browser as plain HTML.

- PHP statements end with a semicolon ;

- all language keywords, classes, functions are **NOT** case sensitive. However all variable names **ARE** case sensitive. ($color, $COLOR, and $coLOR are treated as three different variables)

- Unlike other programming languages PHP has no command for declaring a variable. It is created the moment you first assign a value to it.

- **echo** statement is often used to output data on the screen.

- PHP is a Loosely Typed Language (do not have to declare data types)

---

## Basic syntax

```
<!DOCTYPE html>
<html>
<body>

<h1>My first PHP page</h1>

<?php
echo "Hello World!";
?>

</body>
</html>
```

---

## Comments

```
// single line comment

# also single line comment

/*
mutli
line
comment
*/

// You can also use comments to leave out parts of a code line

$x = 5 /* + 15 */ + 5;
echo $x;
?>
```

---

## Variable Rules

A variable starts with the $ sign, followed by the name of the variable

A variable name must start with a letter or the underscore character

A variable name CANNOT start with a number

A variable name can only contain alpha-numeric characters and underscores (A-z, 0-9, and \_ )

Variable names are case-sensitive ($age and $AGE are two different variables)

---

## Variable Scope

```
<?php
$x = 5; // global scope

function myTest() {
    // using x inside this function will generate an error
    echo "<p>Variable x inside function is: $x</p>";
}
myTest();

echo "<p>Variable x outside function is: $x</p>";
?>
```

Results:
Variable x inside function is:

Variable x outside function is: 5

---

## Global keyword

The global keyword is used to access a global variable from within a function.

To do this, use the global keyword before the variables (inside the function)

PHP also stores all global variables in an array called $GLOBALS[index]. The index holds the name of the variable. This array is also accessible from within functions and can be used to update global variables directly.

```
<?php
$x = 5;
$y = 10;

function myTest() {
    $GLOBALS['y'] = $GLOBALS['x'] + $GLOBALS['y'];
}

myTest();
echo $y;
?>
```

Output --> 15

---

## Static variables

Normally, when a function is completed/executed, all of its variables are deleted. However, sometimes we want a local variable NOT to be deleted. We need it for a further job.
Then, each time the function is called, that variable will still have the information it contained from the last time the function was called.

**NOTE:**The variable is still local to the function.

```
<?php
function myTest() {
    static $x = 0;
    echo $x;
    $x++;
}

myTest();
echo "<br>";
myTest();
echo "<br>";
myTest();
?>
```

Output:
0

1

2

---

## Echo vs print

echo and print are more or less the same. They are both used to output data to the screen.

The differences are small: echo has no return value while print has a return value of 1 so it can be used in expressions. echo can take multiple parameters (although such usage is rare) while print can take one argument. echo is marginally faster than print.

---

## Data Types

supports the following data types:

String

Integer

Float (floating point numbers - also called double)

Boolean

Array

Object

NULL - If a variable is created without a value, it is automatically assigned a value of NULL. Variables can also be emptied by setting the value to NULL

Resource - The special resource type is not an actual data type. It is the storing of a reference to functions and resources external to PHP. A common example of using the resource data type is a database call

---

## Strings

[String Reference ](https://www.w3schools.com/php/php_ref_string.asp)

```
<?php
echo strlen("Hello world!"); // outputs 12

echo strrev("Hello world!"); // outputs !dlrow olleH

echo str_word_count("Hello world!"); // outputs 2

echo strpos("Hello world!", "world"); // outputs 6


?>
```

### Constants

A constant is an identifier (name) for a simple value. The value cannot be changed during the script.

A valid constant name starts with a letter or underscore (no $ sign before the constant name).

Note: Unlike variables, constants are automatically global across the entire script.

```
<?php
define("GREETING", "Welcome to W3Schools.com!", true);
echo greeting;
?>

// Welcome to W3Schools.com!


define("GREETING", "Welcome to W3Schools.com!");

function myTest() {
    echo GREETING;
}

myTest();
```

---

## Operators

String, Logical, Increment/Decrement, Comparison, Assignment, Arithmetic
Array

[Reference](https://www.w3schools.com/php/php_operators.asp)

---

## If / else / elseif Statements

The example below will output "Have a good morning!" if the current time is less than 10, and "Have a good day!" if the current time is less than 20. Otherwise it will output "Have a good night!":

```
<?php
$t = date("H");

if ($t < "10") {
    echo "Have a good morning!";
} elseif ($t < "20") {
    echo "Have a good day!";
} else {
    echo "Have a good night!";
}
?>
```

---

## Switch Statement

This is how it works: First we have a single expression n (most often a variable), that is evaluated once. The value of the expression is then compared with the values for each case in the structure. If there is a match, the block of code associated with that case is executed. Use break to prevent the code from running into the next case automatically. The default statement is used if no match is found.

```
<?php
$favcolor = "red";

switch ($favcolor) {
    case "red":
        echo "Your favorite color is red!";
        break;
    case "blue":
        echo "Your favorite color is blue!";
        break;
    case "green":
        echo "Your favorite color is green!";
        break;
    default:
        echo "Your favorite color is neither red, blue, nor green!";
}
?>
```

## Loops

while - loops through a block of code as long as the specified condition is true

do...while - loops through a block of code once, and then repeats the loop as long as the specified condition is true

for - loops through a block of code a specified number of times

foreach - loops through a block of code for each element in an array

[Examples](https://www.w3schools.com/php/php_looping.asp)

---

## User Defined Functions

Besides the built-in PHP functions, we can create our own functions.

A function is a block of statements that can be used repeatedly in a program.

A function will not execute immediately when a page loads.

A function will be executed by a call to the function.

```
<?php
function writeMsg() {
    echo "Hello world!";
}

writeMsg(); // call the function
?>
```

## Function Arguments

Information can be passed to functions through arguments. An argument is just like a variable.

Arguments are specified after the function name, inside the parentheses. You can add as many arguments as you want, just separate them with a comma.

The following example has a function with one argument ($fname). When the familyName() function is called, we also pass along a name (e.g. Jani), and the name is used inside the function, which outputs several different first names, but an equal last name:

```
<?php
function familyName($fname) {
    echo "$fname Refsnes.<br>";
}

familyName("Jani");
familyName("Hege");
familyName("Stale");
familyName("Kai Jim");
familyName("Borge");
?>

//Jani Refsnes.
//Hege Refsnes.
//Stale Refsnes.
//Kai Jim Refsnes.
//Borge Refsnes.


// multiple arguments
<?php
function familyName($fname, $year) {
    echo "$fname Refsnes. Born in $year <br>";
}

familyName("Hege", "1975");
familyName("Stale", "1978");
familyName("Kai Jim", "1983");
?>

// Default Argument Value

<?php
function setHeight($minheight = 50) {
    echo "The height is : $minheight <br>";
}

setHeight(350);
setHeight(); // will use the default value of 50
setHeight(135);
setHeight(80);
?>

// Returning Values

<?php
function sum($x, $y) {
    $z = $x + $y;
    return $z;
}

echo "5 + 10 = " . sum(5, 10) . "<br>";
echo "7 + 13 = " . sum(7, 13) . "<br>";
echo "2 + 4 = " . sum(2, 4);
?>
```

---

## Arrays

An array is a special variable, which can hold more than one value at a time.

1.  Indexed arrays - Arrays with a numeric index

```
<?php
$cars = array("Volvo", "BMW", "Toyota");
echo "I like " . $cars[0] . ", " . $cars[1] . " and " . $cars[2] . ".";
?>
```

The count() function is used to return the length (the number of elements) of an array

2.  Associative arrays - Arrays with named keys

```
<?php
$age = array("Peter"=>"35", "Ben"=>"37", "Joe"=>"43");
echo "Peter is " . $age['Peter'] . " years old.";
?>
```

3.  Multidimensional arrays - Arrays containing one or more arrays

[Array Reference](https://www.w3schools.com/php/php_ref_array.asp)

---

## Date/Time/Calendar Functions

[Calendar](https://www.w3schools.com/php/php_ref_calendar.asp)

[Date/Time](https://www.w3schools.com/php/php_ref_date.asp)

## Directory Functions

[Directory](https://www.w3schools.com/php/php_ref_directory.asp)

## Error Handling

[Errors / Logging Constats / Runtime Config](https://www.w3schools.com/php/php_ref_error.asp)

---

## Filter Functions

[Filter](https://www.w3schools.com/php/php_ref_filter.asp)

---

## FTP

The FTP functions give client access to file servers through the File Transfer Protocol (FTP).

The FTP functions are used to open, login and close connections, as well as upload, download, rename, delete, and get information on files from file servers. Not all of the FTP functions will work with every server or return the same results. The FTP functions became available with PHP 3.

If you only wish to read from or write to a file on an FTP server, consider using the ftp:// wrapper with the Filesystem functions which provide a simpler and more intuitive interface.

[FTP Functions](https://www.w3schools.com/php/php_ref_ftp.asp)

---

## PHP Global Variables - Superglobals

Several predefined variables in PHP are "superglobals", which means that they are always accessible, regardless of scope - and you can access them from any function, class or file without having to do anything special.

The PHP superglobal variables are:

$GLOBALS

$\_SERVER

$\_REQUEST

$\_POST

$\_GET

$\_FILES

$\_ENV

$\_COOKIE

$\_SESSION

---

```
<?php
$x = 75;
$y = 25;

function addition() {
    $GLOBALS['z'] = $GLOBALS['x'] + $GLOBALS['y'];
}

addition();
echo $z;
?>
```

In the example above, since z is a variable present within the $GLOBALS array, it is also accessible from outside the function!

---

$\_SERVER is a PHP super global variable which holds information about headers, paths, and script locations.

$\_REQUEST is used to collect data after submitting an HTML form.

```
<form method="post" action="<?php echo $_SERVER['PHP_SELF'];?>">
  Name: <input type="text" name="fname">
  <input type="submit">
</form>

<?php
if ($_SERVER["REQUEST_METHOD"] == "POST") {
    // collect value of input field
    $name = htmlspecialchars($_REQUEST['fname']);
    if (empty($name)) {
        echo "Name is empty";
    } else {
        echo $name;
    }
}
?>
```

---

## Include / Require

The include (or require) statement takes all the text/code/markup that exists in the specified file and copies it into the file that uses the include statement.

Including files is very useful when you want to include the same PHP, HTML, or text on multiple pages of a website.

It is possible to insert the content of one PHP file into another PHP file (before the server executes it), with the include or require statement.

The require statement is also used to include a file into the PHP code. However, there is one big difference between include and require; when a file is included with the include statement and PHP cannot find it, the script will continue to execute:

The include and require statements are identical, except upon failure:

- require will produce a fatal error (E_COMPILE_ERROR) and stop the script

- include will only produce a warning (E_WARNING) and the script will continue

footer.php file

```
<?php
echo "<p>Copyright &copy; 1999-" . date("Y") . " W3Schools.com</p>";
?>
```

To include the footer file in a page, use the include statement:

```
<html>
<body>

<h1>Welcome to my home page!</h1>
<p>Some text.</p>
<p>Some more text.</p>
<?php include 'footer.php';?>

</body>
</html>
```

## Read File and File Open Function

The readfile() function reads a file and writes it to the output buffer. Prints out the txt file.

```
<?php
echo readfile("webdictionary.txt");
?>

OR

<?php
$myfile = fopen("webdictionary.txt", "r") or die("Unable to open file!");
echo fread($myfile,filesize("webdictionary.txt"));
fclose($myfile);
?>
```

fread() and fclose() functions Reference

[File Open](https://www.w3schools.com/php/php_file_open.asp)

[File Create / Write ](https://www.w3schools.com/php/php_file_create.asp)

---

## Cookies / Sessions

A cookie is often used to identify a user. A cookie is a small file that the server embeds on the user's computer. Each time the same computer requests a page with a browser, it will send the cookie too. With PHP, you can both create and retrieve cookie values. --> setcookie()

---

A session is a way to store information (in variables) to be used across multiple pages.

Unlike a cookie, the information is not stored on the users computer.

What is a PHP Session?
When you work with an application, you open it, do some changes, and then you close it. This is much like a Session. The computer knows who you are. It knows when you start the application and when you end. But on the internet there is one problem: the web server does not know who you are or what you do, because the HTTP address doesn't maintain state.

Session variables solve this problem by storing user information to be used across multiple pages (e.g. username, favorite color, etc). By default, session variables last until the user closes the browser.

So; Session variables hold information about one single user, and are available to all pages in one application.

Tip: If you need a permanent storage, you may want to store the data in a database. Note: The session_start() function must be the very first thing in your document. Before any HTML tags.

---

## PHP Filters

Validating data = Determine if the data is in proper form.

Sanitizing data = Remove any illegal character from the data.

Many web applications receive external input. External input/data can be:

- User input from a form

- Cookies

- Web services data

- Server variables

- Database query results

You should always validate external data!
Invalid submitted data can lead to security problems and break your webpage!
By using PHP filters you can be sure your application gets the correct input!

---

##Exception Handling
Exceptions are used to change the normal flow of a script if a specified error occurs.

[Exceptions](https://www.w3schools.com/php/php_exception.asp)
