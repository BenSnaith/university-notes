### Why Study PLC?

- PLC will help you reflect on what you already know (i.e. Java), and conceptualise the most important aspects and compare then with __several__ other major programming languages.
- Here are some of the languages that you will encounter in PLC.

![[Pasted image 20250119201215.png]]

_PLC focuses more on the semantic issues rather than the syntactic._

PLC will help develop...

- Increased capacity to express programming idea.
- Increased ability to learn new programming languages.
- Improved background for choosing a programming language.
- Increased ability to design good quality new languages.
- Overall advancement of computing and an improvement in the quality of software.

### Assessed Outcomes

You will demonstrate sufficient understanding of PLC by being able to;

- __Critically evaluate__ and analyse the suitability of a programming language appropriate for a given task by demonstrating awareness of the PL choices available, and knowledge of the relative strengths and weaknesses of commonly used languages and their selected features.
- __Exhibit__ working knowledge of multiple programming languages by implementing, analysing, or modifying small programs.
- __Demonstrate__ knowledge and practical ability by completing simple tasks based on understanding of demo-code and documentation related to key aspects of the programming languages.

### Natural Languages vs. Programming Languages

| Natural Languages                                         | Programming Languages                                                                      |
| --------------------------------------------------------- | ------------------------------------------------------------------------------------------ |
| Target Audience: Humans Only                              | Target Audience: Man & Machine                                                             |
| Can have multiple connotations                            | Multiple connotations = Confusion                                                          |
| Acquired over time via informal training                  | Acquired over time via formal training                                                     |
| Helps if audience understands underlying cultural context | Helps if a programmer understands underlying design process (and/or computer architecture) |

### Purpose of PLs

- Make a computer do something.
- PL should be easy to understand, for both human and computer

### The Perfect PL

__The Wishlist__
- Easy to learn.
- Expressive.
- Concise.
- Safe.
- Easy to read.
- Efficient to Execute.
- Supports reuse via abstraction.
- Has good libraries.

### The perfect PL does NOT exist

- Some of the criteria are contradictory
	- For example, concise and expressive PLs are typically abstract and thus difficult to learn. They also suffer from efficiency problems. Examples: Lisp, Haskell, and Prolog

- Many of the criteria are context dependent
	- A language can be expressive in certain applications areas but very cumbersome for use in other areas.
	- Pretty much all the mainstream languages are optimised for the specific application domains where they originated.

# Main Programming Paradigms

### Imperative PLs

- Most __common__ high-level PLs fall within this paradigm.
- View computation as structured data stored in memory along with step-by-step instructions to manipulate the data.
- __Essence:__ "Tell the computer what to do step-by-step"
- __Sub-Categories:__ Procedural and Object-Oriented PLs
- Examples: Java, C, Ada, JavaScript, PHP and Python

### Functional PLs

- Functional Programming:
	- Style of programming in which the basic method of computation is the application of function to arguments.
- A __functional PL__ is one that __supports__ and __encourages__ the functional style.

### Aside: How to write a function in Haskell

- Haskell is a functional PL.
- Syntax-wise, writing function in Haskell si different from what you are used to (in Java).
- However, the syntax of writing a function in Haskell is similar to writing a mathematical function.

![[Pasted image 20250119205443.png]]

```haskell
func x y = x^2 + y^2
```

### Imperative vs. Functional PLs

- Let's consider a simple summation function.

```java
int total = 0;
for(int i = 0; i <= 5; i++)
	total += i;
```

```haskell
sum [0..5]
```

### Functional PLs

- View computation as the evaulation of __mathematical__ functions.
- __Essence:__ Do not give the computer step-by-step instructions, rather "Describe what it is that you want".
- Basic method of computation is __application of functions to arguments.__
- One advantage of pure function PLs over imperative PLs is no __side-effects.__
- __Reward:__ Simpler code behaviour leading to better maintainability, re-usability and reliability

- Functions are __first-class citizens__ [1]
- __Meaning__:
	- Functions are no different to other data used in a program.
	- Functions can be used as arguments to functions.
	- Functions can be returned as values from other functions.
	- Functions can be written in terms of other functions (just like maths)

![[Pasted image 20250119212131.png]]

![[Pasted image 20250119212152.png]]

### Functions as Arguments

```haskell
inpFunc = sum[1..5]

applicatorFunc inpFunc a = if s=='s' then inpFunc else inpFunc/5

applicatorFunc inpFunc 'a'
Output: 3.0
applicatorFunc inpFunc 's'
Output: 15.0
```

### Logical PLs

- Even more abstract model of computation than functional PLs
- A computer is viewed as a semi-intelligent agent which has access to knowledge (in a programme)
- The agent can be asked a question and it will do its best to deduce an answer from the knowledge available in the program.

### Agentic-AI

- __What is Agentic-AI:__ "Agentic-AI is a type of AI that can make decisions, solve problems, and adapt to changing conditions"

### Agentic-AI and Logical PLs

"Agentic AI systems provide the best of both worlds: using LLMs to handle tasks that benefit from __flexibility and dynamic responses__, while combining these AI capabilities with __traditional programming__ for _strict rules, logic and performance._ This hybrid approach enables the AI to be both intuitive and precise."

### Programme Execution

| Interpreter Based Execution                                    | Compiler Based Execution                                                     |
| -------------------------------------------------------------- | ---------------------------------------------------------------------------- |
| Source code translated to machine code line by line            | Entire source code is translated to machine code at the same time            |
| Performs prompt analysis of time to analyse source code        | Consumes more time to analyse the source code                                |
| Slow code execution                                            | Much faster code execution                                                   |
| Debugging is relatively easier due to line-by-line translation | Debugging is relatively harder since an error can be anywhere in the program |
| Examples: Prolog, Python                                       | Examples: C, C++                                                             |
