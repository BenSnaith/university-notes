 - Text Representation
	 - Classic methods
	 - Word Embeddings
	 - Contextualised Word
	 - Sentence Embeddings

## Text Representation

Text representations can be broadly classified into two section:

 - **Discrete text representations**: Encoding words or phrases as distinct, separate symbols or tokens, often using methods like one-hot encoding, where each word is represented as a unique identifier without capturing relationships or meaning directly
 - **Distributed/Continuous text representation**: Encoding words or phrases as vectors in a high-dimensional space, where the meaning and relationships between then are captured through their positions and distances in that space.

## Discrete Text Representations

We have three words, `"cat"`, `"dog"`, and `"apple"`.

In a discrete text representation system, they might be represented like this:

 - `"cat"` = `[1, 0, 0]`
 - `"dog"` = `[0, 1, 0]`
 - `"apple"` = `[0, 0, 1]`

## Distributed/Continuous Text Representations

Using the same words: `"cat"`, `"dog"`, and `"bird"`

In a distributed system, them might look like this:

 - `"cat"` = `[0.4, 0.8, 0.2]`
 - `"dog"` = `[0.5, 0.7, 0.1]`
 - `"bird"` = `[0.3, 0.1, 0.9]`

The numbers represent features (e.g. "is a pet", "has fur", "can fly")

## Discrete Text Representations

 - One-hot encoding
 - Bag-of-words representation (BoW)
	 - Basic BoW: CountVectoriser
	 - Advanced BoW: TF-IDF

## One-Hot Encoding

**One-Hot encoding**: Assigning 0 to all elements in a vector except for one, which has a value of 1. This value represented a category of an element.

Example: "He loves coffee." / "She loves tea."

Each word is assigned a unique number (index):

`vocabulary = {"he": 1, "loves": 2, "coffee": 3, "she": 4, "tea": 5}`

![[Pasted image 20251008092108.png]]

 - **Advantages of One-Hot encoding**:
	 - Simple to understand and implement
 - **Disadvantages of One-Hot encoding**:
	 - Cannot capture relationships or similarities between words.
	 - Does not effect the importance of a word in a sentence.
	 - Uses lots of memory and processing power due to large matrices.

## Bag-of-words Representation (BoW)

**Bag-of-words Representation**: Representing text (full sentence) by couting how many times each word appears in a document or sentence It ignores the order of words and focuses only on the frequency of words:

![[Pasted image 20251008092408.png]]

![[Pasted image 20251008092422.png]]

## Advanced BoW Representation

**TF-IDF (Term Frequency-Inverse Document Frequency)**: It not only counts word frequency (like basic BoW, e.g., CountVectoriser) but also adjusts the importance of words based on how common or rare they are across all documents

![[Pasted image 20251008092557.png]]

![[Pasted image 20251008092617.png]]

 - **Advantages of TF-IDF Representation**:
	 - Simple.
	 - Improves on CountVectoriser: It reduces the impact of very common words -> helps to reduce noise.
 - **Disadvantages of TF-IDF Representation**:
	 - No word count.
	 - Corpus-dependent
	 - Cannot capture relationships or similarities between words

![[Pasted image 20251008092832.png]]

## Distributed/Continuous Text Representations

 - Co-occurrence matrix.
 - Static Word Embeddings.
 - Contextualised Word Embeddings
	 - Embeddings from Language Models
	 - Transformer-Based Models
 - Sentence / Paragraph Embeddings in Transformer-Based Models

## Co-occurrence Matrix

A **co-occurrence matrix** counts how often words appear together (near each other) in a text. This matrix helps us see which words are often used together, showing their relationships in the text.

![[Pasted image 20251008093232.png]]

![[Pasted image 20251008093253.png]]

 - `"phone"` co-occurs frequently with `"the"`, `"is"`, and `"amazing"`, showing is is described positively.
 - `"phone"` also co-occurs with `"better"`, and `"than"`, indicating a comparison is being made.
 - `"tablet"` co-occurs with `"the"`, `"than"`, and `"beats"`, showing is it part of a comparison and an action (beating the phone).

 - **Advantages**:
	 - Simple.
	 - Captures word order.
	 - Global context (Uses entire corpus for broader relationships)
 - **Disadvantages**
	 - Uses lots of memory and processing power due to large matrices.
	 - Cannot capture relationships or similarities between words.

## Distributed/Continuous Text Representations

 - **Language Models**
	 - Co-Occurrence Matrix
	 - Static Word Embeddings
	 - Contextualised Word Embeddings
		 - Embeddings from Language Models
		 - Transformer-Based Models
	 - Sentence/Paragraph Embeddings

## Note: Language Models

 - A **language model** is a system trained on large datasets (text), it learns the relationship between words, phrases, and sentences enabling it to represent the human language in vectors.

## Word Embeddings

