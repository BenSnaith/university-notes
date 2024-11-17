Today’s topics.

- Conditional code
- Making decisions
- Program Flow

## Boolean conditions

We can make a decision is programming by performing a Boolean test. the result is either true or false.

A Boolean expression is an expression that evaluates to either true of false

- My favourite colour is pink > true
- I am afraid of programming > false
- This lecture is funny > false

The only questions we can ask in programming are true or false

We can use variables in Boolean expressions:

```JavaScript
int x = 5;
int y = 6;

boolean isXGreaterThanY = x > y;
```

```JavaScript
// Examples of Boolean expressions using variables.
x > 20;
y == 5; // Must use two ='s to differentiate between this and declaring a variable
z <= 33;
x > width;
```

| Operator | Meaning                  |
| -------- | ------------------------ |
| >        | Greater than             |
| <        | Less than                |
| >=       | Greater than or equal to |
| <=       | Less than or equal to    |
| ==       | Equal to                 |
| !=       | Not equal to             |
| !        | Not                      |

```Java
// Example of an if statement.
void setup() {
	size(400, 200)
}

void draw() {
	background(0);
	if (mouseX > width / 2)
		fill(225);
		rect(0, 0, width/2, height/2);
}

// if (boolean condition) {
//    statements to execute if true;
//    is true;
//    you may put an number of statements here;
// } else if (boolean condition) {
//    same concept if first is false;
//
// } else {
//    will execute if all other conditions are false;
// }
```

|     |                     |
| --- | ------------------- |
| &&  | both must be true   |
| \|  | either must be true |

## Implementing a button.

```Java
int x;
int y;
int w;
int h;
boolean light;

void setup() {
	size(200, 200);
	x = 50;
	y = 50;
	w = 30;
	h = 30;
	light = false;
}

void draw() {
	mousePressed() {
		if ((mouseX > x && mouseX < x + w) && (mouseY > y && mouseY < y + h)) {
			light = !light;
		}
```

## How to detect a key being pressed.

```Java
char key;

void keyPressed() {
	if (key == 'r' || key == 'e') {
		k = key;
```