

- Core Services
- Apple Events
-  Timeout Constants 

# Timeout Constants

Specify a timeout value.

## Overview

Your application can use these constants when it calls the `AEInteractWithUser(_:_:_:)` function, or it can supply the specific amount of time (in ticks) that your handler is willing to wait for a response from the user. You can also use the constants with the `AESend(_:_:_:_:_:_:_:)` function.

## Topics

### Constants

var kAEDefaultTimeout: Int

The timeout value is determined by the Apple Event Manager. The default timeout value is about one minute.

var kNoTimeOut: Int

Your application is willing to wait indefinitely. Most commonly, you instead provide a timeout value (in ticks) that will provide a reasonable amount of time for the current operation.

