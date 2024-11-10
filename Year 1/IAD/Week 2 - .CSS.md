## Cascading Style Sheets (CSS)

- In HTML5 we change presentation using Cascading Style Sheets (CSS)
    - In most previous HTML versions, some styles could be changed using attributes
- ‘Cascade’ refers to the fact that a hierarchy of style information may be specified
- Style information may be in the HTML file itself or in a separate file
    - Often contained style sheets
    - Style sheets consist of a set of rules for specifying how page elements should be displayed

## Why Use Style Sheets?

- Separate style information from content information
    - HTML for semantics
    - CSS for presentation
- Style Sheets can be kept in one place, and only one Style Sheet to revise
- If styles are defined in one place, it is easier to keep your complete Web site consistent
- Can have different Style Sheets for different audiences

## Specifying Styles

When changing style properties, we need to make sure that the browser knows three things:

- What we are applying the change to
- Which style properties are being changed
- What these properties are being changed to

## Style Sheet Syntax

We specify each using:

- SELECTOR: the element/group that we apply the change to
- PROPERTY: they style property we wish to change
- VALUE: what we are changing this property to

We combine these using the following syntax

```CSS
SELECTOR {
	PROPERTY: VALUE;
}
```

This tells the browser that:

- For all the tags matching “SELECTOR”…
- …change style property “PROPERTY”…
- …to “VALUE”

If we want to change multiple properties of a single tag type, we separate them with semicolons

```CSS
SELECTOR {
	PROPERTY1: VALUE1;
	PROPERTY2: VALUE2;
}
```

We can add CSS comments as follows

```CSS
/* add your comments here */
```

## Selectors: Elements Selectors

- Selectors define the tag type(s) that a style can be applied to
- This can be either a single type of tag or something more complex
- We select a tag using the <text> inside of the tag, e.g.:
    - The selector for <p> is p
    - The selector for <section> is section
    - The selector for <strong> is strong
- Any style properties changed are changed for all tags of this type

## Selectors: Grouping

- You can group selectors
- In the example below, we have grouped all of the header elements
- The selectors are separated by commas

```CSS
h1, h2, h3, h4, h5, h6 {
	font-style: italic;
}
```

## Selectors: Selecting All Tags

- What if we want to apply a property to all tags in the document?
    - We could list all the tags in the document
        - Not very efficient
        - What if the document changes
    - We could apply the style to the <body> and hope that all content tags inherit these
        - THEY DONT
- We can do this directly
    - To apply a style to ALL tags, use *

```CSS
* {
	property1: value1;
	property2: value2;
}
```

## Commonly Used CSS Properties

|Property|Description|
|---|---|
|color|The color of the text|
|background-color|The background color of an element|
|font-family|The font used for text|
|font-size|The size of the text|
|text-align|Where the text is placed in relation to its container|
|font-weight|The weight of the lettering (bold, normal)|
|list-style-type|Type of bullets/numbering in a list|
|width, height, padding, border, margin|control the size of all these elements|

## CSS font-family values

- The font-family property allows us to specify any font or font family that we choose

```CSS
p {
	font-family: "Times New Roman";
}
```

- Not all browsers/devices support all fonts
    - It is good practice to specify substitutes
    - Simply list options, separated by commas, e.g.:

```CSS
p {
	font-family: "Times New Roman", "Verdana", "Serif";
}
```

- The browser will choose the most appropriate

## Color Values: Names

- Some common colors can be specified by names
- 18 standard color names are supported as standard
    - These are: aqua, black, blue, green, orange, gray, green, olive, purple
- How would we make all unordered lists use blue text

```CSS
ul {
	color: blue;
}
```

## The RGB Color Model

- Humans can see colors as a combination of three primary colors
- The typical primary colors used by computer display hardware are Red, Green and Blue (RGB)
- We can use RGB to specify colors in HTML
- In a 24-bit color graphics system with 8 bits per color channel, R, G, B values typically ranging from 0 - 255 (so 1 byte)
    - 0 = low intensity
    - 255 = high intensity

## Color Values: RGB & HEX

- How do we specify this in our style sheet
- We can do this in three ways
    - Using HEX values
    - Using RGB values

```CSS
p {
	color: \#RGB;
}

body {
	color: rgb(0, 255, 127);
}
```

## Defaults

- Clearly a plain HTML page with no style rules is displayed: some default styling is taking place, e.g:
    - Choice of font
    - Size of headings
    - Spacing between elements
- Who chooses these defaults
    - Often browser vendors
    - Sometimes different choices made by different browsers!
