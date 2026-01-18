### NLP Applications

 - Text-Centric Processing Applications
 - Interactive and Multi-modal Systems Applications

### Text-Centric Processing: Text Classification

 - Categorisation
 - Hate Speech 
 - Spam

### Text Classification

![[Pasted image 20251202155403.png]]

![[Pasted image 20251202155457.png]]

![[Pasted image 20251202155512.png]]

### Feature Extraction

 - **Feature Extraction** is the process of converting raw text data into numerical or structured features that machine learning models can understand and process.

![[Pasted image 20251202155605.png]]

### Feature Engineering - Example

 - Classify a sentence as: Citation or Not Citation:

 1. "According to Smith (2020), machine learning has transformed AI" -> *Citation*
 2. "Machine learning models are widely used in many applications" -> **Not a Citation
 3. "As discussed in [5], deep learning shows better results" -> *Citation*
 4. "This paper explores various approaches to natural language processing" -> *Not a citation*

 - What can you notice about a Citation characteristic?
	 - Contains parentheses.
	 - Contains square-brackets.
	 - Mentions "according to" or "discussed in".

![[Pasted image 20251202155900.png]]

### Classification Types

 - **Binary Classification**: Two classes.
 - **Multiclass classification**: More than two classes.
 - **Multi-label classification**: Allows to have multiple labels simultaneously.
 - **Regression**: Predicts a continuous numerical value.

### Binary Classification

**Binary classification** is a type of supervised machine learning where the goal is to categorise data into one of two possible classes (e.g., Yes/No, True/False, Spam/Not Spam).

### Multi-class classification

**Multi-class classification** is a type of supervised machine learning problem where the goal is to classify input data into more than two classes (categories).

![[Pasted image 20251202160223.png]]

### Multi-label classification

**Multi-label classification** is where each input can be assigned multiple labels at the same time.

![[Pasted image 20251202160322.png]]

### Regression

 - **Regression** is used to predict a continuous numeric values based on input data.

![[Pasted image 20251202160400.png]]

### Sentiment Analysis

 - Sentiment Analysis (opinion mining) is a technique in NLP that identifies **subjective** information from text to determine the **emotional tone** or **attitude** behind words.
 - **Types**: Polarity Detection, Emotion Detection, Aspect-Based.
 - **Applications**: Customer Feedback Analysis, Stock Market Prediction, Chatbots, etc.

![[Pasted image 20251202160558.png]]

1. Data collection.
2. Data cleaning.
3. Data annotation / labelling.
4. Data examining.
5. Tokenisation.
6. Feature Extraction / Vectorisation.
7. Machine Learning Algorithm.
8. Model evaluation.

##### 1. Data Collection

![[Pasted image 20251202160743.png]]

##### 2. Data Cleaning

![[Pasted image 20251202160807.png]]

##### 3. Data Annotation

![[Pasted image 20251202160830.png]]

##### 4. Data Examining

![[Pasted image 20251202160846.png]]

##### 5. Tokenisation

![[Pasted image 20251202160902.png]]

##### 6. Feature Extraction / Vectorisation

![[Pasted image 20251202160927.png]]

##### 7. Machine Learning Algorithm

![[Pasted image 20251202160956.png]]

##### 8. Model Evaluation / Results

 - True Positive
 - False Positive
 - True Negative
 - False Negative

![[Pasted image 20251202161132.png]]

 - Accuracy: (TP + TN) / Total
 - Precision: TP / (TP + FP)
 - Recall: TP / (TP + FN)
 - F1-Score: 2 * (Precision * Recall) / (Precision + Recall)
 - ROC/AUC (Receiver Operating Characteristic / Area Under the Curve): Useful for evaluating models with imbalanced datasets, measuring the trade-off between true positive rate and false positive rate.

