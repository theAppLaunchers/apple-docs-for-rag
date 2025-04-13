

- SwiftUI
-  ToolbarPlacement 

Structure

# ToolbarPlacement

The placement of a toolbar.

iOS 16.0+iPadOS 16.0+Mac Catalyst 16.0+macOS 13.0+tvOS 16.0+visionOS 1.0+watchOS 9.0+

``` source
struct ToolbarPlacement
```

## Overview

Use this type in conjunction with modifiers like toolbarBackground(_:for:) and toolbar(_:for:) to customize the appearance of different bars managed by SwiftUI. Not all bars support all types of customizations.

See ToolbarItemPlacement to learn about the different regions of these toolbars that you can place your own controls into.

## Topics

### Getting placements

static var automatic: ToolbarPlacement

The primary toolbar.

static func accessoryBar&lt;ID>(id: ID) -> ToolbarPlacement

Creates a unique accessory bar placement.

static var bottomBar: ToolbarPlacement

The bottom toolbar of an app.

static var bottomOrnament: ToolbarPlacement

The bottom ornament of an app.

static var navigationBar: ToolbarPlacement

The navigation bar of an app.

static var tabBar: ToolbarPlacement

The tab bar of an app.

static var windowToolbar: ToolbarPlacement

The placement for the containing window’s toolbar, sometimes referred to as the titlebar.

### Deprecated symbols

init&lt;ID>(id: ID)

Creates a custom accessory bar placement.

Deprecated

## See Also

### Setting toolbar visibility

func toolbar(Visibility, for: ToolbarPlacement...) -> some View

Specifies the visibility of a bar managed by SwiftUI.

func toolbarVisibility(Visibility, for: ToolbarPlacement...) -> some View

Specifies the visibility of a bar managed by SwiftUI.

func toolbarBackgroundVisibility(Visibility, for: ToolbarPlacement...) -> some View

Specifies the preferred visibility of backgrounds on a bar managed by SwiftUI.

