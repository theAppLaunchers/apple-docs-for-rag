

- Metal
-  MTLAccelerationStructure 

Protocol

# MTLAccelerationStructure

A collection of model data for GPU-accelerated intersection of rays with the model.

iOS 14.0+iPadOS 14.0+Mac Catalyst 14.0+macOS 11.0+tvOS 16.0+visionOS 1.0+

``` source
protocol MTLAccelerationStructure : MTLResource
```

## Mentioned in 

Improving CPU Performance by Using Argument Buffers

## Overview

To accelerate ray tracing, the device object needs to reorganize your model data into an optimized data structure for intersection testing on that GPU. Create MTLAccelerationStructure objects to contain your model data and reference them in compute and render commands that execute ray-tracing operations.

You don’t define classes that implement this protocol. To create an acceleration structure, you create a descriptor object and configure its properties with your model data. Then call the makeAccelerationStructure(descriptor:) method on the Metal device object to create the object and reserve memory for the structure. To populate the structure with the data, use a MTLAccelerationStructureCommandEncoder to encode GPU commands.

Metal provides multiple descriptor classes, each describing a different type of model data. Choose the appropriate descriptor for each acceleration structure you want to make. Most often, you create an acceleration structure for each list of triangles or bounding boxes. Then collect related geometry structures into a primitive acceleration structure. Create instance acceleration structures when you need to reference instances of primitive acceleration structures at different locations within a scene.

The table below summarizes the descriptor classes:

| Descriptor class | Usage |
|----|----|
| MTLAccelerationStructureTriangleGeometryDescriptor | Describes an acceleration structure for a list of triangles. |
| MTLAccelerationStructureBoundingBoxGeometryDescriptor | Describes an acceleration structure for a list of bounding boxes. |
| MTLPrimitiveAccelerationStructureDescriptor | Describes an acceleration structure for a list of bounding-box or triangle acceleration structures, effectively creating a union of all of the underlying geometry. |
| MTLInstanceAccelerationStructureDescriptor | Describes an acceleration structure for a list of instances of primitive acceleration structures. |

## Topics

### Reading the Structure’s Size

var size: Int

The size of the acceleration structure’s memory allocation, in bytes.

**Required**

### Instance Properties

var gpuResourceID: MTLResourceID

**Required**

## Relationships

### Inherits From

- MTLAllocation
- MTLResource
- NSObjectProtocol

## See Also

### Acceleration Structures

Improving Ray-Tracing Data Access Using Per-Primitive Data

Simplify data access and improve GPU utilization by storing custom primitive data directly in the acceleration structure.

class MTLAccelerationStructureDescriptor

A base class for classes that define the configuration for a new acceleration structure.

class MTLPrimitiveAccelerationStructureDescriptor

A description of an acceleration structure that contains geometry primitives.

class MTLInstanceAccelerationStructureDescriptor

A description of an acceleration structure that derives from instances of primitive acceleration structures.

protocol MTLAccelerationStructureCommandEncoder

An object for encoding commands that build or refit acceleration structures.

struct MTLAccelerationStructureUsage

Options that describe which tasks you can perform on an acceleration structure and how the system performs those tasks.

struct MTLAccelerationStructureRefitOptions

