### The (Very) Early Web (Client-Server Model)

The client (your computer) sends a request for a file to a server, and the server responds with the file.

### The Early Web

The same, but the server responds with a web page.

### Client-side Scripting

The client will reuse this web page / file

### AJAX and “Web 2.0”

### Modern Web Applications


## Languages and Tools

- In the next few weeks, we will cover three key client-side languages: HTML, CSS and JavaScript.
    - These form the foundation of web applications.
    - They are slow to change, so what you learn now will stay relevant.
    - Worth a serious investment in learning properly
- Modern web development relies on knowledge and use of appropriate tools (Angular, Bootstrap, React, jQuery):
    - Designed to make common tasks easier
    - Change quickly — more important to learn concepts and familiarise yourself with incorporating them.
    - You should be able to pick these up quite quickly

## Reference Material

- W3Schools
- W3C

## What is HTML

- HTML: Hyper Text Markup Language
    - Hyper Text
        - Text with hyperlinks
    - Markup
        - Separation of instructions from content
            - Content: what we are interested in
            - Instructions: how it is processes
- The basic language behind web pages
- Markup languages are basic and easy to understand

## Markup Languages

- An HTML source file is essentially a plain text document containing content and instructions
    - If we only have text, how can we tell whether something is **content** or **instruction**
    - In HTML, the characters < and > are special
        - < = start of instruction
        - > = end of instruction
- Our source files might look like this

```HTML
<start>HTML</start>
<bluetext>Hyper Text</bluetext>
<redtext>Markup language</redtext>

// NOT REAL HTML
```

## HTML as a Markup Language

- To complete our understanding we need to know:
    - What kinds of instructions does HTML accept?
        - Probably not <do my CS1IAD homework>
    - What is the syntax for these instructions
        - a line break would be </br>
    - What are the relationships between instructions
        - Can I put a line break in a list?
    - How can i qualify instructions
        - <img/> adds an image to a webpage

## How to create a HTML file

1. Open a new text document.
2. Save as a .html file.
3. Done.

## Basic HTML Document

- We have said that HTML source is just a plain text document with a .html extension
- Browsers need to know which version of HTML is being used
    - Which syntax and semantic rules should they follow
- We need to specify which version of HTML we are using inside our document!
    - is this content or instruction
        - Instruction
        - It instructs the browser to treat the document as HTML5
        - It should be placed inside the characters “<” and “>”
- In a .html document, we specify that by using HTML5 by including the following line:
    
    <!DOCTYPE html>
    
- This is called a Document Type Declaration (DTD) — every standard has one.

## Basic HTML Document Structure

- Now that we have specified the type of document we have, we need to create some sections for us to add to our content
- The four elements present in any HTML/XHTML document are:
    - The HTML section: the “root” of the document
    - The Head: information about the webpage
    - The Body: What is displayed in the webpage
    - The Title: The document’s name — this should contain text.
    - The Head and the Body should appear inside of the HTML section and the title should appear inside of the Head
    - These are all instructions and should be wrapped in <instruction>
- The correct syntax for including the head, title and body sections inside the HTML section as follows:

```HTML
<!DOCTYPE html>
<html lang="en">
	<head>
		<title>A valid HTML5 document</html>
	</head>
	<body>
	</body>
</html>
```

- We will discuss syntax rules (i.e. why the above is correct) later

## Character Encoding

- It is also good practice to specify your char set: how you are encoding characters in your document
    - If you don’t do this, your webpage may be interpreted incorrectly!
- We do this by adding an instruction to the head section of our document as follows

```HTML
<head>
	<meta charset="UTF-8"/>
	<title>A valid HTML5 document</html>
</head>
```

- This specified that the document is encoded using UTF-8, a version of Unicode. This is the most common encoding for web documents

## Commonly Used Tags

|   |   |
|---|---|
|Tag|Description|
|<h1> — <h6>|A heading for a page or section. Ranges from <h1> (most important) to <h6> (least important)|
|<p>|A paragraph of text|
|<pre>|Preformatted text in which line breaks and spacing are preserved|
|<blockquote>|A large block of quoted text|
|<em>|Used to emphasise a short snippet of text|
|<strong>|Used to strongly emphasise a short snippet of text|
|<div>|A division or a section in an HTML document|

## Container Tags

- Container tags:
    - Come in pairs <TAG> and </TAG>
    - The first tag in a pair is the start tag, the second tag (starting with “/”) is the end tag
        - HTML5 some end tags may be omitted
        - This is not good practice! Always close your tags
    - The text between the start and end tags is the element content e.g:
        - <TAG> text and markup being formatted or defined </TAG>
- Examples: The <html>, <head> and <body> tags are all container tags (start → end)

## Empty Tags

