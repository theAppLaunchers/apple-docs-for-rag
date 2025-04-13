

- PackageDescription
- Package
- Package.Dependency
-  package(name:url:from:) Deprecated

Type Method

# package(name:url:from:)

Adds a package dependency that uses the version requirement, starting with the given minimum version, going up to the next major version.

SwiftPM 5.2–5.6Deprecated

``` source
static func package(
    name: String,
    url: String,
    from version: Version
) -> Package.Dependency
```

Deprecated

use package(url:from:) instead

## Parameters 

`name`  

The name of the Swift package or `nil` to deduce the name from the package’s Git URL.

`url`  

The valid Git URL of the package.

`version`  

The minimum version requirement.

## Return Value

A `Package.Dependency` instance.

## Discussion

This is the recommended way to specify a remote package dependency. It allows you to specify the minimum version you require, allows updates that include bug fixes and backward-compatible feature updates, but requires you to explicitly update to a new major version of the dependency. This approach provides the maximum flexibility on which version to use, while making sure you don’t update to a version with breaking changes, and helps to prevent conflicts in your dependency graph.

The following example allows the Swift package manager to select a version like a `1.2.3`, `1.2.4`, or `1.3.0`, but not `2.0.0`.

```
.package(url: "https://example.com/example-package.git", from:
"1.2.3"),
```

