

- PackageDescription
- Target
- Target.Dependency
-  product(name:package:) 

Type Method

# product(name:package:)

Creates a dependency on a product from a package dependency.

``` source
static func product(
    name: String,
    package: String? = nil
) -> Target.Dependency
```

## Parameters 

`name`  

The name of the product.

`package`  

The name of the package.

## Return Value

A `Target.Dependency` instance.

## See Also

### Creating a Target Dependency

static func product(name: String, package: String, condition: TargetDependencyCondition?) -> Target.Dependency

Creates a target dependency on a product from a package dependency.

Deprecated

static func product(name: String, package: String) -> Target.Dependency

Creates a dependency on a product from a package dependency.

Deprecated

static func product(name: String, package: String, moduleAliases: [String : String]?, condition: TargetDependencyCondition?) -> Target.Dependency

Creates a target dependency on a product from a package dependency.

static func target(name: String, condition: TargetDependencyCondition?) -> Target.Dependency

Creates a dependency on a target in the same package.

static func target(name: String) -> Target.Dependency

Creates a dependency on a target in the same package.

Deprecated

static func byName(name: String, condition: TargetDependencyCondition?) -> Target.Dependency

Creates a dependency that resolves to either a target or a product with the specified name.

static func byName(name: String) -> Target.Dependency

Creates a dependency that resolves to either a target or a product with the specified name.

Deprecated

struct TargetDependencyCondition

A condition that limits the application of a target’s dependency.

init(stringLiteral: String)

Creates a target dependency instance with the given value.

init(extendedGraphemeClusterLiteral: Self.StringLiteralType)

init(unicodeScalarLiteral: Self.ExtendedGraphemeClusterLiteralType)

