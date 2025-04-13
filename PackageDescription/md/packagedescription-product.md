

- PackageDescription
-  Product 

Class

# Product

The object that defines a package product.

``` source
class Product
```

## Overview

A package product defines an externally visible build artifact that’s available to clients of a package. Swift Package Manager assembles the product from the build artifacts of one or more of the package’s targets. A package product can be one of three types:

Library  
Use a *library product* to vend library targets. This makes a target’s public APIs available to clients that integrate the Swift package.

Executable  
Use an *executable product* to vend an executable target. Use this only if you want to make the executable available to clients.

Plugin  
Use a *plugin product* to vend plugin targets. This makes the plugin available to clients that integrate the Swift package.

The following example shows a package manifest for a library called “Paper” that defines multiple products:

```
let package = Package(
    name: "Paper",
    products: [
        .executable(name: "tool", targets: ["tool"]),
        .library(name: "Paper", targets: ["Paper"]),
        .library(name: "PaperStatic", type: .static, targets: ["Paper"]),
        .library(name: "PaperDynamic", type: .dynamic, targets: ["Paper"]),
    ],
    dependencies: [
        .package(url: "http://example.com.com/ExamplePackage/ExamplePackage", from: "1.2.3"),
        .package(url: "http://some/other/lib", .exact("1.2.3")),
    ],
    targets: [
        .executableTarget(
            name: "tool",
            dependencies: [
                "Paper",
                "ExamplePackage"
            ]),
        .target(
            name: "Paper",
            dependencies: [
                "Basic",
                .target(name: "Utility"),
                .product(name: "AnotherExamplePackage"),
            ])
    ]
)
```

## Topics

### Creating a Library Product

static func library(name: String, type: Product.Library.LibraryType?, targets: [String]) -> Product

Creates a library product to allow clients that declare a dependency on this package to use the package’s functionality.

class Library

The library product of a Swift package.

### Creating an Executable Product

static func executable(name: String, targets: [String]) -> Product

Creates an executable package product.

class Executable

The executable product of a Swift package.

### Creating a Plugin Product

static func plugin(name: String, targets: [String]) -> Product

Defines a product that vends a package plugin target for use by clients of the package.

class Plugin

The plug-in product of a Swift package.

### Naming the product

let name: String

The name of the package product.

## Relationships

### Inherited By

- Product.Executable
- Product.Library
- Product.Plugin

## See Also

### Configuring Products

var products: [Product]

The list of products that this package vends and that clients can use.

