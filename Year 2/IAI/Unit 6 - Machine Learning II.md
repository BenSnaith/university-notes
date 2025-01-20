## Data Cleaning and Feature Selection
### Data Cleaning:
- Handle missing data (e.g. NaN, NULL values)
- Direct and treat outliers
- Normalise or scale features
- Encode categorical variables (e.g. one-hot encoding)
### Feature Selection
- Reduce irrelevant or redundant data to enhance model accuracy
- E.g. Focus on significant predictors like word frequency in spam detection

## Decision Tree (DT) Approach
### Definition:
- A supervised ML algorithm using rules to classify data based on attribute values 
- Composed of nodes (decision points), branches (attribute values), and leaves (classifications)
### How It Works:
1. Identify the best attribute to split data
2. Create nodes and branches for attribute value
3. Repeat until a leaf node (classification) is reached
### Algorithm
1. Pick the best attribute (e.g. based on information gain or Gini impurity)
2. Ask a relevant question
3. Follow the answer path
4. Iterate until classification
### Example:
- Goal: Predict if a player will play tennis
- Attributes: Outlook, Humidity, Wind
- Root node: Outlook (Sunny, Overcast, Rain)
### Advantages: 
- Simple and Interpretable
- Handles nominal and numerical data
## K-Nearest Neighbour (k-NN) Approach
### Definition:
- A supervised ML Algorithm that classifies data based on the labels of the nearest neighbour
### How It Works
1. Store all training data
2. For a new test instance, find the closest training instances (e.g. using Euclidean distance)
3. Assign the majority label among these neighbours
### Key Points:
- Assign label of the closest neighbour
- Larger: Ensures more robust predictions but increases computation
- Distance metrics: Euclidean, Manhattan, etc.
### Example:
- Task: Classify a test point based on its neighbours in a 2D space
## Unsupervised Learning
### Definition:
- ML technique to discover patterns or structure in unlabelled data
### Key Concepts:
- Clustering: Group similar objects together to maximise intra-cluster similarity and minimise inter-cluster similarity 
- E.g. Grouping documents based on term frequencies
### Applications:
- Document clustering 
- Customer segmentation in marketing 
### Difference from Supervised Learning
- No labelled outputs in training data
- Focuses on discovering structures rather than predictive mapping
## Example Models Overview 
### 1. Decision Trees:
- Rule-based classification
- Easily interpretable
### 2. K-Nearest Neighbour (k-NN):
- Classifies based on similarity
- Suitable for smaller datasets
### 3. Other Models:
- Support Vector Machines (SVMs)
- Neural Networks (ANNs)
- Hidden Markov Models (HMMs)
- Bayesian Networks (BNs)
## Clustering Example: Document Clustering
### Goal: Group similar documents based on important terms
### Approach:
- Extract term frequencies from documents
- Compute similarity measures
- Cluster using algorithms like -means
### Why Clustering?
- Reduces data complexity
- Uncovers hidden insights
