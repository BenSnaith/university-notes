### Unit Objectives

- Explain the role of cryptography in Information Security.
- Define and use a number of basic ciphers.
- Understand public key cryptosystems and their use in protecting computer asset confidentiality, integrity and availability.
- Employ existing cryptographic principles and tools in a range of Information Security applications and scenarios.

### Introduction

- Cryptography = __"Secret Writing" (Greek)__
	- The art and science of concealing meaning.
	- Strongest control tool against numerous security threats.
	- Building multiple areas of higher mathematics.
- For this module, we will regard cryptography as a supporting tool
	- We will explore the main principles
	- With examples...
	- ...and applications

### Terminology

- __Encryption (encoding, enciphering)__ = the process of scrambling a message so that its meaning is not obvious.
- __Decryption (decoding, deciphering)__ = the reverse process.

![[Pasted image 20250128114543.png]]

- __Plaintext__ = the original message.
- __Ciphertext__ = the encrypted message.
- __Key__ = A device used to influence the way in which encryption and decryption are carried out
- __Cryptosystem (cipher)__ = a system for encryption and decryption.

![[Pasted image 20250128114946.png]]

# Cryptosystems

### Formal Definition

A cryptosystem is a 5-tuple*

	(E, D, P, C, K)

Where:

- P is the set of plaintext units**
- C is the set of ciphertext units
- K is the set of (possible) keys
- E: P x K -> C is the encryption function.
- D: C x K -> P is the decryption function

\* an n tuple (where n > 0) is an ordered list of n elements (set theory)
\** i.e., symbols such as 'a' or 'b', or symbol blocks such as 'ab' or 'def'

### Using a Cryptosystem

Choose an encryption key k$E$ ∈ K and decryption key k$D$ ∈ K such that for all plaintext messages p ∈ P

![[Pasted image 20250128115858.png]]
![[Pasted image 20250128115914.png]]
![[Pasted image 20250128115933.png]]
![[Pasted image 20250128120004.png]]

### Reminder: Modular Arithmetic

The London to Glasgow train leaves London at 20:00, and reaches Glasgow five hours later.

At what time does it arrive in Glasgow

__Solution:__

__The answer is 1:00 because 20 + 5 = 25 and (25 % 24 = 1). We apply % 24 to the intermediate result because there are 24 hours in a day__

- $x$ $mod$ $n$ is the remainder of $x$ $div$ $n$
- Examples
	- 7 / 3 = 2 remainder 1; therefore 7 % 3 = 1
	- 12 % 10 = 2; 50 % 7 = 1; 28 % 7 = 0
- Modulo operator in programming languages
	- Java, C, etc: '%': $y = x$ % $n$

__Cryptography uses "modulo 26" arithmetic -- why?, because there are 26 letters in the alphabet.__

### A Simple Example: The Shift Cipher

Represent letters as numbers:

![[Pasted image 20250128120651.png]]

- P = C = {0, 1, 2, 3, ..., 25}
- K = {1, 2, 3, ..., 25}
- k$E$ = k$D$ = k
- E(p, k) = p + k % 26
- D(c, k) = c - k % 26

Split plaintext into letters:

![[Pasted image 20250128121039.png]]

Replace letters with their numerical representations:

![[Pasted image 20250128121108.png]]

Apply the encryption function E(p, k) = p + k % 26; e.g for k=10

![[Pasted image 20250128121206.png]]

Convert the encryption result back to letters

![[Pasted image 20250128121244.png]]

Use the cipher text

![[Pasted image 20250128121507.png]]

### The Caesar Cipher

- The shift cipher with k = 3
- Of historical importance
	- Said to have been first used by Julius Caesar
	- Effective in roman times
		- relatively safe: few people knew how to read
		- encryption pE -> p + 3 % 26 easy to remember 
- Shift cipher trivial to break in modern times, for any k
	- Just try all 25 possible keys!*

\* we will return to this when we explore cryptanalysis later in this unit.