## What is PHP?

Server-side Scripting (Programming)

- Server-side code resides on a web server computer
- Server reads processes the code based on HTTP requests from client
- Server-side code creates an HTML web page and other resources
- Server sends the result back to the requesting web clients

PHP: HyPertext preProcessor (PHP)

The most widely used server-side scripting language created by Rasmus Lerdorf in 1994

- Cross-platform: Can be used on machines running different platforms
- Free and Open Source: Anyone can run a PHP-enabled server free of charge
- Compatible: Supported by the most popular web server
- Simple: Lost of built-in functionality; familiar syntax
- Well-documented: Many online resources
- Fast: fast to program and fast to execute
- Easy to learn: does not require any formal training in programming languages

## Full-Stack Web Application Development

- Client side:
    - Web browsers: Chrome, Firefox, Safari, IE etc.
    - Scripting: HTML, JavaScript, CSS, JQuery, React etc.
- Web Server side:
    - Web servers: Apache, Microsoft IIS, nginx etc.
    - Scripting: PHP, Ruby, Python, Perl, Node.js, Laravel and many other web frameworks
- Data Server:
    - Database server: MySQL, Oracle, MongoDB, CouchDB, SQLite etc.
    - Database operations: SQL/ORM, NoSQL/ODM
- Source / Testing / Debugging / Integration / Deployment tools:
    - Git, Grunt, Xdebug, Subversion, Bitbucket

## Web Application Frameworks and Content Management Systems

Web Application Framework: a set of libraries and tools that help to build a web app normally with a fully-layered workflow environment

