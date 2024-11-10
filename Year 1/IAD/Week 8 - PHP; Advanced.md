## PHP: Connect to databases

- Abstraction Layers
    - OBDC: Open DataBase Connection (Unified)
    - PDO: PHP Data Objects
- Vendor Specific Database Extensions
    - MySQLi: MySQL
    - OC18: Oracle
    - MongoDB
    - PostgreSQL
    - SQLite

## PDO: PHP Data Objects

One class pre-defined by PHP. It is a database library that allows you to connect many different database programs.

|Name|Description|
|---|---|
|__construction|Creates a PDO instance representing a connection to a database|
|query|performs a SQL SELECT query on the database returning a result set as a PDOStatement object|
|exec|performs a SQL query that modifies the database; return the number of affected rows|
|setAttribute|set various DB connection properties|
|quote|encodes a value for use within the query|
|prepare|prepares a statement for execution and returns a PDOstatement object|

## Querying a Database in PHP with PDO

- Call the constructor to create a PDO object
    
    `new PDO($dsn, $username, $password);`
    
- DSN (Data Source Name) contains the information required to connect to the database. In a format:
    
    `“dbprogram:dbname=database;host=server”`
    
- Example:

```PHP
# connect to MySQL database club on localhost by default username / password
$db = new PDO("mysql:dbname=club;host=localhost", "root","");
# query the member table
$rows=$db->query("SELECT * FROM member");
```

- The $rows returned by PDO’s query method is technically not an array but an object of type PDOStatement
- The member table in the club database:
    
    member(ID, username, password, programme, reason, gender)
    

## PDOStatement object and methods

PDOStatement: Represents a prepared statement and, after the statement is executed, an associated result set

Here are some of its methods:

|   |   |
|---|---|
|`columnCount()`|number of columns in the results|
|`fetch()`|return the next row from a result set|
|`fetchColumn(number)`|return one column from the news tow of result set|
|`rowCount()`|number of rows returned by the query|
|`bindParam($para, $var)`|Binds a parameter to the specified variable name|
|`execute()`|Executes a prepared statement|

```PHP
if($rows->rowCount() > 0) {
	$first_row = $rows->fetch();
}
```

## A PDO query example

The query method returns the PDOStatement object with all rows:

- each row is an associative array of [column name ⇒ value]
- example: $row[”username”] gives the value of the username column

```PHP
<?php
...
	$db = new PDO("mysql:dbname=club;host=localhost", "root", "");
	$rows = $db->query("SELECT * FROM member");
	foreach ($rows as $row) {
?>
		<li> Name: <?= $row["username"] ?>,
				 Programme: <?= $row["programme"] ?> </li>
<?php
}
...
?>:
```

- Name: Helen; Programme: Computer Science
- Name: Ali; Programme: Cyber Security

## Catching an exception

```PHP
try {
	statements(s);
}
catch(ExceptionType $name) {
	code to handle the afformentioned error
}
```

- A try / catch statement attempts to run some code, but if it throws a given kind of exception, the program jumps to the catch block and runs that code to handle the errors

## Examples with error handling

```PHP
<?php
try {
	$db = new PDO("mysql:dbname=club;host=localhost", "root", "");
	$rows = $db->query("SELECT * FROM member");
	foreach($rows as row) { ... }
}
catch(PDOException $ex) {
	// this catches the exception when it is thrown
	?>

	<p>Sorry, a database error has occurred. Please try again.</p>
	<p>(Error details: <?= $ex->getMessage() ?></p>
	
	<?php
}
...
```

## SQL injection

- SQL Injection: A flaw where the user is able to inject arbitrary commands into your SQL query

```PHP
$qstr = "SELECT username, programme, FROM member
		WHERE username = '$name' AND password = '$password'";
```

- What if the user enters the password: ‘ OR ‘1’=’1

```PHP
$qstr = "SELECT username, programme, FROM member
		WHERE username = '$name' AND password = ' OR '1'='1'";
```

