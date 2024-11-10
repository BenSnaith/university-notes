## JavaScript: Brief Background

- JavaScript is a programming language but with particular features designed to make it suitable for client-side programming and is included in all web browsers
    - Invented by Brendan Eich at Netscape in 1995, and then further developed by Netscape and Sun Microsystems, Originally name LiveScript, it’s name was changed to JavaScript as a marketing ploy.
    - It includes objects, attributes methods, and similar control structures to those used in Java
    - But the primitive data types are different, it contains many features that don’t exist in Java, and vice-versa.
    - Can also be run independently or on the server side using node.js
    - JavaScript was promoted by Netscape
    - Afterwards Microsoft introduced its own version (JScript)
    - In 1999 ECMA defined a standard for JavaScript
        - European Computer Manufacturers Association — an international standards organisation
        - Strictly the language should be known as ECMAScript
            - You will often see versions labelled using this terminology (ES6)

## Type Systems

- almost all modern programming languages use a type system
    - All data in the language has some type which tells us what the data represents
        - e.g. an int, an array, a string etc
    - Operations are defined over these types
        - Type systems are designed so that operations which make sense to humans are allows

```CSS
int a = 1;
int b = 2;
a + b; // add two integers - allowed
```

## Type Checking

- The process of ensuring that programs conform to their type rules is called type checking
    - Those programs which conform to the type rules run
    - Those programs which do not conform don’t run (or atleast warn us that a problem exists)
- We can choose when type checking occurs:
    - Before runtime: The entire program is type-checked before it is ran, being rejected if it does not meet the time rules. This is called static typing
    - At runtime: The program is type-checked as it is run, only failing when it tries to execute a statement which does not meet the type rules. This is called dynamic typing.
- Examples:
    - Statically typed languages: Java, C/C++, C# (mostly)
    - Dynamically typed languages: JavaScript, Ruby, Python
- A simple way to think of the difference between dynamically and statically typed languages is to compare when programs will be rejected.

```JavaScript
x = null;
x.message; // An error - null doesnt contain type "message"
```

- Will be rejected
    - by a statically typed language before it is run
    - by a dynamically typed language only when the x.message is reached
- Statically typed languages find errors earlier than than dynamically typed ones, why would we choose a dynamically typed one over a static one?

## Dynamic Typing: Advantages

- We will say that a perfect static typechecker accepts all correct programs and rejects all incorrect ones before running them.
- It turns out that implementing such a system is impossible
- To make a practical static typechecker, we must reject some correct programs.
- Consider the following functions

```JavaScript
function process(err, res) {
	if (err!==null) console.log(err.message);
	else console.log(res.message);
}
```

`process(null, {message: ‘success’});`

- According to our type system, the above program is correct
    - Because of the condition in the if statement, the incorrect line will never run
    - A dynamically typed language would accept this program
    - Most statically typed languages would reject it

`process(undefined, {message: ‘success’});`

- According to our type system the above program is incorrect
    - By changing the input, the incorrect branch will run.
    - A statically typed language would reject this before running it.
    - A dynamically typed language would reject it only after reaching an incorrect statement

```JavaScript
if ((new Date).getDay() !== 6) let err = null;
process(err,{message:'success'});
```

- According to our type system, the above program is incorrect.
    - It is possible for the incorrect line to be run (if it is Saturday!)
    - A statically typed language would only reject it on a Saturday!
        - This is a bug! if we are going to use dynamic typing, make sure to test thoroughly!

## Dynamic and Static Typing: Summary

- Statically typed languages reject incorrect programs before runtime
- Dynamically typed languages reject incorrect programs at runtime
    - We know about errors earlier with statically typed languages.
- Statically typed languages sometimes reject correct programs
    - They are more restrictive, but less likely to contain errors
- Dynamically typed languages sometimes accept incorrect programs
    - They are way less restrictive, but more likely to contain errors
    - We need to test these programs very carefully!
- JavaScript is a dynamically typed language — make sure that you are aware of the above.

## Compilation and Interpretation

- Java is typically compiled:
    - when we want to distribute a program, we don’t distribute the source files
    - instead we compile to bytecode and distribute that
- JavaScript is typically interpreted:
    - when we want to distribute it, we do distribute the source files
    - and some interpreter performs the instructions they contain.
- Users need to have an interpreter — fortunately these are included in browsers

## What JavaScript can do?

