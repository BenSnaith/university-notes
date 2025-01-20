## Multi-Layered Perceptrons (MLPs)
### Limitations of Single-Layer Perceptrons:
- Restricted to linear classification
- Cannot solve non-linear problems like XOR.
### Multi-Layer Perceptrons
- Address the limitations of single-layer perceptrons by introducing hidden layers
#### Layers include:
- **Input Layer**: Takes raw data (features)
- **Hidden Layers**: Perform non-linear transformations.
- **Output Layer**: Produces final predictions
### Notations:
$𝑎^𝑖_𝑙$ : output of the node $i$ in layer $l$
$w^l_ij$ : weight for connection from node $i$ in layer $l$ to node $j$ in layer $l+1$
### Applications: 
- Recognising hand-written digits, language-translation, image classification
## Shallow vs Deep Neural Networks
### 1. Shallow Neural Networks:
- Contain a single hidden layer
- Suitable for simpler problems
### 2. Deep Neural Networks (DNNs):
- Contain multiple hidden layers
- Capable of extracting complex patterns and hierarchies
### Key advantage of DNNs:
- Perform automatic feature extraction, reducing the need for manual feature engineering
### Training DNNs:
- Process known as Deep Learning involves optimising weights across multiple layers
## Training Multi-Layer Neural Networks
### 1. Initialisation:
- Assign random values to weights and biases
- Ensure they are small to avoid saturation of activation functions during training
### 2. Forward Propagation:
- Input Layer: 
	- Pass the feature vector to the network
- Hidden Layers:
	- Compute the weighted sum of inputs for each neuron
	- Apply the activation function
- Output Layer: 
	- Repeat the above for the output later to compute the final predictions
### 3. Compute Error:
- Use a loss function to measure the difference between the predicted outputs and target values.
    - **Common Loss Functions:**
        - Mean Squared Error (MSE):
        - Cross-Entropy Loss (for classification):
#### Loss Function Components:
- Error Term: Measures fit to the data
- Regularisation Term: Penalises overfitting
### 4. Backward Propagation (Backprop)
- **Output Layer:**
    - Compute the error gradient with respect to output activations
- **Hidden Layers:**
    - Propagate the error backward:
        - Distributes the blame for errors to the connected neurons.
### Gradient Descent Algorithm:
- Optimises weights to minimise loss function
- Update rule: $w(i+1)=w(i)−g(i)η(i)$
	- EVERY BRACKETS IN THIS IS TO THE POWER OF BUT YOU CANT DO MULTIPLE CHARS ON HIGHER LEVEL ON OBSIDION so like $w^i$
- Gradient: $𝑔^𝑖 = ∇𝑓(𝜔^i)$
- Training rate: $𝜂^𝑖$
### Variants of Gradient Descent
- Stochastic Gradient Descent (SGD): Updates weights after each training sample
- Adam Optimiser: Adaptive learning rates for faster convergence
## Neural Network Types
### 1. Feedforward Neural Networks (FNNs):
- Data flows in one direction (input to output)
- E.g. MLPs
### 2. Recurrent Neural Networks (RNNs):
- Retain short-term memory through loops
- E.g. text prediction
### 3. Convolutional Neural Networks (CNNs)
- Specialised for image data
- Extract spatial hierarchies (e.g. edges, shapes)
### 4. Generative Adversarial Networks
- Generate new data by opposing generator and discriminator networks

