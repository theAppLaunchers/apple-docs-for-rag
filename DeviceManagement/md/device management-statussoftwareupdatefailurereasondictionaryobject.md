

- Device Management
-  StatusSoftwareUpdateFailureReasonDictionaryObject 

Object

# StatusSoftwareUpdateFailureReasonDictionaryObject

A dictionary that contains details about a software update failure.

iOS 17.0+iPadOS 17.0+macOS 14.0+tvOS 18.4+Device Assignment ServicesVPP License Management

``` source
object StatusSoftwareUpdateFailureReasonDictionaryObject
```

## Properties

`count`

`integer`

 (Required) 

The number of times the current software update failed. If there are no failures, or no pending software update, this is `0`.

`reason`

`string`

If present, this describes the reason for last software update failure. This key isn’t present if there are no failures or no pending software update.

`timestamp`

`string`

If present, this is the RFC 3339 timestamp of the last software update failure. This key isn’t present if there are no failures or no pending software update.

