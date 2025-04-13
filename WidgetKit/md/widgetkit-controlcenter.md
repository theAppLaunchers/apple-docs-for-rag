

- WidgetKit
-  ControlCenter 

Class

# ControlCenter

An object that contains a list of user-configured controls and is used for reloading controls.

iOS 18.0+iPadOS 18.0+Mac Catalyst 18.0+

``` source
class ControlCenter
```

## Overview

ControlCenter provides information about user-configured controls, such as their push information. For controls that use doc:IntentConfigurableControl, you can retrieve the user-edited values.

### Getting Configured Control Information

To get a list of user-configured controls, use currentControls(). This property provides an array of ControlInfo objects containing the following information:

```
struct ControlInfo {
    public let kind: String
    public func configurationIntent(of intentType: Intent.Type = Intent.self) -> Intent?
    public var pushInfo: ControlPushInfo?
}
```

The `kind` string matches the parameter you use when defining the control type. If your control uses doc:IntentConfigurableControl, the `configurationIntent` function provides the custom intent containing the user-customized values for each individual control. If your control returns `true` for `supportsPushUpdates`, `pushInfo` will return the latest push info for this individual control.

### Requesting a Reload of Your Controls

Changes in your app’s state may affect a control’s state. When this happens, you can tell ControlCenter to reload the template for either a specific kind of control or all controls. For example, your user might press a button in your app that changes state shared by a control. The app should reload that control for its display to reflect the new state.

You do not need to reload controls in response to push notifications. The system will reload any controls configured for push notifications on your behalf.

If you only need to reload a certain kind of control, you can request a reload for only that kind. For example, in response to the user toggling an appliance on or off, you could request a reload for only the appliance widgets:

```
ControlCenter.shared.reloadControls(ofKind: "com.myhome.appliancepower")
```

To request a reload for all of your controls:

```
ControlCenter.shared.reloadAllControls()
```

## Topics

### Instance Methods

func currentControls() async throws -> [ControlInfo]

Retrieves information about user-configured controls.

func reloadAllControls()

Reloads the templates for all configured controls belonging to the containing app.

func reloadControls(ofKind: String)

Reloads the templates for all controls of a particular kind.

### Type Properties

static let shared: ControlCenter

## See Also

### Controls

Creating controls to perform actions across the system

Perform your app’s actions from Control Center, the Lock Screen, and the Action button.

Adding refinements and configuration to controls

Customize the way controls display across the system and offer people the ability to configure them.

struct ControlWidgetToggle

A control template representing a toggle.

struct ControlWidgetButton

A control template representing a button.

