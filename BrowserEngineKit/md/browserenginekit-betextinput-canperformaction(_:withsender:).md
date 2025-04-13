

- BrowserEngineKit
- BETextInput
-  canPerformAction(\_:withSender:) 

Instance Method

# canPerformAction(\_:withSender:)

Returns whether text related actions, such those included in UIResponderStandardEditActions, can be handled

iOS 17.4+iPadOS 17.4+tvOS 17.4+visionOS 1.1+

``` source
func canPerformAction(
    _ action: Selector,
    withSender sender: Any?
) -> Bool
```

**Required**

## Parameters 

`action`  

The method selector for the action method.

`sender`  

The object that’s sending the message.

## Return Value

A Boolean value that indicates whether the text view can handle the action message.

## Mentioned in 

Supporting extended text interactions

Integrating custom browser text views with UIKit

## Discussion

Indicates whether the text view can process a given action.

## Overview

This method is similar to responds(to:), except that even if your text view implements the action message, it can decline to handle it by returning `false` from this method.

## See Also

### Updating the text system

var asyncInputDelegate: (any BETextInputDelegate)?

A system-provided input delegate is assigned when the system is interested in input changes.

**Required**

