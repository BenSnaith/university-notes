![[Pasted image 20251013225836.png]]

![[Pasted image 20251013225854.png]]

## Authentication Methods

![[Pasted image 20251013225930.png]]

## Something you do (dynamic bio-metric)

It's the unique ways in which individuals act, including:

 - Handwriting
 - Keystroke
 - Voice Recognition
 - Walking Speed
 - Gestures

![[Pasted image 20251013230054.png]]

## Risk Assessment for User Authentication

Described an organisation's degree of certainty that a user had presented a credential that refers to his or her identity.

More specifically is defined as:

*The degree of confidence in the vetting process used to establishthe identity of the individual to whom the credential was issued.*

*The degree of confidence that the individual who uses the credential is the individual to whom the credential was issues.*

## Risk Assessment for User Authentication: Potential Impact

 - FIPS 199 defines three levels of potential impact on organisations or individuals should there be a breach of security
	 - **Low**
		 - An authentication error could be expected to have a limited adverse effect of organisational operations, organisations assets, or individuals.
	 - **Moderate**
		 - An authentication error could be expected to have a serious adverse effect.
	 - **High**
		 - An authentication error could be expected to have a severe or catastrophic adverse effect.

## Maximum potential impact for each assurance level

![[Pasted image 20251013230709.png]]

## Password-based Authentication

 - Widely used line of defence against intruders
 - User provides name / login and password
 - System compares the password with the one stored for that specific login

## Password Vulnerabilities

![[Pasted image 20251013230902.png]]

![[Pasted image 20251013230920.png]]

## UNIX Implementation

 - Original scheme
	 - Up to eight printable characters in length.
	 - 12-bit salt used to modify DES encryption into a one-way hash function.
	 - Zero value repeatedly encrypted 25 times.
	 - Output translated to 11 character sequence.
 - Now regarded as inadequate
	 - Still often required for compatibility with existing account management software or multivendor environments.

## Improved Implementations

![[Pasted image 20251013231416.png]]

## Password Cracking

 - Dictionary Attacks
	 - Develop a large dictionary of possible passwords and try each against the password file
	 - Each password must be hashed using each salt value and then compared to stored hash values
 - Rainbow Table Attacks
	 - Pre-compute tables of hash values for all salts
	 - A mammoth table of hash values
	 - Can be countered by using a sufficiently large salt value and a sufficiently large hash length.
 - Password crackers exploit the fact that people choose easily guessable passwords
	 - Shorter password lengths are also easier to crack.
 - John the Ripper
	 - Open-source password cracker first developed in 1996.
	 - Uses a combination of brute-force and dictionary techniques.

## Modern Approaches

 - Complex password policy
	 - Force users to pick stronger passwords
 - However, password-cracking techniques have also improved
	 - The processing capacity available for password cracking has increased dramatically.
	 - The use of sophisticated algorithms to generate potential passwords.
	 - Studying examples and structures of actual passwords in use.

## Password File Access Control

![[Pasted image 20251014102435.png]]

## Password Selection Strategies

![[Pasted image 20251014102528.png]]

## Proactive Password Checking

 - Rule Enforcement
	 - Specific rules that passwords must adhere to.
 - Password Checker
	 - Compile a large dictionary of passwords not to use.
 - Bloom Filter
	 - Used to build a table based on hash values.
	 - Check desired password against this table.

## Tokens

 - Objects that a user possesses for the purpose of user authentication are called tokens.
 - In this section, we examine two types of tokens that are widely used.

## Memory Cards

 - Can store by do not process data.
 - The most common is the magnetic stripe card.
 - Can include an internal electronic memory.
 - Can be used alone for physical access:
	 - Hotel room
	 - ATM
 - Provides significantly greater security when combined with a password or PIN.
 - Drawbacks of memory cards include:
	 - Requires a special reader
	 - Loss of token
	 - User dissatisfaction

## Smart Card and Smart Tokens

![[Pasted image 20251014103000.png]]

![[Pasted image 20251014103017.png]]

## Electronic Identity Cards (eID)

 - Use of smart cards as a national identity card for citizens
 - Can serve the same purposes as other national ID cards, and similar cards such as a driver's license, for access to government and commercial uses.
 - Can provide stronger proof of identity and can be used in a wider variety of applications.
 - In effect, is a smart card that has been verified by the national government as valid and authentic.

 - Most advanced deployment is the German Card *neuer Pseronalasweis*
 - Has human-readable data printed on its surface
	 - Personal Data
	 - Document Number
	 - Card Access Number (CAN)
	 - Machine Readable Zone (MRZ)

![[Pasted image 20251014103405.png]]

![[Pasted image 20251014103421.png]]

## Password Authenticated Connection Establishment (PACE)

 - Ensures that the contactless RF chip in the eID card cannot be read without explicit access control.
 - For online applications, access is established by the user entering the 6-digit PIN (which should only be known to the holder of the card).
 - For offline applications, either the MRZ printed on the back of the card or the six-digit card access number (CAN) printed on the front is used.

## Bio-metric Authentication

 - Attempts to authenticate an individual based on unique physical characteristics.
 - Based on pattern recognition.
 - Is technically complex and expensive when compared to passwords and tokens.
 - Physical characteristics used include:
	 - Facial characteristics
	 - Fingerprints
	 - Hand Geometry
	 - Retinal Pattern
	 - Iris
	 - Signature
	 - Voice

![[Pasted image 20251014103824.png]]

![[Pasted image 20251014103836.png]]

![[Pasted image 20251014103852.png]]

![[Pasted image 20251014103907.png]]

## Remote User Authentication

 - Authentication over a network, the Internet, or a communications link is more complex.
 - Additional security threats such as:
	 - Eavesdropping, capturing a password, replaying an authentication sequence that has been observed.
 - Generally rely on some form of a challenge-reponse protocol to counter threats.

![[Pasted image 20251014104142.png]]

![[Pasted image 20251014104159.png]]

![[Pasted image 20251014104235.png]]

![[Pasted image 20251014104247.png]]