- What will the above query return? Why is this bad?
- Injected SQL can:
    - Change the query to output others data (revealing private information)
    - Insert a query to modify existing data (increase bank account balance)
    - Delete existing data (…; DROP TABLE students; …)
    - Bloat the query to slow down the server (JOIN a JOIN b JOIN c)
- You should not directly include variables or query parameters in a query
- They might contain illegal characters or SQL syntax to mess up the query

## Quoting Variables

```PHP
# get query parameters
$username = $db->quote($_POST["username"]);
$password = $db->quote($_POST["password"]);
$query = "SELECT username, gender, programme, FROM member
					WHERE username=".$username. " AND password=".$password;
```

- Similar to securing against HTML injection, escape the string before you include it in your query
- Call PDO’s quote method on any variable to be inserted
- quote method escapes any illegal chars and surrounds the value with ‘ quotes
- Prevents bugs and security problems in queries containing user input

## Prepared Statements and Bound Parameters

A better secure approach:

`PDO::prepare()` — prepare SQL statements with bound parameters

`PDOStatement::bindParam` — Binds a parameter to the specified variable name

`PDOStatement::execute` — Executes a prepared statement

Three main advantages:

- Reduces parsing time: the preparation on the query is done only one (although the statement is executed multiple times)
- Bound parameters minimise bandwidth to the server: you need send only the parameters each time and not the whole query
- Immune to SQL injection: because parameter values, which are transmitted later using a different protocol, need not be correctly escaped, If the original statement template is not derived from external input, SQL injection cannot occur.

## Examples

The SQL statement can contain zero or more named (:name) or question mark (?) parameter markers for which real values will be substantiated when the statement is executed.

Example 1:

Example 2:

## Exercise: Register form

```PHP
<form method = "post" action=“register.php">
Username: <input type="text" name="username" /><br /><br />
Password: <input type="password" name="password" /><br /><br />
Please Choose: <br>
Female <input type="radio" value="female" name=“gender" />
Male <input type="radio" value="male" name=“gender" /><br /><br />
Your Programme: <br>
<select name="programme">
<option value="Computer Science" selected="selected"> Computer Science </option>
<option value="Computing for Business"> Computing for Business </option>
<option value="Multimedia Computing"> Multimedia Computing </option>
<option value=“Joint programme "> Joint programme </option>
</select><br/> <br/>
Reason to Join in:
<textarea name=“Reason" rows="3" cols="40"> Your notes here
</textarea> <br /><br />
<input type="submit" name="submit" value="Register" />
<input type="reset" value="clear"/>
</form>
```

## Exercise: connectdb.php

```PHP
<?php
// Creates a PDO object called $db and establishes
// the MySQL database connection
try {
	$db = new PDO("mysql:host=localhost;dbname=club", "root", "");
	$db -> setAttribute(PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION);
}
catch(PDOException $ex) {
?>
	<p>Sorry, a database error occured.</p>
	<p>Error details: <em> <?= $ex->getMessage() ?></em></p>
<?php
}
?>
```

## Exercise: register.php

```PHP
<?php
include("connectdb.php");
# Get form data and do form validation:
if(isset($_POST["username"])) {
	$username = $_POST["username"];
}
else {
	echo "Please input your user name";
	exit;
}

if(!empty(trim($_POST["password"])) {
	$password = password_hash($_POST["password"]);
}
else {
	echo "<p><b>You forgot to enter your password</b></p>";
	exit;
}

$gender = $_POST["gender"];
$programme = $_POST["programme"];
$reason = $_POST["reason"];

try {
	# insert a member record based on the form data
	$sth=$db->prepare("INSERT INTO member VALUES
		('',:username,:password,:programme,:reason,:gender) ");
	
	$sth->bindParam(':username', $username, PDO::PARAM_STR, 10);
	$sth->bindParam(':password', $password, PDO::PARAM_STR, 64);
	$sth->bindParam(':programme', $programme, PDO::PARAM_STR, 20);
	$sth->bindParam(':reason', $reason, PDO::PARAM_STR, 100);
	$sth->bindParam(':gender', $gender, PDO::PARAM_STR, 10);
	
	$sth->execute();
}
catch(PDOException $ex) {
	// this catches the exception when it is thrown
?>
	<p>Sorry, a database error occured. Please try again</p>
	<p>(Error details: <?= $ex->getMessage() ?>)</p>
<?php
}
?>
```

