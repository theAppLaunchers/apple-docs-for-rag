

- PackageDescription
- Target
-  target(name:dependencies:path:exclude:sources:resources:publicHeadersPath:cSettings:cxxSettings:swiftSettings:linkerSettings:plugins:) 

Type Method

# target(name:dependencies:path:exclude:sources:resources:publicHeadersPath:cSettings:cxxSettings:swiftSettings:linkerSettings:plugins:)

Creates a regular target.

``` source
static func target(
    name: String,
    dependencies: [Target.Dependency] = [],
    path: String? = nil,
    exclude: [String] = [],
    sources: [String]? = nil,
    resources: [Resource]? = nil,
    publicHeadersPath: String? = nil,
    cSettings: [CSetting]? = nil,
    cxxSettings: [CXXSetting]? = nil,
    swiftSettings: [SwiftSetting]? = nil,
    linkerSettings: [LinkerSetting]? = nil,
    plugins: [Target.PluginUsage]? = nil
) -> Target
```

## Parameters 

`name`  

The name of the target.

`dependencies`  

The dependencies of the target. A dependency can be another target in the package or a product from a package dependency.

`path`  

The custom path for the target. By default, the Swift Package Manager requires a target’s sources to reside at predefined search paths; for example, `[PackageRoot]/Sources/[TargetName]`. Don’t escape the package root; for example, values like `../Foo` or `/Foo` are invalid.

`exclude`  

A list of paths to files or directories that the Swift Package Manager shouldn’t consider to be source or resource files. A path is relative to the target’s directory. This parameter has precedence over the sources parameter.

`sources`  

An explicit list of source files. If you provide a path to a directory, the Swift Package Manager searches for valid source files recursively.

`resources`  

An explicit list of resources files.

`publicHeadersPath`  

The directory containing public headers of a C-family library target.

`cSettings`  

The C settings for this target.

`cxxSettings`  

The C++ settings for this target.

`swiftSettings`  

The Swift settings for this target.

`linkerSettings`  

The linker settings for this target.

`plugins`  

The plug-ins used by this target.

## Discussion

A target can contain either Swift or C-family source files, but not both. It contains code that is built as a regular module that can be included in a library or executable product, but that cannot itself be used as the main target of an executable product.

