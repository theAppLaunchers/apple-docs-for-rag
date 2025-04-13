

- CallKit
- CXErrorCodeCallDirectoryManagerError
-  noExtensionFound 

Type Property

# noExtensionFound

The call directory manager can’t find a corresponding app extension.

iOS 10.0+iPadOS 10.0+Mac Catalyst 10.0+visionOS 1.0+watchOS 9.0+

``` source
static var noExtensionFound: CXErrorCodeCallDirectoryManagerError.Code { get }
```

## See Also

### Constants

static var unknown: CXErrorCodeCallDirectoryManagerError.Code

An unknown error occurred.

static var currentlyLoading: CXErrorCodeCallDirectoryManagerError.Code

The call directory manager is loading the app extension.

static var loadingInterrupted: CXErrorCodeCallDirectoryManagerError.Code

The system interrupted the call directory manager while loading the app extension.

static var entriesOutOfOrder: CXErrorCodeCallDirectoryManagerError.Code

The entries in the call directory are out of order.

static var duplicateEntries: CXErrorCodeCallDirectoryManagerError.Code

There are duplicate entries in the call directory.

static var maximumEntriesExceeded: CXErrorCodeCallDirectoryManagerError.Code

There are too many entries in the call directory.

static var extensionDisabled: CXErrorCodeCallDirectoryManagerError.Code

The call directory extension isn’t in an enabled state.

static var unexpectedIncrementalRemoval: CXErrorCodeCallDirectoryManagerError.Code

A request occurred before confirming incremental loading.

