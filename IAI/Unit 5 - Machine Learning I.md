## What is Machine Learning?
- A field enabling computers to learn from data without explicit programming [Arthur Samuel, 1959]
- A computer program is said to learn from experience for a task and performance measure if performance improves with experience [Tom Mitchell, 1998]
### Key Idea:
- Automates learning patterns from data instead of hand-coded logic

## Machine learning vs Traditional Programming
### Traditional Programming:
- Rules are manually defined by programmers 
- Less flexible, ideal for static, well-structured data
- E.g. Arithmetic operations, spelling correction
### Machine Learning:
- Learns rules and patterns from data
- Adapts to dynamic, unstructured data
- E.g. Grammar checking, speech recognition, image analysis
## Difference Between Machine Learning and Deep Learning
### Machine Learning:
- Uses various algorithms to identify patterns in data
- Requires future engineering (manual feature extraction)
### Deep Learning:
- A subset of ML that uses multi-layered neural networks
- Excels in tasks like object detection and natural language processing
## Applications of Machine Learning
- Predictive text
- Self-driving cars
- Speech and gesture recognition
- Fraud detection in finance
- Face and fingerprint recognition
- Spam email filtering
- Bioinformatics and medical diagnosis
## Forms of Learning
### 1. Supervised Learning
- Uses labelled datasets to learn a mapping function
- Goal: Predict output for new input
- Example: Spam email classification
### 2. Unsupervised Learning
- Analyses data without labelled outputs
- Goal: Understand the underlying structure or distribution 
- Example: Clustering users in social networks
### 3. Reinforcement Learning
- Learns optimal actions by interacting with an environment and receiving rewards/punishments
- Example: Game AI improving its strategy over time
## Supervised Learning: Key Concepts
### Classification:
- Predicts categorical labels (e.g. spam vs non-spam)
- Workflow:
	1. Define a labelled dataset: Pairs of inputs() and outputs()
	2. Learn a predictive model to map to
	3. Evaluate the model using unseen test data
### Regression:
- Predicts continuous values (e.g. house prices)
### Example: Spam Email Detection
- Features:
	- Number of special characters (e.g. $, %)
	- Presence of words like "Award" or "Free"
	- Generic greetings, misspellings, or excessive punctuation
- Workflow:
	1. Extract features from emails
	2. Train a model to distinguish spam (1) and non-spam (0)
	3. Test and validate the model's predictions on new emails
## Machine Learning Workflow
### 1. Define the Problem:
- Identify an interesting, unsolved problem
- Choose a problem requiring pattern recognition or classification
### 2. Construct the Dataset:
- Collect reliable, labelled data
- Include relevant features; exclude irrelevant ones
### 3. Prepare and Pre-Process the Data
- Clean the data (remove duplicates, fill missing values)
- Select features using intuition or statistical methods
### 4. Choose and Train a Model:
- Experiment with models like Decision Trees, SVMs, or Neural Networks
- Optimise for accuracy and generalisability
### 5. Test and Validate the Model:
- Split the data into training (66%) and testing (33%) sets
- Evaluate performance using metrics like classification accuracy
### 6. Use the Model for Predictions:
- Apply to new, unseen data
## Inductive Learning and Overfitting
### Inductive Learning:
- Learns a hypothesis from examples to approximate a target function
- E.g. Curve fitting to match data points
### Overfitting:
- Model fits training data too closely but performs poorly on new data
- Solution: Use simpler models or regularisation techniques
## Evaluation of ML Models
### Classification Accuracy:
- Ratio of correct predictions to total predictions
### Confusion Matrix:
- Summarises prediction results:
	- True Positives (TP): Correctly predicted events
	- False Positives (FP): Incorrectly predicted events
	- True Negatives (TN): Correctly predicted non-events
	- False Negatives (FN): Incorrectly predicted non-events