- We often want to use a CSS Reset to remove default styling and improve consistency. Simple example

```CSS
* {
	margin: 0;
	padding: 0;
	border: 0;
}
```

## Inheritance

- Some CSS properties are inherited by default.
    - They take the same value as their parent element
- font-family is a good example of this, If you change the text of a paragraphs, emphasised text in the paragraph will use the same font.
- We can apply font-family to the body to style all text in a document through inheritance

```CSS
body {
	font-family: Arial;
}
```

Be careful when using * as it makes inheritance impossible

## Style Location

Three Ways to specify styles:

- External Style Sheets:
    - Use a separate file to define a style and import it into any number of HTML documents so as to create a uniform style for all those documents
- Document Level Style Sheet:
    - Use a <style> tag in the document header so as to affect all the tags of a particular form in that document
- Inline Styles:
    - Use a style attribute in a particular tag

## External and Document Level Styles

- We include style sheets in the <head> of our document
- For external style sheets we use the following empty tag.

```CSS
<link rel="stylesheet" type="text/css" href="style.css"/>
```

- The style information goes in the document specified by the href attribute (style.css)
    - We need to create this document separately
- For document level style sheets use the following container tag

```CSS
<style type="text/css"> style information </style>
```

- The style information goes in between the opening and closing tags

## Inline Styles

- We can also change the style of a specific tag using inline styles
- Appears in a specific tag. Not ideal because:
    - Removes document uniform
    - Mixes CSS and HTML
    - Re-coupling content and presentation
- We do this by adding the style attribute to a tag
    - Its “attribute value” should be set in the form as the CSS property and value

```CSS
<TAG style="PROPERTY:VALUE">
```

## Best Practice

- We have defined 3 ways to add styles to the document
    - Which to choose?
        - Use the most generic possible
        - Easiest to modify or replace
- Use:
    - External Style Sheets unless you have a good reason not to!
    - Document level style sheets if your style only makes sense in relation to the given page
        - If you find this, think about whether what you have done is a good idea!
    - Inline styles should be avoided!

## Well Designed Websites

- Why would/do people visit your website?
- Inventive use of CSS / HTML
- NO! It’s to use the website
- If you want visitors:
    - Offers useful/interesting content and services
    - Make what you are offering obvious and make it as easy as possible to reach!
- How?
    - Need to know how users view websites

## How do Users view your Site?

- Eye tracking studies show that in one dominant reading pattern:
    - First, users scan the top of the page horizontally
    - Then, they can scam some of the left hand side of the page vertically
    - The some more horizontal scanning and finally some more vertical scanning
- Called the F-Pattern
    - The scanning pattern can be F-Shaped
    - But doesn’t have to be (could be E-shaped)
- Implication: put content that you want users to see in areas covered by the F pattern

## Visual Hierarchies

- Another technique for drawing attention to key content is visual hierarchies
- What is a visual hierarchy?
    - Using contrast of visual properties to imply importance
    - In simple terms, making some part of our site stand out visually
- Can be used to support scanning
    - Draw attention to section headings
- …or calls to action/advertising
- Easy ways to create a visual hierarchy
    - Size
    - Color
    - Spacing

## CSS and Web Design

- Notice that both the F-Pattern and visual hierarchy place importance on layout
    - Where elements are on the page
    - How big are they
    - How well separated they are from other content
- We need to be able to control layout using CSS

## CSS Box Model

- HTML elements are treated as boxes
- How they sit in relation to each other depends on the display mode

## Block Elements

- Large blocks of content typically use `display:block`
- By default, their boxes span the entire width of their parent element and force a new line at the end

## Inline Elements

- Smaller snippets of content typically use `display:inline`
- Their boxes wrap their content and don’t force a new line

# INSERT THE PARENT CHILD REALTION PHOTOS

## CSS Box Model

- Each box is divided into four areas, the size of which can be controlled with CSS

![[Untitled 54.png|Untitled 54.png]]

## Resizing Content

- HTML elements typically contain content, such as
    - The text in the paragraph
    - The actual image in an image tap
- In CSS, this content has a size — the box (i.e. rectangle) which surrounds the content
- We can change the size of this box using the CSS properties, width and height
- These can be set absolutely

```CSS
p {
	height: 50px;
}
```

- Or relatively — as a percentage of the parent element’s size

```CSS
p {
	height: 50%;
}
```

## CSS Box Model

