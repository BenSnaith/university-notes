# Classification of Cryptosystems 

### (symmetric vs. asymmetric)

- __Symmetric (classical, single-key) cryptosystem__
	- k$E$ = k$D$ = k
	- E and D are "mirror-image" processes*
- __Asymmetric cryptosystem__
	- k$E$ != k$D$
	- E and D typically involve different steps

\* more precisely D(k, .) = E(k, .)$^-1$

### (stream vs. block)

- __Stream cipher__
	- each plaintext symbol is encrypted independently
	- i.e. P is a set of symbols, e.g., P = {a, b, c, ..., z}
- __Block cipher__
	- The plaintext message is divided into blocks of n > 1 symbols, and these blocks are encrypted separately
	- i.e. P is a set of string of length n > 1, such as P = {aa, ab, ac, ad, ..., zy, zz}
	- Note that the different instances of the same symbol may be encrypted differently.

