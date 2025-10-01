![[Pasted image 20251001090838.png]]

## Text analytics

**Text Analytics** is the process of extracting meaningful insights, patters, and information from unstructured text data.

**Example**:

|          | Review                                                      | Sentiment Analysis | Keywords                    |
| -------- | ----------------------------------------------------------- | ------------------ | --------------------------- |
| Review 1 | The product is amazing! I love it.                          | Positive           | amazing, love               |
| Review 2 | Terrible product. The product stopped working after a week. | Negative           | terrible, stopped working   |
| Review 3 | Good quality, but delivery was late                         | Neutral            | good quality, late delivery |

**Actionable Insight**:

To improve customer satisfaction:
 - Maintain the high quality product quality.
 - Address delivery delays to enhance the overall customer experience.

## NLP different levels of text analytics

 - **Lexical Analysis**: The process of breaking down a text file into paragraphs, phrases, and words.
 - **Syntactic or Syntax Analysis**: A technique for checking grammar, arranging words and displaying relationships between them.
 - **Semantic Analysis**: The process of looking for meaning in a statement.
 - **Discourse Integration**: A feeling of context
 - **Pragmatic Analysis**: Focus on the overall communicative and social content, as well as its impact on interpretation.

## Data Life-Cycle

![[Pasted image 20251001091748.png]]

## Data Cleaning

