

- Bundle Resources
- App Privacy Configuration
-  NSPrivacyTrackingDomains 

Property List Key

# NSPrivacyTrackingDomains

A list of the internet domains your app or third-party SDK uses for tracking.

iOS 17.0+iPadOS 17.0+Mac Catalyst 14.0+macOS 14.0+tvOS 17.0+visionOS 1.0+watchOS 10.0+

## Details 

Name  
Privacy Tracking Domains

Type  

array of strings

## Overview

If the user has not granted tracking permission through the App Tracking Transparency framework, network requests to these domains fail and your app receives an error.

## See Also

### Declaring tracking

NSPrivacyTracking

A Boolean value that indicates whether your app or third-party SDK uses data for tracking.

**Name:** Privacy Tracking Enabled