- Padding and Margin each extend in four directions (top, bottom, left and right)
- We can change a single direction of any of these components by adding -DIRECTION to its name (where DIRECTION is the direction we want to change)
- For instance:
    - To change the amount of padding on top of an element, we would change the property padding-top
    - To change the size of the margin to the left of an element we would change the property margin-left
- As with height and width, these can be set to either absolute or relative values
- We can also change multiple directions of padding and margin in a single line
- Assume that padding is what we want to change
    - padding: 10px, 15px, 20px, 25px
        - top, right, bottom, left (anti-clockwise)
    - padding: 10px, 15px, 20px
        - top, left and right, bottom
    - padding: 10px, 15px
        - top and bottom, left and right
    - padding: 10px
        - same everywhere
    - Same syntax for margin

## CSS Margins

- Aside from sizes, we can also set the margin in any direction to auto
- This means that the browser will auto-matically calculate a margin based on the box and element lies inside
- If the margins on opposite sides of a box (i.e. top and bottom or left and right) are both set to auto, then they will automatically be given the same value
- Because of this, we can centre align a box horizontally using, for instance:

```CSS
p {
	margin: 0 auto;
}
```

- This relies on elements having a fixed width — won’t work be default for all tags

## CSS Borders

- Borders have 3 main properties:
    - border-width: width of the border
    - border-style: line-style of the border (default value solid)
    - border-color: color of the border
- We can set all three properties together using the border property, listing the properties in the same order as above

```CSS
* {
	border: 25px solid black;
}
```

- We can also control each side of the border individually using border- followed by a direction from: top, bottom, left, right and a property, e.g.

```CSS
* {
	border-top-color: red;
}
```

## CSS Box Model: Total Size

- When calculating the size of an element, we must include:
    - The size of the content area (controlled by width and height)
    - The size of the padding, border and margin
    - Remember that we have one of each on each side of the box
    - padding:10px adds 20px to the width as there is a left and a right

## CSS Margins

- Margins are not really part of the size of an element
    - They only tell us how far the element should be from others
- When two margins touch, we get margin collapsing
    - The two margins do not add
    - One margin disappears, leaving us with the biggest of the original values
    - This is the lowest value at which the two elements are separated by (at least) their defined margins
- If two HTML elements, one with margin 10px and one with margin 50px touch, how much space will they be separated by?
    - 50px (biggest one wins)

## Box Sizing

- Sometimes we want to constrain the total size of our element (excluding margin)
- We can do this by changing the CSS box-sizing property

```CSS
SOME_SELECTOR {
	box-sizing: border-box;
	width: 200px;
}
```

- Then we are constraining the combined width of SOME_SELECTOR’s content, padding and border to be 200px

## Positioning Methods

- In CSS2, two main properties
    - position allows manual positioning of elements
        - Associated properties; top, bottom, left and right
    - float — allows block level elements to sit together
    - These properties (in particular float) had complications
- In CSS3 we will achieve the same results with flexible boxes
- Flexboxes use the property-value pair display:flex
- Can also use CSS Grid which is newer

## Flexible Boxes — Basics

- Start with the following markup:

```CSS
<div class="container">
	<p> ... </p>
	<p> ... </p>
	<p> ... </p>
</div>
```

- What is its default appearance?
    - Paragraphs are stacked on top of each other inside the <div>

![[Untitled 1 32.png|Untitled 1 32.png]]

- But make the container a flexible box

```CSS
.container {
	display: flex;
}
```

![[Untitled 2 30.png|Untitled 2 30.png]]

- If one is wide, we can allow new lines within the container

```CSS
.container {
	flex-wrap: wrap;
}
```

![[Untitled 3 28.png|Untitled 3 28.png]]

## Flexible Boxes — Justify-Content

- If a container is a flexible box, we can change its justify-content property
    - This changes how extra space in a row is allocated
- Example values:
    
    - flex-start
    
    ![[Untitled 4 25.png|Untitled 4 25.png]]
    
    - space-between
    
    ![[Untitled 5 25.png|Untitled 5 25.png]]
    

## Flexible Boxes — align-items

- If a container is a flexible box, we can change it’s align-items property
    - This changes how items are vertically aligned if they are of different heights to the container
- Example value:
    
    - flex-start
    
    ![[Untitled 6 20.png|Untitled 6 20.png]]
    
    - center
    
    ![[Untitled 7 19.png|Untitled 7 19.png]]
    

## Styling Classes and IDs

- Just as we can use selectors to select all elements of a particular type, we can also select by class and/or id

```CSS
<p>Paragraph 1</p>
<p class="important">Paragraph 2</p>
<p class="important">Paragraph 3</p>
```

