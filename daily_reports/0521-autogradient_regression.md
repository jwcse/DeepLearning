# 21/05/18 Daily Report

## Auto Gradient

*torch.Tensor* is the central class of the package. If we set its attribute .requires_grad as True, it starts to track all operations on it. When we finish our computation we can call .backward() and have all the gradients computed automatically. The gradient for this tensor will be accumulated into .grad attribute.

If you want to compute the derivatives, you can call .backward() on a Tensor as mentioned above. If Tensor is a scalar (i.e. it holds a one element data), you don’t need to specify any arguments to backward(), however if it has more elements, you need to specify a gradient argument that is a tensor of matching shape.


We've seen gradient descent operating by our handling. The code below is implementation of gradient descent using pytorch library.

### Code 1

This code is from [hunkim's code](https://github.com/hunkim/PyTorchZeroToAll/blob/master/03_auto_gradient.py).

```python

import torch
from torch.autograd import Variable

x_data = [1.0, 2.0, 3.0]
y_data = [2.0, 4.0, 6.0]

w = Variable(torch.Tensor([1.0]),  requires_grad=True)  # Any random value

# our model forward pass


def forward(x):
    return x * w

# Loss function


def loss(x, y):
    y_pred = forward(x)
    return (y_pred - y) * (y_pred - y)

# Before training
print("predict (before training)",  4, forward(4).data[0])

# Training loop
for epoch in range(10):
    for x_val, y_val in zip(x_data, y_data):
        l = loss(x_val, y_val)
        l.backward()
        print("\tgrad: ", x_val, y_val, w.grad.data[0])
        w.data = w.data - 0.01 * w.grad.data

        # Manually zero the gradients after updating weights
        w.grad.data.zero_()

    print("progress:", epoch, l.data[0])

# After training
print("predict (after training)",  4, forward(4).data[0])



```


### Code 2

```python
import torch
from torch.autograd import Variable


# 1) Declaration

x_tensor =torch.Tensor(3, 4)    # FloatTensor of size 3x4

x_variable = Variable(x_tensor)

# 2) Variables of a Variable

# .data -> wrapped tensor
x_variable.data

# .grad -> gradient of the variable
x_variable.grad

# .requires_grad -> whether variable requires gradient
x_variable.requires_grad

# .volatile -> inference mode with minimal memory usage
x_variable.volatile


# 3) Graph & Variables
x = Variable(torch.FloatTensor(3, 4), requires_grad=True)
y = x**2 + 4*x  # requires_grad = True
z = 2*y + 3     # requires_grad = True

# .backward(gradient, retain_graph, create_graph, retain_variables)
# compute gradient of current variable w.r.t. graph leaves

gradient = torch.FloatTensor(3, 4)
z.backward(gradient)
# x.grad, y.grad, z.grad


```

## Linear Regression in Pytorch

By using pytorch, process of forward, backwardpropagation and updating for optimization becomes easier.
Let's look at the *Linear Regression* as example. The process of coding in pytorch can be divided into three part :

### 1. Design model using class with Variables
Neural networks can be constructed using *torch.nn* package.
*nn* depends on 'autograd' to define models and differentiate them.

An *nn.Module* contains layers, and a method *forward(input)* that returns 'output'.

A typical training proceduer for a neural network is as follows :
- Define the neural network that has some learnable parameters(or weights)
- Iterate over a dataset of inputs
- Process input through the network
- Compute the loss(how far is the output from being correct)
- Propagate gradients back into the network's parameters
- Update the weights of the network, typically using a simple update rule :
'weight = weight - learning_rate * gradient'

### 2. Construct loss and optimizer

### 3. Training cycle (forward, backward, update)


```python
import pytorch
from torch.autograd import Variable

# Data definition
x_data = Variable(torch.Tensor([[1.0], [2.0], [3.0]]))
y_data = Variable(torch.Tensor([[2.0], [4.0], [6.0]]))


# Model class in Pytorch way
class Model(torch.nn.Module):
  def __init__(self):
  """
    In the constructor we instantiate two nn.Linear module
  """
  super(Model, self).__init__()
  self.linear = torch.nn.Linear(1, 1) # One in and one out
  
  def forward(self, x):
    """
      In the forward function we accept a Variable of input data and we must return a Variable of output data.
      We can use Modules defined in the constructor as well as arbitrary operators on Variables.   
    """
      y_pred = self.linear(x)
      return y_pred

# our model
model = Model()
  
# Construct our loss function and an Optimizer. The call to model.parameters()
# in the SGD constructor will contain the learnable parameters of the two
# nn.Linear modules which are members of the model.
criterion = torch.nn.MSELoss(size_average=False)
optimizer = torch.optim.SGD(model.parameters(), lr=0.01)  # parameter : (what need to be updated, learning_rate)

# Training loop
for epoch in range(500):
        # Forward pass: Compute predicted y by passing x to the model
    y_pred = model(x_data)

    # Compute and print loss
    loss = criterion(y_pred, y_data)
    print(epoch, loss.data[0])

    # Zero gradients, perform a backward pass, and update the weights.
    optimizer.zero_grad()
    loss.backward()
    optimizer.step()


# After training
hour_var = Variable(torch.Tensor([[4.0]]))
y_pred = model(hour_var)
print("predict (after training)",  4, model(hour_var).data[0][0])
```




