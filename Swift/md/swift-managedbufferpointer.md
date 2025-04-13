

- Swift
-  ManagedBufferPointer 

Structure

# ManagedBufferPointer

Contains a buffer object, and provides access to an instance of `Header` and contiguous storage for an arbitrary number of `Element` instances stored in that buffer.

iOS 8.0+iPadOS 8.0+Mac Catalyst 13.0+macOS 10.10+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
@frozen
struct ManagedBufferPointer where Element : ~Copyable
```

## Overview

For most purposes, the `ManagedBuffer` class can be used on its own. However, in cases where objects of various different classes must serve as storage, you need to also use `ManagedBufferPointer`.

A valid buffer class is non-`@objc`, with no declared stored properties. Its `deinit` must destroy its stored `Header` and any constructed `Element`s.

## Example Buffer Class

```
 class MyBuffer { // non-@objc
   typealias Manager = ManagedBufferPointer
   deinit {
     Manager(unsafeBufferObject: self).withUnsafeMutablePointers {
       (pointerToHeader, pointerToElements) -> Void in
       pointerToElements.deinitialize(count: self.count)
       pointerToHeader.deinitialize(count: 1)
     }
   }

   // All properties are *computed* based on members of the Header
   var count: Int {
     return Manager(unsafeBufferObject: self).header.0
   }
   var name: String {
     return Manager(unsafeBufferObject: self).header.1
   }
 }
```

## Topics

### Creating a Buffer

init(bufferClass: AnyClass, minimumCapacity: Int, makingHeaderWith: (AnyObject, (AnyObject) -> Int) throws -> Header) rethrows

Create with new storage containing an initial `Header` and space for at least `minimumCapacity` `element`s.

init(unsafeBufferObject: AnyObject)

Manage the given `buffer`.

### Inspecting a Buffer

var capacity: Int

The actual number of elements that can be stored in this object.

var header: Header

The stored `Header` instance.

var buffer: AnyObject

Returns the object instance being used for storage.

func isUniqueReference() -> Bool

Returns `true` if `self` holds the only strong reference to its buffer; otherwise, returns `false`.

### Accessing Buffer Contents

func withUnsafeMutablePointerToElements&lt;E, R>((UnsafeMutablePointer&lt;Element>) throws(E) -> R) throws(E) -> R

Call `body` with an `UnsafeMutablePointer` to the `Element` storage.

func withUnsafeMutablePointerToHeader&lt;E, R>((UnsafeMutablePointer&lt;Header>) throws(E) -> R) throws(E) -> R

Call `body` with an `UnsafeMutablePointer` to the stored `Header`.

func withUnsafeMutablePointers&lt;E, R>((UnsafeMutablePointer&lt;Header>, UnsafeMutablePointer&lt;Element>) throws(E) -> R) throws(E) -> R

Call `body` with `UnsafeMutablePointer`s to the stored `Header` and raw `Element` storage.

### Comparing Buffers

static func != (Self, Self) -> Bool

Returns a Boolean value indicating whether two values are not equal.

### Default Implementations

Equatable Implementations

## Relationships

### Conforms To

- Copyable

  Conforms when `Header` conforms to `Copyable`, `Header` conforms to `Escapable`, `Element` conforms to `Copyable`, and `Element` conforms to `Escapable`.

- Equatable

  Conforms when `Header` conforms to `Copyable`, `Header` conforms to `Escapable`, `Element` conforms to `Copyable`, and `Element` conforms to `Escapable`.

## See Also

### Buffer Implementation

class ManagedBuffer

A class whose instances contain a property of type `Header` and raw storage for an array of `Element`, whose size is determined at instance creation.

