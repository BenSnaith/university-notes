- Lecture Notes
    
    ## Eliza: first steps into AI
    
    - ELIZA is an early natural language processing computer program created from 1964 to 1966 at the MIT Artificial Intelligence Laboratory by Joseph Weizenbaum
    - Eliza simulated conversation by using a ‘pattern matching’ and substitution methodology that gave users an illusion of understanding on the part of the program
    - [Reference](https://en.wikipedia.org/wiki/ELIZA)
    
    ## More on Eliza
    
    - Alan Turing: “If a computer could think, how could we tell?” If the responses from the computer were indistinguishable from that of a human, the computer could be said to be thinking.
    - Joseph Weizenbaum: Once a particular program is unmasked, once its inner workings are explained in language sufficiently plain to induce understanding, its magic crumbles away; it stands revealed as a mere collection of procedures, each quite comprehensible. The observer says to himself “I could have written that”
    
    ## An example conversation with ELIZA
    
    ![[Untitled 49.png|Untitled 49.png]]
    
    ## Writing the Eliza program.
    
    - Weizenbaum identified five “fundamental technical problems” for ELIZA to overcome:
        - the identification of critical words in the input
        - the discovery of minimal context
        - the choice of appropriate transformations
        - The generation of responses appropriate to the transformation in the absence of critical words
        - The provision of an ending capacity for ELIZA scripts
    - We will look at building our own, simplified, ELIZA
    - We have an additional problem, how will we get the input that the user typed
    
    ## Getting the user input
    
    - When we move onto Java. we can use classes like out `Scanner` to read keyboard inputs.
    - In the meantime, in Processing we can use the `keyPressed` method to read a line of input typed at the keyboard
    - We need two variables, one to hold the keys that are typed and one to store the whole line of input when the user presses Enter.
    
    ```Java
    // Variable to store text currently being typed
    String typing;
    // Variable to hold the saved input
    String input;
    
    void setup() {
    	size(480, 270);
    	typing = "";
    	input = "";
    }
    ```
    
    ## Getting user input
    
    ```Java
    void keyPressed() {
     if (key == '\n') { // end of line
    	// save the input
    	input = typing;
    	// clear the typing
    	typing = "";
    } else if (key == BACKSPACE && typing.length()>0) {
    	typing = typing.substring(0, typing.length()-1);
    	} else if (Character.isLetterOrDigit(key) || Character.isSpaceChar(key)) {
    		// Otherwise, add the character to the string
    		typing = typing + key;
    	}
    }
    ```
    
    Lets look at this method in detail…
    
    ## User presses the “Enter” key
    
    - A line of input is ended when the user presses the “Enter” key and enters a newline ‘\n’.
    - The first part of the method handles that event:
    
    ```Java
    if (key == '\n') {
    	// save the input
    	input = typing;
    	// clear the typing
    	typing = "";
    }
    ```
    
    - The `input` variable gets assigned the line of text that was typed in
    - The `typing` variable is cleared ready for the next line of input
    
    ## The `substring` method
    
    - To handle the user pressing the backspace for delete, our `keyPressed` method contains:
    
    ```Java
    } else if (key = BACKSPACE && typing.length()>0) {
    	// Remember typing will hold the current word that is being typed which is why we
    	// index at 0.
    	typing = typing.substring(0, typing.length()-1)
    }
    ```
    
    - We can only delete a character when the length of `typing` is greater than 0, which makes a lot of sense.
    - We create a copy of the `typing` string which is one character shorter using the `substring` method.
    - The `substring` method is another of the useful methods of the `String` class. The first parameter is the start character index (included) and the second parameter is the end character index (not included)
    
    ## The `character` class
    
    - to limit input to letters (lower and upper case) digits and whitespace, our keyPressed method contains the following code:
    
    ```Java
    } else if (Character.isLetterOrDigit(key) || Character.isSpaceChar(key)) {
    	// Otherwise, concatenate the String
    	// Each character typed by the user is
    	// added to the end of the String variable
    	typing = typing + key;
    }
    ```
    
    - The character class is a Java class the provides methods that allows us to work with single characters.
    - It is a utility class for character, in the same way the String is a class for strings.
    
    ## A design for our Eliza
    
    - Now that we have a way of getting input from the keyboard, we can make a design for our Eliza application.
    - Doing thing in and object oriented way prompts us to write a class called Responder. Related code goes together in a class
    - The Responder will have a method called generateResponse that has a single String parameter being the user’s input, and it will return a new String being Eliza’s response.
    - Step 1 is write a simple Responder that always responds with the same response.
    
    ## Documenting Design
    
    - We can use a **class diagram** to document the design.
    - Here is a class diagram for our Eliza program. We treat the `setup`/`draw` tab as one class and create a new class called `Responder`
    - In a class diagram, each box represents a class and each arrow a relationship between classes.
    
    ![[Untitled 1 28.png|Untitled 1 28.png]]
    
    - We can replace a simple and rather stupid `Responder` with a more intelligent version, so long as we keep to the design for a `Responder`
    
    ## UML diagrams
    
    - Here is the box representing the `Responder` class:
    
    ![[Untitled 2 26.png|Untitled 2 26.png]]
    
    - The top segment contains the class name.
    - The middle segments contains the variables (the Responder class has none)
    - The bottom segment contains the methods
    - The + means that the method is public, a - would mean that it is private, each parameter is written as name: type and then we put a : followed by the return type.
    
    ## `Responder` version 0.1
    
    - This is our simple responder class. Note that it follows the design:
    
    ```Java
    public class Responder
    {
    
    	public Responder() {
    		// no variable so nothing here
    		// I think we are making a constructor to initialise this and then use the method
    	}
    
    	public String generateResponse(String question) {
    		return "That sounds interesting. Tell me more...";
    	}
    }
    ```
    
    ## Using the `Responder`
    
    - This is the key part of what we need in the setup/draw tab:
    
    ```Java
    String input; // updated in keyPressed
    String typing; // also updated in keyPressed
    Responder eliza;
    
    void setup() {
    	size(480, 270);
    	input = "";
    	typing = "";
    	eliza = new Responder();
    }
    ```
    
    ## Using the `Responder`
    
    - This is the key part of what we need in the setup/draw tab:
    
    ```Java
    void draw() {
    	background(255);
    	fill(0);
    	text("Input: " + typing, 50, 100);
    	if (input.length() > 0) {
    		System.out.println("You said: " + input);
    		String response = eliza.generateResponse(input);
    		System.out.println("Eliza said: " + response);
    		input = "";
    	}
    }
    
    // keyPressed method not shown as before
    ```
    
    ## Making a better response
    
    - There are a number of ways we could generate a more interesting response.
        1. We could select a response at random from an array of possible responses. Note this ignores the input
        2. Identify a keyword in the input and respond with a predefined response for that keyword
        3. We could refine the keyword strategy to have an array of responses from each keyword and we could pick a response at random from a list of possible responses. (We leave this as an exercise)
    - Let’s look at the first two options
    
    ## Selecting from an array of responses
    
    - In this strategy, we create a set of possible responses
    - Each individual response is a `String`.
    - Each `String` is stored in an array
    - When the user asks a question, we will return one of the responses at Random.
    
    ## Creating a Java tab in processing
    
    - Tabs with “.java” extension are saved as as Java files. The left-most TAB must be your `setup`/`draw` tab.
    - We will base this new version on version 1 described above, and use a Java `Responder` class.
    - We can dip down into pure Java by renaming the new class tab to be “Responder.java”
    - When writing pure Java code, we cannot access Processing specific values/methods such as `width`,`mouseX`,`rect`,`random`, etc, in pure Java
    - The random method is part of Processing and we can’t use it from a plain Java class.
    - Java has a `Random` class so we can use that class to do the same thing.
    - To get access to additional Java classes we need to use the import statement (as we did for `ArrayList` and `Scanner`)
    
    ## Importing classes
    
    - Another powerful aspect of OOP is that when people write classes, other people can use them by importing them into their projects.
    - As we saw in the previous week, Java has a utility library called `java.util.` It comes free with Java and includes utility classes such as `Scanner` and `ArrayList`
    - Another utility class is called `Random` and it can be used to generate all kinds of random values of different types
    - Processing’s `random` method only generates random `float` values and so is less powerful than using this class
    
    ## Using `java.util.Random`
    
    We can use pure Java anywhere inside Processing…
    
    ```Java
    import java.util.Random; // import the class
    
    Random rndGen; // declare a Random variable
    
    void setup() {
    	rndGen = new Random();
    	print("Random Integer: ");
    	println(rndGen.nextInt());
    	print("Random Integer range 0 to 9: ");
    	println(rndGen.nextInt(10));
    	print("Random Boolean: ");
    	println(rndGen.nextBoolean());
    	print("Random Float: ");
    	println(rndGen.nextFloat());
    }
    ```
    
    ## Output from that example
    
    - Here is a sample of the output from that program on the previous slide
    
    ```Java
    Random Integer: 987501494
    Random Integer range 0 to 9: 2
    Random Boolean: true
    Random Float: 0.082733154
    ```
    
    - As `Random` is a class it has lots of different methods to generate random values
    - That is different to processing’s `random` method, which always returns a `float` value
    - Every Java library class has a documentation. Read the once for `java.util.Random` [here](https://docs.oracle.com/javase/8/docs/api/java/util/Random.html).
    
    ## `Responder` version 2
    
    - After our experiment with the use of `Random`, here are the changes to our `Responder` class:
    
    ```Java
    import java.util.Random;
    
    public class Responder
    {
    	private String[] responses = {
    		"I'm not sure I understand you fully.",
    		"That sounds interesting. Tell me more...",
    		"Are you sure",
    		"Why do you ask?",
    		"What comes to mind when you ask that",
    		"Have you asked such questions before",
    		"Have you asked anyone else"
    		// We can have as many responses as we want.
    	}
    	private Random rndGen;
    }
    ```
    
    ## The rest of the `Responder`
    
    - Here is the rest of the `Responder` with the new code highlighted
    
    ```Java
    	public Responder() { // constructor
    		rndGen = new Random();
    	}
    	
    	// generate a response to input
    	public String generateResponse(String question) {
    		int randomIndex = rndGen.nextInt(responses.length);
    		return responses[randomIndex];
    	}
    }
    ```
    
    - We need to construct the random number generator, then to `generateResponses`, we return a responses from a random index.
    - We are ignoring the input question.
    
    ## Associating keywords with responses
    
    - The next version of the responder aims to get responses that are connected to the question.
    - The plan is we look for keywords. Lets say “hello” and “computer” are key words, we might have the following conversation:
    
    ```Java
    You say: Hello Eliza
    Eliza says: Hi. What seems to be your problem?
    You say: I am having trouble with my computer
    Eliza says: Why do you mention computers?
    ```
    
    - How do we associate a keyword with a response
    
    ## Associating keys with values
    
    - We need a data structure that allows us to associate a word with a string.
    - We can use another class from the util library, `java.util.Hashmap`.
    - This class allows a key to be associated with a value
    - Keys and Values can be of any class
    - We can see the Java documentation for the class [here](https://docs.oracle.com/javase/8/docs/api/java/util/HashMap.html).
    
    ## Visualising a `HashMap`
    
    - We can `put` any number of key-value pairs into a `HashMap`
    - We can then use the key to `get` the value back
    
    ![[Untitled 3 24.png|Untitled 3 24.png]]
    
    ## The `HashMap` documentation
    
    - Import this class from `java.util.HashMap`
    
    ```Java
    public HashMap();
    ```
    
    Constructs an empty HashMap with the default initial value capacity (16) but will expand as necessary
    
    ```Java
    Public V put(K key, V value)
    ```
    
    Associates the specified value with the specified key in this map, if the map previously contained a mapping for the key, the old value is replaced.
    
    ```Java
    public V get(Object key)
    ```
    
    Returns the value to which the specified key is mapped, or null if this map contains no mapping for this key.
    
    ## An example of `HashMap`
    
    - Here is an example of using a `HashMap`
    
    ```Java
    import java.util.HashMap;
    
    HashMap<String, String> contacts;
    
    void setup() {
    	contacts = new HashMap<String, String>();
    	contacts.put("Tony", "3447");
    	contacts.put("Aston", "0121 204 3000");
    	println("Aston: ", contacts.get("Aston"));
      println("Tony: ", contacts.get("Tony"));
    	println("tony: ", contacts.get("tony"));
    ```
    
    - There are two methods of this class, `put` and `get`
    - There is also a difference in the way we declare the variable
    
    ## Using a `HashMap`
    
    - First thing we should notice is something different about how to declare and assign a HashMap variable
    
    ```Java
    // declare the variable
    HashMap<String, String> contacts;
    // assigns a value
    contacts = new HashMap<String, String>();
    ```
    
    - We need to write inside < and > what the type is for the key and the value
    - The declaration here says both the **key** and the **value** are `String` types
    
    ## Putting data into a `HashMap`
    
    - The put method allows us to enter data. There are two parameters, the key and the value.
    - In our example we entered two sets of key-value pairs:
    
    ```Java
    // use the put method to enter the key-value pairs
    contacts.put("Tony", "3447");
    // enter another key-value pair
    contact.put("Aston", "0121 204 3000");
    ```
    
    ## Getting the values back out
    
    - We use the get method to get the value that is associated with a given key.
    
    ```Java
    	println("Aston: ", contacts.get("Aston"));
      println("Tony: ", contacts.get("Tony"));
    	println("tony: ", contacts.get("tony"));
    ```
    
    - The first two print statements here output 3447 and 0121 204 3000 respectively
    - The final print statement will output null because key “tony” has not value associated with it. Keys are case sensitive.
    
    ## A `HashMap` example
    
    This Java class implements a simple phone book to store and retrieve contacts
    
    ```Java
    import java.util.HashMap;
    public class PhoneBook {
    	private HashMap<String, String> numbers;
    
    	public phoneBook() {
    		numbers = new HashMap<String, String();
    	}
    	
    	public void saveNumber(String name, String number) {
    		numbers.put(name, number);
    	}
    
    	public String lookupNumber(String name) {
    		return numbers.get(name);
    	}
    }
    ```
    
    ## Using a HashMap in our Eliza
    
    - Now we know how to use a HashMap, we can add one to our eliza program.
    - We would need to make the following changes to the Responder class:
        1. Import the `java.util.HashMap` class
        2. Declare a parameter of type `HashMap` in which the keys and values are both type `String`.
        3. In the constructor, we need to assign a value to out new variable and then `put` some key-value pairs into the hashmap
        4. In the `generateResponse` method, we need to see if any of the words in the question are keys in our HashMap. if they are we should return the value associated with the keyword, if not we can return one of our existing responses.
    
    ## Implementing the `HashMap` version
    
    ```Java
    import java.util.Random;
    import java.util.HashMap;
    public class Responder {
    	private String[] responses {
    		// as before
    	}
    	private Random rngGen; // as before
    
    	private HashMap<String, String> keyResponses;
    
    	public Responder() {
    		rndGen = new Random();
    		keyResponses = new HashMap<String, String>();
    		addKeyResponses();
    	}
    ```
    
    ## Filling with key-value pairs
    
    ```Java
    private void addKeyResponses() {
    	keyResponses.put("sorry", "Apologies are not necessary");
    	keyResponses.put("remember", "What else do you recollect");
      keyResponses.put("computer", "Why mention computers");
    	// etc...
    }
    ```
    
    ## Responding to a question
    
    - In the `generateResponse` for this version, we need to use the text of the question.
    - The plan is we search the question for a keyword, then we return the value associated with that key
    - If there is no keyword, we will return a random responses from our array of other responses.
    
    ```Java
    public String generateResponse(String question) {
    	// search for keywords in question
    	String response = findKeyResponse(question);
    	if (response == null) {
    		// return a random response
    		int randomIndex = rndGen.nextInt(responses.length);
    		response = responses(randomIndex);
    	}
    	return response;
    }
    ```
    
    ## Finding a keyword and reponse
    
    - The last thing we need is the method that kinds a keyword in the question and returns a response.
    - The plan here is to use the split method to split the question on spaces.
    - Then we go through the array of words, searching for a keyword and response
    
    ```Java
    private String findKeyResponse(String text) {
    	String[] words = text.toLowerCase().split(" ");
    	for(int i = 0; i < words.length; i++) {
    		String response = keyResponses.get(words[i]);
    		if (response != null) {
    			return response;
    		}
    	}
    	return null;
    }
    ```
    
    ## Analysis of String methods
    
    - In the previous slide, we had the following line of code
    
    ```Java
    String[] words = text.toLowerCase().split(" ");
    ```
    
    - With String methods we can chains the methods together using the dot syntax because each method returns a new copy of the String
    - The above code is equivalent to:
    
    ```Java
    String lower = text.toLowerCase();
    String words[] = lower.split(" ");
    ```
    
    You can write the longer version if you find it easier to follow
    
    - We convert to lower case because out keywords are all in lowercase, remember the HashMap is key sensitive.