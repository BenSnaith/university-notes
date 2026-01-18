### Information Extraction

**Information Extraction** is the process of parsing through unstructured data and extracting essential information into more editable and structured data formats.

![[Pasted image 20251202162157.png]]

![[Pasted image 20251202162214.png]]

![[Pasted image 20251202162230.png]]

### Dependency Parsing

**Dependency Parsing** analyses the grammatical structure of a sentence by identifying relationships between words.

*The cat sat on the map*

 - **sat** -> root (main verb)
 - **cat** -> subject (nsubj) of sat
 - **the** -> determiner (det) modifying cat
 - **on**  -> preposition (prep) modifying sat
 - **mat** -> object of the preposition (pobj)
 - **the** -> determiner (det) modifying mat

![[Pasted image 20251202163045.png]]

### Relation Extraction

**Relation Extraction** (RE) is a task that identifies and classifies semantic relationships between entities within text.

![[Pasted image 20251202163159.png]]

### Knowledge Base

**Knowledge Base** is a centralised library of organised information.

![[Pasted image 20251202163237.png]]

![[Pasted image 20251202163256.png]]

### Information Extraction - Evaluate

![[Pasted image 20251202163404.png]]

### Topic Modelling

**Topic Modelling** is used to identify and extract hidden topics and themes from a large collection of text documents. It is usually done through **unsupervised machine learning technique**.

![[Pasted image 20251202163502.png]]

### Document-Term Matrix

A **Document-Term Matrix** (frequency table of words) is a mathematical matrix that describes the frequency of terms that occur in a collection of documents.

![[Pasted image 20251202163600.png]]

### Unsupervised Machine Learning

![[Pasted image 20251202163632.png]]

- Using **Language Models** for Topic Modelling can improve the task by applying context-aware topic modelling.

![[Pasted image 20251202163715.png]]

### Topic Modelling - Evaluate

**Coherence Metrics** measure how well words in a topic make sense together.

 - Topic 1: ["dog", "puppy", "cat", "pet", "animal"]
 - Topic 2: ["cheese", "planet", "banana", "car", "desk]

Coherence scores:

 - Topic 1 -> 0.65 (good coherence)
 - Topic 2 -> 0.05 (bad coherence)

### Summarisation 

**Text Summarisation** is a technique for generating a summary of long texts, without losing the overall meaning.

 - *Extraction-based summarisation*

![[Pasted image 20251202164031.png]]

 - *Abstraction-based summarisation*

![[Pasted image 20251202164041.png]]

### Extraction-based summarisation

![[Pasted image 20251202164108.png]]

### Abstraction-based summarisation

![[Pasted image 20251202164137.png]]

### Summarisation - Evaluate

![[Pasted image 20251202164708.png]]