- In CSS, we can apply a rule to an element class using the class selector
    - When applied to an element with class = “CLASS_NAME” it has the form .CLASS_NAME (note the leading “.”)
- To make the above paragraphs bold for instance, we could use:

```CSS
.important {
	font-weight: bold;
}
```

## Selectors: ID Selector

- Just as we can use selectors to select all elements of a particular type, we can also select by class and/or ID

```CSS
<section id="featured"> ... </section>
<section id="featured"> ... </section>
```

- In CSS, we can apply a rule to an identified element using the id selector
    - When applied to an element with id = “ID_TEXT” it has the form \#ID_TEXT
- To give the top rated section a border, for instance, we could use:

```CSS
\#top-rated {
	border: 1px solid black;
}
```

## Child Selector

- In CSS, say we have two selectors: selector_1 and selector_2
- We can combine these to create a new selector which affects tags matching selector_2 only if they are a (direct or indirect child of) tags matching selector_1 as follows:

selector_1 selector_2

- Example selectors:
    - `header h2`
        - an <h2> heading inside of a <header> tag
    - `main p`
        - a <p> inside of the <main>
    - `\#testimonials p strong`
        - a <strong> tag inside a paragraph
        - The paragraph must inside of an element with the id = “testimonials”

## Direct Child Selector

- More rarely, we may only want to select direct children
- If we have two selectors: selector_1 and selector_2 then …

`selector_1 > selector_2`

- Is a selector for tags matching selector 2 which are direct children of those matching selector_1
- Example selectors:
    - `li > ol`: an ordered list nested directly inside a list item
    - `p .important > a`: an anchor link nested directly inside any tag with the class important. the important tag is itself nested (directly or indirectly) inside a paragraph

## Styling Nested Tags: Examples

```HTML
<!DOCTYPE html>
<html lang="en">
	<head>
		<meta charset="UTF-8">
		<title>CSS Nested Titles</title>
		<style type="text/css">
			em { color: red; }
		</style>
	</head>
	<body>
		<h1><em>An emphasised heading</em></h1>
		<p><strong><em>Some strongly emphasised text</em></strong></p>
		<p><em>Some emphasised text</em></p>
	</body>
</html>
```

- This renders as:

![[Untitled 8 18.png|Untitled 8 18.png]]

```HTML
<!DOCTYPE html>
<html lang="en">
	<head>
		<meta charset="UTF-8">
		<title>CSS Nested Titles</title>
		<style type="text/css">
			p em { color: red; }
		</style>
	</head>
	<body>
		<h1><em>An emphasised heading</em></h1>
		<p><strong><em>Some strongly emphasised text</em></strong></p>
		<p><em>Some emphasised text</em></p>
	</body>
</html>
```

(p em) This renders as:

![[Untitled 9 17.png|Untitled 9 17.png]]

```HTML
<!DOCTYPE html>
<html lang="en">
	<head>
		<meta charset="UTF-8">
		<title>CSS Nested Titles</title>
		<style type="text/css">
			p > em { color: red; }
		</style>
	</head>
	<body>
		<h1><em>An emphasised heading</em></h1>
		<p><strong><em>Some strongly emphasised text</em></strong></p>
		<p><em>Some emphasised text</em></p>
	</body>
</html>
```

(p > em) This renders as:

![[Untitled 10 17.png|Untitled 10 17.png]]

## Selector Summary

|Description|HTML|CSS Selector|
|---|---|---|
|Select tag|<TAG>|TAG|
|Select identified tag|<TAG id=”UNIQUE”>|\#UNIQUE|
|Select class of any tag|<TAG class=”REPEATABLE”>|.REPEATABLE|
|Select class of specific tag|<TAG class=”REPEATABLE”>|TAG.REPEATABLE|
|Select (direct or indirect) child tag|<TAG1><TAG2>|TAG1 TAG2|
|Select direct child tag|<TAG1><TAG2>|TAG1 > TAG2|

## The Cascade: Motivation

- Assume that we have the following markup in a HTML document …

`<p id=”my-special-paragraph”> … Some Text… </p>`

… liked to a stylesheet containing the following rules:

```CSS
p {
	font-size: 10px; /* Selector matches all paragraphs */
}

\#my-special-paragraph {
	font-size: 20px; /* Selector matches only the above */
}
```

- Both selectors match the paragraph
- Which style do you think should be applied? why?
- The id selector trumps the element selector.
- General principles
    - More specific rules override less specific rules
    - If rules have the same specificity, later rules override earlier ones