- Empty Tags:
    - Have only a single tag like <TAG />
    - Contain no content (hence, empty)
    - Good practice to self close
        - Empty tags are singular (i.e. do not come in pairs). We can indicate this by making them self-closing.
        - This is done with the final “/”, e.g.
            - <TAG /> self closes
            - <TAG> does not

## Tag Attributes

- So far we have looked at tags
    - Container Tags: <TAG>Content</TAG>
    - Empty Tags: <TAG />
- … what if we want to change the properties of a tag?
- We use attributes
- They have the forms
    - Container: <TAG ATTRIBUTE = “VALUE”>Content</TAG>
    - Empty: <TAG ATTRIBUTE = “VALUE”/>

## Tag Attribute Basics

- General form <TAG ATTRIBUTE = “VALUE”>
    - TAG — What type of tag is being used. Determines which attributes make sense to use. For instance:
        - In tables, we can use the colspan attribute to make a cell span several columns.
        - It wouldn’t make sense to use this with a paragraph!
    - ATTRIBUTE — Which property is actually being set
    - VALUE — What is that property being set to

## Tag Attribute System

- It is good practice to obey the following rules:
    - Attribute names should be lowercase
    - Attribute values should be enclosed with quotation marks
- In notes we break these rules by capitalising, here is how it should really look

<tag attribute=”value”>

- this means we have been using a fake template
- How to include attributes>
    - Just list them separated by spaces

<tag attribute1=”value1” attribute2=”value2”>

## Comments

- Good practice to use comments in your code
- Useful for documentation
- Helps you (or others) to maintain a website
- This is ignored by the browser
- <!— COMMENT —>

## Good Practice

- Use lower case tag name:
    - <p> not <P>
- Use lower case attribute names and quotation marks for attribute values
    - <a href=”url”> not <a HREF=url>
- Close all container tags
    - <h1> … </h1> not <h1> <h2> <h3>
- And self-close all empty tags
    - <img /> not <img>

## Semantic Elements

![[Untitled 53.png|Untitled 53.png]]

- Different pages have different content but often structure their content similarly
- HTML5 has introduced a range of semantic elements to support common ways of structuring documents:
    - <header — the header of a section
    - <nav> — a navigation section
    - <main> — the main content area
    - <section> — a section of a document
    - <article> — a self-contained article
    - <aside> — content tangentially related to the main textual flow (a sidebar)
    - <footer> — the footer of a section

![[Untitled 1 31.png|Untitled 1 31.png]]

## Creating new Semantic Elements

- HTML is a very flexible language
- If a tag doesn’t exist, you can create an equivalent yourself!

  

- Two tags allow us to do this:
    - <div> — used for a large block of content (like <article>)
    - <span> — used for small snippets of content (like <em>)
- Neither tag has any inherent semantic meaning. We qualify them with attributes which indicate content type:
    - id — used for content types which can occur only once per-page (like <main>)
    - class — used for content types which can occur multiple types per-page (like <section>)

  

- How to represent this featured content type in HTML?
- No appropriate tag in HTML standard
- What are it’s properties?
    - Large block of content: <div>
    - Multiple occurrences per-page: class

```HTML
<div class="featured-item">
	<img src="..." alt="..." height="..." width="..." />
	<h2>Headline Text</h2>
</div>
```

## Example: Headings

- Heading tags are container tags which create HTML headings
- Range from h1 (most important) to 6 (least important)

```HTML
<body>
	<h1>The Most Important Heading</h1>
	<h2>The Most Important Heading</h2>
	...
	<h6>The Most Important Heading</h6>
</body>
```

![[Untitled 2 29.png|Untitled 2 29.png]]

## Example: Paragraphs

- Paragraph tags are container tags which create paragraphs of text
- The text is automatically formatted

```HTML
<body>
	<h1>Document containing two paragraphs</h1>
	<p> Even if     you really  screw   it up,  they don't  matter
	</p>
	<p>
	blank lines are also ignored
	</p>
</body>
```

![[Untitled 3 27.png|Untitled 3 27.png]]

## Example: Pre-Formatted Text

- Pre tags are container tags which create sections of pre-formatted text
    - User formatting (line breaking and spacing) is persevered

```HTML
<body>
	<pre>
			This preserves
		line breaks
	and spacing
	</pre>
</body>
```

![[Untitled 4 24.png|Untitled 4 24.png]]

## Introduction to Forms

- A form is an area that can contain form elements
- Form elements are elements that allow the user to enter information e.g.
    - Text fields
    - Radio buttons
    - Checkboxes
    - Drop-down menus
    - Text area fields
- A form is defined with the <form> tag
    - We need to add another block level element which does
        - Can be, for instance <p>, <h1>, etc

```HTML
<form>
	<p>
		... Some form input ...
	</p>
</form>
```

## Form Tags (and important attributes)

