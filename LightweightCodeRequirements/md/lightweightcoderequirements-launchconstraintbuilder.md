

- LightweightCodeRequirements
-  LaunchConstraintBuilder 

Structure

# LaunchConstraintBuilder

A custom parameter attribute that constructs launch constraints from closures.

iOS 17.4+iPadOS 17.4+Mac Catalyst 17.4+macOS 14.4+tvOS 17.4+visionOS 1.1+watchOS 10.4+

``` source
@resultBuilder
struct LaunchConstraintBuilder
```

## Topics

### Type Methods

static func buildBlock([any LaunchConstraint]...) -> [any LaunchConstraint]

Builds flat array from a variadic set of arrays

static func buildEither(first: [any LaunchConstraint]) -> [any LaunchConstraint]

Produces content for a conditional statement in a multi-statement closure when the condition is true

static func buildEither(second: [any LaunchConstraint]) -> [any LaunchConstraint]

Produces content for a conditional statement in a multi-statement closure when the condition is false

static func buildExpression(any LaunchConstraint) -> [any LaunchConstraint]

Builds an expression within the builder

static func buildExpression([any LaunchConstraint]) -> [any LaunchConstraint]

Builds an expression within the builder

static func buildOptional([any LaunchConstraint]?) -> [any LaunchConstraint]

Produces content for a conditional statement in a multi-statement closure when the condition is true and has no else option

## See Also

### Checking code requirements for launching processes

func SecCodeCheckValidityWithProcessRequirement(code: SecCode, flags: SecCSFlags, requirement: ProcessCodeRequirement) -> ValidationResult

Checks whether the code associated with a running process satisfies a lightweight code requirement.

var launchRequirement: LaunchCodeRequirement?

struct LaunchCodeRequirement

A lightweight code requirement that you use to evaluate the executable for a launching process.

func allOf(requirement: () -> [any LaunchConstraint]) -> any LaunchConstraint

Creates a constraint that requires a launching process’s executable to satisfy all of the provided constraints.

func anyOf(requirement: () -> [any LaunchConstraint]) -> any LaunchConstraint

Creates a constraint that requires a launching process’s executable to satisfy any of the provided constraints.

protocol LaunchConstraint

A protocol to which a lightweight code requirement constraint conforms if you can use it in launch code requirements.