## The Cascade: Formally

- A rule takes precedence over another if:
    - It is inline
    - else, it has more ID selector
    - else, it has more class selectors
    - else, it has more element selectors
    - else, it is defined later
- This is called the cascade
- We can override the hierarchy by adding “!important” …

`selector { property_1: value_1 !important }`

- But we should ONLY add this for debugging — do not leave it in your final stylesheets

## Support Considerations

- Key support considerations
    - Browser Version: what functionality do I have access to?
    - Screen Size: how will my site appear?
        - In particular screen width is important — people are willing to scroll vertically, but not horizontally!

## Support Implications

- In 2009, you could expect >95% of visitors to be using:
    - one of 4 browsers
    - screen widths between 800px and 1680px
- In 2016, to server >95% of visitors, you need to support:
    - one of 7 browsers (and many more versions)
    - screen widths between 320px and 1920px
- In 2021, to server >95% of visitors, you need to support:
    - one of 6 browsers (and many mor versions)
    - screen widths between 320px and 1920px

## Supporting Different Screen Widths

- Common approaches:
    - Server-side — have separate codebases for mobile and desktop and serve based on which device is being used.
        - Separate URLs
        - Dynamic serving
    - Client-side
        - Responsive layout
- Responsive design is not the standard
    - Lowers maintenance requirements
    - Improves SEO
    - Avoids redirects

## Responsive Design

- In responsive design we typically create a series of frozen layouts for different ranges of device width…
    - This gives us the advantages of frozen design (designer control) without the restriction of a fixed design size.
- And fall back into the liquid layout when the screen size is very small.
    - This is when screen space is at its most precious — liquid layouts allow us to maximise out usage of screen space

## Responsive Design: Breakpoints

- The first step in creating a responsive layout is choosing breakpoints — screen widths at which we change to a different design
- Below are the breakpoints for Bootstrap — a popular front-end framework

|Device Type|XS|S|M|L|XL|XXL|
|---|---|---|---|---|---|---|
|Break-point|0px|576px|768px|992px|1200px|1400px|

- We can create breakpoints in pure CSS using media queries

## CSS Media Queries

```CSS
/* Style rules for extra small screens */

@media (min-width:576px) {
	/* Style rules for small screens */
}

@media (min-width:768px) {
	/* Style rules for small screens */
}
```

## CSS Grid Layout

- Creating a good design can be hard work
- Creating 4 designs for different screen sizes is even more so!
- Any way to ease the process?
- Grids give us a framework in which to design
- Often combined with the principles of responsive design to give us a responsive grid

## Grid-based Layout: Conceptually

![[Untitled 11 15.png|Untitled 11 15.png]]

## Grid-based Layout: (Pseudo)Code

![[Untitled 12 14.png|Untitled 12 14.png]]

## Responsive Grid: Code

- We can specify in out HTML how many columns an items should occupy at different screen width

`<div class=”col-xs-6 col-md-4 col-lg-2”>`

- If behaviour not specified at given width, use same behaviour as at next-smallest width

## Bootstrap

- Bootstrap is a front-end framework
- It implements a responsive grid (meaning that we don’t have to write the style rules ourselves)
- It also contains a variety components for quick implementation of common UI elements

## Including Bootstrap on Your Page

```CSS
<!DOCTYPE html>
<html lang="en">
	<head>
		<meta charset="utf-8">
		<meta name="viewport" content="width=device-width, initial-scale=1">
		<title>Bootstrap 101 Template</title>
		<!-- Bootstrap CSS -->
		<link rel="stylesheet"
			href="https://cdn.jsdelivr.net/npm/bootstrap@5.1.1/dist/css/bootstrap.min.css" />
	</head>
	<body>
	<!-- Page Content Here -->
	<!-- Bootstrap JS -->
	<script src="https://cdn.jsdelivr.net/npm/bootstrap@5.1.1/dist/js/bootstrap.bundle.min.js"></script>
	</body>
</html>
```

## The Bootstrap Grid

- Any element that you want to be responsive should be wrapped in `<div class=”container”>`
    - Each container can contain many responsive elements
    - But you can’t nest containers inside each other
- A group of elements which you want to display on the same line (at some screen size) should be wrapped in `<div class=”row”>`
    - Each row can contain multiple elements
    - And rows can be nested inside each other
- Control the sizes of elements at different screen sizes using the syntax seen previously `(class=”col-*-*”)`
- Give elements offsets using attribute `class=”offset-*-*”`