- Open new windows
- Display dialog boxes
- Prompt a user to provide some input and then process that input some way
- Create custom-based HTML pages on the fly, depending on actions that the user takes
- Validate inputs to fields of a form before submitting the form fields to a server .. etc

## Adding JavaScript to HTML

- We include JavaScript in an HTML document using the <script> tag
    - This is a container tag
    - It tells the browser where JavaScript code starts and ends
    - Can appear in the head or the body, depending on purpose
- Attributes of the <script> tag:
    - src=”myscript.js”: used to specify a URL location of a file in the case where the JavaScript code is to be defined separately
- To add inline JavaScript

```JavaScript
<script type="text/javascript">
	your script here
</script> 
```

- To add external JavaScript in file “myscript.js”

```JavaScript
<script src="myscript.js">
</script>
```

- Notice that the script is required even for external tags

## Variable Declarations

- As JavaScript is dynamically typed, type deduction is performed by the interpreter at run time, not specified by the developer:
    - The interpreter can deduce the type of a variable from the value assigned to it.
    - We do not have to declare the type of a variable, just declare that it is a variable with the let keyword and then start using it:

```JavaScript
let x = 10; // x is declared and hold an integer
let y = "myString"; // y is declared and holds a string
let z; // z is created and uninitialised
```

- We can even reuse the same variable for a different type:

```JavaScript
let x = 10; // x is declared and holds an integer
x = "My String"; // x now holds a string
```

- var also works but let has better scope.

## Constant

- We can also declare constants

const

- JavaScript will throw an error if you try to change a const

```JavaScript
const pi = 3.14159;
pi = "eat your pie lol"; // error cannot change type const
```

## Variable Naming

- A JavaScript variable name (identifier) must
    - begin with a letter, underscore or dollar sign
    - contain only letters, digits, underscores, and dollar signs
    - not be a reserved keyword
- These identifiers are valid:
    - let x1;
    - let $my_var$;
    - let _TEMP;
- While these are not:
    - let 1_var (starts with digit)
    - let a_&_b; (contains invalid char &)
    - let true; (true is a reserved keyword)

## Data Types

- We can express 5 types of basic data in JavaScript:
    
    - Numbers
    
    let a = 10;
    
    let b = 1.5;
    
    - Text
    
    let c = “my string”;
    
    let d = “The previous string was “ + c;
    
    - Boolean Values
    
    let e = true;
    
    let f = false;
    
- There are also two special data types, `null` and `undefined`

## Terminating Statements

- To terminate a statement, we use a semicolon
    - If we terminate a statement, we can include another on the same line, e.g;

`let x = 10; let y = “my string”;`

- If we omit the semicolons, the interpreter will try to insert them automatically if we have statements on separate lines

`//correct - no semi colon but on separate lines`

`let x = 10`

`let y = “my string”`

  

`//incorrect - no semicolons or new lines`

`let x = 10 let y = “my string”`

- Automatic semicolon insertion is not to be relied on

## JavaScript Collections

- There are two frequently used collections in JavaScript:
- Arrays:

```JavaScript
let arr = [10, 12, "My String"]; // Mixed-type collection
arr[0]; // indexed from 0 (arr[0] == 10)
arr.length; // with a length of arr.length == 3
```

- Objects

```JavaScript
let obj = {
	prop1 : 3.14,
	prop2 : "My String"
} // associates property names and values

obj["prop1"]; // Can look up values by propery name
obj.prop2; // using either of these two forms
```

## JavaScript Comments

Its the same as Java.

## Control Flow Statements

- With the JavaScript that we have seen so far, we can simply have seen so far, we can simply execute a series of statements in sequence
- This is not very useful, we often want to:
    - Repeatedly execute a single block of code
    - Determine which block of code to execute based on some condition
- A statement which allows us to do this is called a control flow statement
- JavaScript allows us to do this in similar ways to Java. We will look at:
    - for and while loops
    - if statements
    - switch statements

## for Loop

- for Loop
- The loop is used when you know in advance how many times the script should run

```JavaScript
for(startValue;stopCondition;increment) {
	code to be executed
}
```

## while Loop

- while Loop
    - The while loop is used when you want to stop after some condition is met

```JavaScript
while(continueCondition) {
	code to be executed
}
```

## if Statement

- Conditional statements have syntax and semantics in the Java style:

```JavaScript
let able_to_learn_to_drive;
let able_to_vote;
if (my_Age < 17) {
	able_to_learn_to_drive = false;
	able_to_vote = false;
}
else if (my_Age < 18) {
	able_to_learn_to_drive = true;
	able_to_vote = false;
}
else {
	able_to_learn_to_drive = true;
	able_to_vote = true;
}
```