## Hash your passwords!

- Passwords should never be stored or sent in plain text
- Hashing algorithms take an input and return a hashed value
    
    `hash(string $algo, string $data[, bool $raw_output=false])`
    
    `password_hash(string $password, int $algo[,array $options])`
    
- Verified a password
    
    `password_verify(string $password, string $hash)`
    

## Cookies

What are cookies?

- Small pieces of information about a user that are stored on the user’s computer in text files by a Web server
- Sent by a server to a browser, and then sent back by the browser on future page requests
- Store information between visits to a webpage

Why use cookies?

- A web page script can read the previously stored browser cookie data
- Cookies can be used for authentication, user tracking and maintaining user preferences, shopping carts
    - Query strings can become too long
    - They are lost when someone closes a tab, can be difficult to get back

## What is stored?

- A cookie’s data consists of a single name/value pair, sent in the header of the client’s HTTP request

## How cookies are sent

- When the browser requests a page, the server may send back a cookie(s) with it
- If your server has previously send any cookies to the browser. the browser will send them back on subsequent requests

## Setting Cookies using PHP

`setcookie(name[,value,expires,path,domain])`

- Expires determines how long a cookie can remain on a client system before it is deleted
    - If not included then the cookie expires when the page is closed
- Path determines the availability of a cookie to other web pages on a server
- Domain is for sharing cooking across servers in the same domain

## How long does a cookie exist?

- Session cookie: the default type; a temporary cookie that is stored only in the browser’s memory
    - When the browser is closed, temporary cookies will be deleted
    - Can not be used for tracking long-term information
    - Safer, because no programs other than the browser can access them
- Persistent cookie: one that is stored in a file on the browser’s computer
    - Can track long-term information
    - Potentially less secure, because users can open cookie files, see/change the cookie values etc.

## setcookie() examples

```PHP
setcookie("user", "mike");
setcookie("pie", "apple");
# No duration argument so these will only exist for as long as the browser is open

setcookie("user", "Mike", time() + 3600);
# Expires after one hour added to the current time (seconds)

setcookie("user", "", time() - 3600);
# Delete the previously created cookie
```

## Retrieving cookie information

- Cookies that are available to the current web page are automatically assigned to the $_COOKIE super global array
- Access each cookie by using the cookie name as a key in the associative $_COOKIE[] array
    
    `$var = $_COOKIE[”name”];`
    
- Newly created cookies are not available until after the current webpage is reloaded
- `isset()` finds out whether a cookie has been set or not

```PHP
if(isset($_COOKIE["user"])) {
	$user = $_COOKIE["user"];
	echo "Welcome $user!\n";
}
else {
	echo "Welcome guest!\n";
print_r($_COOKIE);
```

## Facts about Cookies

- Cookies are only data, not program code
- Cookies cannot erase or read information form the user’s computer
- Cookies are usually anonymous (do not contain personal information)
- Cookies can be used to track your viewing habits on a particular site
- Each individuals server or domain can store around 20-50 cookies on a user’s computer
- The largest cookie size is around 3-4KB

## Cookie Limitations

- Users can easily disable the cookie feature
- People move around
- Users may delete cookies
- PHP sets limit size on cookies
- You have to set it before you can send HTTP headers
- Less secure than session
- Session variables in PHP overcome some of the limitations of cookies

## What is a session?

A session is a sequence of HTTP requests and responses between a specific web browser and a server from one client until the client logs out, or times out

- Sessions allow you to keep track of your users even when clients disable cookies in their Web browsers
- Session data is stored on the server (not browser)
- Session ID serves as a reference to the session data
- Session ID is stored in the web browser via cookie (sessions are built on top of cookies)

## How sessions are established

- Client’s browser makes an initial request to the server
- Server notes client’s IP address/browser, stores some local session data, and sends a session ID as a cookie back to client
- Client sends that same session ID back to the server on future requests
- Server uses session ID to retrieve the data for the client’s session later