- **Identify and sort out missing data**: check for empty or null values in the dataset. Example: empty string (""), NaN (Not a Number), NULL, or None.
- **Reduce noisy data**: remove irrelevant or unnecessary parts. Example: Special Characters (@, #, etc.), extra spaces, HTML tags (in web scraped data), etc.
- **Identify and remove duplicate records**.
- **Lower-casing**: Hello -> hello

## Data Cleaning - Using RegEx

**Regular Expression** is a pattern maching-tool used to search, extract or replace using specific patterns.

```python
# Import RegEx
import re

# Specify your text
text = "Visit our website at https://www.example.com or follow us on https://twitter.com/example"

# RegEx patterns to match URLs
url_pattern = r"http[n]?://\S+"

# Remove URLs (using substitute)
clean_text = re.sub(url_pattern, "", text)

print(clean_text)
```

## Data Cleaning - Using Spacy

![[Pasted image 20251001092510.png]]

## Tokenisation - Lexical Analysis

**Tokenisation** breaks down the raw text (a sentence) into understandable part (words) called **tokens**.

![[Pasted image 20251001092642.png]]

**Challenges**:
 - No space or punctuation to define word boundaries
 - Symbols with word can change the meaning: 100 vs $100
 - You're -> **You are** and not **Your**

**Different techniquest for tokenisation

 - **White Space Tokenisation**
	 - "Hi my name is Ben" -> Hi | my | name | is | Ben
	 - "Hi myname is Ben" -> Hi | myname | is | Ben
 - **Dictionary-based Tokenisation
	 - "Hi myname is Ben" -> Hi | my | name | is | Ben
 - **Python libraries with prebuild functions and utilities
	 - NLTK, sklearn, SpaCy, Quepy, etc.
 - **BERT Tokeniser (pre-trained model)**
	 - "I love NLP!" -> 

## Removing Stopwords - Lexical Analysis

 - English has a lot of connecting words, which appear very frequently like "is", "and", "the", and "a" -> **Stop words**
 - **Do we need them all?**
	 - "I went running yesterday" -> ~~I went~~ running yesterday
	 - "We went on a run yesterday" -> ~~We~~ went ~~on a~~ run yesterday
	 - "They ran all day yesterday" -> ~~They~~ ran ~~all~~ day yesterday
 - **But the intent may change based on stop words
	 - "Put my money in my checking account" -> "Put money in checking account".

 - **Predefined Lists** (Library-based)
	 - e.g. using Python libraries such as: NLTK (Natural Lanuguage Toolkit), SpaCy.
 - **Custom Stopword Lists**
 - **Statistical**
	 - e.g. TF-IDF
 - **Transformer Models (BERT)

## Lemmatisation - Lexical Analysis

- Lemmatisation is the algorithmic process of determining the **lemma** of a word based on its intended meaning.
- Lemmatisation depends on correctly identifying the **intnded part of speech** and **meaning** of a word in a sentence.
- **Examples**
	- rocks -> rock
	- feet -> foot
	- run, running, ran -> run
- **Intended meaning of "stripes"?
	- plural noun -> Lemma: stripe
	- 3rd person present verb -> Lemma: strip
- Usually requires **database** support
	- e.g. to map "am", "are", "were", to "be" (no procedural technique)
- For example: **WordNet**
	- **WordNet** is a large lexical database (databse of words) of English, Nouns, Verbs, Adjectives and Adverbs are grouped into sets of synontms.

## Stemming - Lexical Analysis

- Stemming is the process of reducing derived words to their word stem (base or root form)
- **Examples**
	- manageable -> manag
	- managing -> manag
	- rained -> rain
- The stem is found by removing **Suffixes** and **Prefixes**.
- Related words map to the same stem even if this stem is not a valid root.

## Lemmatisation vs Stemming

| Input    | Lemmatisation | Stemming     |
| -------- | ------------- | ------------ |
| swimming | swim          | swim~~ming~~ |
| caring   | care          | car~~ing~~   |
| taught   | teach         | taught       |

## POS tagging - Syntax Analysis

**Part of Speech** (POS) tagging is a task of labelling each word in a sentence with its appropriate part of speech. **POS** include nouns, verb, adverbs, adjectives, pronouns, conjunction, and their sub-categories.

 - **Example**:
	 - "Give me your **answer**" -> Noun
	 - "**Answer** the question" -> Noun
 - POS tagging methods:
	 - Lexical Based Methods
	 - Rule Based Methods
	 - Probabilistic Methods
	 - Deep Learning Methods
 - Python libraries with prebuild functions and utilities: NLTK, TextBlob, SpaCy, etc.

## Word-sense disambiguation - Syntax Analysis

 - **Word-sense disambiguation** is the process of determining the intended meaning of a word based on its context.
 - Consider the following sentences:
	 - He read a **book** before bed.
	 - We need to **book** a table at the restaurant
		 - POS
	 - He deposited money at the **bank**.
	 - They say by the river **bank** and watched the sunset.

## NLP - Semantic Analysis

- **Semantic Analysis** is the process of looking for meaning in a statement.
 - Semantic role labelling

![[Pasted image 20251001095735.png]]

## NER Tagging - Semantic Analysis

 - **Named Entity Recognition** (NER): Identify and classify named entities (e.g. names of people, organisations, locations) in the text.

## Dependency Parsing - Semantic Analysis

- **Dependency Parsing** is the process of analysis the grammatical structure of a sentence based on the dependencies between the words in a sentence.

## Discourse Integration

**Discourse Integration** is the process of understanding how individual sentences or parts of a text relate to each other within a larger context.

 - **Anaphora Resolution**
 - **Contextual References**

**Importance of Discourse Integration**

Consider the following sentences:

 - Alex was feeling cold. **He** put on a jacket
 - **That**'s not right!

## Pragmatic Analysis

**Pragmatic Analysis** helps uncover the deeper meaning of words and sentences by going beyond their literal interpretation.

 - **Understanding Intentions
 - **Figurative Meaning**

**Importance of Syntactic or Syntax Analysis**

Consider the following sentences:

 - **"Can you open the window?"**
 - **"He's in hot water"**

## NLP - Data Labelling

![[Pasted image 20251001102426.png]]

## AI NOTES

# Natural Language Processing: Data Pre-processing and Text Analytics

## Course Information

- **Lecturer**: Dr Amal Htait
- **Email**: a.htait@aston.ac.uk
- **Module**: DG3NLP: Natural Language Processing
- **Institution**: Aston University, Birmingham, UK

---

## Table of Contents

1. [Introduction to Text Analytics](#introduction)
2. [Data Pre-processing](#data-preprocessing)
3. [Lexical Analysis](#lexical-analysis)
4. [Syntactic Analysis](#syntactic-analysis)
5. [Semantic Analysis](#semantic-analysis)
6. [Discourse Integration](#discourse-integration)
7. [Pragmatic Analysis](#pragmatic-analysis)
8. [Data Labelling and Balancing](#data-labelling)

---

## <a name="introduction"></a>1. Introduction to Text Analytics

### Definition

**Text Analytics** is the process of extracting meaningful insights, patterns, and information from unstructured text data.

### Key Distinction

- **Data Pre-processing**: Cleaning and preparing raw text
- **Text Analytics**: Extracting insights from processed text

### Example Application: Customer Review Analysis

|Review|Sentiment|Keywords|
|---|---|---|
|"The product is amazing! I love it."|Positive|amazing, love|
|"Terrible product. Stopped working after a week"|Negative|terrible, stopped working|
|"Good quality, but delivery was late"|Neutral|good quality, late delivery|

**Actionable Insight**: Maintain product quality, address delivery delays

---

## <a name="data-preprocessing"></a>2. Data Pre-processing

### Core Steps

1. **Text Cleaning**
2. **Lowercasing**
3. **Tokenization**
4. **Stop-word Removal**
5. **Stemming/Lemmatisation**
6. **Removing Duplicates/Nulls**
7. **Spelling Correction/Normalisation**

### Data Cleaning Techniques

#### Tasks

- Identify and handle missing data (empty strings, NaN, NULL, None)
- Remove noisy data (special characters, extra spaces, HTML tags)
- Remove duplicate records
- Convert text to lowercase

#### Python Libraries

- **RegEx**: Pattern matching for cleaning
- **SpaCy**: Advanced NLP operations

#### Example: Using RegEx

```python
import re

text = "Visit our website at https://www.example.com or follow us on http://twitter.com/example!"

# Remove URLs
url_pattern = r"http[s]?://\S+"
clean_text = re.sub(url_pattern, "", text)
# Output: "Visit our website at or follow us on!"
```

#### Example: Using SpaCy

```python
import spacy

nlp = spacy.load("en_core_web_sm")
text = "Let's clean this text: Remove punctuation! And lowercase it."
doc = nlp(text)

cleaned_words = []
for token in doc:
    if not token.is_punct:
        cleaned_words.append(token.text.lower())

cleaned_text = " ".join(cleaned_words)
# Output: "let's clean this text remove punctuation and lowercase it"
```

---

## <a name="lexical-analysis"></a>3. Lexical Analysis

### Definition

The process of breaking down text into paragraphs, phrases, and words.

### Purpose

- Word identification
- Text simplification

---

### 3.1 Tokenization

#### Definition

Breaking raw text (sentences) into understandable parts (words) called **tokens**.

**Example**: "What restaurants are nearby?" → ["What", "restaurants", "are", "nearby"]

#### Challenges

- No spaces/punctuation in some languages (e.g., Chinese: 寵物 = pet)
- Symbols change meaning (100 vs £100)
- Contractions (You're → You are, not Your)

#### Tokenization Techniques

1. **White Space Tokenization**
    
    - "Hi my name is Amal" → ["Hi", "my", "name", "is", "Amal"]
    - Limitation: "Hi myname is Amal" → ["Hi", "myname", "is", "Amal"]
2. **Dictionary-Based Tokenization**
    
    - Uses word dictionaries to split compound words
    - "Hi myname is Amal" → ["Hi", "my", "name", "is", "Amal"]
3. **Library-Based Tokenization**
    
    - **Python libraries**: NLTK, sklearn, SpaCy, Quepy
4. **BERT Tokenizer** (Subword tokenization)
    
    - "I love NLP!" → ["[CLS]", "I", "love", "NL", "##P", "!", "[SEP]"]

#### Example: SpaCy Tokenization

```python
import spacy

nlp = spacy.load("en_core_web_sm")
text = "SpaCy is a great NLP library."
doc = nlp(text)

for token in doc:
    print(token.text)
# Output: SpaCy, is, a, great, NLP, library, .
```

#### Example: BERT Tokenization

```python
from transformers import BertTokenizer

tokenizer = BertTokenizer.from_pretrained('bert-base-uncased')
text = "BERT is a great NLP model."
tokens = tokenizer.tokenize(text)
# Output: ['bert', 'is', 'a', 'great', 'nlp', 'model', '.']
```

---

### 3.2 Stop-word Removal

#### Definition

**Stop words** are common connecting words (e.g., "is", "and", "the", "a") that appear frequently but carry minimal meaning.

#### Purpose

- Reduce data size
- Focus on meaningful words

#### Example

- "I went running yesterday." → "went running yesterday"
- "We went on a run yesterday." → "went run yesterday"

#### Important Consideration

Stop words can be crucial for intent:

- "put **my** money in **my** checking account" vs "put money in checking account"

#### Stop-word Removal Methods

1. **Predefined Lists (Library-based)**
    
    - NLTK (Natural Language Toolkit)
    - SpaCy
2. **Custom Stop-word Lists**
    
    - Domain-specific stop words
3. **Statistical Methods**
    
    - TF-IDF (Term Frequency-Inverse Document Frequency)
4. **Transformer Models**
    
    - BERT (learns context, doesn't explicitly remove stop words)

#### Example: SpaCy Stop-word Removal

```python
import spacy

nlp = spacy.load("en_core_web_sm")
text = "This is just a simple example to demonstrate stop word removal."
doc = nlp(text)

no_stopwords = []
for token in doc:
    if not token.is_stop:
        no_stopwords.append(token.text)

result = " ".join(no_stopwords)
# Output: "Simple example demonstrate stop word removal."
```

---

### 3.3 Lemmatisation

#### Definition

The algorithmic process of determining the **lemma** (base/dictionary form) of a word based on its intended meaning.

#### Key Features

- Depends on correctly identifying the **part of speech** and **meaning**
- Produces valid dictionary words
- Context-aware

#### Examples

- rocks → rock
- feet → foot
- run, running, ran → run

#### Ambiguous Example: "stripes"

- As **plural noun** → Lemma: stripe
- As **3rd person present verb** → Lemma: strip

#### Implementation

Requires **database support** (e.g., WordNet)

**WordNet**: A large lexical database grouping nouns, verbs, adjectives, and adverbs into synonym sets.

- URL: https://wordnet.princeton.edu
- Online demo: https://textanalysisonline.com/nltk-wordnet-word-lemmatizer

#### Diagram: Lemmatisation Mapping

```
am  ─┐
are ─┼→ be
were─┘
```

---

### 3.4 Stemming

#### Definition

The process of reducing derived words to their **word stem** (base/root form) by removing suffixes and prefixes.

#### Key Features

- Uses rule-based approach
- May not produce valid dictionary words
- Faster than lemmatisation
- Context-independent

#### Examples

- manageable → manag
- managing → manag
- rained → rain

#### Suffix/Prefix Structure Example

```
unreliability = un + rely + able + ity
├─ PREFIX: un (negative)
├─ BASE: rely (depend with full trust)
├─ SUFFIX: able (capable of)
└─ SUFFIX: ity (quality/condition)
```

#### Popular Algorithm

**Porter Stemming Algorithm**: https://9ol.es/porter_js_demo.html

---

### 3.5 Lemmatisation vs Stemming

|Input|Lemmatisation|Stemming|
|---|---|---|
|swimming|swim|swimming|
|caring|care|caring|
|taught|teach|taught|

**Key Difference**: Lemmatisation produces dictionary words; stemming may not.

---

## <a name="syntactic-analysis"></a>4. Syntactic (Syntax) Analysis

### Definition

A technique for checking grammar, arranging words, and displaying relationships between them.

### Importance

Compare:

- "The cat chased the mouse." ✓ (grammatically correct)
- "Mouse the chased cat the." ✗ (grammatically incorrect)

---

### 4.1 Part-of-Speech (POS) Tagging

#### Definition

Labelling each word in a sentence with its appropriate part of speech (noun, verb, adverb, adjective, pronoun, conjunction, etc.).

#### Context Matters

- "Give me your **answer**" → Noun
- "**Answer** the question" → Verb

#### POS Tagging Methods

1. **Lexical-Based Methods**
2. **Rule-Based Methods**
3. **Probabilistic Methods**
4. **Deep Learning Methods**

#### Python Libraries

- NLTK
- TextBlob
- SpaCy

#### Common POS Tags

|Tag|Meaning|Examples|
|---|---|---|
|ADJ|Adjective|new, good, high, special|
|ADP|Adposition|on, of, at, with, by, into|
|ADV|Adverb|really, already, still, early|
|CONJ|Conjunction|and, or, but, if, while|
|DET|Determiner|the, a, some, most, every|
|NOUN|Noun|year, home, costs, time|
|NUM|Numeral|twenty-four, fourth, 1991|
|PRT|Particle|at, on, out, over, per|
|PRON|Pronoun|he, their, her, its, my|
|VERB|Verb|is, say, told, given, playing|

#### Online Tool

https://parts-of-speech.info/

---

### 4.2 Word-Sense Disambiguation

#### Definition

Determining the intended meaning of a word based on its context.

#### Examples

- "He read a **book** before bed." (book = noun, reading material)
- "We need to **book** a table at the restaurant." (book = verb, reserve)
- "He deposited money at the **bank**." (bank = financial institution)
- "They sat by the river **bank** and watched the sunset." (bank = edge of river)

#### Technique

Uses **POS tagging** to determine context and meaning.

---

## <a name="semantic-analysis"></a>5. Semantic Analysis

### Definition

The process of looking for meaning in a statement.

### Importance

Consider: "Milk drinks the baby."

- **Syntactically correct** (proper sentence structure)
- **Semantically incorrect** (illogical meaning)

---

### 5.1 Semantic Role Labeling

Identifies the semantic relationships between words.

#### Example

**Sentence**: "Lansky left Australia to study the piano at the Royal College of Music"

Semantic roles:

- **Student**: Lansky
- **Object**: Lansky
- **Departing**: left
- **Source**: Australia
- **Purpose**: to study
- **Education**: study
- **Subject**: the piano
- **Institution**: Royal College of Music

---

### 5.2 Named Entity Recognition (NER)

#### Definition

Identifying and classifying named entities (people, organizations, locations, dates, etc.) in text.

#### Common Entity Types

- **PERSON**: Names of people
- **NORP**: Nationalities, religious/political groups
- **ORG**: Organizations, companies, agencies
- **GPE**: Geopolitical entities (countries, cities, states)
- **DATE**: Dates and periods
- **LOC**: Non-GPE locations
- **PRODUCT**: Products
- **EVENT**: Named events
- **WORK OF ART**: Titles of books, songs, etc.
- **LANGUAGE**: Languages
- **TIME**: Times smaller than a day
- **PERCENT**: Percentages
- **MONEY**: Monetary values
- **QUANTITY**: Measurements
- **ORDINAL**: Ordinal numbers (first, second)
- **CARDINAL**: Cardinal numbers

#### Example

**Text**: "Apple Inc. is planning to open a new store in San Francisco on January 15, 2024."

NER Tags:

- **Apple Inc.** → ORG
- **San Francisco** → GPE
- **January 15, 2024** → DATE

#### Online Visualizer

displaCy Named Entity Visualizer (SpaCy)

---

### 5.3 Dependency Parsing

#### Definition

Analyzing the grammatical structure of a sentence based on dependencies between words.

#### Example: "rainy weather"

```
rainy ←─ amod ─→ weather
```

(amod = adjectival modifier)

#### Complex Example

**Incorrect analysis**:

- eat sushi with tuna (ambiguous: eating sushi that has tuna, or eating sushi while having tuna separately?)

**Correct analysis**:

- Requires understanding of sentence structure through dependency relationships

**Note**: Dependency parsing reveals how words relate to form meaning.

---

## <a name="discourse-integration"></a>6. Discourse Integration

### Definition

Understanding how individual sentences or parts of text relate to each other within the larger context.

### Key Concepts

1. **Anaphora Resolution**
    
    - Resolving pronouns to their referents
    - Example: "Alex was feeling cold. **He** put on a jacket." (He = Alex)
2. **Contextual References**
    
    - Understanding implicit references
    - Example: "**That's** not right!" (What does "that" refer to?)

### Importance

Without discourse integration, text loses coherence and meaning across sentences.

---

## <a name="pragmatic-analysis"></a>7. Pragmatic Analysis

### Definition

Understanding the deeper meaning of words and sentences beyond their literal interpretation.

### Key Concepts

1. **Understanding Intentions**
    
    - "Can you open the window?"
        - Literal: Asking about ability
        - Pragmatic: Polite request to open the window
2. **Figurative Meaning**
    
    - "He's in hot water."
        - Literal: Person is in heated water
        - Pragmatic: Person is in trouble

### Importance

Pragmatic analysis is crucial for:

- Natural dialogue systems
- Understanding indirect speech acts
- Interpreting sarcasm, irony, and metaphors
- Cultural and social context

---

## <a name="data-labelling"></a>8. Data Labelling and Balancing

### 8.1 Data Labelling

#### Purpose

Creating training datasets for supervised machine learning models.

#### Example: Sentiment Analysis

|Training Examples|Labels|
|---|---|
|Simply loved it|Positive|
|Most disgusting food I have ever had|Negative|
|Stay away, very disgusting food!|Negative|
|Menu is absolutely perfect, loved it!|Positive|
|A really good value for money|Positive|
|This is a very good restaurant|Positive|
|Terrible experience!|Negative|
|This place has best food|Positive (Test)|
|This place has most pathetic serving food!|Negative (Test)|

**Split**:

- Training data: Used to train the model
- Test data: Used to evaluate model performance

---

### 8.2 Data Balancing

#### Problem

Imbalanced datasets (e.g., 90% positive, 10% negative reviews) lead to biased models.

#### Solutions

1. **Undersampling**
    
    - Reduce majority class samples to match minority class
    - **Advantage**: Faster training
    - **Disadvantage**: Loss of potentially useful data
2. **Oversampling**
    
    - Add samples to minority class (duplication or synthetic generation)
    - **Advantage**: No data loss from majority class
    - **Disadvantage**: Risk of overfitting

#### Example: Python Undersampling

```python
import random

# Example dataset: (text, label)
dataset = [
    ("Hello, how are you?", 0),
    ("Let's meet tomorrow.", 0),
    ("Can you send me the report?", 0),
    ("Are you coming to the party?", 0),
    ("Don't forget our meeting.", 0),
    ("Hi, long time no see!", 0),
    ("See you at the gym.", 0),
    ("Are you free tonight?", 0),
    ("You won a prize! Click here!", 1),
    ("Congratulations! You've been selected!", 1),
    ("Urgent: Claim your reward now!", 1)
]

# Separate majority and minority classes
majority = [sample for sample in dataset if sample[1] == 0]
minority = [sample for sample in dataset if sample[1] == 1]

# Undersample majority to match minority size
random.seed(42)
majority_undersampled = random.sample(majority, len(minority))

# Combine balanced dataset
undersampled_dataset = majority_undersampled + minority

print("Before undersampling:", {0: len(majority), 1: len(minority)})
print("After undersampling:", {0: len(majority_undersampled), 1: len(minority)})
# Output:
# Before: {0: 9, 1: 3}
# After: {0: 3, 1: 3}
```

---

## NLP Data Life-Cycle Overview

```
Data Collection
      ↓
Text Cleaning ←────────────┐
      ↓                     │
Tokenization                │
      ↓                     │
Remove Stopwords            │
      ↓                     │
POS Tagging                 │
      ↓                     │
NER Tagging                 │
      ↓                     │
Stemming/Lemmatisation      │
      ↓                     │
Data Labelling              │
      ↓                     │
Data Balancing              │
      ↓                     │
Model Training              │
      ↓                     │
Data Analysis ←─────────────┘
      ↓
Information Retrieval
```

---

## Recommended Reading

- **Eisenstein, Jacob**. _Introduction to Natural Language Processing_. MIT Press, 2019.
    - Chapter 8: Lexical and Syntactic Analysis
    - Chapter 11: Semantic Analysis

---

## Summary

This lecture covered the essential pipeline for NLP data processing:

1. **Data Pre-processing**: Cleaning, lowercasing, handling missing data
2. **Lexical Analysis**: Tokenization, stop-word removal, stemming/lemmatisation
3. **Syntactic Analysis**: POS tagging, word-sense disambiguation
4. **Semantic Analysis**: NER, dependency parsing, semantic role labeling
5. **Discourse Integration**: Anaphora resolution, contextual understanding
6. **Pragmatic Analysis**: Understanding intentions and figurative language
7. **Data Preparation**: Labelling and balancing datasets for model training

Each step builds upon the previous, transforming raw text into structured, meaningful data suitable for machine learning applications.