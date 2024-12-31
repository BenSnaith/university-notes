## Definition
- NLP = Automatic (or semi-automatic) processing of human language.

- Natural Languages include things like English and French and NOT Java or Python
- It's ultimate goal is for natural human-to-computer communication

## NLP Applications
- Auto-correct and Auto-complete
- Text classification
- Chat bots and Virtual Assistants
- Text Extraction
- Machine Translation
- Text Summarisation 
## NLP Sub-fields:
- NLU - Natural Language Understanding
- NLG - Natural Language Generation
## NLP Challenges
- Human language is complicated, confusing, and ever-changing
- We rely on a lot of contextual information as humans:
	- ### Implicit references:
		- The trees were swaying wildly outside Anne's window as she prepared for bed, and the gutters were overflowing
		- ---> It was a dark and stormy night
	- ### Ambiguous references / semantics:
		- "Call me a Taxi please"
		- ---> Their name is now a Taxi? Or they need to get a taxi?
	- ### Imprecise rules:
		- Work -> Worked
		- Teach -> Taught
	- ### Great Variety of languages:
		- English: Hi
		- Spanish: Hola
	- ### Slang words
		- BFF -> Best Friends Forever
		- OMG, this stand-up is hilarious! I'm dying.
## NLP Levels
### 1. Lexical Analysis:
- The process of breaking down a text file into paragraphs, phrases, and words
### 2. Syntactic or Syntax Analysis:
- A technique for checking grammar, arranging words, and displaying relationships between them
### 3. Semantic Analysis:
- The process of looking for meaning in a statement
### 4. Discourse Integration:
- Refers to a feeling of context
### 5. Pragmatic Analysis:
- Focuses on the overall communicative and social context, as well as its impact on interpretation

## NLP Lexical Analysis - Tokenisation
- Breaks the raw text (a sentence) into understandable parts (words) called tokens 
### Challenges:
- No space or punctuation to define words boundaries
- Symbol with word can change meaning: 100 and £100
- You're -> You are and not Your
### Different Techniques:
- #### White Space Tokenization:
	- "Hi my name is Amal" -> "Hi" | "my" | "name" | "is" | "Amal"
	- "Hi myname is Amal" -> "Hi" | "myname" | "is" | "Amal"
- #### Dictionary based tokenisation:
	- "Hi myname is Amal" -> "Hi" | "my" | "name" | "is" | "Amal"
- #### Subword Tokenisation:
	- lower -> low | er
	- smartest -> smart | est
- #### Python libraries with prebuilt functions and utilities
	- NLTK, sklearn, SpaCy, Quepy, etc.
### Stop words:
- English has a lot of connecting words which appear very frequently like "is", "and", "the", and "a" => Stop words.

- Do we need them all?
	- "~~I~~ went running yesterday" -> went running yesterday
	- "~~We~~ went ~~on a~~ run yesterday" -> went run yesterday
	- "~~They~~ ran ~~all~~ day yesterday" -> ran day yesterday

- But the intent may change based on stop words
	- "put *my* money in *my* checking account" -> "put money in checking account"
### Lemmatization:
- The algorithmic process of determining the lemma of a word based on its intended meaning

- Depends on correctly identifying the intended part of speech and meaning of a word in a sentence:
	- Rocks -> rock
	- Feet -> foot
	- Run, running, ran -> run

	- Intended meaning of "stripes"?
		- Plural noun -> Lemma: stripe
		- 3rd person present verb -> Lemma: strip

- Usually required database support.
	- E.g. to map "am" "are" "were" to "be" (no procedural technique)
	- For example: WordNet
		- WordNet is a large lexical database (database of words) of English
			- Nouns, verbs, adjectives and adverbs are grouped into sets of synonyms.
		- Used to find the lemma

### Stemming
- Process of reducing derived words to their word stem (base or root form)
- E.g.
	- Manageable -> manag
	- Managing -> manag
	- Rained -> rain

- The stem is found by removing suffixes and prefixes
- Related words map to the same stem, even if this stem is not  a valid root.
## NLP - Syntax Analysis
### Part of Speech tagging (POS)
- Labelling each word in a sentence with its appropriate part of speech
- Includes nouns, verb, adverbs, adjectives, pronouns, conjunction and their sub-categories
- E.g.:
	- "Give me your **answer**" -> Verb
	- "**Answer** the question" -> Verb
- #### Methods:
	- Lexical Based Methods
	- Probabilistic Methods
	- Deep Learning Methods

- #### Python libraries with prebuilt functions and utilities:
	- NLTK, TextBlob, SpaCy, etc.
### Dependency Parsing
- Process of analysing the grammatical structure of a sentence based on the dependencies between the words in a sentence.
## NLP - Semantic Analysis
- The process of looking for meaning in a statement
![[Pasted image 20241128202047.png]]
## Vectorisation
- The process of converting text into numerical representation
- Also called text representation, text vectorisation or word embedding
### One-hot encoding
- Basic technique for text representation
- E.g.
	- s1. "This is example one."
	- s2. "Now, here is out example number two."
- vocabulary = { "here": 1,  
					"is": 2,  
					"now": 3,  
					"number": 4,  
					"one": 5,  
					"our": 6,  
					”example": 7,  
					"this": 8,  
					"two": 9
			}
### Word embedding
- A learned representation for text where words or phrases from the vocabulary are mapped to vectors of real numbers.
	- cat => [-0.4, 0.37, . . . 0.02, -0.34, -0.15]

- It is capable of capturing context of a word in a document, semantic and syntactic similarity, relation with other words etc.

- Syntax refers to grammar 
- Semantics refers to meaning
- Similarity when the words are used in the same way, like synonyms or days of the week
- Relation with other words for example, in the case of Pronoun (WOKE) and Verb: "We passes the test"
#### Limitation
- One of the main limitations of word embeddings is that words with multiple meanings are conflated into a single representation (a single vector in the semantic space)
- In other words, polysemy and homonymy are not handles properly, since their meanings are condensed together in the same vector.

- Example:
	- John walked by the river **bank**.
	- Suzan walked into the **bank**.