

- Xcode Release Notes
- Xcode 10 Release Notes
-  Swift 4.2 Release Notes for Xcode 10 

Article

# Swift 4.2 Release Notes for Xcode 10

Update your code to use new language features and test your apps against changes.

## Overview

Read these notes when you’re writing Swift apps in Xcode 10.

### Swift Compiler

#### New Features

- The behavior of casts from optional types to generic types has changed in some circumstances in Swift 4.2. For example:

  ```
  struct ConditionalCast {
      func cast(value: Any?) -> T? {
          return value as? T
      }
  }
  ```

  If value is `nil` and the type `T` is an optional type at runtime, the return value will now be `.some(nil)` rather than `nil`. This behavior is consistent with the casting behavior when concrete types are used rather than generic types. (40916953)

- The C `long double` type is now imported as Float80 on i386 and x86_64 for macOS and Linux. The `tgmath` functions in the Darwin and glibc modules now support Float80 as well as Float and Double. Several tgmath functions have been made generic over BinaryFloatingPoint and FloatingPoint so that they’re automatically available to any conforming type. (SR-2046) (27196587)

- C macros containing casts are no longer imported to Swift if the type in the cast is unavailable or deprecated, or produces some other diagnostic when referenced. These macros were already only imported under very limited circumstances with very simple values, so this is change unlikely to affect your code. (36528212)

- To help prevent inconsistent hashing for Cocoa objects, overriding the hashValue on NSObject property now produces a compiler warning, and hash(into:)) is now marked as nonoverridable. To customize hashing in NSObject subclasses, you need to override the hash property, not hashValue. The example below shows a sample implementation for an NSObject subclass with a custom definition for hashing. Note that hashing and equality go hand in hand: if you override hash, you also need to override isEqual(_:), and vice versa (42780635):

  ```
  class Person: NSObject {
      let name: String

      init(name: String) {
          self.name = name
          super.init()
      }

      override func isEqual(_ other: Any?) -> Bool {
          guard let other = other as? Person else { return false }
          return other.name == self.name
      }

      override var hash: Int {
          var hasher = Hasher()
          hasher.combine(name)
          return hasher.finalize()
      }
  }
  ```

- Swift 4.1 warnings about overlapping accesses are now errors in Swift 4 mode. These new errors most commonly arise when a generic mutating method that modifies a variable is passed a non-escaping closure that reads from the same variable. Code that previously compiled with a warning will need to be updated. For more information, see Upgrading exclusive access warning to be an error in Swift 4.2. (34669400)

- The Swift compiler defaults to a new compilation strategy that can greatly speed up debug builds. This strategy allows each compilation job to process a batch of files instead of just a single file.Projects that had sped up debug builds by opting into building with Whole Module Optimization in Debug mode (at `-Onone`) should try the new compilation style. To do so, choose the Incremental option for the Compilation Mode build setting and ensure that your project is not using older whole-module settings for Debug builds such as `SWIFT_WHOLE_MODULE_OPTIMIZATION=YES` or `SWIFT_OPTIMIZATION_LEVEL=-Owholemodule`.

  The new compilation strategy should be transparent in terms of the build products. However, in case it causes a problem, you can revert to the previous single file strategy with a custom Build Setting `SWIFT_ENABLE_BATCH_MODE=NO`. (39253613)

### Known Issues

- If you indirectly modify a property using a nonmutating setter that’s defined in a protocol or extension on a class instance, the Swift compiler might miscompile it by releasing the instance after the getter is invoked. This might cause the program to crash or have unpredictable behavior at runtime. (45274900)

  For example:

  ```
  protocol SomeProtocol { }
  class SomeClass: SomeProtocol { }

  extension SomeProtocol {
      var someNonmutatingProperty: CGPoint {
          nonmutating set { _ = self }
          get { return .zero }
      }
  }

  // Might be miscompiled, deallocating SomeClass() too early.
  SomeClass().someNonmutatingProperty.x = 42
  ```

  **Workaround:** Break the operation up into multiple statements so that the get and set operations occur in different statements:

  ```
  let someObject = SomeClass()
  // First get the nonmutating property value.
  var temp = someObject.someNonmutatingProperty
  temp.x = 42
  // Then modify it.
  someObject.someNonmutatingProperty = temp
  ```