## Switch statement

- Use switch statement if you want to select one of those many blocks of code to be executed

```JavaScript
switch(n) {
	case 1: execute code block 1
	break;
	case 2: execute code block 2
	break;
	default: execute default code block
	break;
}
```

- How it works:
    - First we have a single expression (here “n”) that is evaluated once
    - The value of the expression is then compared with the values for each case in the structure
    - If there is no match, the block of code associated with that case is executed
    - Use break to prevent the code from running into the next case automatically
    - The default case is used when none of the other cases are met

## Modifying a webpage using JavaScript

- The Document Object Model (DOM) is an API for interacting with XML and HTML documents
    - It allows us to interact with webpages using JavaScript
    - We can read from HTML pages
    - … and we can modify HTML pages
- Big Topic - will deal with this detail later

```JavaScript
window.onload = function() {
	
	let movies = ["Blade Runner", "Good Will Hunting", "The Good the Bad and the Ugly"];

	let body = document.querySelector('body');
	if (body) {
		let movieList = document.createElement('ul');
		for (let i = 0; i < movies.length; i++) {
			movieList.insertAdjactentHTML (
				'beforeend',
				'<li>' + movies[i] + '</li>'
			);
		}
		body.appendChild(movieList);
	}
};
```

## Errors in JavaScript

- I have the following JavaScript linked to my HTML file.

```JavaScript
let username;
let name_confirmed = false;
while(!name_confimed) {
	// loop content unimportant
}
let greeting = "Hello " + username;
alert(greeting);
```

- What happens when they run it?
    - Nothing
- It contains an error and JavaScript fails silently — it doesn’t display error messages
    - This is good — we don’t want users to see errors on our page!
    - How do we diagnose the errors though

## Document Object Model

- When we load an HTML page into a browser, a document object is created corresponding to the displayed document
    - It is global, so we can access it anywhere
    - It represents documents with a tree structure that will familiar to us from our discussion of parent/child elements
    - Nodes in the tree element HTML elements (tags and their content) or text

## Accessing HTML elements

- Each element has a JavaScript object associated with it
- We can access elements by navigating through the DOM tree, but this is not convenient or robust
- Instead, we can get any element with an ID from the DOM using a method getElementById:

```JavaScript
document.getElementById("someID");
```

- We can also access the first element which matches a CSS selector

```JavaScript
document.getElementById("ul li");
```

## Timing Interactions with the DOM

- If I want to read/write a particular DOM element, what does this imply about WHEN the code should run?
    - The element will only exist in the DOM when the element has been loaded into the browser
    - I cannot run the code until the page has loaded!

DO NOT TRY TO PROGRAMATICALLY INTERACT WITH A DOM ELEMENT BEFORE IT HAS LOADED — IT IS SAFER TO WAIT UNTIL THE ENTIRE DOCUMENT HAS LOADED

## Modifying HTML elements (1)

- We can get the element from the DOM using, for instance

```JavaScript
document.getElementById("someID");
```

- We can get the HTML inside any element from the DOM using

```JavaScript
document.getElementById("someID").innerHTML;
```

- We can also modify the page this way

```JavaScript
document.getElementById("someID").innerHTML = "<p>Some HTML code</p>";
```

- This dynamically changes the appearance of the code
- The inner HTML property allows us to overwrite the existing content of an element. What if we want to add it?
- We can use the insertAdjacentHTML method
- Takes two (string) parameters:
    - First indicates where to insert HTML
    - Second is the HTML to insert

```JavaScript
document.getElementById("someID").insertAdjacentHTML (
	"beforeend",
	"<h1>HTML to insert</h1>"
);
```

- We can also bypass HTML and construct elements directly

```JavaScript
let ul = document.createElement('ul');
```

- Creates a HTML element and

```JavaScript
document.getElementById("someID").appendChild(ul);
```

- Adds it to the page

## Trigger JavaScript: Event Driven Programming

- We have (mostly) dealt with static JavaScript added to the page. This runs once, meaning no dynamic interaction with the user
- HTML documents contain an embedded GUI. Can use this to create documents which respond dynamically to user input
- Do this using events

## Event Driven Programming

Determined by:

- An event — some occurence on the page
- A callback — the code which is called when the event fires

## Commonly Used Events

