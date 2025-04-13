

- Synchronization
-  AtomicRepresentable 

Protocol

# AtomicRepresentable

A type that supports atomic operations through a separate atomic storage representation.

iOS 18.0+iPadOS 18.0+Mac Catalyst 18.0+macOS 15.0+tvOS 18.0+visionOS 2.0+watchOS 11.0+

``` source
protocol AtomicRepresentable
```

## Overview

Types that conform to the `AtomicRepresentable` protocol can be used as the `Value` type parameter with the `Atomic` type. Conformances that utilize existing atomic storage representations as their own representation will get the primitive atomic operations available on `Atomic` for free. Such operations include `load`, `store`, `exchange`, `compareExchange`, and `weakCompareExchange`.

## Conforming to the AtomicRepresentable protocol

Conforming your own custom types allow them to be used in the `Atomic` type and get access to all of the primitive atomic operations explained above. There are two main ways to conform your type to `AtomicRepresentable`:

1.  Using a predefined `RawRepresentable` conformance

2.  Manually conforming to `AtomicRepresentable`

If you custom type already conforms to `RawRepresentable`, then adding the `AtomicRepresentable` conformance may be really simple! If the `RawValue` associated type of your type is already itself an `AtomicRepresentable`, then all you need to do is add the conformance and you’re done!

```
enum TrafficLight: UInt8 {
  case red
  case yellow
  case green
}

extension TrafficLight: AtomicRepresentable {}
```

And that’s it! Here, we’re utilizing Swift’s automatic `RawRepresentable` conformance synthesis for enums by declaring our “raw value” to be a `UInt8`. By adding the `AtomicRepresentable` conformance, we automatically figure out how to do the conformance from the `RawRepresentable` implementation and do all of th necessary work for you. However, it is still possible to customize this behavior using the manual method explained below.

Defining your own `AtomicRepresentable` conformance is pretty simple. All you have to do is decide what atomic storage representation fits best for your type, and create the bidirectional relationship between the two.

```
// A point in an x-y coordinate system.
struct GridPoint {
  var x: Int
  var y: Int
}

extension GridPoint: AtomicRepresentable {
  typealias AtomicRepresentation = WordPair.AtomicRepresentation

  static func encodeAtomicRepresentation(
    _ value: consuming GridPoint
  ) -> AtomicRepresentation {
    let wordPair = WordPair(
      first: UInt(bitPattern: value.x),
      second: UInt(bitPattern: value.y)
    )

    return WordPair.encodeAtomicRepresentation(wordPair)
  }

  static func decodeAtomicRepresentation(
    _ representation: consuming AtomicRepresentation
  ) -> GridPoint {
    let wordPair = WordPair.decodeAtomicRepresentation(representation)

    return GridPoint(
      x: Int(bitPattern: wordPair.first),
      y: Int(bitPattern: wordPair.second)
    )
  }
}
```

Here, we’re going to select `WordPair`’s atomic storage representation as our own. This is very important because we only get the atomic operations like `load` and `store` if our representation is one of the *fundamental* storage representations. Luckily for us, `WordPair` does use one of these types as its storage type.

In addition to selecting what storage representation our type will use, we define two static functions that go from both our custom type to its representation and the representation back to our own type. Because our representation is the same as `WordPair.AtomicRepresentation`, we will actually go through `WordPair`’s `AtomicRepresentable` conformance to help define our own.

This is all you need to do to conform your custom type to the `AtomicRepresentable` protocol. From here, you can use this type in all of the primitive atomic operations like shown below:

