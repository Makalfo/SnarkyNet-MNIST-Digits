# SnarkyNet - MNIST Handwritten Digits
SnarkyJS implementation the Deep Neural Network for MNIST Handwritten Letters. <br>
Proof of Concept / Work in Progress

## Description
SnarkyJS implementation of a Deep Neural Network for the MNIST Handwritten Digits Dataset. 
The training and prediction from the Neural Network are separated as follows:
 - Training of the model performed in Tensorflow
 - Subsequent weights are integrated into a SNAPP for prediction
The weights obtained during the training and validation via Tensorflow can be utilized in the
SnarkyJS Neural Network's circuit to create a proof of the prediction utilized in the SNAPP.

### Implementation Decisions
Training of the model is performed in Tensorflow to maintain the efficiencies including GPU 
support, methods for evaluating performance, and optimization. The weights obtained from 
training the model in Tensorflow are utilized in a SnarkyJS implementation of an equivalent 
model as the circuits are not required for training but are necessary for the prediction of 
the model. Thus, the weights from the training can be ported over directly into the circuit 
for the calculations. 

### Model Implementation
The Neural Network consists of two layers:
- Dense layer of 512 nodes with the RelU Activation Function
- Dense layer of 10 nodes with a (pseudo) Softmax Activation Function

## Flow
 1. Create Tensorflow model of the proposed model type to obtain the weights of the model.
    The weights are stored in `./src/weights.js` and imported into the SNAPP
 3. Create SnarkyJS equivalent model (`SnarkyNet`) with the weights for each layer (`SnarkyLayer`)
 4. Create a smart contract extension utilizing the SnarkyJS model (`SmartSnarkyNet`)
 5. Run verification tests

## Notes
Currently, the RelU and Leaky RelU are the two activation functions that are utilized in 
the model until there is a method for expotential as that will allow for a sigmoid and a proper
softmax function. There is a pseudo softmax function to calculate relative probabilities
for the classifications but it is lacking the exp implementation. 
