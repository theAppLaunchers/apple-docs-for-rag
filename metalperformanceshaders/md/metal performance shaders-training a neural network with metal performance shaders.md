

- Metal Performance Shaders
-  Training a Neural Network with Metal Performance Shaders 

Sample Code

# Training a Neural Network with Metal Performance Shaders

Use an MPS neural network graph to train a simple neural network digit classifier.

Download

macOS 10.15+Xcode 11.0+

## Overview

The sample code describes how to write a neural network using MPSNNGraph and how to train the network to recognize a digit in an image. The sample trains a network for 300 iterations on a batch size of 40 images. You’ll see how to set up training of weights and biases using data sources, including how to initialize and update weights. You’ll also see how to validate the network using a test dataset.

Note

This sample code project is associated with WWDC 2019 session 614: Metal for Machine Learning.

You can use any dataset of your choice to train this model. The following dataset works well for this purpose:

MNIST Dataset

Please note that Apple does not own the copyright to this dataset nor makes any representations about the applicable terms of use for this dataset.

If you choose to use this dataset, the sample includes a script that downloads the dataset from that location and pass it as input to the model.

### Configure the Sample Code Project

Before you run the sample code project in Xcode:

- Make sure your Mac is running macOS 10.15 or later.

- Make sure you are running Xcode 11 or later.

## See Also

### Neural Networks

class MPSImage

A texture that may have more than four channels for use in convolutional neural networks.

class MPSTemporaryImage

A texture for use in convolutional neural networks that stores transient data to be used and discarded promptly.

Objects that Simplify the Creation of Neural Networks

Simplify the creation of neural networks using networks of filter, image, and state nodes.

Convolutional Neural Network Kernels

Build neural networks with layers.

Recurrent Neural Networks

Create recurrent neural networks.

