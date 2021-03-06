# Research Report 
    
## About

The report contains studies, discussion and notes based on research performed in Image Lab, Chung-Ang University at 2018 September to October.

## Goals

The purpose of our program is to
* Understand basic knowledge of machine learning and deep neural network 
* Comprehend state-of-the-art techniques and models in deep learning
* Design and implement denoising model with good performance 

## Research Plan


### 1st Week, September
* Graduate Paper
* Seminar on recent research paper 
* Study on paper


### 2nd Week, September
* Seminar on recent research paper 
* Study on paper


### 3rd Week, September
* Seminar on recent research paper 
* Study on paper


### 4th Week, September
* Seminar on recent research paper 
* Study on paper


### 1st Week, October
* Seminar on recent research paper 
* Study on paper


### 2nd Week, October
* Seminar on recent research paper 
* Study on paper


### 3rd Week, October
* Seminar on recent research paper 
* Study on paper


### 4th Week, October
* Seminar on recent research paper 
* Study on paper



# Graudate Paper

This section is about paper related to graduation.

The paper's topic is *Progress of Configuration in Android
on Pre-trained Deep Learning Model
Implemented by TensorFlow*

## 1 Introduction

As Deep Learning technology has developed
rapidly recently, it has shown positive performance
in various fields. The deep learningbased
system has shown excellent performance
in areas that were considered impossible in
the past, such as AlphaGo, who won the Go
match, and Google duplex, which understand
the context of dialogue and engage in conversation
naturally. Furthermore, efforts are being
made to mount Deep Learning models on
smartphones used by many people such as
[MobileNets](https://arxiv.org/abs/1704.04861). Various deep learning libraries
are being released to implement deep learning,
and [TensorFlow](https://arxiv.org/abs/1603.04467), developed by Google,
provides an interface for deep learning in mobile
devices. Smart phones using the Android
platform went further on Android Studio, and
Google launched the TensorFlow Lite, a lighter
solution. In this paper, the goal is to explore
how to use the previously learned deep learning
model in Android.



## 2 BACKGROUND

### 2.1 TensorFlow
TensorFlow is an open-source library created by
Google for machine learning and deep learning
that is configured to run quickly. A flexible
architecture can be adopted and deployed on
one or more CPUs or GPUs, and can be applied
to a wide range of areas as well as machine
learning and neural network research.


### 2.2 TensorFlow Lite
TensorFlow Lite is a solution for making TensorFlow
lightweight for mobile and embedded
devices. Supports hardware acceleration with
existing TensorFlow and end points, and can
convert implemented TensorFlow models to
perform at low capacity and at high speed.


### 2.3 TensorFlowInferenceInterface
Java interface class that Google implements to
call up and use a model implemented with
TensorFlow using Java. In September 2016, a
commit for that class was raised for the first
time. It provides a convenient function to use
TensorFlow on an Android platform.


### 2.4 Protocol Buffers File
A file with an extension of ’.pb’ is a protocol
buffers-type file that is a serialized data structure
developed by Google and released on open
source. TensorFlow can extract the graph form
of the learned model in the form of ’.pb’ and the
values of parameters obtained after training can
be extracted into a ’.ckpt’ file. These two files
can be combined as new ’.pb’ files containing
the graph and parameter values of the learned
deep learning model at the same time. In this
paper, we will assume that ’.pb’ file as the
newly freezed graph from now on.


### 2.5 Android NDK and JNI
Android NDK is a set of tools that allows
Android to utilize native code such as C and
C++. They are often used when a library that
is implemented in other languages is reused
or operations with heavy calculations, such as
physics simulations, are required to be used at
higher performance. JNI provides an interface
for calling other languages within Java.


### 2.6 TensorFlow in Android Studio
Android Studio is an integrated development
tool for developing Android platform-based
applications, enabling you to install the libraries
and dependencies that applications
need. Libraries for running TensorFlow can also
be easily set up and deployed in Android Studio.


### 2.7 ML Kit
ML Kit is an iOS and Android SDK that was
released by Google that provides variety of
Machine Learning APIs through Firebase. It
is possible to infer using the TensorFlow Lite
and experiment with other machine learning
models using A/B testing through the interface
with the Firebase. It is currently registered as a
beta version.


## 3 MAIN
### 3.1 Native Code Implementation
Before Google unveiled the TensorFlowInreferenceInterface,
developers had to write native
code to run on Android platforms based on
some of the TensorFlow codes written in C++.
Because it was necessary to implement code
that operated by reading ’.pb’ file containing
information from learned deep learning, Android
developers had difficulty on accessing
and implementation.


### 3.2 Advent of TensorFlowInferenceInterface
As Google introduced the TensorFlow-
InreferenceInterface, developers can
handle deep learning only with Java
code without writing native code.
’libandroid tensorflow inference java.jar’,
providing a Java interface and ’libtensorflow
inference.so’, a native library of JNI
codes for TensorFlow provides easy way to
mount models and make inferences about
given inputs. By May 2017, all necessary APIs
could be installed with simple inputs from the
Gradle, a project distribution tool.


### 3.3 Optimization using TensorFlow Lite
The advent of the TensorFlow Lite has allowed
the company to reduce the size and speed
of the Deep Learning network. Existing ’.pb’
files could be converted to ’.tflite’ files using
the TensorFlow Lite TOCO script and mounted
through the Interpreter class provided by the
TensorFlow Lite.


### 3.4 ML Kit
ML Kit is a tool that provides a number of
APIs based on the TensorFlow Lite model, and
uploads the model for use in post-host applications.
The FireBaseLocalModelSource class
allows you to call in models that exist in your
local area, or you can also use the FireBase-
CloudModelSource to register in remote areas.


## 4 CONCLUSION
As Deep Learning has developed in many areas,
various methods have been employed for
using Deep Learning models in smart phones.
Google, which is responsible for the Android
platform, has constantly updated how developers
can use the easy-to-use libraries to implement
deep learning-based applications. In this
paper we looked at the transition process of
using deep learning based on Android. In the
future, more developers will be able to lower
the barriers to deep learning and create more
practical deep learning-based applications.


## REFERENCES
[1] A. Howard, M. Zhu et al. MobileNets: Efficient Convolutional
Neural Networks for Mobile Vision Applications
arXiv:1704.04861, 2017


[2] M. Abadi, A. Agarwal et al. Tensorflow:Large-scale
machine learning on heterogeneous distributed systems
arXiv:1603.04467, 2016


## Reference Image 

This part wass not included in paper. In order to help easy understanding, this section was inserted.
### Tensorflow Lite Architecture
![image](https://github.com/jwcse/DeepLearning/blob/master/img/tensorflowlite.png)

### JDK & JNI
![image](https://github.com/jwcse/DeepLearning/blob/master/img/JNI_NDK.png)






# GoogLeNet(Inception)

Subtitle : Inception(Going Deeper with Convolutions)

## 1 Summary

This model showed good performance at ImageNet Large-Scale Visual Recognition Challenge 2014(ILSVRC14).

* Compared with AlexNet, 12 times less parameters and more accurate

* Unlike traditional way of building single convolutional operation to build up the network, designed layer to 
compute a lot. This is similar with *Network in Network* paper.

* In case of *Network in Network*, convolutional filter was substituted by MLP. In this paper, *Inception module* 
substitutes the same part.

## 2 Introduction

Generally in case of CNN(Convolutional Neural Network), the deeper the network becomes, the better the performance the more layers you have. However, the problem with this approach is that the deeper the network, the more parameters you need to learn. What's particularly noticeable about this is the deep-seated Convolution.


In most CNN, as images go through a resolution operation, channels get bigger and the heat and width are reduced. So let's take a closer look at a specific example. 


Let's say there's data with a size of 192 x 28 x 28 (C x H x W). Suppose the filter is 5x5, the stripe is 1, and the padding is 2. If you had 32 filters, the result would be 32 x 28 x 28. The problem arises here. Each filter has a size of 192 x 5 x 5, and the result is 32 x 28 x 28, so the total required operation is 192 x 5 x 32 x 28 x 28. It requires a massive operation of 1.2 million. It's too much of a burden to stack these computations up.

This is not the only problem. What if you have to design a model yourself? Setting up a hyperparameter, such as the size of a filter, will begin with a problem. But the use of a concept, **Inception** can solve this problem.


## 3 Network in Network

Before understanding **Inception**, it is necessary to figure out the concept of *Network in Network*.

<img src="https://github.com/jwcse/DeepLearning/blob/master/img/net_in_net.jpg" width="900" height="700">

Convolution Operation is a method of using linear operation and non-linear operation, as if scanning the filter for input images. 
In the *Network in Network* paper, tried to change this convolution operation to a Neural Network.

MLP(Multi-layer Perceptron) itself is kind of function approximator, so this can be seen as effort to find out awesome function instead of convolution.

The picture below shows the concept of MLPConv.

<img src="https://github.com/jwcse/DeepLearning/blob/master/img/mlpconv_layer.png" width="850" height="500">


And, below picture shows overall structure of *Network in Network*.

<img src="https://github.com/jwcse/DeepLearning/blob/master/img/net_in_net_overall.png" width="850" height="500">


<img src="https://github.com/jwcse/DeepLearning/blob/master/img/1x1_conv.jpg" width="850" height="500">


The important thing we should concentrate on is that, this process(utilizing n-layer of MLP Conv) is equal to computing convolution and then applying 1x1 convolution.


Finally, the meaningful thing in *Network in Network* is the introduction of **1x1 convolution**. Because of **1x1 convolution**, it has been possible to implement moer non-linear function. Furthermore, this operation includes pooling in channel unit. Thus, if we set number of 1x1 convolution less than input channel number, dimension reduction is possible!


## 4 Inception Module

The convolution filter uses multiple filters for local construction to repeatedly generate output. So in case of network in *Network in Network*, if the purpose was to *dense* and deepen the sparse structure with MLP, this paper's purpose is to perform something between convolution and MLPConv.



<img src="https://github.com/jwcse/DeepLearning/blob/master/img/1x1_conv.jpg" width="750" height="330">


## 5 Full Structure

### 5.1 Overall Structure
<img src="https://github.com/jwcse/DeepLearning/blob/master/img/googlenet.png" width="850" height="330">


### 5.2 Table on Architecture

<img src="https://github.com/jwcse/DeepLearning/blob/master/img/googlenet_arch_table.png" width="850" height="600">





### 5.3 Characteristic
* Proceed 1x1, 3x3, 5x5 convolution parallelly, and then concate


* Apply diverse size of receptive field


* More dense form compared with traditional convolutional filter


* In order to make convolution more efficient, channel reduction is applied. 1x1 convolution is added before 3x3 or 5x5.


* Designed to compute more complex calculation, without much increase of computation.


* Especially, controling 1x1 convolution, quantity of computation can be controlled. So, accuracy-speed trade-off can be determined.





# MobileNets

MobileNets: Efficient Convolutional Neural Networks for Mobile Vision Applications


## 1 Introduction

There are two main approaches for small network.

One is to compress the trained model, and the other one is to train the small network.

This paper concentrates on the latter concept.

This kind of work is valuable in that deep learning can be performed inside small devices or smartphones.


## 2 Main Idea

In MobileNets, the most important idea is *Depthwise Separable Convolution*.

*Width Multiplier* and *Resolution Multiplier* are parameters to reduce the overall size more. 


### 2.1 Depthwise Separable Convolution

This concept was firstly introduced in Google's *Xception* paper.

#### 2.1.1 Concept Overview
<img src="https://github.com/jwcse/DeepLearning/blob/master/img/depthwise_sep_conv.PNG" width="800" height="550">


#### 2.1.2 VS Standard

The picture below shows why quantity of computation is reduced compared with standard version. 

<img src="https://github.com/jwcse/DeepLearning/blob/master/img/standard_vs_depthwise.PNG" width="800" height="550">

#### 2.1.3 Applied Module

<img src="https://github.com/jwcse/DeepLearning/blob/master/img/depthwise_apply.PNG" width="800" height="550">


### 2.2 Width Multiplier : Thinner Models
α(Alpha) is the parameter that ultimately determines the width of the network, which adjusts the number of input and output channels of each layer by α ratio.

α value is usually selected among 1, 0.75, 0.5 and 0.25.

This way can be applied on any network, but size-accuracy trade-off exists.

If the structure is resized, training should be done from the start again.

### 2.3 Resolution Multiplier : Reduced Representation
ρ,
as its name suggests, the parameter that determines the input resolution is adjusted to that ratio.


This parameter is applied on input image and each layer's intermediate representation.

For example, input image of 224 size can be decreased like 192, 160, 128.


## 3 Architecture

<img src="https://github.com/jwcse/DeepLearning/blob/master/img/mobilenet_arch_table.PNG" width="700" height="950">


## 4 Result

The result below shows that with losing 1 percent of accuracy, computation has decrease by 9 times.

<img src="https://github.com/jwcse/DeepLearning/blob/master/img/depth_vs_full_conv_mobilenet.PNG" width="800" height="530">



<img src="https://github.com/jwcse/DeepLearning/blob/master/img/mobilenets_add_result.png" width="700" height="820">


# FPGA
## 1 Introduction
Field-Programmable Logic Array.

<img src="https://github.com/jwcse/CAU-ImageLab2018/blob/master/img/FPGA_simple_structure.jpg" width="850" height="700">


FPGA is an integrated circuit which is repetitively arranged with programmable logic blocks, surrounded with programmable interconnects and connected with I/O blocks.  

FPGA provide the next generation in the programmable logic devices. 

The word 'Field' in the name refers to the ability of the gate arrays to be programmed for a specific function by the user instead of by the manufacturer of the device. 

The word 'Array' is used to indicate a series of columns and rows of gates that can be programmed by the end user. 

It is now very common to design and update features without changing hardware. In fact, most of these things go through the process of updating programs in ROMs on systems using microprocessors.

It will be really comfortable if integrated circuit can be updated like software program. FPGA enables this. 

## 2 Structure


<img src="https://github.com/jwcse/CAU-ImageLab2018/blob/master/img/FPGA_structure.jpg" width="850" height="700">

### 2.1 Logic Block
Gate, Flip-flop, multiplexer, memory is included.

Basically, LUT and D-flip-flop is main component.

Logic block is called LAB(Logic Array Block) by Altera and called CLB(Configurable Logic Block) by Xilinx.

<img src="https://github.com/jwcse/CAU-ImageLab2018/blob/master/img/FPGA_logic_block.jpg" width="850" height="700">


### 2.2 I/O Block
Circuits for constructing input and output circuits for design purposes are arranged such as external pins and I/O protection circuits.


### 2.3 Programmable Interconnects
It consists of an electrical connection switch between the logical block and the wire to connect the signal between the logical block and the I/O cell. 

The length of wiring plays an important role in the structure of the FPGA because it has a very important effect on the operating speed of the digital circuit.

Delay time can be determined depending on how to set routing.


## 3 vs ASIC
Almost all products, including mobile phones, MP3s, and PMPs, contain application specific integrated circuit (ASIC). 

These ASICs are produced in high-performance processes in mass production but at low cost. 

But it's only true if it's mass production. In order for an ASIC developer to design an IC and turn it into a chip, he or she will have to pay the cost of non-Recurrent Engineering (NRE) Cost to receive samples of the IC he designed. 

Currently, you have to pay between 50 and 60 million won if you use the 0.18um process, and the NRE costs hundreds of millions of won if you use the newer process. 

cf> Non-Recurrent Engineering (NRE) Cost: First cost of researching, designing and testing new products

The problem is that if these expensive samples don't work as design errors, then the cost will be the same. Nevertheless, if the volume of production is huge, the cost is buried and chips are produced at a low price.

On the other hand, the price of each FPGA is prohibitively high compared to the price of ASIC, but in case of small mass production, NRE is not included in ASIC, which is relatively cheaper than ASIC. 

In addition, for technologies that are not optimized yet, the use of FPGA will be most effective as you simply reprogram hardware upon upgrade.

As such, the FPGA is the optimal solution for products with relatively small volume but high cost and hardware upgrades.


## 4 vs CPLD
Similar to FPGA as a complex programmable logic device (CPLD), CPLDs are also used to implement normal digital logics.

Each FPGA vendor also produces CPLDs, which Xilinx has a CPLD product line called CoolRunner and Altera call Max. 

There is a different internal structure than the FPGA, but the difference between the users is as follows:

First, the logic size that can be implemented with CPLD is relatively small compared to FPGA. In addition, SRAM, Adder/Multiplayer, complex I/O, and multiple hardwired logics are not available in CPLDs. Therefore, CPLDs are suitable for making glue logics or relatively simple sequential logics.

CPLD is much cheaper than FPGA. And because it's usually flash-based, you don't need a device like an external program memory chip, like the FPGA, and you don't need the number of superfluous disks that are typically needed. Therefore, the system BOM Cost can also be used in sensitive areas. And because CPLDs consume less power than FPGA, we can consider using power-sensitive systems.

## 5 Selection of FPGA
There are many different types of FPGA in the commercial market, so designers can design depending on the circuit you want the flag to be used, you should select the most suitable element and use it. 

In case of FPGA selection, the number of gates, inputs and outputs of devices, maximum operating speed and device price
serve as an important element.

Optimized design improves circuit performance, so the FPGA design environment is also an important factor.

These are species of FPGA.


<img src="https://github.com/jwcse/CAU-ImageLab2018/blob/master/img/FPGA_species.PNG" width="850" height="700">


## 6 FPGA Design Process

<img src="https://github.com/jwcse/CAU-ImageLab2018/blob/master/img/FPGA_design_process.PNG" width="730" height="930">


# Optimization for Learning

The purpose of deep learning is to figure out the parameters to reduce the value of loss function as possible as we can.

This is connected to finding out optimized value for parameters, and we call this **optimization**.

In neural-net, this is uneasy problem because space for parameter is broad and a lot of parameters exist as layers go deeper.

## 1 SGD

Using slope of parameters, getting closer to the most optimized to titled way is called **SGD**, which stands for Stochastic Gradient Descent.

![equation](https://latex.codecogs.com/gif.latex?W%5Cleftarrow%20%5Ceta%20%5Cfrac%7B%5Cpartial%20L%7D%7B%5Cpartial%20W%7D)

Assuming *W* as parameter for update and *L* as loss function, we can write down the equation as above.

(![equation](https://latex.codecogs.com/gif.latex?%5Ceta) stands for learning rate or step size. This is usually set between 0.01 and 0.001)

This is simple implementation for SGD.

```python
class SGD:
    def __init__(self, lr=0.01):
        self.lr = lr
        
    # params, grads are dictionary variables    
    def update(self, params, grads):
        for key in params.keys():
            params[key] -= self.lr * grads[key]
       
optimizer = SGD()
...

```


SGD is simple and easy for us to implement, but this can be inefficient.

Because SGD is *anisotropy* function, which means character is determined according to direction(slope), the path for optimization is not eficient.

The drawback can be represented like this picuture, which shows zig-zag path.


<img src="https://github.com/jwcse/CAU-ImageLab2018/blob/master/img/SGD_zigzag.png" width="770" height="520">


## 2 Momentum


The **Momentum** method is literally giving a kind of 'inertia' to the process of moving through the Gradient Descent. 

Apart from the current direction of travel through the Gradient, it is a method of moving a certain amount further in that direction while remembering how it was moved in the past. 

In the form of the formula: When v is a moving vector, the movement can be expressed in the following manner.

![equation](https://latex.codecogs.com/gif.latex?%5Cnewline%20v%5Cleftarrow%20%5Calpha%20v%20-%20%5Ceta%20%5Cfrac%7B%5Cpartial%20L%7D%7B%5Cpartial%20W%7D%20%5Cnewline%5Cnewline%20W%20%5Cleftarrow%20W%20&plus;%20v)

```python

import numpy as np


class Momentum:

    """모멘텀 SGD"""

    def __init__(self, lr=0.01, momentum=0.9):
        self.lr = lr
        self.momentum = momentum
        self.v = None
        
    def update(self, params, grads):
        if self.v is None:
            self.v = {}
            for key, val in params.items():                                
                self.v[key] = np.zeros_like(val)
                
        for key in params.keys():
            self.v[key] = self.momentum*self.v[key] - self.lr*grads[key] 
            params[key] += self.v[key]




```

<img src="https://github.com/jwcse/CAU-ImageLab2018/blob/master/img/Momentum.gif" width="780" height="600">




It can be expected that the Momentum method will have the effect of exiting the local minima as shown above.

If using the existing SGD, it is not possible to move into the local minima on the left side as the gradient becomes zero. 

On the other hand, using the momentum method requires storing each variable the amount of travel in the past, in addition to the existing variables W, which requires twice the memory for the variable.


## 3 Nesterov Accelerated Gradient (NAG)

Nesterov Accelerated Gradient (NAG) is based on the Momentum method, but the method in which the Gradient is calculated is slightly different. 

For a quick understanding, let's look at the following picture first.


<img src="https://github.com/jwcse/CAU-ImageLab2018/blob/master/img/NAG.jpeg" width="780" height="330">


In the Momentum method, the gradient and moment step in the current position are calculated and combined independently when calculating vector v. 

In NAG, however, consider the moment step first, and then obtain the gradient at the moment to move the gradient step.

This is simple implementation of NAG.

```python

class Nesterov:

    """Nesterov's Accelerated Gradient (http://arxiv.org/abs/1212.0901)"""
    # NAG는 모멘텀에서 한 단계 발전한 방법이다. (http://newsight.tistory.com/224)
    
    def __init__(self, lr=0.01, momentum=0.9):
        self.lr = lr
        self.momentum = momentum
        self.v = None
        
    def update(self, params, grads):
        if self.v is None:
            self.v = {}
            for key, val in params.items():
                self.v[key] = np.zeros_like(val)
            
        for key in params.keys():
            self.v[key] *= self.momentum
            self.v[key] -= self.lr * grads[key]
            params[key] += self.momentum * self.momentum * self.v[key]
            params[key] -= (1 + self.momentum) * self.lr * grads[key]


```


NAG allow us to move more effectively than Momentum. 

In the case of momentum, we can go much further by the inertia than we expect, but in case of NAG, how to move is decided after moving little bit.

Thus, while enjoying the benefits of quick mobilization, you may find it much easier to brake at the right time to stop.


## 4 Adagrad(Adaptive Gradient)

In neural-net, learning rate is important. If this value is too small, training-time takes long and training is not well-performed in the opposite case.

For the efficient technique to determine learning rate, there is *learning rate decay*. This method slowly decreases learning rate as training is proceeded. In this concept, learning rate is set large in initial stage and set small as time goes by.


**Adagrad** is a method of moving the variables by setting the step size differently for each variable when updating them. 

The basic idea of this algorithm is that 'the variables that have not changed much so far will increase step size, and the variables that have changed a lot so far will be smaller.'

Among parameters, largely moved(largely updated) parameter's learning rate is set low.

The point is that *learning rate decay is applied for each parameter's element*.


We can write down the equation and code like below.

![equation](https://latex.codecogs.com/gif.latex?%5Cnewline%20h%5Cleftarrow%20h&plus;%20%5Cfrac%7B%5Cpartial%20L%7D%7B%5Cpartial%20W%7D%5Codot%20%5Cfrac%7B%5Cpartial%20L%7D%7B%5Cpartial%20W%7D%20%5Cnewline%20%5Cnewline%20%5Cnewline%20W%5Cleftarrow%20W%20-%20%5Ceta%20%5Cfrac%7B1%7D%7B%5Csqrt%7Bh%7D%7D%5Cfrac%7B%5Cpartial%20L%7D%7B%5Cpartial%20W%7D)


```python

class AdaGrad:

    """AdaGrad"""

    def __init__(self, lr=0.01):
        self.lr = lr
        self.h = None
        
    def update(self, params, grads):
        if self.h is None:
            self.h = {}
            for key, val in params.items():
                self.h[key] = np.zeros_like(val)
            
        for key in params.keys():
            self.h[key] += grads[key] * grads[key]
            params[key] -= self.lr * grads[key] / (np.sqrt(self.h[key]) + 1e-7) # Adding small value 1e-7 ; prevents dividing by zero.


```


## 5 RMSprop

One bad thing of AdaGrad is that update is not proceeded as past slope is multiplied and added.

In other words, quantity of update becomes zero if training is performed for a long time.

This method complements the drawback of AdaGrad.

Instead of utilizing 'past-slope', new slope information is reflected.

This is called *EMA(Exponential Moving Average)*, that highly dimishes effect of past-slope.


```python

class RMSprop:

    """RMSprop"""

    def __init__(self, lr=0.01, decay_rate = 0.99):
        self.lr = lr
        self.decay_rate = decay_rate
        self.h = None
        
    def update(self, params, grads):
        if self.h is None:
            self.h = {}
            for key, val in params.items():
                self.h[key] = np.zeros_like(val)
            
        for key in params.keys():
            self.h[key] *= self.decay_rate
            self.h[key] += (1 - self.decay_rate) * grads[key] * grads[key]
            params[key] -= self.lr * grads[key] / (np.sqrt(self.h[key]) + 1e-7)  

```


## 6 Adam

*Momentum + AdaGrad*

This method was suggested at 2015.

Adam configures three hyperparameters. One is for learning rate, The other two : coefficient for 1st-order momentum and coefficeint for 2nd-order momentum. According to this method's inventer, 0.9 and 0.999 is great enough value for each hyperparameter.

```python

class Adam:

    """Adam (http://arxiv.org/abs/1412.6980v8)"""

    def __init__(self, lr=0.001, beta1=0.9, beta2=0.999):
        self.lr = lr
        self.beta1 = beta1
        self.beta2 = beta2
        self.iter = 0
        self.m = None
        self.v = None
        
    def update(self, params, grads):
        if self.m is None:
            self.m, self.v = {}, {}
            for key, val in params.items():
                self.m[key] = np.zeros_like(val)
                self.v[key] = np.zeros_like(val)
        
        self.iter += 1
        lr_t  = self.lr * np.sqrt(1.0 - self.beta2**self.iter) / (1.0 - self.beta1**self.iter)         
        
        for key in params.keys():
            #self.m[key] = self.beta1*self.m[key] + (1-self.beta1)*grads[key]
            #self.v[key] = self.beta2*self.v[key] + (1-self.beta2)*(grads[key]**2)
            self.m[key] += (1 - self.beta1) * (grads[key] - self.m[key])
            self.v[key] += (1 - self.beta2) * (grads[key]**2 - self.v[key])
            
            params[key] -= lr_t * self.m[key] / (np.sqrt(self.v[key]) + 1e-7)
            
            #unbias_m += (1 - self.beta1) * (grads[key] - self.m[key]) # correct bias
            #unbisa_b += (1 - self.beta2) * (grads[key]*grads[key] - self.v[key]) # correct bias
            #params[key] += self.lr * unbias_m / (np.sqrt(unbisa_b) + 1e-7)

```


## Comparison

For SGD, Momentum, AdaGrad and Adam, compared methods with following code.

The picture below shows the result.

```python

# coding: utf-8
import sys, os
sys.path.append(os.pardir)  # 부모 디렉터리의 파일을 가져올 수 있도록 설정
import numpy as np
import matplotlib.pyplot as plt
from collections import OrderedDict
#from common.optimizer import *   # d


def f(x, y):
    return x**2 / 20.0 + y**2


def df(x, y):
    return x / 10.0, 2.0*y

init_pos = (-7.0, 2.0)
params = {}
params['x'], params['y'] = init_pos[0], init_pos[1]
grads = {}
grads['x'], grads['y'] = 0, 0


optimizers = OrderedDict()
optimizers["SGD"] = SGD(lr=0.95)
optimizers["Momentum"] = Momentum(lr=0.1)
optimizers["AdaGrad"] = AdaGrad(lr=1.5)
optimizers["Adam"] = Adam(lr=0.3)

idx = 1

for key in optimizers:
    optimizer = optimizers[key]
    x_history = []
    y_history = []
    params['x'], params['y'] = init_pos[0], init_pos[1]
    
    for i in range(30):
        x_history.append(params['x'])
        y_history.append(params['y'])
        
        grads['x'], grads['y'] = df(params['x'], params['y'])
        optimizer.update(params, grads)
    

    x = np.arange(-10, 10, 0.01)
    y = np.arange(-5, 5, 0.01)
    
    X, Y = np.meshgrid(x, y) 
    Z = f(X, Y)
    
    # 외곽선 단순화
    mask = Z > 7
    Z[mask] = 0
    
    # 그래프 그리기
    plt.subplot(2, 2, idx)
    idx += 1
    plt.plot(x_history, y_history, 'o-', color="red")
    plt.contour(X, Y, Z)
    plt.ylim(-10, 10)
    plt.xlim(-10, 10)
    plt.plot(0, 0, '+')
    #colorbar()
    #spring()
    plt.title(key)
    plt.xlabel("x")
    plt.ylabel("y")
    
plt.show()


```


<img src="https://github.com/jwcse/CAU-ImageLab2018/blob/master/img/optimizer_compare.PNG" width="740" height="740">




