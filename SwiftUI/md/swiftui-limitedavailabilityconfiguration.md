

- SwiftUI
-  LimitedAvailabilityConfiguration 

Structure

# LimitedAvailabilityConfiguration

A type-erased widget configuration.

iOS 16.1+iPadOS 16.1+Mac Catalyst 16.1+macOS 13.0+visionOS 1.0+watchOS 9.1+

``` source
@MainActor @frozen @preconcurrency
struct LimitedAvailabilityConfiguration
```

## Overview

You don’t use this type directly. Instead SwiftUI creates this type on your behalf.

## Relationships

### Conforms To

- WidgetConfiguration

## See Also

### Creating widgets

Building Widgets Using WidgetKit and SwiftUI

Create widgets to show your app’s content on the Home screen, with custom intents for user-customizable settings.

Creating a widget extension

Display your app’s content in a convenient, informative widget on various devices.

Keeping a widget up to date

Plan your widget’s timeline to show timely, relevant information using dynamic views, and update the timeline when things change.

Making a configurable widget

Give people the option to customize their widgets by adding a custom app intent to your project.

protocol Widget

The configuration and content of a widget to display on the Home screen or in Notification Center.

protocol WidgetBundle

A container used to expose multiple widgets from a single widget extension.

protocol WidgetConfiguration

A type that describes a widget’s content.

struct EmptyWidgetConfiguration

An empty widget configuration.

