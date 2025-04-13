

- ManagedSettings
-  SafariSettings 

Structure

# SafariSettings

Constraints on Safari’s AutoFill and cookie behaviors.

iOS 15.0+iPadOS 15.0+Mac Catalyst 15.0+

``` source
struct SafariSettings
```

## Overview

Use `SafariSettings` to manage Safari settings for cookies and AutoFill. You can prevent AutoFill and specify the websites from which Safari accepts cookies.

## Topics

### Specifying a Cookie Policy

var cookiePolicy: SafariSettings.CookiePolicy?

Defines the conditions under which Safari accepts cookies.

static let cookiePolicy: SettingMetadata&lt;SafariSettings.CookiePolicy>

The metadata for the setting that configures Safari’s policy for cookies.

enum CookiePolicy

The conditions under which Safari accepts cookies.

### Denying AutoFill

var denyAutoFill: Bool?

A Boolean value that indicates whether Safari’s AutoFill feature is active.

static let denyAutoFill: SettingMetadata&lt;Bool>

The metadata associated with the setting that deactivates Safari’s AutoFill feature.

## Relationships

### Conforms To

- ManagedSettingsGroup

## See Also

### Restricting Web Content

var safari: SafariSettings

Settings that affect Safari’s search results and cookie policies.

var webContent: WebContentSettings

Settings that affect web content.

struct WebContentSettings

An object that configures which websites a user can access.