|Event|Applicable to|Triggered|
|---|---|---|
|onload|the global window object|… when the page is loaded|
|onchange|Form input elements|… when a change id made to the element|
|onclick|Most elements|… when an element is clicked on with the mouse|
|onmouseover|Most elements|… when the mouse cursor moves over an element|
|onmouseout|Most elements|when the mouse cursor moves away from an element|

```JavaScript
document.getElementById('button').onclick = 
// code to be executed
```

## Anonymous Functions: Use Cases

- We might use an anonymous function as a callback from an event, e.g:
- I want to greet the user by name, but not until the user clicks on a button:

```JavaScript
document.getElementById("button").onclick = 
		function() {
		let name = getUsername();
		greetUserByName(name);
		};
```

## Variable Scope

- When introducing procedural programming, we said that we wanted procedures to be modular (i.e self contained)
- The best way to do this is to minimise which variables are in scope within a procedure (which variables it can affect)
- Variables can have two levels of scope
    - Global Scope: accessible anywhere
    - Local Scope: accessible within a certain context

## Global Scope

- There are two main ways to create a function with global scope
    - Declare a variable outside a function
    - Declare a variable using the let keyword
- A globally scoped variable can be accessed in all parts of your program

```JavaScript
//Global variable
let msg = "Hello world";
//Function using global variable
function helloWorld() {
	document.querySelector("body").innerHTML = msg;
}
```

- What does the function helloWorld do when called

WE DONT KNOW

- The msg var will be evaluated when the function is ran, until then we do not know
- Every other part of the program has access to msg
- It could be modified anywhere (non-local changes)
- This breaks modularity and makes it very hard to diagnose problems in our code>

- Best practice: we should avoid global variables whenever possible

## Global Scope: Problems

- A simple program in which global scope causes problems

```JavaScript
//Global variable
let msg = "Hello World!";
//Func using global var
function helloWorld() {
	document.querySelector("body").innerHTML = msg;
}
// Update of global variable
msg = "Goodbye World";
/* Hello world is called - it will look up the value of
	variable alert_string and find that it contains "Goodbye World".
	This is what will be printed
*/
helloWorld();
```

## Local Scope

- If we declare a variable inside a function and use the let keyword, it has local scope
- A locally scoped variable can only be accessed inside the body of the function in which it is formed in which it is defined (or nested functions)

```JavaScript
//Function using local variable
	function helloWorld() {
		// local variable
		let msg = "Hello World";
		document.querySelector("body").innerHTML = msg;
	}
```

- So now what does the helloWorld function do now?
    - Prints “Hello World” — it is impossible for any external factors to affect this
    - Much more modular

## Definition vs Initialisation

- When we try to use an undeclared variable is JavaScript, we get a syntax error:

```JavaScript
function functionA() {
	//Error - a is undeclared
	document.querySelector("body").innerHTML = a;
}
```

- When we try t use a previously defined variable, things work as expected

```JavaScript
function functionB() {
	let b = "This is function b";
	//Prints this is functionB
	document.querySelector("body").innerHTML = b;
}
```

- What about when we use a variable that is yet to be defined

```JavaScript
function functionC() {
	//prints undefined
	document.querySelector("body").innerHTML = c;
	let c = "this is functionC";
}
```

- In JavaScript all variables declared in a given context are created at the start of that context…
- … however they are not given a value until they are assigned to.
- If they are used before they are assigned to, they have a value of undefiend

```JavaScript
function functionC() {
	//prints undefined
	document.querySelector("body").innerHTML = c;
	let c = "this is functionC";
	//Prints "This is functionC"
	document.querySelector("body").innerHTML = c;
}
```

- The exception to this is functions - as long as it is in scope, a function can be used above the place where it is defined

## Name Collissions

- If two variables with the same name are in scope at the same time we say that the variable names collide. We can avoid collisions by using let.
- In the case of a collision, the variable with the most limited scope is the one which is used
- This doesn’t overwrite the colliding variable, only hides it from view (shadowing)
- Example:

```JavaScript
var msg = "Goodbye world";
function helloWorld() {
	/* Collision - two variables called alert_string are in scope. The local alert_string
	has the most limited scope and so will be used */
	var msg = "Hello World";
	// Prints "Hello World"
	document.querySelector("body").innerHTML = msg;
}
```

## Application: Password Checker

- We will create a sign-up form with a password field
- We want users to create a password which;
    - is at least 6 characters long
    - is composed of only alphanumeric characters
    - contains at least one number, one lower case letter and one upper case letter
