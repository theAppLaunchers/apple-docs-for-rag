

- Metal Performance Shaders Graph
- MPSGraphExecutable
-  init(package:descriptor:) 

Initializer

# init(package:descriptor:)

Initialize the executable with the Metal Performance Shaders Graph package at the provided URL.

iOS 17.0+iPadOS 17.0+Mac Catalyst 17.0+macOS 14.0+tvOS 17.0+visionOS 1.0+

``` source
init(
    package mpsgraphPackageURL: URL,
    descriptor compilationDescriptor: MPSGraphCompilationDescriptor?
)
```

## Parameters 

`mpsgraphPackageURL`  

The URL where to read the serialized MPSGraphExecutable.

`compilationDescriptor`  

Compilation descriptor to be used to specialize, since the executable was created with a compilationDescriptor already this one overrides those settings to the extent it can.