- Passing a let property of a generic class that has function type as an argument to another function or method may cause a compiler crash. (41056468)

  **Workaround:** Assign the property to a local variable, and pass the local variable as an argument instead.

  ```
  class A {
      let function: (B) -> B
  }

  func takeFunction(_: (Int) -> Int) {}

  func passFunction(from a: A) {
      // Reference to a.function as an argument here may crash
      // the compiler.
      takeFunction(a.function)

      // Workaround: assign to a local variable, and pass the
      // local variable instead.
      let function = a.function
      takeFunction(function)
  }
  ```

- The compiler may crash or miscompile when forming an array of heterogeneous class objects as an `AnyObject` array (42666956):

  ```
  func f(_: [AnyObject])
  f([NSObject.self, NSString.self]) // May crash or miscompile.
  ```

  **Workaround:** Individually assign the class objects to variables of type AnyObject, then form an array of those variables:

  ```
  let myNSObject: AnyObject = NSObject.self
  let myNSString: AnyObject = NSString.self

  f([myNSObject, myNSString])
  ```

- The Swift compiler may crash when trying to assign a super method reference to a variable of optional function type (43360405):

  ```
  class X: NSObject {
      var f: ((Any?) -> Bool)?
      func setF() {
          f = super.isEqual(to:) // May crash the compiler.
      }
  }
  ```

  **Workaround:** Assign the closure to a non-optional variable first, then assign the non-optional variable to the optional.

  ```
  class X: NSObject {
      var f: ((Any?) -> Bool)?

      func setF() {
          let f2: (Any?) -> Bool = super.isEqual(to:)
          // Work around compiler crash.
          f = f2
      }
  }
  ```

- Compilation might fail without displaying the errors responsible for the failure. For example, you might see the message “Command CompileSwiftSources failed with a nonzero exit code” without an accompanying failure reason. (43033749)

  **Workaround:** Disable batch mode by adding a user-defined build setting named `SWIFT_ENABLE_BATCH_MODE` and set it to `NO`.

- Invoking a mutating method that returns `Self` on a value of protocol type may cause the compiler to crash (43507711):

  ```
  protocol Example {
      mutating func test() -> Self
  }

  func foo(x: inout Example) {
      _ = x.test() // May crash the compiler.
  }
  ```

  **Workaround:** If possible, make the method non-mutating, or have the method return `Void` or the protocol type instead of `Self`:

  ```
  protocol Example {
      mutating func test() -> Example // Instead of Self.
  }

  func foo(x: inout Example) {
      _ = x.test()
  }
  ```

  If that isn’t possible, add a wrapper method in a protocol extension that invokes the `Self`-returning method and returns the protocol type:

  ```
  extension Example {
      mutating func testWorkaround() -> Example {
          return test()
      }
  }

  func foo(x: inout Example) {
      _ = x.testWorkaround() // Invoke testWorkaround instead of test to avoid compiler crash.
  }
  ```

#### Resolved Issues

- An Objective-C method that takes a block argument annotated with `__attribute__((noescape))` invoked by Swift, no longer raises an incorrect “closure argument passed as `@noescape` to Objective-C has escaped” runtime error. (40857699)

- The Swift REPL shipped in the Command Line Tools package now successfully imports Objective-C frameworks or Swift frameworks that depend on Objective-C frameworks. (40537961)

- Generic conversions to AnyHashable at runtime is improved. For example, creating a dictionary using the `init(uniqueKeysWithValues:)` initializer is more stable because the keys you pass are implicitly converted to AnyHashable using the improved conversion behavior. (40583597)

- When switching over an `@objc` enumeration, if the value is not one of the recognized cases and the switch does not have a default case, the program will trap at run time. (20420436)

- The Swift REPL now successfully imports frameworks. (40458863)

- Assigning between properties of a value of protocol type no longer raises in-out exclusivity errors in some circumstances. (39524104)

- The runtime stability of availability conditions (`if #available`) is improved. (41849700)

- A conditional conformance no longer implies conformances to any inherited protocols, unlike unconditional ones. This is because the optimal conditional requirements are likely to be different between the two protocols if the inherited protocol can use less restrictive requirements (SR-6569).

  For example:

  ```
  protocol Base {}
  protocol Sub: Base {}
  struct Generic {}

  extension Generic: Base where Param: Base {}
  extension Generic: Sub where Param: Sub {}
  ```

  The first extension has to exist, because the second one does not imply a conformance of `Generic` to `Base` (if it did, it would imply it with the same conditional requirements as the `Sub` conformance, that is, `Param: Sub`). This particularly affects hierarchies like Hashable`: `Equatable, and BidirectionalCollection`: `Collection, and helps achieve precision in the bounds of types conforming to them. (36499373)