- When a password doesn’t meet criteria, we want to provide an informative error message
- How to validate a program?

## Validating the password

- Our current knowledge of form validation in HTML allows us to:
    - specify that a field is required
    - specify that a field should match a single regular expression
- Possible to check that all of our conditions hold a single regular expression — but not so elegant
- Not possible to provide an informative error message
- Need to know how to validate forms using JavaScript

## Accessing Form Data

Several pieces of useful syntax:

- let form = document.getElementById(”form-id”);
    
    assigns the form object with id = form-id to a variable
    
- let element = form.elementName;
    - If there is a single form element with name = “elementName” assigns it to a variable
    - If there is multiple form elements with name = “elementName” then it assigns an array to a variable
- let v = element.value;
    
    Assigns the value input into an element to a variable
    

This is fine for element which have only one possible value (text, password, drop-down menus and text-areas)

For radio buttons and check boxes we need other information. Assume element is one of these types - as we typically have groups of such elements, it will be an array:

- element.length
    
    The number of options within the element
    
- element[i]
    
    The option of the element which is in position i
    
- element[i].checked
    
    Whether element i has been checked
    

## Custom Validation

- We can interact with HTML5’s form validation API using JavaScript

  

- As we have seen, we can read user-entered data using JavaScript
- Clearly we can implement validation logic in JavaScript
- How to indicate that an element is/isn’t valid

  

- In the DOM, form elements have method setCustomValidity
    - It takes a (string) error message as a parameter
    - If the error message is empty, the element is valid…
    - … otherwise it is invalid.
- Consider the following form:

```JavaScript
<form id="sign-up">
	...
	<input type="password" name="pass" required/>
	<input type="password" name="confirmpass" required/>
	...
</form>
```

- How do we validate that the two passwords are the same
    - This is impossible using HTML
    - Instead we use JavaScript
- Function to validate the passwords:

```JavaScript
function validatePassword() {
	let form = 
	document.getElementById('signup');
	if(form.pass.value === form.confirmpass.value)
    form.confirmpass.setCustomValidity('');
	else
    form.confirmpass.setCustomValidity(
			'The two passwords do not match');
}
```

When to call the function?

- Whenever the password is changed:

```JavaScript
window.onload = function() {
	...
	let form = 
	document.getElementById('signup');
	form.pass.onchange = validatePassword;
	form.confirmpass.onchange = 
	validatePassword;
	...
}
```

## Application: Password checker

- We want to create a password which:
    - is at least 6 characters long
    - is composed only of alphanumerical characters
    - contains at least one number, one lower case letter and one upper case letter
- We need to write a JavaScript function to provide error messages

```JavaScript
validate_pass('Pass1'); // Too short
validate_pass('Password'); // Must contain a number 
validate_pass('Pw1!'); // too short, only alphanumeric characters allowed

validate_pass('Pass1'); // fine
```

## Regular Expression Syntax

- In JavaScript, we can specify a regular expression as follows

/pattern to be matched/

- JavaScript strings have a match method which checks whether the strings contains a substring matching the given pattern

```JavaScript
	"regular".match(/regular/);            //matches
"regular expression".match(/regular/);   //matches
"cat".match(/at/);                       //matches
"cot".match(/at/);                       //no match
"Regular expression".match(/regular/);   //no match
```

- We can modify regular expressions to ignore case as follows:

“Regular Expression”.match(/regular/i); //matches

- The “special characters” are the same of for HTML

## Reminder RegEx

|Syntax|Explanation|Example|
|---|---|---|
|. (dot)|Any character|[i.] matches “it”, “if”, “is”, “his”, “i&”|
|\ .|The dot character|[i\.] matches “Hi.”, “Pi.” NOT “Hi”, “Pi”|
|\w|Any alphanumeric char (a-z, A-Z, _)|\w\w\w matches “www”, “com”, “999”, “a_1” but not “a,b”|
|?|Zero or one repetitions|[ho?t] matches “hot” and “ought” but NOT “hoot”|
|+|One or more repetitions|[ho+t] matches “hot” and “hoot” but NOT “ought”|
|*|Zero or more repetitions|[ho*t] matches “ought”, “hot”, and “hoot”|
|[ … ]|One of a set of characters|[i[fs]] matches “if”, “is”, “his”, but not “it”|
|( … )|Groups of characters|(an)+ matches “ban”, “banana” but not “barn”|
|^string|Start of an input|^string matches “strings” not “substring”|
|$|End of input|string$ matches “substring” not “strings”|