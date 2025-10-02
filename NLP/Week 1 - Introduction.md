## Natural Language Processing

**Natural Language Processing** is a field of science and engineering dedicated to the study and development of automatic systems that are capable of *understanding* and *generating* natural human language.

## NLP and ML

TODO
## Sub-fields of NLP

- **Natural Language Understanding**
- **Natural Language Generation**

## Common Terminology

 - **Corpus** - A large collection of texts used for training NLP models. For example, a corpus might consist of a vast set of news articles (also called a Dataset).
 - **Documents** - Individual pieces of text within a corpus. For instance.
 - **Vocabulary** - The set of unique words in a corpus. For instance, the vocabulary might include words like "economy", "politics" and "innovation".
 - **Words** - The basic units of language, such as "economy", "politics", and "innovation".
 - **Token** - A unit of text that a language model processes, such as "economy", "!", "123".

## Applications of NLP

 - **Text-Centric Processing applications**
 - **Interactive & Multi-Modal Systems applications**

## Representing words

 - In language, a **signifier** is a word and the signified is the actual thing or idea that it represents
 - **Sentence**: "Luna feeds the cat of her brother"
	 - **Signifiers**:
		 - "Luna" refers to a specific person (Luna)
		 - "cat" refers to the animal (cat)
		 - "brother" refers to a specific person (her bother)
	 - **Signified**:
		 - Luna is feeding a particular cat that belongs to her brother.
	 - **Specificity**:
		 - "The cat" refers to one specific cat, not cats in general.
		 - "Her brother" refers to a specific person, not brothers in general.
	 - **Relationships**:
		 - The sentence shows a relationship between Luna, her brother, and the cat.
	 - **Comparison**:
		 - If we say, "Luna feeds cats", the meaning changes
			 - "Cats" now refers to cats in general, not a specific cat
			 - The relationship to her bother is no longer part of the sentence.
		- If we say, "Luna feeds the dog", the meaning also changes
			- "Dog" now refers to a specific dog, not all cats.

## NLP: Word-to-Vector Conversion

- Words like "cat" and "dog" are related because they both represent animals.

## NLP Challenges

 - NLP is **difficult** because human language is complicated, confusing, and ever-changing.
 - We rely on a lot of contextual information as humans
	 - **Implicit references**:
		 - The trees were swaying wildly outside Anne's window as she prepared for bed, and the gutters were overflowing -> **It was a dark and stormy night**
	- **Ambiguous References / Semantics**:
		- "Call me a taxi please." -> **Their name is now a Taxi? Or they need to get a Taxi?**
	- **Imprecise rules**:
		- Work -> **Worked**
		- Teach -> **Taught**
	- **Great variety of languages**
	- **Slang Words**:
		- syfm
		- sybau

## AI NOTES

# Natural Language Processing: Introduction to NLP (Lecture 1)

## Course Information

- **Lecturer**: Dr Amal Htait
- **Email**: a.htait@aston.ac.uk
- **Module**: DG3NLP: Natural Language Processing
- **Institution**: Aston University, Birmingham, UK

### Teaching Team

- **Dr Amal Htait** (Module Leader): a.htait@aston.ac.uk
- **Dr Phil Weber** (Module Tutor): p.weber1@aston.ac.uk
- **Support**: WASS (Web Appointment Scheduling System), discussion forum, lab sessions

---

## Assessment Structure

### Blackboard Quiz 1 (20%)

- **Format**: Closed book, in-person
- **Duration**: 45 minutes - 1 hour
- **When**: Week 5 (during lab time)

### Blackboard Quiz 2 (20%)

- **Format**: Closed book, in-person
- **Duration**: 45 minutes - 1 hour
- **When**: Week 11 (during lab time)

### Coursework (60%)

- **Release**: ~Week 9
- **Submission**: ~Week 12
- **Components**:
    - Functional Python solution to real-world NLP scenario
    - Written project report

---

## Module Schedule

|Week|Topic|
|---|---|
|1|Introduction to NLP|
|2|Data pre-processing and text analytics|
|3|Vector Semantics and Embeddings|
|4|Language Modelling|
|5|AI/ML methods and tools (Quiz 1)|
|6|Text Classification|
|7|Reading Week|
|8|Information Extraction / Topic Modelling / Summarisation|
|9|Speech|
|10|Interactive applications|
|11|NLP and Ethics (Quiz 2)|
|12|Coursework Support|

---

## What is Natural Language Processing?

### Definition

