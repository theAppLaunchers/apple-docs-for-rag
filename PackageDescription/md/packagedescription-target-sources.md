

- PackageDescription
- Target
-  sources 

Instance Property

# sources

The source files in this target.

``` source
final var sources: [String]?
```

## Discussion

If this property is `nil`, Swift Package Manager includes all valid source files in the target’s path and treats specified paths as relative to the target’s path.

A path can be a path to a directory or an individual source file. In case of a directory, Swift Package Manager searches for valid source files recursively inside it.

## See Also

### Configuring File Locations

var path: String?

The path of the target, relative to the package root.

var exclude: [String]

The paths to source and resource files that you don’t want to include in the target.

var resources: [Resource]?

The explicit list of resource files in the target.

struct Resource

A resource to bundle with the Swift package.

var publicHeadersPath: String?

The path to the directory that contains public headers of a C-family target.

