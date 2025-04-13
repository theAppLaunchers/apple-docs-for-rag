

- Core Data
-  NSLightweightMigrationStage 

Class

# NSLightweightMigrationStage

An object that describes a series of models suitable for lightweight migration.

iOS 17.0+iPadOS 17.0+Mac Catalyst 17.0+macOS 14.0+tvOS 17.0+visionOS 1.0+watchOS 10.0+

``` source
class NSLightweightMigrationStage
```

## Overview

Use NSLightweightMigrationStage when you have a series of models to migrate and those models are compatible with lightweight migrations. Instances of this class supplement your custom migration stages and help maintain a consistent stage order for the entire migration.

## Topics

### Creating a migration stage

convenience init([String])

Creates a lightweight migration stage with the specified version checksums.

### Accessing the checksums

var versionChecksums: [String]

The array of version checksums.

## Relationships

### Inherits From

- NSMigrationStage

### Conforms To

- CVarArg
- CustomDebugStringConvertible
- CustomStringConvertible
- Equatable
- Hashable
- NSObjectProtocol

## See Also

### Migration stages

class NSCustomMigrationStage

An object that enables you to participate in the migration between two versions of the same model.

class NSMigrationStage

An abstract base class for describing an individual stage of a migration.