```
func atomicGridPoint(_ gridPoint: Atomic) {
  let newGridPoint = GridPoint(x: 123, y: -456)

  let oldGridPoint1 = gridPoint.load(ordering: .relaxed)

  gridPoint.store(newGridPoint, ordering: .releasing)

  let oldGridPoint2 = gridPoint.exchange(
    desired: oldGridPoint1,
    ordering: .acquiringAndReleasing
  )

  let (exchanged1, oldGridPoint2) = gridPoint.compareExchange(
    expected: oldGridPoint1,
    desired: newGridPoint,
    ordering: .sequentiallyConsistent
  )

  let (exchanged2, oldGridPoint3) = gridPoint.weakCompareExchange(
    expected: newGridPoint,
    desired: oldGridPoint2,
    ordering: .relaxed
  )
}
```

## List of Fundamental Atomic Representations

When defining your own `AtomicRepresentable` conformance, it is critical that your custom type should choose from the following list of types as its own `AtomicRepresentation`:

- `UInt8.AtomicRepresentation`

- `UInt16.AtomicRepresentation`

- `UInt32.AtomicRepresentation`

- `UInt64.AtomicRepresentation`

- `UInt.AtomicRepresentation`

- `Int8.AtomicRepresentation`

- `Int16.AtomicRepresentation`

- `Int32.AtomicRepresentation`

- `Int64.AtomicRepresentation`

- `Int.AtomicRepresentation`

- `WordPair.AtomicRepresentation`

Note

`Int8.AtomicRepresentation` is the same type as `UInt8.AtomicRepresentation` and the same is true for all of the same sized integer types. If your type wraps an unsigned integer, you should prefer to use an unsigned integer’s atomic representation instead of a signed ones and vice versa. `Int` and `UInt`’s representation will be 64 bits wide on 64 bit systems and 32 bit wide on 32 bit systems. `Int64` and `UInt64` always conform to `AtomicRepresentable` on 64 bit systems, but on 32 bit systems they will only conform if the platform supports double wide atomics. `WordPair` will only conform to `AtomicRepresentable` on platforms that support double wide atomics, but if they do it will be 128 bits wide on 64 bit systems and 64 bits wide on 32 bit systems.

## Topics

### Associated Types

associatedtype AtomicRepresentation : BitwiseCopyable

The storage representation type that `Self` encodes to and decodes from which is a suitable type when used in atomic operations.

**Required**

### Type Methods

static func decodeAtomicRepresentation(consuming Self.AtomicRepresentation) -> Self

Recovers the logical atomic type `Self` by destroying some `AtomicRepresentation` storage instance returned from an atomic operation.

**Required**

static func encodeAtomicRepresentation(consuming Self) -> Self.AtomicRepresentation

Destroys a value of `Self` and prepares an `AtomicRepresentation` storage type to be used for atomic operations.

**Required**

## Relationships

### Inherited By

- AtomicOptionalRepresentable

### Conforming Types

- Bool
- Double
- Duration
- Float
- Float16
- Int
- Int128
- Int16
- Int32
- Int64
- Int8
- Never
- ObjectIdentifier
- OpaquePointer
- Optional

  Conforms when `Wrapped` conforms to `AtomicOptionalRepresentable`.

- UInt
- UInt128
- UInt16
- UInt32
- UInt64
- UInt8
- Unmanaged

  Conforms when `Instance` conforms to `Copyable` and `Escapable`.

- UnsafeBufferPointer

  Conforms when `Element` conforms to `Escapable`.

- UnsafeMutableBufferPointer

  Conforms when `Element` conforms to `Escapable`.

- UnsafeMutablePointer

  Conforms when `Pointee` conforms to `Escapable`.

- UnsafeMutableRawBufferPointer
- UnsafeMutableRawPointer
- UnsafePointer

  Conforms when `Pointee` conforms to `Escapable`.

- UnsafeRawBufferPointer
- UnsafeRawPointer
- WordPair

## See Also

### Atomic Values

struct Atomic

An atomic value.

struct AtomicLazyReference

A lazily initializable atomic strong reference.

struct WordPair

A pair of two word sized `UInt`s.

protocol AtomicOptionalRepresentable

An atomic value that also supports atomic operations when wrapped in an `Optional`. Atomic optional representable types come with a standalone atomic representation for their optional-wrapped variants.

