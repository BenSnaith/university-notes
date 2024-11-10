## Causes of Runtime Errors

Incorrect Implementation

- The specification is not met.

Inappropriate object request

- For instance:
    - Invalid array access
    - Method call on a null reference

Inconsistent object state

- Extended a class, breaking contract in a overridden method
- Derived information in the class is not kept up to date (e.g. “Number of items”)

Environment

- Web server or the network is down
- No disk space left

User input

- Incorrect format of the input data
- Typos (e.g. when searching for a name)

File processing

- Missing files.
- Unreadable / unwritable files due to a lack of permissions

## Exploring Errors

Example project

- We will use the Address Book projects on Blackboard
- This week: GUI and text-based versions

Topics

- Raising errors (from the server side)
- Handling errors (from the client side)

## Address Book Projects

`AddressBook` methods

- `ContactDetails getDetails(String key)`
- `void addDetails(ContactDetails details)`
- `void changeDetails(String oldKey, ContactDetails details)`
- `ContactDetails() search(String keyPrefix)`
- `void removeDetails(String key)`
- `String listDetails()`

Storage details

- Details stored twice in the `TreeMap`: once with the name, and once with phone number as key

## Defensive Programming

Extremes in client-server interaction

- Should a server assume all clients are well-behaved?
- Or should it assume they are potentially hostile?

Tradeoffs

- Either of these changes implementation quite a bit
- In practice, we will be somewhere in the middle, but the policy must be clear for all clients. Where do we write this down?

## Issues to Address

- How much checking should a server do on the parameters?
- How to report errors?
- How can a client anticipate failure?
- How can a client deal with failure?

## Example Situation

- Suppose we create an empty AddressBook
- Now we try to remove an entry, and a runtime error results
- Whose fault is this?
- Anticipation and prevention are better than trying to blame someone

## Parameter Values

- Method parameters are a major “vulnerability” to server objects:
    - Constructor parameters initialize state
    - Method parameters influence behaviour
- Parameter checking is a defensive measure

## What went wrong?

```Java
public void removeDetails(String key) {
	ContactDetails details = book.get(key);
	book.remove(details.getName());
	book.remove(details.getPhone());
}
```

- If the key has no entry, `book.get` return a `null` reference
- When we try to follow it, the JVM raises an exception that stops the program

## Checking the Parameter

```Java
public void removeDetails(String key) {
	if(keyInUse(key)) {
		ContactDetails details = book.get(key);
		book.remove(details.getName());
		book.remove(details.getPhone());
	}
}
```

- We can we protect against this by checking if the parameter has an appropriate value before using it
- How can we let the client know that the parameter was invalid

## Approaches for Server Error Handling

Report them to the user

- Should we present some message?
- Is there even someone to see the message?
- Can they do something about the error?

Report them to the client object

- We can return a diagnostic values, or
- We can throw an exception

## Returning a Diagnostic

```Java
public boolean removeDetails(String key) {
	if(keyInUse(key)) {
		ContactDetails details = book.get(key);
		book.remove(details.getName());
		book.remove(details.getPhone());
		return true;
	}
	else {
		return false;
	}
} 
```

## Use of the Diagnostic Value

```Java
if(addresses.removeDetails("foobar")) {
	// continue normally
}
else {
	// attempt to handle error
}
```

- The client can use the special return value to react to the successful or unsuccessful removal of an entry
- If the server return an object, a special null value can indicate failure

## Pitfalls of Diagnostic Values

What the client should do

- Use the return value to attempt recovery
- This avoids program failure

What the client might do

- Ignore or misinterpret the return value
- Likely to lead to program fail

Alternative: Exceptions

- They require action from the client
- They can provide more information than a special return value

## Exceptions

What are they

- Java language features treated specially at runtime
- No need for diagnostic return values
- Instead of returning normally, invocation triggers exception handling catch blocks

Enforcement of recovery actions

- Client must catch the exception somewhere in the call hierarchy, or the program will terminate
- We cannot ignore the exception: this encourages writing specific recovery actions

## Throwing an Unchecked Exception

```Java
/**
 * ...
 * @throws NullPointerException
 */
public ContactDetails getDetails(String key) {
	if(key == null) {
		throw new NullPointerException("null key in getDetails");
	}
	return book.get(key);
}
```

1. Create new exception object
2. Throw it
3. Document it

## Exception Class Hierarchy

![[Untitled 47.png|Untitled 47.png]]

## Exception Categories

Unchecked exceptions

- Compiler does not check if clients handle it
- Subclass of RuntimeException
- Unanticipated failures: recovery is unlikely (e.g. bugs)
- Example: IllegalArgumentException

Checked exceptions

- Compiler checks that clients are handling it
- Subclass of Exception but not RuntimeException
- Anticipated failures: recovery possible (e.g. wrong input)
- Example: FileNotFoundException

## Parameter Checking

```Java
public ContactDetails getDetails(String key) {
	if(key == null) {
		throw new NullPointerException("null key");
	}
	if(key.tring().length() == 0) {
		throw new IllegalArgumentException("Empty key");
	}
	return book.get(key);
}
```

## Exceptions in Constructors

```Java
public ContactDetails(String name, String phone, String addr) {
	if(name == null) { name = ""; }
	if(phone == null) { phone = ""; }
	if(addr == null) { addr = ""; }
	
	this.name = name.trim();
	this.phone = phone.trim();
	this.address = addr.trim();
	
	if(this.name.length() == 0 && this.phone.length() == 0) {
		throw new IllegalStateException("Either the name or phone must not be blank");
	}
}
```