- Properties in the header generated by the Swift compiler are now correctly annotated with OS availability information. (37090774)

- The compiler now correctly handles when a nested type in a Codable type has the same name as a property of the Codable type (SR-6569). (37570349)

- When a property satisfies a requirement in an `@objc` protocol, the selectors for its getter and setter are in all circumstances now inferred from the protocol requirement. (37363245)

- The compiler now correctly emits code that references the type metadata for a private or internal type that should not be accessible, e.g., because it’s from another module or (in non-WMO mode) source file. The `-emit-public-type-metadata-accessors` compiler flag that was used as a workaround will no longer be available. (39763787)

- An improved error message is displayed when you pass an optional value where a nonoptional value is required by context. The error message now presents a clear choice between different strategies for fixing the problem, describes what each strategy means, and provides Fix-it dialogs to repair your code. (42081852)

  For example:

  ```
  error: value of optional type 'X?' must be unwrapped to a value
  of type 'X'
  f(x)
    ^
  note: coalesce using '??' to provide a default when the optional value
  contains 'nil'
    f(x)
      ^
       ?? default value
  note: force-unwrap using '!' to abort execution if the optional value
  contains 'nil'
    f(x)
      ^
       !
  ```

  When accessing a member of an optional value, the Fix-it dialog includes optional chaining as a potential solution:

  ```
  error: value of optional type 'X?' must be unwrapped to refer to
  member 'f' of wrapped base type 'X'
    let _: Int = x.f()
                 ^
  note: chain the optional using '?' to access member 'f'
  only for non-'nil' base values
    let _: Int = x.f()
                 ^
                  ?
  note: force-unwrap using '!' to abort execution if the optional
  value contains 'nil'
    let _: Int = x.f()
                 ^
                  !
  ```

- The os_signpost(_:dso:log:name:signpostID:) and os_log(_:dso:log:type:_:) functions have been updated to not have a labeled `type` parameter. (40528229)

- The zero property on UIEdgeInsets can now be used. (40735990)