**Natural Language Processing (NLP)** is a field of science and engineering dedicated to the development and study of automatic systems capable of **understanding** and **generating** natural (human) languages.

### Core Relationship

NLP is a subfield of **Artificial Intelligence (AI)** and heavily overlaps with **Machine Learning (ML)**.

### Sub-fields of NLP

1. **Natural Language Understanding (NLU)**
    
    - Focuses on comprehension of human language
    - Example: Understanding "What's the weather like in New York today?" involves:
        - Identifying the query type (weather inquiry)
        - Extracting location (New York)
        - Extracting temporal information (today)
2. **Natural Language Generation (NLG)**
    
    - Focuses on producing human-like text
    - Examples: Text completion, email writing, story generation
    - Tools: InferKit demo (https://app.inferkit.com/demo)

---

## Basic NLP Terminology

|Term|Definition|Example|
|---|---|---|
|**Corpus**|Large collection of texts used for training NLP models (also called Dataset)|Set of news articles|
|**Documents**|Individual pieces of text within a corpus|Each news article|
|**Vocabulary**|Set of unique words in a corpus|"economy", "politics", "innovation"|
|**Words**|Basic units of language|"economy", "politics", "innovation"|
|**Token**|Unit of text that a language model processes|"economy", "!", "123", " ", "😊"|

**Important distinction**: Tokens can include words, punctuation, numbers, spaces, and even emojis.

---

## NLP Applications

### Category 1: Text-Centric Processing

#### 1. Text Classification

Assigning categories or labels to text documents.

**Examples**:

- **News categorization**: Sorting articles into Food, Sports, Politics
- **Sentiment analysis**: Positive/Negative/Neutral
- **Spam detection**: Spam vs. legitimate email
- **Hate speech detection**

**Demo**: MonkeyLearn Sentiment Analysis (https://monkeylearn.com/sentiment-analysis-online/)

#### 2. Information Extraction

Identifying and extracting specific information from text.

**Examples**:

- **Named Entity Recognition (NER)**: Extracting person names, organizations, locations
    - Input: "SpaceX is an aerospace manufacturer headquartered in California. It was founded in 2002 by entrepreneur Elon Musk."
    - Output: PERSON → Elon Musk, ORG → SpaceX, LOCATION → California
- **Keyword Extraction**: Identifying important terms
    - Example: "elon musk", "spacesuit", "second image"

**Demos**:

- NER: https://monkeylearn.com/name-extractor-online/
- Keywords: https://monkeylearn.com/keyword-extractor-online/

#### 3. Text Summarisation

Condensing longer texts into shorter versions while preserving key information.

**Two approaches**:

**a) Extraction-based summarisation**

- Selects existing sentences/phrases from the original text
- Example:
    - Source: "Peter and Elizabeth took a taxi to attend the night party in the city. While in the party, Elizabeth collapsed and was rushed to the hospital."
    - Summary: "Peter and Elizabeth attend party city. Elizabeth rushed hospital."

**b) Abstraction-based summarisation**

- Generates new sentences that capture the meaning
- Example:
    - Source: Same as above
    - Summary: "Elizabeth was hospitalized after attending a party with Peter."

#### 4. Question Answering

Systems that can answer questions based on knowledge or context.

**Examples**:

- Google's AI Overview answering "who is the king of england"
- Answer: "Charles III is the current King of the United Kingdom, which includes England..."

#### 5. Auto-correct / Auto-complete

Predicting and correcting text as users type.

**Examples**:

- Google search suggestions: "Natural L" → "natural language processing"
- Spelling correction: "Natural Lnaguage" → "Did you mean: Natural Language"

---

### Category 2: Interactive & Multimodal Systems

#### 1. Chatbots

Conversational agents that interact with users.

**Historical context**:

- **ELIZA (1966)**: First chatbot, simulated Rogerian psychotherapist using pattern matching
- **Modern chatbots**: Context-aware, AI-powered assistants for customer service, booking, support

**Example applications**:

- Flight booking assistance
- Customer support
- Information retrieval

#### 2. Speech Transcription

Converting spoken language to written text.

