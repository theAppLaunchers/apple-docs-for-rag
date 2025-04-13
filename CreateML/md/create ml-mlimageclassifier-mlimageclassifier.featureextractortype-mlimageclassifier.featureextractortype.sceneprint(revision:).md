

- Create ML
- MLImageClassifier
- MLImageClassifier.FeatureExtractorType
-  MLImageClassifier.FeatureExtractorType.scenePrint(revision:) 

Case

# MLImageClassifier.FeatureExtractorType.scenePrint(revision:)

A feature extractor trained on millions of images.

iOS 15.0+iPadOS 15.0+Mac Catalyst 15.0+macOS 10.14+visionOS 1.0+

``` source
case scenePrint(revision: Int?)
```

## Parameters 

`revision`  

The sceneprint version. The supported versions include 1 and 2. If `nil` defaults to the latest version.

## Mentioned in 

Creating an Image Classifier Model

## Discussion

Note

The case’s associated value indicates which revision of the feature extractor to use. Set this to 1 when creating a scene print feature extractor.

The scene print feature extractor works best with images of real world objects because it trained on millions of such images. Scene print is not suitable for character recognition, because the input images are highly binary in nature (pixels are either on or off).

When you train an image classifier using scene print, or make predictions with the resulting model, use images with 299x299 pixels or more. The model upscales smaller images, to 299x299 before it feeds them to the feature extractor, which may result in poor accuracy.

Typically, scene print works best if the source of your training data matches the source of the images you want to classify. For example, if your app classifies images captured with an iPhone camera, train your model using images captured in the same way, if possible.

## See Also

### Selecting a feature extractor type

case custom(MLImageClassifier.CustomFeatureExtractor)

A feature extractor that you provide as a Core ML model file or a layer within that file.

struct CustomFeatureExtractor

A custom feature extractor a training session uses to train an image classifier.