- When a Swift method is exposed to Objective-C with a custom selector beginning with “new”, “copy”, or “mutableCopy”, it will correctly return an owned (+1) value rather than an autoreleased (+0) one when called from Objective-C, as expected by Objective-C ARC. (SR-6065\](https://bugs.swift.org/browse/SR-6065) (34834291)

- The Bundle initializer init(for:) now returns the correct bundle when used on a class that inherits from a generic class. (40367300)

- The type(of:) function now provides the expected result when object is being observed using key-value observing. (37319860)

### Swift Language

#### New Features

- Custom compile-time warnings or error messages can be emitted using the `#warning(_:)` and `#error(_:)` directives (SE-0196). (16015824)

  ```
  #warning("This code is incomplete.")

  #if BUILD_CONFIG && OTHER_BUILD_CONFIG
        #error("BUILD_CONFIG and OTHER_BUILD_CONFIG can't both be set")
  #endif
  ```

- Public classes may now have internal required initializers. The rule for required initializers is that they must be available everywhere the class can be subclassed, but previously required initializers on public classes were forced to be public themselves. This limitation was a holdover from before the introduction of the `open`-`public` distinction in Swift 3. (22845087)

- As part of fully implementing SE-0054, `ImplicitlyUnwrappedOptional` is now an unavailable typealias of Optional``. Declarations annotated with ‘`!`’ have the type Optional``. If an expression involving one of these values will not compile successfully with the type Optional``, it is implicitly unwrapped, producing a value of type `T`. In some cases this will cause code that previously compiled to require updating. For more information, see Reimplementation of Implicitly Unwrapped Optionals. (33272674)

- The new CaseIterable protocol describes types which have a static allCases property that’s used to describe all of the cases of the type. Swift synthesizes the allCases property for enumerations that have no associated values. (SE-0194) (17102392).

  For example:

  ```
  enum Suit: CaseIterable {
      case spade
      case heart
      case diamond
      case club
  }

  print(Suit.allCases)
  // prints [Suit.heart, Suit.club, Suit.diamond, Suit.spade]
  ```

- Various function-like declarations can now be marked as `@inlinable`, making their bodies available for optimizations from other modules. Inlinable function bodies must only reference public declarations, unless the referenced declaration is marked as `@usableFromInline` (SE-0193). (40566899)

  Note that the presence of the attribute itself does not force inlining or any other optimization to be performed, nor does it have any effect on optimizations performed within a single module.

#### Resolved Issues

- Protocol conformances are now able to be synthesized in extensions in the same file as the type definition, allowing automatic synthesis of conditional conformances to Hashable, Equatable and Codable. For instance, if there is a generic wrapper type that can only be Equatable when its wrapped type is also Equatable, the `==` method can be automatically constructed by the compiler:

  ```
  struct Generic {
      var property: Param
  }

  extension Generic: Equatable where Param: Equatable {}
  // Automatically synthesized inside the extension:
  // static func ==(lhs: Generic, rhs: Generic) -> Bool {
  //     return lhs.property == rhs.property
  // }
  ```

  Code that wants to be as precise as possible should generally not conditionally conform to Codable directly, but rather its two constituent protocols Encodable and Decodable, or else one can only (for instance) decode a `Generic` if `Param` is Encodable in addition to Decodable, even though Encodable is likely not required:

  ```
  // Unnecessarily restrictive:
  extension Generic: Codable where Param: Codable {}

  // More precise:
  extension Generic: Encodable where Param: Encodable {}
  extension Generic: Decodable where Param: Decodable {}
  ```

  Finally, due to Decodable having an initializer requirement, it’s not possible to conform to Decodable in an extension to a class that isn’t `final`. Such a class needs to have any initializers from protocols be `required`, which means they need to be in the class definition. (SR-6803) (39199726)

- Runtime query of conditional conformances is now implemented. Therefore, a dynamic cast such as `value as? P`, where the dynamic type of value conditionally conforms to `P`, will succeed when the conditional requirements are met. (SE-0143) (40349058)

  ```
  protocol P {}

  struct DoesntConform {}
  struct Conforms: P {}

  struct Generic {}
  extension Generic: P where Param: P {}

  print(Generic() as? P) // nil
  print(Generic() as? P)
  // Optional(main.Generic())
  ```

### Swift Migrator

#### Resolved Issues

- The Swift 4.2 migrator correctly updates member variable references to global variable references. (41658300)

### Swift Package Manager

#### New Features

- The `generate-xcodeproj` command has a new `--watch` option to watch the file system and automatically regenerate the Xcode project if needed. (32390792)

- The `swiftLanguageVersions` property in the PackageDescription manifest API for tools version 4.2 is changed from an array of integers to an array of `SwiftVersion` enumeration cases. (SE-0209) (38721967) For example:

  ```
  // swift-tools-version:4.2
  import PackageDescription

  let package = Package(
      // ...
      swiftLanguageVersions: [.v3, .v4]
  )
  ```

- The package manager now supports declaring a dependency on a package using its path on disk instead of the Git URL. This requires updating the package’s tools version to 4.2. (39418745)

- The scheme generation logic is improved and generates schemes as follows: One scheme contains all regular and test targets of the root package; One scheme per executable target containing the test targets whose dependencies intersect with the dependencies of the exectuable target. (30955712).

- The PackageDescription API in tools version 4.2 supports a new type of target called a “system library target”, which moves the current system-module packages feature from package to target level. (39418939)

- Swift targets are now compiled using batch mode. (39262812)

- The package manager emits deprecation notices for manifests that use the version 3 API in a package dependency graph. (41792011)

#### Known Issues

- The package manager might crash if a package graph contains shared dependencies with versioned and revision based requirements. Consider the following example package graph:

  ```
  Root package:
      PackageA@branch
  PackageA:
      PackageB@branch
      PackageC@branch
  PackageB:
      PackageC@1.0.0..

  According to the package manager’s dependency resolution rules, this should resolve to: PackageA @ branch, PackageB @ branch and PackageC @ branch. However, since the shared dependency PackageC is referenced with a `1.0.0..Swift Standard Library

#### New Features

- Range is now conditionally a RandomAccessCollection when its `Bound` is `Strideable` with a SignedInteger stride. This means that you can now use use Range as a collection when these criteria are met. (40564272)

  CountableRange is now a constrained generic type alias for a Range, rather than an independent type. This means that you can still use CountableRange in the same ways as before: extend it, take it as an argument to a function, or declare a variable of that type. But you can also now use ranges and countable ranges interchangeably:

  ```
  let countableRange: CountableRange = 0..(_ countableRange: CountableRange) { }
  f(range)
  ```

  ClosedRange and CountableClosedRange have the same behavior as Range and CountableRange, respectively.

- The standard library types Optional, Array, ArraySlice, ContiguousArray, Dictionary, `DictionaryLiteral`, Range, and ClosedRange now conform to the Hashable protocol when their element or bound types (as the case may be) conform to AnyHashable. This makes synthesized Hashable implementations available for types that include stored properties of these types. (SE-0143, 40567748)

- The standard library now uses a high-quality, randomly seeded, universal hash function, represented by the new Hasher struct. Random seeding varies the result of hashValue on each execution of a program, improving the reliability of the standard library’s hashed collections, Set and Dictionary. In particular, random seeding enables better protection against (accidental or deliberate) hash-flooding attacks.

  As a consequence of random seeding, the elements in sets and dictionaries may have a different order on each execution. This may expose some bugs in your existing code that accidentally relies on repeatable ordering.

  Additionally, the Hashable protocol now includes an extra function requirement, hash(into:). The new requirement is designed to be much easier to implement than the old hashValue property, and it generally provides better hashing. To implement hash(into:), feed the exact same components of your type that you compare in the Equatable protocol’s `==` implementation to the supplied Hasher:

  ```
  struct Foo: Hashable {
      var a: String?
      var b: [Int]
      var c: [String: Int]

      static func ==(lhs: Foo, rhs: Foo) -> Bool {
          return lhs.a == rhs.a && lhs.b == rhs.b && lhs.c == rhs.c
      }

      func hash(into hasher: inout Hasher) {
          hasher.combine(a)
          hasher.combine(b)
          hasher.combine(c)
      }
  }
  ```

  Automatic synthesis for Hashable (SE-0185) has been updated to generate hash(into:) implementations. For example, the `==` and hash(into:) implementations above are equivalent to the ones synthesized by the compiler, and can be removed without changing the meaning of the code.

  Synthesis has also been extended to support deriving hashValue from hash(into:), and vice versa. Therefore, code that only implements hashValue continues to work in Swift 4.2. This new compiler functionality works for all types that can implement Hashable, including classes.

  Note that these changes don’t affect Foundation’s hashing interface. Classes that subclass NSObject should override the hash property, like before.

  In certain controlled environments, such as while running particular tests, it may be helpful to selectively disable hash seed randomization, so that hash values and the order of elements in set and dictionary values remain consistent across executions. You can disable hash seed randomization by defining the environment variable `SWIFT_DETERMINISTIC_HASHING` with the value of 1. The Swift runtime looks at this variable during process startup and, if it’s defined, replaces the random seed with a constant value. (SE-0206) (35052153)

- The standard library now has a random generator API. The Swift standard library now supports generating and using random numbers. Swift collections now support shuffle() and shuffled() operations as well as choosing a randomElement(). Numeric types can now generate a uniform value in a range, for example: `Int.random(in: 1...10)` or `Double.random(in: 0..Bool provides a random `true` or `false` method: random().

  The RandomNumberGenerator protocol has been introduced as a source of randomness to drive these methods, with a default implementation for each platform. This implementation wraps `arc4random_buf(_:_:)`. (40564129)

- `Random.default` is renamed SystemRandomNumberGenerator to avoid misuse and to conform to naming guidelines. For more information, see the amendment in SE-202. (42298827)

#### Resolved Issues

- The behavior of the description and debugDescription properties for floating-point numbers use a new algorithm that is both more accurate and significantly faster than the previous code. In particular, it’s now guaranteed that `Double(String(d)) == d` for every Double value `d`. Previously these unconditionally printed a fixed number of decimal digits (15 and 17 for Double, respectively). They now print exactly as many digits as are needed for the resulting string to convert back to the original source value, and no more (SR-106). (40565639)

## See Also

### Release Notes

Build System Release Notes for Xcode 10

Update your apps to use new features, and test your apps against changes.

Interface Builder Release Notes for Xcode 10

Update your apps to use new features, and test your apps against changes.

Source Editor Release Notes for Xcode 10

Update your programming workflow to use new features, and test your workflow against changes.

