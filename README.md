# NeuroEvolve
This is an API which allows you to create, modify, customize and run your own neural network. It can act as a building block for a NEAT algorithm.

### Usage

`from NeuroEvolve import *`

##### Creating a neural network.

` neuralnet = NeuroES(Number_of_inputs , Number_of_outputs , Output_activation_function)`

NeuroES is a class with which you can interface with your neural network, initially it takes and creates the input and output layer only with Output activation function. For now 'SoftMax' is the only output activation function supported.(Add any other if you want).

##### Adding Layers

` neuralnet.add_layer(Number_of_nodes, Layer_activation_function) `

To add a layer use the above function with number of nodes in the layer and the activation function to be used for each node in the layer, for now Sigmoid and Relu are the supported activation functions. Bias is also added for each node in layer.

##### Completing network

` neuralnet.completed_network()`

This function has to be called to tell the object that the neural network is complete, only then can the neural network be drawn or operated upon or its weights can be set. Once completed the neural network cannot be modified again, this is a lock on the neural network.

##### Edit Mode

` neuralnet.edit_mode() `

This allows us to edit the neural network later on to add new layers , nodes. This basically reverses what completed_network() does and unlocks the neural network.

##### Edit Function

Here are a few neural network edit functions which are self-explanatory.
Layer numbers start from zero and exclude input and output layer.

```
 neuralnet.add_node(layer_number)
 neuralnet.remove_node(layer_number) 
 neuralnet.remove_layer(layer_number) 
 neuralnet.change_input(Number_of_inputs) 
 neuralnet.change_output(Number_of_outputs) 
```

After editing , the function completed_network has to be called to lock it again before any operations are performed.

##### Weights

` neuralnet.init_rand_weights() `

This function initialises the weights of neural network with a uniform distribution of (-1,1).

` neuralnet.get_weights() `

This function returns the current weights of the neural network.

` neuralnet.get_weight_count() `

This function returns the number of total weights needed for the neural network to run, we use this count to create our own weights.

` neuralnet.set_weights(weights) `

This functions sets the weights of the neural network as per the "weights" list given to it.

` neuralnet.clear_weights() `

Clears the current weights of the network


##### Visalizing/ Drawing

` neuralnet.draw() `

Draws the current 'LOCKED' neural network. This is just a basic representation of how your network looks.


##### Evaluation

` neuralnet.evaulate(current_input) `

Given a list of inputs , the locked neural network is evaluated with activation functions, weights and biases to give a list of outputs. 


##### Activation Functions

The start of the program contains the initial drawing function created by @author: craffel.
And the rest of the activation functions. New activation functions can be created which can be used for your own network.

##### Example

```
from  NeuroEvolve import *
nn=NeuroES(8,4,softmax)
nn.add_layer(10,relu)
nn.add_layer(5,sigmoid)
nn.completed_network()
```