**Technology**: Automatic Speech Recognition (ASR) **Demo**: Speechnotes (https://speechnotes.co/dictate/)

#### 3. Optical Character Recognition (OCR)

Extracting text from images.

**Example**:

- Input: Image of a receipt
- Output: Structured text data (shop name, items, prices, total) **Demo**: ImageToText (https://www.imagetotext.info/)

#### 4. Generative AI

Creating new content across multiple modalities.

**Popular tools**:

- **Text**: ChatGPT, Claude, Gemini, GPT-4
- **Code**: GitHub Copilot, AlphaCode
- **Images**: DALL-E 3, Duet AI
- **Mixed**: Scribe, Cohere Generate

#### 5. Voice Assistants

AI systems that respond to voice commands.

**Examples**:

- Siri (Apple)
- Alexa (Amazon)
- Google Assistant

**Capabilities**:

- Home automation
- Information retrieval
- Task management
- Entertainment control

---

## Representing Words in NLP

### The Signifier-Signified Relationship

**Linguistic concept**: A **signifier** is a word/symbol; the **signified** is the actual thing or idea it represents.

#### Example Analysis

**Sentence**: "Luna feeds the cat of her brother."

**Signifiers** (words used):

- "Luna" → refers to a specific person
- "cat" → refers to a specific animal
- "brother" → refers to a specific person

**Signified** (actual meaning):

- Luna (the person) is performing the action of feeding
- A particular cat (not cats in general)
- The cat belongs to her brother (specific relationship)

#### Why This Matters for NLP

**Specificity**:

- "the cat" = one specific cat
- "cats" = cats in general (different meaning)

**Relationships**:

- The sentence encodes relationships: Luna ↔ brother ↔ cat

**Context changes meaning**:

- "Luna feeds cats" → general action, no brother relationship
- "Luna feeds the dog" → different animal entirely

---

### Word-to-Vector Conversion

NLP systems cannot directly process words—they need numerical representations.

**Concept**: Convert words into vectors (arrays of numbers) that capture their meaning and relationships.

#### Example

```
"cat"  = [0, 1, 0, 1, ..., 0, 0]
"dog"  = [0, 1, 0, 1, ..., 0, 1]
"car"  = [1, 0, 1, 0, ..., 1, 0]
```

#### Visualization in Vector Space

```
      ↑
      |    cat
      |   ↗
      |  dog
      | ↗
      |________→
     
     car is distant from cat/dog
```

**Key insight**: Similar words (cat, dog) have similar vectors and appear close together in vector space. Dissimilar words (car) are farther apart.

**Additional context**: This concept forms the foundation of **word embeddings** (covered in Week 3), where semantic relationships are captured mathematically. Modern approaches like Word2Vec and GloVe create dense vector representations that capture nuanced relationships like:

- king - man + woman ≈ queen
- Paris - France + Italy ≈ Rome

---

## Challenges in NLP

### Why is NLP Difficult?

**Core problem**: Human language is complicated, confusing, and ever-changing.

### Major Challenges

#### 1. Implicit References

Humans rely heavily on contextual information that's not explicitly stated.

**Example**:

- **Text**: "The trees were swaying wildly outside Anne's window as she prepared for bed, and the gutters were overflowing."
- **Implicit meaning**: It was a dark and stormy night (never directly stated)

#### 2. Ambiguous References / Semantics

Same words/phrases can have multiple meanings depending on context.

**Example 1**: "Call me a Taxi please."

- Meaning A: Please hail a taxi for me (request for transportation)
- Meaning B: Refer to me as "Taxi" (change my name)

**Example 2** (from real-world AI failure):

- "Siri I'm bleeding really bad can you call me an ambulance"
- Siri: "From now on, I'll call you 'An Ambulance'. OK?"

**Example 3**: News headline ambiguity

- "San Jose cops kill man with knife"
- Meaning A: Cops killed a man who had a knife
- Meaning B: Cops used a knife to kill a man

#### 3. Imprecise Rules

Languages don't always follow consistent patterns.

**Example**: English past tense

- work → worked (regular pattern: add -ed)
- teach → taught (irregular pattern: vowel change)
- go → went (completely irregular)

**Challenge**: No single rule works for all cases—systems must learn exceptions.

#### 4. Great Variety of Languages

Over 7,000 languages worldwide with vastly different structures.

**Examples**:

- **English**: "Hi" (Latin script, left-to-right)
- **Spanish**: "Hola" (Latin script with diacritics)
- **Hindi**: "नमस्ते" (Devanagari script)
- **Arabic**: "مرحبا" (Arabic script, right-to-left)

**Challenge**: Different writing systems, grammatical structures, and semantic patterns require language-specific models.

#### 5. Slang and Informal Language

Non-standard expressions that change rapidly.

**Examples**:

- BFF → Best Friends Forever
- "OMG, this stand-up is hilarious! I'm dying."
    - "dying" doesn't mean literal death (hyperbolic expression)

**Challenge**: Slang evolves quickly, varies by region/community, and often requires cultural context.

---

## Critical Evaluation of Lecture Content

### Strengths

1. **Comprehensive overview**: Covers breadth of NLP applications effectively
2. **Practical examples**: Includes live demos and real-world use cases
3. **Progressive structure**: Builds from basics to challenges logically

### Areas for Deeper Consideration

#### 1. **NLP vs ML Relationship Oversimplified**

The lecture presents NLP and ML as overlapping circles within AI. However, the relationship is more nuanced:

- NLP is a **domain/application area** (what we're trying to solve)
- ML is a **methodology** (how we solve it)
- Modern NLP is almost entirely ML-based, but traditional NLP used rule-based approaches

#### 2. **Ambiguity Example Limitations**

The "Call me a Taxi" example is clever but somewhat contrived. More common ambiguities include:

- **Prepositional phrase attachment**: "I saw the man with the telescope" (Who has the telescope?)
- **Pronominal reference**: "The dog chased the cat and it ran away" (Which ran—dog or cat?)

#### 3. **Word Vector Explanation**

The vector representation section is simplified. Important missing context:

- Vectors shown are **binary** (0s and 1s), but modern embeddings use **dense, continuous values**
- The example doesn't explain **dimensionality** (typical: 50-300 dimensions)
- Doesn't mention how these vectors are learned (e.g., through neural networks)

#### 4. **Missing: Evaluation Metrics**

The lecture doesn't address how we measure NLP system performance:

- Accuracy, Precision, Recall, F1-score
- Human evaluation methods
- Benchmarks (GLUE, SuperGLUE)

#### 5. **Ethical Considerations Deferred**

While "NLP and Ethics" is scheduled for Week 11, introducing ethical concerns earlier would be valuable:

- Bias in training data
- Privacy concerns (data collection)
- Misinformation generation capabilities
- Environmental cost of training large models

---

## Additional Context: Current State of NLP (2025)

### Recent Developments Not Covered in Lecture

#### 1. **Large Language Models (LLMs)**

- GPT-4, Claude 4, Gemini represent massive shifts in NLP capabilities
- These models blur the line between NLU and NLG
- They've made many traditional NLP techniques obsolete while creating new challenges

#### 2. **Multimodal Models**

- Modern systems combine text, images, audio, and video
- Examples: GPT-4V (vision), Whisper (speech), DALL-E 3 (text-to-image)

#### 3. **Few-Shot and Zero-Shot Learning**

- Modern models can perform tasks with minimal or no training examples
- This challenges the traditional supervised learning paradigm

#### 4. **Prompt Engineering**

- A new skill: crafting inputs to get desired outputs from LLMs
- Becoming as important as model training itself

---

## Recommended Reading

**Primary Text**:

- **Eisenstein, Jacob**. _Introduction to natural language processing_. MIT Press, 2019.
    - Introduction (foundational concepts)
    - Chapter 4 (word representation basics)

**Additional Resources** (supplementary):

- **Jurafsky & Martin**. _Speech and Language Processing_ (3rd ed. draft) - Free online
    
    - More comprehensive than Eisenstein
    - Chapter 2 (Regular Expressions, Text Normalization)
    - Chapter 6 (Vector Semantics and Embeddings)
- **Bird, Klein, & Loper**. _Natural Language Processing with Python_ (NLTK Book)
    
    - Excellent for practical implementation
    - Free online: https://www.nltk.org/book/

---

## Key Takeaways

1. **NLP is interdisciplinary**: Combines linguistics, computer science, and cognitive science
    
2. **Two main branches**: Understanding (NLU) and Generation (NLG)—modern systems increasingly do both
    
3. **Applications are everywhere**: From autocorrect to chatbots to search engines
    
4. **Core challenge**: Language is ambiguous, context-dependent, and constantly evolving
    
5. **Mathematical representation is essential**: Words must be converted to numbers (vectors) for computational processing
    
6. **No perfect solution exists**: Every NLP approach involves tradeoffs between accuracy, speed, and generalizability
    
7. **Rapid field evolution**: Techniques from 5 years ago may already be outdated
    

---

## Preparation for Next Lecture

**Week 2 Topic**: Data pre-processing and text analytics

**Expect to learn**:

- Text cleaning techniques
- Tokenization methods
- Stop-word removal
- Stemming vs. Lemmatisation
- Data labelling and balancing

**Suggested preparation**:

- Review basic Python string operations
- Familiarize yourself with the concept of "tokens"
- Think about: What makes text "clean" vs "dirty"?