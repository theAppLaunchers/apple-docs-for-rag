

- Core ML
-  Getting a Core ML Model 

Article

# Getting a Core ML Model

Obtain a Core ML model to use in your app.

## Overview

Core ML supports a variety of machine learning models, including neural networks, tree ensembles, support vector machines, and generalized linear models. Core ML requires the Core ML model format (models with a `.mlmodel` file extension).

Using Create ML and your own data, you can train custom models to perform tasks like recognizing images, extracting meaning from text, or finding relationships between numerical values. Models trained using Create ML are in the Core ML model format and are ready to use in your app.

Apple also provides several popular, open source models that are already in the Core ML model format. You can download these models and start using them in your app.

Additionally, various research groups and universities publish their models and training data, which may not be in the Core ML model format. Use Core ML Tools to convert these models to use in your app.

## See Also

### Core ML models

Updating a Model File to a Model Package

Convert a Core ML model file into a model package in Xcode.

Integrating a Core ML Model into Your App

Add a simple model to an app, pass input data to the model, and process the model’s predictions.

class MLModel

An encapsulation of all the details of your machine learning model.

Model Customization

Expand and modify your model with new layers.

Model Personalization

Update your model to adapt to new data.

