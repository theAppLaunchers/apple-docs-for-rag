

- Vision
-  VNImageOption 

Structure

# VNImageOption

An option key passed into an image request handler that takes an auxiliary image.

iOS 11.0+iPadOS 11.0+Mac Catalyst 13.0+macOS 10.13+tvOS 11.0+visionOS 1.0+

``` source
struct VNImageOption
```

## Discussion

Pass an option key into the VNImageRequestHandler instance on creation or request. Option keys are used to describe specific properties of an image or specify how an image needs to be handled.

## Topics

### Initializers

init(rawValue: String)

Initializes an option key using its string name.

### Options Dictionary Keys

static let properties: VNImageOption

The dictionary from the image source that contains the metadata for algorithms like horizon detection.

static let cameraIntrinsics: VNImageOption

An option to specify the camera intrinstics.

static let ciContext: VNImageOption

An option key to specify the context to use in the handler’s Core Image operations.

## Relationships

### Conforms To

- Equatable
- Hashable
- RawRepresentable
- Sendable

