

- SceneKit
-  SceneKit 3D Data Types 

API Collection

# SceneKit 3D Data Types

SceneKit-specific vectors, matrices, and related functions and operations.

## Overview

Important

In macOS 10.13, iOS 11, tvOS 11, and watchOS 4 (or later), use data types provided by the system SIMD library (such as `float3` and `float4x4`) and the corresponding SceneKit methods (such as simdPosition and simdTransform) instead. These types provide faster performance, offer more concise C, C++, and Swift syntax (such as `+` and `*` operators instead of functions), and interoperate better with other technologies (such as Model I/O, GameplayKit, and the Metal Shading Language).

## Topics

### Vectors

struct SCNVector3

A representation of a three-component vector.

struct SCNVector4

A representation of a four-component vector.

### Transforms and Rotations

struct SCNMatrix4

A representation of a 4 x 4 matrix.

typealias SCNMatrix4

A representation of a 4 x 4 matrix.

typealias SCNQuaternion

A representation of a quaternion.

### Scalars

typealias SCNFloat

The element type for SceneKit vectors and matrices.