**Word Embeddings** are vector representations of a word. Each word is represented by a fixed vector size while capturing its semantic and syntactic relation with other words.

![[Pasted image 20251008094248.png]]

## Statistical Word Embeddings

A variety of word-to-vector techniques has been explored like **Word2Vec**, **GloVe**, **Fasttext**, etc.

**Word2Vec** is a famous algorithm for representing word embeddings. It's a prediction-based method for representing words rathen than count based techniques like co-occurence matrix.

![[Pasted image 20251008094439.png]]

## Word2Vec: CBOW and Skip-gram

![[Pasted image 20251008094507.png]]

![[Pasted image 20251008094525.png]]

## Word2Vec

![[Pasted image 20251008094539.png]]

![[Pasted image 20251008094607.png]]

## Word2Vec: Limitations

 - **Out-of-Vocabulary (OOV) Words**
 - **Local Context Dependency**: It only uses nearby words to learn word meanings, which can limit its accuracy.
 - **Language-Specific Training**: You can't reuse parameters for new languages
 - **Large corpus needed**: It requires a bif dataset to work well, especially with the Skip-Gram model.
 - **Polysemy and Homonymy**: are not handled properly, since their meanings are condensed together in the same vector.

## Word2Vec: Example

![[Pasted image 20251008094852.png]]

## GloVe

**Global Vectors** (GloVe) is considered a **hybrid technique** for continous word representation combining the count-based technique (co-occurence matrix) & prediction-based technique (Word2Vec).

Slightly better for capturing semantic relationships

**Limitations**

 - **Memory cost** is more in GloVe compared to Word2Vec
 - **Polysemy and Homonymy** are not handled properly (same as Word2Vec)

## Contextualised Word Embeddings

 - **Certain language models** helped going from static word embeddings (like Word2Vec) to contextualised word representations, for the purpose of capturing the meaning of a word based on its specific context in a sentence.

## Convolution Neural Network (CNN)

![[Pasted image 20251008095258.png]]

## ELMo

**ELMo** (Embeddings from Language Models) was developed in 2018 and it ==goes beyond traditional embedding techniques==

**ELMo** is a contextualised word embeddings learned from the internal states of a deep bidirectional language model.

**ELMo** uses character-level CNNs (Convolutional Neural Networks) to convert words into raw word vectors (word embedding) which are then fed into bi-directional LSTMs (Long Short-Term Memory) to train.

![[Pasted image 20251008095751.png]]

## ELMo: Limitations

 - **ELMo** uses character-level CNNs (Convolution Neural Networks) to convert words into raw word vectors. it's been claimed that characted level language models such as **ELMo** perform as well as word-based ones.
 - **ELM0** uses bidirectional LSTM, which captures context only within one sentence. It cannot model long-range dependencies across sentences.

## BERT

 - **BERT** (Bidirectional Encoder Representations from Transformers), developed by Google AI, gives an even deeper sense of language context and flow than previous techniques.
 - **BERT** understands complex sentences slightly more precise then the previous method.
 - **BERT's** key technical innovation is applying many layers of **bidirectional** training of **Transformer encoder**, with a technique named **Masked Language Model** (MLM).

## BERT: Transformers

 - **Transformers** were introduced in 2017, used primarily in the field of NLP.
 - Transformers are designed to handle ordered sequences of data.
 - The transformers use a mechanism called attention and consists of two main components: a set of **encoders** and a set of **decoders**

## BERT vs ELMo

![[Pasted image 20251008100339.png]]

## BERT for Word Embedding: Example

![[Pasted image 20251008100410.png]]

## BERT: Possible Applications

 - For classification: fake news classification, aspect based sentiment analysis.
 - To better understand the intent behind search queries
 - For question answering on SQuAD and NQ datasets.
 - Used in specific domains, but a domain-specifc pre-trained models are needed, for example: SciBERT and BioBERT

## BERT: Limitations (for text representation)

 - Computationally Expensive: BERT requires a lot of computational power and memory, making it slow and costly to train or run, especially on large datasets.
 - Not ideal for Real-Time Applications: Due to its size and complexity, BERT is less efficient for real-time tasks like chatbots or live translations.
 - Struggles with Long Texts: BERT has a fixed input length (usually 512 tokens), so it struggles with very long documents or conversations.

## Sentence/Paragraph Embeddings

- Averaging Word Embeddings
- Language Models:
	- Doc2Vec
	- Pre-trained models: SentenceBERT

## Doc2Vec

![[Pasted image 20251008102136.png]]

## SentenceBERT

 - SentenceBERT was introduces in 2018, based on BERT, it is able to derive semantically meaningful sentence embeddings
 - SBERT can be fine-tuned on specific tasks like Natural Language Inference (NIL) (e.g., SNLI, MultiNLI) or semantic similarity datasets.

![[Pasted image 20251008102311.png]]