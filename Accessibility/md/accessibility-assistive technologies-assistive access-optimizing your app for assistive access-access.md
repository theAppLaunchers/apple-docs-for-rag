

- Accessibility
- Assistive technologies
- Assistive Access
-  Optimizing your app for Assistive Access 

Article

# Optimizing your app for Assistive Access

Adjust your app’s UI to make sure it works well for people who use Assistive Access.

## Overview

In general, make sure your standard app UI works well for Assistive Access. However, you can make small adjustments to your UI to make sure it looks and works as you expect in Assistive Access. You can optimize your UI when Assistive Access is running in one of these ways:

- Opt in to full-screen mode to get more screen space for your UI

- Remove workflows or UI elements that aren’t appropriate in the context of Assistive Access

### Opt in to full-screen mode

Adding the UISupportsFullScreenInAssistiveAccess key to your app’s `Info.plist` file with a value of `YES` allows your app’s UI to expand into all the available space above the Back button in Assistive Access. It also lists your app as Optimized for Assistive Access in Settings, so that a trusted supporter configuring Assistive Access on someone’s behalf knows that your app’s UI is optimized for this feature.

If you add this key to your app’s `Info.plist`, ensure your UI is adaptive so that it works with flexible screen dimensions. Don’t rely on fixed screen sizes in your app design or logic. Use safe areas and layout guides to avoid overlapping your app’s UI with system UI or hardware elements. For more information, see safeAreaInsets and safeAreaLayoutGuide.

If you don’t add this key to your app’s `Info.plist`, a trusted supporter can still choose to make your app available in Assistive Access. By default, the system draws apps in a reduced frame to fit them onscreen with the prominent Back button in Assistive Access. This frame matches the dimensions of a smaller iPhone or iPad screen, so you don’t need to make changes to your existing UI for your app to work in Assistive Access.

### Remove unnecessary UI elements

It may not be possible for a person who’s using your app while Assistive Access is running to complete certain tasks or workflows, due to the differences described in Understand certain differences in Assistive Access on iPhone. In situations like this, you can make note of these differences when you test your app in Assistive Access, and remove workflows or UI elements that aren’t appropriate in the context of Assistive Access.

To make small adjustments to your UI in Assistive Access, you check whether Assistive Access is running on the device using SwiftUI or the Accessibility framework.

- SwiftUI
- Accessibility framework

```
import SwiftUI

@Environment(\.accessibilityAssistiveAccessEnabled) private var isAssistiveAccessEnabled

if isAssistiveAccessEnabled {
  // Assistive Access is on. Make small adjustments specific to Assistive Access.
}
```

```
import Accessibility

if AccessibilitySettings.isAssistiveAccessEnabled {
  // Assistive Access is on. Make small adjustments specific to Assistive Access.
} 
```

## See Also

#### Related reference

#### Related articles

#### Related design guidance

#### Related videos

Meet Assistive Access

