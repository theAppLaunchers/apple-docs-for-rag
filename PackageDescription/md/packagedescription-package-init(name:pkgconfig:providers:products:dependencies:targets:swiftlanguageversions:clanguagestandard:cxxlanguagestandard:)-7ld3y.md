

- PackageDescription
- Package
-  init(name:pkgConfig:providers:products:dependencies:targets:swiftLanguageVersions:cLanguageStandard:cxxLanguageStandard:) 

Initializer

# init(name:pkgConfig:providers:products:dependencies:targets:swiftLanguageVersions:cLanguageStandard:cxxLanguageStandard:)

Initializes a Swift package with configuration options you provide.

``` source
init(
    name: String,
    pkgConfig: String? = nil,
    providers: [SystemPackageProvider]? = nil,
    products: [Product] = [],
    dependencies: [Package.Dependency] = [],
    targets: [Target] = [],
    swiftLanguageVersions: [Int]? = nil,
    cLanguageStandard: CLanguageStandard? = nil,
    cxxLanguageStandard: CXXLanguageStandard? = nil
)
```

## Parameters 

`name`  

The name of the Swift package, or `nil`, if you want the Swift Package Manager to deduce the name from the package’s Git URL.

`pkgConfig`  

The name to use for C modules. If present, the Swift Package Manager searches for a `.pc` file to get the additional flags required for a system target.

`providers`  

The package providers for a system package.

`products`  

The list of products that this package vends and that clients can use.

`dependencies`  

The list of package dependencies.

`targets`  

The list of targets that are part of this package.

`swiftLanguageVersions`  

The list of Swift versions that this package is compatible with.

`cLanguageStandard`  

The C language standard to use for all C targets in this package.

`cxxLanguageStandard`  

The C++ language standard to use for all C++ targets in this package.

