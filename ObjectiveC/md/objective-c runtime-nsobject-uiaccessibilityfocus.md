

- Objective-C Runtime
- NSObject
-  UIAccessibilityFocus 

API Collection

# UIAccessibilityFocus

An informal protocol that provides a way to determine whether an assistive app, such as VoiceOver, has focus on an accessible element.

## Overview

VoiceOver and other assistive technologies place a virtual focus on elements, which allows users to inspect an element without activating it. If you know the current location of the virtual focus, you can optimize the user experience for assistive technology users. For example, if your application expects people to tap once to select an object and then double-tap to activate it, VoiceOver users must make an extra tap to focus VoiceOver on the object before tapping to select it. To improve the VoiceOver user’s experience, you can move selection to an element at the same time VoiceOver focuses on the element. In this way, the user can activate the element without having to tap again to select the element.

## Topics

### Getting focus information

func accessibilityElementDidBecomeFocused()

Sent after an assistive technology has set its virtual focus on the accessibility element.

func accessibilityElementDidLoseFocus()

Sent after an assistive technology has removed its virtual focus from an accessibility element.

func accessibilityElementIsFocused() -> Bool

Returns a Boolean value indicating whether an assistive technology is focused on the accessibility element.

func accessibilityAssistiveTechnologyFocusedIdentifiers() -> Set&lt;UIAccessibility.AssistiveTechnologyIdentifier>?

Returns a set of identifier keys indicating which assistive app has focus on the accessibility element.

## See Also

### Related Documentation

Accessibility Programming Guide for iOS

### Improving Accessibility

UIAccessibility

A set of methods that provides accessibility information about views and controls in an app’s user interface.

UIAccessibilityContainer

Provide a set of methods that view subclasses use to make subcomponents accessible as separate elements.

UIAccessibilityAction

A set of methods that accessibility elements can use to support specific actions.

UIAccessibilityDragging

A pair of properties to allow you to fine-tune how drags and drops are exposed to assistive technologies.

