### Unit Objectives

- Learn about the tasks involved in implementation.
- Techniques involved in writing maintainable code.
- What is meant by _defensive programming_ and for to enforce intention.
- What tools are used in software implementation.

### Implementation - What does it involve

Two different views:

- Bennett et al. (2010) wrote:

"Implementation is concerned with the _process_ of building the new system. This involves _writing program code_. developing _database_ tables, _testing_ the new system, setting it up with _data_, possibly transferred from an old system. _training-users_ and eventually _switching over to the new system_."

- Braude & Bernstein (2011) however stated:

"The implementation phase consists of _programming_ which is the translation of the software design developed in the design phase to a programming language. It also involves _integration_, the assembly of the software parts."

- One thing in common is that `implementation` involves constructing a software system based on a design: this involves _writing program code._
- To facilitate the coding process, one needs to consider:
	- Which programming _languages_ to use for developing the required software.
	- Which _software tools_ will be used to support the software development process.
	- How to ensure that the code, though written by different programmers, will be _easy to read, understand, and maintain_.
	- How to effectively _manage changes to programs_ throughout the development process.

### Language Choice

The choice of the programming language depends on the nature of the required software system.

- e.g., JavaScript, CSS, and HTML for _client-side_ web application
- For server side scripting we could use; _PHP, Java SpringBoot, Ruby, Python_.
- Lots of simultaneous, lightweight communications? Maybe _Node.js with websockets_.
- Where a client prefers to use Microsoft products only, the implementation is likely to be _C#_.
- If the tasks require a substantial amount of processing on _tree_ data structures, a _functional programming language_ such as _Lisp, Haskell_ or possibly _Julia_ is likely to be a good choice.
- 