## Checked Exception: Example

```Java
public void saveToFile(String path) {
	File f = new File(path);
	if(!f.exists()) throw new FileNotFoundException("Oh no!");
	// ...
}
```

- If the file, does not exist, FileNotFoundException will be thrown
- FileNotFoundException extends IOException
- IOException extends Exception, and not RuntimeException
- Therefore, it is a checked exception

Compiler forces you to choose: which one makes sense?

1. Catch it
2. Let it propagate up the call stack

```Java
public void saveToFile(String path) {
	throws FileNotFoundException {
		File f = new File(path);
		if(!f.exists()) throw new FileNotFoundException("Oh no!");
		// ...
	}
}
```

Here we let the checked exception propagate

- This code is not meant to deal with missing files
- We let the exception propagate by adding the throws clause

Notes about syntax

- Throws clause take a comma-separated list of exceptions
- Polymorphism is considered: throws IOException will let FileNotFoundException through, too

## Try Blocks

```Java
try {
	addressBook.saveToFile(filename);
	tryAgain = false;
}
catch(IOException e) {
	System.out.println("Unable to save to " + filename);
	tryAgain = true;
}
```

- Clients catching an exception must protect call with try
- Control will transfer immediately to the catch block
- This mean that line 3 will not run
- Catch block cannot use variables from the try block, why (they are separate blocks duh!)

## Finding an Exception Handler

To find the handler, we continue going up the call stack until we find the handler, Let’s try following a chain of invocations which ends at an exception

![[Untitled 1 26.png|Untitled 1 26.png]]

## Catching Multiple Exceptions — Polymorphism

```Java
try {
	...
	ref.process();
	...
}
catch(Exception e) {
	// Take action on the execution
	...
}
```

- Use polymorphism to simplify
- Subclass handlers must precede superclass handlers

```Java
try {
	...
	ref.process();
	...
}
catch(Exception e) {
	// Take action on the execution
	...
}
catch(RuntimeException e) {
	// Take action on the execution
	...
}
```

What is wrong with this?

- Second catch block is the subclass, it will never be reached and this will not compile

## Catching Multiple Exceptions — Alt. Handlers

```Java
try {
	...
	ref.process();
	...
}
catch(EOFException|FileNotFoundException e) {
	// Take action on either of the exceptions mentioned
	...
}
```

Alternative error handlers have been available since Java 7

## Finally Blocks

```Java
try {
	...
	ref.process();
	...
}
catch(Exception e) {
	// Take action on the execution
	...
}
finally {
	// Perform any actions here that must happen either way
}
```

- Always runs, regardless of exception or not
- Runs even if a return statement is ran in a previous block
- Very useful for freeing resources acquired during the try block (e.g. Closing files and Scanners etc.)

## Defining New Exceptions

```Java
public class NoMatchingDetailsException extends Exception {
	private String key;
	
	public NoMatchingDetailsException(String key) {
		this.key = key;
	}
	
	public String getKey() { return this.key; }
	public String toString() {
		return super.toString() + "No details for " + key + " found";
	}
}
```

- Extend the Exception or RuntimeException classes
- Useful for providing specific diagnostic to handlers.

## Error Recovery

```Java
AddressDetails details = null;
try {
	details = addresses.getDetails(...);
} catch(Exception e) {
	System.out.println("Error: " + e);
}
String phone = details.getPhone(); // bad: ignores
```

Rule of thumb: listen to error indications

- Check diagnostic return values
- Do not ignore exceptions
- You may need a loop to try again

## Attempting Recovery with a Loop

```Java
boolean successful = false;
int attempts = 0;
do {
	try {
		addressbook.saveToFile(filename);
		successful = true;
	} catch(IOException e) {
		System.out.println("Unable to save to " + filename);
		if(attempts++ < MAX_ATTEMPTS)
			filename = an alternative file name;
	}
} while(!successful && attempts < MAX_ATTEMPTS);
if(!successful) {
	// Report the problem and give up
}
```

## Error Avoidance

Concept

- Ask the server before you invoke a service

Advantages

- More robust clients simplify servers
- Unchecked exceptions can be used
- Client logic is also simplified

Disadvantaged

- May increase client-server coupling
- Client may duplicate server checks

## Error Avoidance Examples

```Java
for(Iterator<Actor> it = list.iterator(); it.hasNext(); ) {
Actor a = it.next();
}
String key = postCodeDatabase.search(postCode);
if(key != null && key.length() > 0) {
	ContactDetails uni = book.getDetails(key);
	...
} else {
	// deal with the postcode error
}
```

## Assertions — Motivation

Internal constraints in your code

- “ContactDetails should have a non-blank key”
- “removeDetails should leave key no longer in use”
- Informalllt know but not documented

Exceptions are not a good fir

- These are internal checks we use for development
- Should not ship those to production

## Assertions — Use

```Java
public void removeDetails(String key) {
	if(key == null) {
		throw new IllegalArgumentException("Null");
	}
	if(keyInUse(key)) {
		// remove details
	}
	assert !keyInUse(key);
	assert consistentSize() : "Inconsistent book size"
```

- Requires special compiler and JVM flags
- Explicitly says what should happen at a point
- Readable and executable

## Assertions — Scenarios

```Java
// bad code: should not use assertions to do work
assert book.remove(details.getName()) != null
assert book.remove(details.getPhone()) != null
```

When not to use assertions

- Not for production use
- Not for providing real functionality

Use exceptions, or assertions

- Exceptions: external preconditions
- Assertions: Internal pre/postconditions