- Server-side (mostly MVC-based):
    - Laravel (PHP)
    - Django (Python)
    - Express (Node.js / JS)
    - Ruby on Rails (Ruby)
    - [ASP.NET](http://ASP.NET) (C#)
- Client-side:
    - Bootstrap
    - React.js
    - Angular.js

Content Management System (CMS): an application built for the purpose of providing rich tools to maintain, organise and add contents dynamically to a website.

- Drupal
- Word Press
- Joomla

## Web Development Stacks

- LAMP stack: Linux, Apache, MySQL, PHP (Perl or Python)
    - Windows: WAMP
    - Mac: MAMP
    - Cross-platform: XAMPP

Other stacks:

- Mean stack: MongoDB, Express.js, AngularJS, Node.js
- WINS stack: Windows, IIS (server), .NET, SQL Server

## PHP Code Block

- PHP as a server-scripting language is desired to interact with HTML and can be embedded in an HTML page using PHP tags:
    
    `<?php … ?>`
    
- A block of PHP code begins with `<?php` and ends with `?>`
- PHP tags must be used so that the server knows what to process as PHP
- Everything outside these tags is processes as HTML
- When a PHP script is run, the entire script is replaced by the output of the script being run on the server.
- PHP Code declaration blocks (scripts) are separate sections within a web page that are interpreted by the scripting engine
- When includes PHP tags, the filename extension must be .php.

## PHP program with HTML

```HTML
<!DOCTYPE html>
<html>
	<head>
		<title>Hello World Example!</title>
	</head>

	<body>
		<?php
			print "Hello world!\n"; // This php will be replaced will Hello World!
		?>
	</body>
</html>
```

## Variables

- PHP is weaky-typed, no need to declare data types
- Variable type declared by assignment:
    
    `$variable_name = value;`
    
- Examples:
    
    ```PHP
    $name = 'angus';
    $age_in_months = 9;
    $is_fluffy = TRUE;
    ```
    
- Variable names always begin with a dollar sign $, on both declaration and usage
- Variable names are cases sensitive and can include letters, numbers or underscores but no spaces

## Data Types

|Data Types|Description|
|---|---|
|int|Positive or negative numbers with no decimal places|
|float|Positive or negative numbers with decimal places or numbers written using exponential notation|
|boolean|A logical value, TRUE or FALSE|
|string|An array of characters|
|NULL|An empty value, also referred to as a NULL value|
|object|A multi-valued type|
|array|A multi-valued type|

## Working with data types

- Variables can be cast from one type to another in the same way as Java
    
    ```PHP
    $age_string = "21";
    $age = (int) $age_string;
    ```
    
- Generally you do not need to do this, PHP will handle it automatically
- Note: a variables type is not defined explicitly, much the same as it is in JS

## Arithmetic Operations

|Operator|Name|Description|
|---|---|---|
|+|Addition|Adds two operands|
|-|Subtraction|Subtracts one operands from another operand|
|*|Multiplication|Multiplies one operand by another operand|
|/|Division|Divides one operand by another operand|
|%|Modulus|Return the remainder of a division|

## Math Functions

|Function|Description|
|---|---|
|abs|Absolute value|
|ceil, floor|Ceiling and floor|
|min, max|Smallest or largest of a set of values|
|pow|Exponentiation|
|rand|Random integer in a given range|
|round|Round a number to the nearest integer|
|sqrt|Square root|

## Strings

- Strings are declared using single or double quotation marks

$name = “Angus”;

- Accessed as arrays automatically. Indexing starts from 0.

`$description = “Happy Bunny!”;`

`$description[6] returns B`

- Concatenate string by the dot notation

`$description.$name;`

Result: “Happy Bunny!Angus”

## String functions

`$name = “Angus “;`

|Function|Example|Output|
|---|---|---|
|strlen|strlen($name)|6|
|strtoupper|strtoupper($name)|“ANGUS ”|
|strtolower|strtolower($name)|“Angus ”|
|trim|trim($name)|“Angus”|
|strpos|strpos($name, “gus”)|2|
|substr|substr($name, 3, 1)|u|
|strcmp|strcmp($name, “Angus “)|TRUE|

## Booleans

- Booleans can be either “true” or “false”
    - Constants: true or false. both are case-insensitive
    - True can also be returned as a 1
    - False can be returned as a 0
- PHP can treat any value as a Boolean
- False values:
    - FALSE
    - 0
    - 0.0
    - “”
    - NULL

## Comparison and Logical Operators

- Comparison operators: used to compare two operands with a Boolean value of true or false returned
- Logical operators: used to do logical operations on operands with a Boolean value of true and false returned

|Name|Symbol|Example|Description|
|---|---|---|---|
|Equal to|==|$a == $b|The value of a is equal to b|
|Not Equal to|!=|$a != $b|The value of a is not equal to b|
|Less than|<|$a < $b|The value of a is less than b|
|More than|>|$a > $b|The value of a is greater than b|
|Less than or equal to|<=|$a <= $b|The value of a is less than or equal to b|
|Greater than or equal to|>=|$a >= $b|The value of a is greater than or equal to b|
|Identical|===|$a === $b|a and b are exactly identical|
|and|&&|$a && $b|If both operands are true the statement is true|
|or|\||$a \| $b|If either operand is true then the statement is|
|not|!|! $a|Return the logical opposite (not) of the operand|

## Displaying variables and text strings

- To print a variable

`print $variable; or echo $variable;`

- To print a text string, speech marks must always be used

`print “text”; or echo “text”;`

- To print both text strings and variables, three methods

```PHP
echo $voting_age." is voting age"; // dot to concat
echo $voting_age," is voting age"; // commas to combine to arguments
print "$voting_age is voting age";
```

- If necessary to avoid ambiguity, can enclose variable in { }:

`print “Today is your {$voting_age}th birthday.\n”;`

- The differences between print and echo:
    - echo has no return while print has a return value of 1
    - echo can take multiple parameters while print can take one argument

## Single vs Double Quotation

- Values enclosed within single quotation marks will be treated literally
- Values enclosed within double quotation marks will be interpreted
- For escaped characters: such as \n
    - Double quotes will result in their represented values printed
    - Single quotes will always display exactly what you typed (except for \` and \\)

## Escape Characters

Same as in Java!

## Defining Constants

- Constants are set once and never change, two ways:

```PHP
const CONSTANT_NAME = value;
define("CONSTANT_NAME", value);
```

- Conventions are to name constants in ALL CAPS
- Constants do not need a $

## Comments

Same as in Java!

## Control Structures

- Same control structures as most other languages
    - Conditionals
        - if / else if / if else if else
        - switch
    - Looping
        - while
        - do … whole
        - for
        - for each

## Arrays in PHP

- PHP Arrays: an ordered map which associated values to keys.
    - Store a group of objects (elements) accessed using an index
    - Not statically defined
    - No need to set the size in advance
    - Can store any type of object, not just one type!
    - Elements can be added or deleted at any time
- Arrays can be defined using:

```PHP
$students = array();
$students = array("Ali", "Mike", "Lucy", "Peter");
$students[] = "Faye";
```

## Array Index

- Arrays can contain integer and string index at the same time

```PHP
$var = array(
	"bar0",
	"foo" => "bar",
	5 => " bar5"
);
```

- Two popular types:
    - Enumerative Array: indexed by integers
    - Associative Array: indexed by string

## Enumerated Arrays

- These are the arrays that are numerically indexed
- If no index specified, the index for the first element starts at 0

`$students = array(”Ali”, “Mike”, “Lucy”, “Peter”);`

|0|1|2|3|
|---|---|---|---|
|Ali|Mike|Lucy|Peter|

- We can set the position at which we want each element to reside

`$students = array(1⇒”ali”, 2⇒”Mike”, 4⇒”Lucy”, 9⇒”Peter”);`

|   |   |   |   |   |   |   |   |   |   |
|---|---|---|---|---|---|---|---|---|---|
|0|1|2|3|4|5|6|7|8|9|
||Ali|Mike||Lucy|||||Peter|

## Associative Arrays

- Specify a string rather than an integer within the square brackets (like a map)
- One element can be referenced using the string index associated with the element with the index string quoted:

```PHP
<?php
		$member["name"] = "Mary";
		$member["age"] = 30;
		$member["job"] = "Engineer";
?>
```

- Use ⇒ symbol to assign a value to the array

```PHP
$member = array("name" => "Mary", "age" => 30, "job" => "Engineer");
```

- To print the name element:

```PHP
echo $member["name"];
```

## Array Operations

```PHP
$var = $name[index] # get element value
$name[index] = value; # set element value
$name[] = value; # append

$a1 = array(); # empty array (length 0)
$a1[0] = 22; # stores 22 at index 0 (length 1)
$n = $a1[0] + 1; # $n will be 23

$a2 = array(5, "strings", "in", "an", "array");
$a2[] = "the end"; # add string to the end (at index 5)
```

- To append, use brackets notation without specifying an index
- Element type is not specified, can mix types

## Multidimensional Arrays

```PHP
$member_dat = array(
	(array("name"=>"Dave", "memno"=>"457", "distance"=>"10K")),
	(array("name"=>"Steve", "memno"=>"459", "distance"=>"5K")),
	(array("name"=>"Marie", "memno"=>"460", "distance"=>"10K")));

print $member_dat[0]["distance"]; # 10k
print $member_dat[2]["name"]; # Marie
print $member_dat[1]["memno"]; # 459
```

## Array Functions

- PHP has several built-in functions that can be used to manipulate the elements in an array:
    - `count()` or `sizeof()` — returns the number of elements contained in an array
    - `print_r()` — print arrays contents
    - `array_merge()` — merge two different arrays
    - `sort()` — used to sort enumerated arrays
    - `ksort()` — sort an array by key
    - `array_slice()` — extract a slice of the array
    - `explode()` — break apart a string into an array
    - `implode()` — merge an array into a unified string

## Looping through Arrays

- Accessing elements in an array is by looping with the foreach statement

```PHP
foreach ($array as $temp) {
	// do something with $temp
}
foreach ($array as $key => $temp) {
	// do something with $key and $temp
}
```

- $temp is a temporary variable that stores the value of the array element
- Useful for an array that has non-contiguous indexes
- Limitation: cannot modify the elements since variable used is only a copy of an actual array element

## Defining Functions

Basic syntax for defining a function:

```PHP
function function_name() {
	// function code
}

function function_name($arg1, $arg2) {
	// function code with args
}
```

- Must have the function keyword
- Functions must have unique names (like Java)
- Functions like all PHP code must be contained within `<?php ... ?>` tags;
- Function names can be any combination of letters, number and underscored. They must begin with either a letter or an underscore
- Function names are cases insensitive
- A parameter or argument is a variable that is used within a function (variable scope)
- It’s normal to place function definitions toward the top of a script or in a separate file
- Functions are best used for code that may be executed in several places in a script

## Return values and call functions

- A return statement is a statement that returns a value to the statement that called the function
- A function with no return statement implicitly returns NULL
- Functions are called by writing the function’s name and parameter values in parenthesis separated by commas

```PHP
function slope($x1, $y1, $x2, $y2) {
	return ($y2 - $y1) / ($x2 - $x1);
}

$x = 4;
$y = 6;
$my_slope = slope(0, 0, $x, $y);
```

## Auto-loading including Files

- It is useful to keep scripts in separate files
- We need then to include files in the main php script
- The entire contents of the included file is inserted in the calling script
- Useful for defining reused functions needed by multiple pages

## Including Files

- Calling statements

```PHP
include("filename");
include_once("filename");
require("filename");
require_once("filename");
```

- Error handling: include file not found
    - `include()`: A warning is given and the script continues to run
    - `require()`: An error is given and the script is halted

## Good Practices

- Web pages can be a mixture of HTML and PHP
- PHP takes longer to process than html
- We want to limit the number of time spent in PHP code blocks
- DO NOT use print or echo to output HTML when it is not necessary

## Expression Blocks

- PHP expression block: evaluates and embeds an expression’s value into HTML
- `<?= expr ?>` is equivalent to `<?php print expr; ?>` e.g.

```PHP
<?php $i = 5 ?>
<h2> The answer is <?=$i*7 ?></h2>
<p> I can count to <?= $i ?> ! </p>
```

## HTML Forms: a quick review

- Form: a group of UI controls that accepts information from the user and sends the information to a web server
- Form elements allow the user to enter information:
    - text input box
    - text area field
    - drop-down list
    - radio button
    - checkbox, etc

## Form: Method and Action Attributes

Syntax:

```HTML
<form method="get/post" action="destination_URL">
	...
	<input type="submit" />
</form>
```

- method attribute: transmit form data supplied by the user
- Two methods are get and post: Default method is get
- action attribute: specify where the form data is going to be transmitted. Typically a file that contains the necessary code (e.g. PHP code) for processing the form data and generated the desired output and displays it
- Must have a submit button
- One page may contain many forms if so desired

## GET vs POST

- GET (Default)
    - Asks a server for a page or data
    - Appends the information entered by the user to the end of the URL
    - Should only be used for forms that don’t handle sensitive user information
    - Not suitable for large volumes of data
- POST (recommended)
    - Submits data to a web server and retrieves the response
    - The values entered by the user are not appended to the URL but stored within the body of the request
    - Should always be used if the data is going to change the server’s database as it is more secure
    - Can be used for large amounts of data

## Query String and Parameters

- Query String: a set of parameters passed from a browser to a web server
- Often passed by placing name/value pairs at the end of a URL
- PHP code on the server can examine and utilize the values of parameters
- A way for PHP code to produce different output based on values passed from the user

## Handing the Form

- PHP store the information in special variables (super global arrays)
    - $_GET, $_POST: parameters passed to GET and POST requests
    - $_REQUEST: parameters passed to any type of request
- The PHP receiving script will assign what the user entered into this elements into a variable called $_REQUEST[”name”]
- $_REQUEST[”name”] can then be used like any other variables
- “name” is the value of the element’s name attribute in the form
- The spelling and capitalisation of the variables must match the corresponding name values in the HTML form

## Form Validation

Never trust data entered on an HTML Form!

Validation: ensuring that form’s values are correct

- Types of validation:
    - Preventing blank values
    - Ensuring the validity of values
    - Ensuring the format and range of values
    - Ensuring that values fit together
- Examine parameter values, and if they are bad, show an error message and abort

## Client vs. Server-Side Validation

Validation can be performed:

- Client-side (before the form is submitted)
    - can lead to a better user experience but not enough
- Server-side (after the form is submitted e.g. in PHP)
    - needed for truly secure validation but slower
- Both
    - best mix of convenience and security, but required the most effort to program

## Basic Server-side form validation

Form data needs to be validated using conditionals and functions

- A common function which can be used is the `isset()` function which tests if a variable has a value

```PHP
if(isset($somevariable)) {
	// $somevariable has a value
}
else { ...
```

- This function checks if a variable is set. i.e. the variable has a value other than NULL
- It could have 0 or an empty string and still be true

## Validation example

```PHP
if(isset($_POST['gender'])) {
	$gender = $_POST['gender'];
}
else {
	$gender = NULL;
}

if($gender == 'male') {
	echo '<p>Good Day Sir!</p>';
}
elseif ($gender == 'female') {
	echo '<p>Good Day Madame</p>';
}
else {
	echo '<p>Good day Thing</p>'
}
echo "$username, welcome to the club!"
...
```

- In this example if the user checks either gender radio button then `$_POST[’gender’]` will have a value — meaning that the condition is true
- In this case the shorthand version of this variable `$gender` is assigned the value of `$_POST[’gender’]` so we don’t have to repeatedly write it out
- If the condition of `$gender` is not set then `$gender` will be assigned the value of `NULL`

## More Validation

- The `isset()` function returns TRUE for and empty string. This is not an effective way to validate text inputs and text boxes from an HTML form
- The `empty()` function will check whether a variable has an empty value, an empty string, 0, NULL, or FALSE

```PHP
if(isset($_POST['username'])) {
	$username = $_POST['username'];
}
else {
	echo "Please input your username";
	exit;
}

if(!empty(trim($_POST['password']))) {
	$password = $_POST['password'];
}
else {
	exit('You forgot to enter your password!');
}
```

The is_numeric() function will check that the submitted variables are of numeric type. There is also `is_string()`, `is_int()`, `is_float()` …

## Further form validation

- How do you test for integers vs. real numbers vs. strings?
- How do you test for a valid credit card number?
- How do you test that a person’s name has a middle initial?
- How do you test whether a given string matches a particular complex format?
- You could use _regular expressions_

## HTML Injection Problem

- A user might submit information to a form that contains HTML syntax
- A flaw where a user is able to inject arbitrary HTML content into your page
- Why is this bad? it allows others to:
    - disrupt the flow/layout of your site
    - put words into your mouth
    - run JS on your users’ computers
- Injecting JavaScript content is called cross-site scripting or XSS

## Injection Example

screen shot this you

## Using Single Script

- The preceding examples have used two separate scripts for handing HTML forms:
    - One that displays the form
    - Another that handled it using PHP
- Another technique is to have one script that displays and handles a form using the following condition

```PHP
if(form has been submitted) {
	// handling statement
}
else {
	// display the form
}
```

- To determine if the form has been submitted:
    - Use a hidden input element in the form e.g. name it ‘submitted’
    - use `$_POST[’submitted’]`

`<input type=”hidden” name=”submitted” value=”true” />`

```PHP
if(isset($_POST['submitted'])) {
	// handle the form
}
else {
	// display the form elements
}
```

- Check $_POST[’submitted’], assuming that’t the name of a hidden input type in the form
- Hidden fields are used to “save the state” within an HTML form
- They are now shown on the webpage but the information is set with the other form input elements