

- TipKit
- Tips
- Tips.ConfigurationOption
-  Tips.ConfigurationOption.CloudKitContainer 

Structure

# Tips.ConfigurationOption.CloudKitContainer

A type for specifying the CloudKit container used for syncing tips.

iOS 18.0+iPadOS 18.0+Mac Catalyst 18.0+macOS 15.0+tvOS 18.0+visionOS 2.0+watchOS 11.0+

``` source
struct CloudKitContainer
```

## Overview

For more information on CloudKit syncing, see cloudKitContainer(_:).

## Topics

### Type Properties

static var automatic: Tips.ConfigurationOption.CloudKitContainer

Syncs the TipKit datastore using the first container in your app’s entitlements with a “.tips” suffix or, if none is available, the primary container is used.

### Type Methods

static func named(String) -> Tips.ConfigurationOption.CloudKitContainer

Syncs the TipKit datastore using the specified CloudKit container.

## Relationships

### Conforms To

- Equatable
- Sendable

