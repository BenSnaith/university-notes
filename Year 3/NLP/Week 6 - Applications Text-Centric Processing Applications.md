## NLP Applications

 - Text-Centric Processing Applications.
 - Interactive and Multi-modal Systems Applications.

## Text-Centric Processing: Text Classification

 - Things we want to do/prevent
	 - Categorisation
	 - Hate-speech
	 - Spam

## Text Classification

 - Data pre-processing

![[Pasted image 20251029092214.png]]

![[Pasted image 20251029092236.png]]

![[Pasted image 20251029092341.png]]

## Feature Extraction

 - **Feature Extraction** is the process of converting raw text data into numerical or structured features that machine learning models can understand and process.

![[Pasted image 20251029092547.png]]

## Feature Engineering - Example

 - Classify a sentence as: Citation or Not Citation

	 1. "According to Smith (2020), machine learning has transformed AI" -> **Citation**.
	 2. "Machine learning models are widely used in many applications" -> **Not a citation**.
	 3. "As discussed in [5], deep learning shows better results"   -> **Citation**.
	 4. "This paper explores various approaches to natural language processing" -> **Not a citation**.

 - What can you notice as a Citation characteristic

	 - Contains parentheses.
	 - Contains square brackets.
	 - Mentions "according to" or "discussed in".

![[Pasted image 20251029093011.png]]

 - *Sentence 1* -> concatenate [bi-gram] and [1, 0, 1] -> [# # # #]
 - *Or* -> concatenate [TF-IDF] and [1, 0, 1] -> [# # # #]

## Classification types

 - **Binary classification**: Two classes
 - **Multi-class classification**: More than two classes
 - **Multi-label classification**: Allows to have multiple labels simultaneously.
 - **Regression**: Predicts a continuous numerical value.

## Binary Classification

**Binary Classification** is a type of supervised machine learning where the goal is to categorise data into one of two possible classes (e.g., Yes/No, True/False, Spam/Not Spam).

![[Pasted image 20251029093432.png]]

## Multi-class Classification

 - **Multi-class Classification** is a type of supervised machine learning problem where the goal is to classify input data in to more than two classes (categories)

![[Pasted image 20251029093733.png]]

## Multi-label Classification

![[Pasted image 20251029093807.png]]

## Regression

 - **Regression** is used to predict a continuous numeric value based on input data.

## Sentiment Analysis

 - **Sentiment Analysis** (opinion mining) is a technique in NLP that identifies **subjective** information from text to determine the **emotional tone** or **attitude** behind words.
 - **Types**: Polarity Detection, Emotion Detection, Aspect-Based.
 - **Applications**: Customer Feedback Analysis, Stock Market Prediction, Chatbots, etc.

![[Pasted image 20251029094041.png]]

## Sentiment Analysis

1. Data collection
2. Data cleaning
3. Data annotation / labelling
4. Data examining
5. Tokenisation
6. Feature extraction / Vectorisation
7. Machine learning algorithm
8. Model evaluation

## Data Collection

![[Pasted image 20251029094420.png]]

## Data Cleaning

 - Anonymity.
 - Remove personal data.
 - Remove "noisy" data.
 - Lower case.

## Data Annotation

 - Manual
 - Automated
 - Hybrid

## Data Examining

![[Pasted image 20251029094606.png]]

## Tokenisation

 - NLTK
 - SpaCy
 - TextBlob
 - Gensim
 - BERT

## Feature Extraction

![[Pasted image 20251029094807.png]]

## Machine Learning Algorithm

![[Pasted image 20251029094858.png]]

## Sentiment Analysis

![[Pasted image 20251029094927.png]]

## Model Evaluation / Results

 - True +ve
 - False +ve
 - True -ve
 - False -ve

 - **Confusion Matrix**: A table that visualises the performance of a classification model by showing the counts of true positives, true negatives, false positives, and false negatives.

![[Pasted image 20251029095405.png]]

![[Pasted image 20251029095429.png]]

 - **Accuracy**: (TP + TN) / Total
 - **Precision**: TP / (TP + FP)
 - **Recall**: TP / (TP + FN)
 - **F1-Score**: 2 * (Precision * Recall) / (Precision + Recall)
 - **ROC/AUC**: (Receiver Operating Characteristic Area Under the Curve), Useful for evaluating models with imbalanced datasets, measuring the trade-off between true positive rate and false positive rate.

