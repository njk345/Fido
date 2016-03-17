# Fido

An open-source, highly modular C++ machine learning library for embedded electronics and robotics. Fido includes implementations of neural networks, reinforcement learning, and genetic algorithms. Fido is especially suited for robotic contexts, as it is written in C++ with minimal use of the standard library, comes packaged with a robotic simulator, and provides and easy interface in which to write robotic drivers.

## Getting Started

Clone the github repository.
```
$ git clone https://github.com/FidoProject/Fido.git
```

Move to the Software directory and build the library using cmake.
```
$ cd Fido/Software && make
```

Now you may use Fido in your C++ projects, by including any of the header files located in the Software directory.

## Example Code

An example of creating and training a neural network using Fido.

```cpp
#include "Fido/Software/NeuralNet.h"
#include "Fido/Software/Backpropagation.h"

// Trains a neural network to perform linear regression
int main() {
  // Creates a neural network with 1 input, 1 output, 2 hidden layers, 4 neurons per hidden layer, and a sigmoid activation function.
  net::NeuralNet neuralNetwork = NeuralNet(2, 1, 2, 4, "sigmoid");
  std::vector< std::vector<double> > input = { {1}, {2}, {5}, {6} };
  std::vector< std::vector<double> > correctOutput = { {2}, {4}, {10}, {12} };
  
  // Create backpropagation object with a learning rate of 10%, a momentum term of 0.001, an acceptable error level of 5%, and a maximum number of training iterations of 10000
  net::Backpropagation backprop = Backpropagation(0.1, 0.001, 0.05, 10000);
  backprop.trainOnData(&network, input, correctOutput);
}
```

## Contributing

Send us a pull request. We will be happy to add you as a contributor and credit you in the README if you do so.
