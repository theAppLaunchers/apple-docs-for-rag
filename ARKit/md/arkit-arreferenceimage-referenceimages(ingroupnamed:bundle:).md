

- ARKit
- ARReferenceImage
-  referenceImages(inGroupNamed:bundle:) 

Type Method

# referenceImages(inGroupNamed:bundle:)

Loads all reference images in the specified AR Resource Group in your Xcode project’s asset catalog.

iOS 11.3+iPadOS 11.3+Mac Catalyst 13.1+

``` source
class func referenceImages(
    inGroupNamed name: String,
    bundle: Bundle?
) -> Set?
```

## Parameters 

`name`  

The name of an AR Resource Group from your Xcode project’s main asset catalog.

`bundle`  

The bundle from which to load asset catalog resources, or `nil` to use your app’s main bundle.

## Return Value

A set of all unique reference images in the specified group.

## Discussion

To use the images for image detection in a world-tracking AR session, provide this set for your session configuration’s detectionImages property.