## Client/Server Architecture

![[Untitled 58.png|Untitled 58.png]]

## Setting Session Variables in PHP

- PHP script needs to start the session using `session_start()`
- When call session_start:
    - If the server hasn’t seen this before, a new session is created
    - Otherwise, existing session data is loaded into $_SESSION
- Once the session has started, values can be registered to the session, e.g.
    
    ```PHP
    session_start();
    $_SESSION["user"] = "Mike";
    ```
    
- $_SESSION global array storing session data which can be retrieved on future pages based on the session ID
- If a client’s web browser is configured to accept cookies, the session ID is assigned to a temp cookie named PHPSESSID

## Accessing Session Variables

- Session variables are available after you’ve established them
    
    `echo $_SESSION[”user”];`
    
- Use `isset()` to ensure that a session variable is set before you attempt to use it

```PHP
$_SESSION["name"] = value;
$variable = $_SESSION["name"];

if(isset($_SESSION["name"])) {
	$name = $_SESSION["name"];
	echo "welcome back, $name!\n";
}
else {
	echo "Never heard of you before\n";
}
```

## Modify / Delete Session Variables

A sessions data is temporary and does not require that you explicitly clean after yourself, but you may wish to delete some data for you various tasks

```PHP
// Open the session to modify or remove it
session_start();

// To change the variable, just overwtire it
$_SESSION["user"] = "Lucy";

// Remove a single variable in the session
unset($_SESSION["user"]);

// Unset all of the session variables
$_SESSION = array();

// This would destory the session variables
session_destory();
```

## Using sessions without cookies

- By default sessions rely on the use of a cookie PHPSESSID which contains session ID
- Every sunsequent page that calls session_start() makes use of the cookie

Problem: Users have cookies turned off!

Solution: pass along the session ID as a query string from page to page

- PHP helps to automate this process with the build-in SID constant
- If the browser supports cookies, this constant is empty; otherwise, SID contains a string similar to the following
    - PHPSESSID=illiifcksqnbtcjnr5ei10p8u7

`<a href=”myscript.php?<?php echo SID; ?> “> HOME PAGE </a>`

## Sessions vs. Cookies

Sessions

- Data is retained on the server
- Data lasts until the users closes the browser or times out
- Session are generally more secure
- Sessions allow for more data to be stored
- Sessions can be used without cookies
- For most of our web applications, use sessions
- Sensitive data, use sessions

Cookies

- Data stored on the client
- Cookies are easier to program
- Cookies require less of the server
- Cookies can be set to a long lifespan
- In general store and retrieve just a couple of small pieces of information use cookies
- If you want data to work next day, use cookies

## Web Authentication

Authentication: tell a web application about who you are

- Basic authentication (BA): defined in HTPP and uses standard fields in the HTTP header, removing the need for handshakes
- Form-based authentication: a programmatic method normally using the standard HTML form fields to pass the username and password values to the server and the server then validates the credentials and then creates a session that is tied to a unique key that is passed between the client and the server on http requests
- Token-based authentication for API: each request to a server is accompanied by a signed token which the server verifies for authenticity and only then responds to the request

## Web Browser Redirection

- PHP `header()` can be used to redirect the Web browser form a current page to another
    
    `header(”Location: $url”);`
    
- Because redirection is the least thing to occur on the ‘current page’, header function is normally followed by `exit()` which stops execution of the current script
- `header()` function should be called before anything is written to the page (including HTML). Call it before the <HTML> tag.

## PHP Programming So Far

- Write the initial HTML part
- Write some embedded PHP code blocks
    - Define functions
    - Include external files
    - Connects to the database
    - Queries/Updates/Insert to the database
    - Retrieves the query results
    - Prints the results within some HTML
- Completes the HTML page

## Procedural vs. Object-Oriented

Procedural

- Top-down design
- Function as a programming unit
- Local data focused
- Limited code reuse
- Complex code

Object-Oriented

- Object focused design
- Classes as programming unit
- Protected data
- Code reuse
- Complex design