- <form> tags define the whole form object. Goes into the body of your code
- <input> tags define different ways to enter data to the form, they go between form tags.
    - type — defines the appearance and behaviours of the input
    - name — identifies a specific input (or set of inputs) within the form
    - value — associates a value with a given option
    - placeholder — hint about the expected contents of a form input (e.g. name, telephone number, email address)
- <label> groups a text label with a particular input

## Input: Text

- Text
    - Used to enter a single line of text
- Syntax
    - <input type=”text” name=”username” placeholder=”Username” />

## Input: Email

- Text
    - Used to enter a single email address
    - Simple check of whether it is valid and can be carried out automatically
- Syntax

```HTML
<input type=”email” name=”email” placeholder=”Email” />
```

## Input: Password

- Text
    - Used to enter a single line of text
    - Text is not visible on the screen
- Syntax
    - <input type=”password” name=”password” placeholder=”Password” />

## Input: Radio Buttons

- Radio Buttons
    - Used to choose from a set of options
    - Only a single option can be selected
- Syntax

```HTML
<label><input type="radio" name="rdo" value="a" />A</label>
<label><input type="radio" name="rdo" value="b" />B</label>
```

- name - same name given to a whole group of radio buttons
- value - a value assigned to each radio button. Can be accessed with JavaScript

## Input: Checkboxes

- Checkboxes
    - Used to choose from a set of options
    - Multiple options can be selected
- Syntax

```HTML
<label><input type="checkbox" name="cbx" value="a" />A</label>
<label><input type="checkbox" name="cbx" value="b" />B</label>
```

- name - same as radio buttons
- value - same as radio buttons

## Input: Drop Down Menus

- Drop Down Menus
    - Used to choose from a set of options
    - Only the selected option is displayed until the box is clicked on
- Syntax

```HTML
<select name="dropbox">
	<option>Option 1</option>
	<option>Option 2</option>
</select>
```

## Input: Text Areas

- Text Areas
    - Used to enter multiple lines of text
- Syntax

```HTML
<textarea name="txtAr" rows="4" cols="40">
	Default Input
</textarea>
```

- rows — Default starting rows of the text area
- cols — Default starting columns of the text area

## Input: Submit Button

- Submit Button
    - Pressed when form is completed
    - Sends data to a server
- Syntax

```HTML
<input type="submit" value="Submit" />
```

- value — Determines what appears on the button

## Compound Forms

- Can have multiple types of inputs in a single form
- Should have ONE submit button
- Format the form (i.e. line breaks) manually)

![[Untitled 5 24.png|Untitled 5 24.png]]

## Form Validation

- What happens when we submit an incomplete form?
    - We get error messages
    - The data entered into the form persists so that we don’t have to start from the beginning
- This is an example of form validation

  

- Client-side validation of forms is common practice
    - Form is checked for completeness
    - Form data is checked for correct type
    - Stops invalid data being sent
    - Saves load on server
- We can do this with JavaScript
    - Historically, we had to do this with JS
- HTML5 introduces attributes which help us to validate forms without using JavaScript

## Required Attribute

- The indicate that an input is received, we can give it the required attribute
- required is a Boolean attribute:
    - It does not take an attribute value
    - Its present indicates that a form element is required
    - Its absence indicates that a form element is not required
- A required input element is invalid if it is empty

```HTML
<input type="password" name="pw" required />
```

## Pattern Attribute

- Many form inputs take textual data which we want to match to some pattern
- Do we know any good tools for checking whether something matches a pattern?
    - Regular Expressions
- The pattern attribute takes a regular expression as a value
- The element is invalid if it doesn’t match the regular expression

```HTML
<input type="text" name="word" pattern="[aeiou]" />
```

## Error Messages

- Browsers provide default messages for input values which are invalid
- But we want to give users more information
    - Helps them to fix problems
- If we add the title attribute to a tag, its value is displayed in the error message

```HTML
<input type="name" name="word" pattern="[aeiou]" 
 title="Your word needs to contain a vowel" />
```

## Regular Expressions

- We described email addresses in terms of character patterns.  
    For instance:  
    - A username consists of one or more letters (upper or lower case), digits, underscores or dots
- We can use regular expressions to:
    - Check whether a character pattern appears in a string
    - Find (and extract) substrings matching a given pattern
    - Replace substrings matching a given pattern
- JavaScript string have a match method which checks whether the string contains a substring matching the given pattern.

|   |   |   |
|---|---|---|
|Input|Regular Expression|Does it Match?|
|regular|regular|Yes - the two string are the same|
|regular expression|regular|Yes - the expression is a substring of the input (reg ex)|
|cat|at|Yes - the expression is a substring of the input|
|cot|at|No - the expression is not a substring of the input|
|Regular expression|regular|No - wrong case|

## Common RegEx

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