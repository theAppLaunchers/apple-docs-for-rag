

- Virtualization
- VZError
-  internalError 

Type Property

# internalError

An internal error occurred.

macOS 11.0+

``` source
static var internalError: VZError.Code { get }
```

## Discussion

The system reports this error when the virtual machine unexpectedly stops.

## See Also

### Getting the error codes

static var invalidVirtualMachineConfiguration: VZError.Code

An invalid configuration error.

static var invalidVirtualMachineState: VZError.Code

An invalid state error.

static var invalidVirtualMachineStateTransition: VZError.Code

An invalid state transition error.

static var invalidDiskImage: VZError.Code

An invalid disk-image error.

static var networkError: VZError.Code

A network error, such as a failed connection.

static var notSupported: VZError.Code

The operation isn’t supported.

static var outOfDiskSpace: VZError.Code

The host is out of disk space.

static var operationCancelled: VZError.Code

The user canceled the installation of Rosetta or the app canceled the installation of a guest OS.

static var installationFailed: VZError.Code

An error occurred during installation.

static var installationRequiresUpdate: VZError.Code

The framework canceled the installation because the host requires a software update in order to complete the installation.

static var invalidRestoreImage: VZError.Code

The restore image is invalid.

static var invalidRestoreImageCatalog: VZError.Code

The restore image catalog is invalid.

static var noSupportedRestoreImagesInCatalog: VZError.Code

The restore image catalog has no supported restore images.

static var restoreImageCatalogLoadFailed: VZError.Code

The restore image catalog failed to load.

static var restoreImageLoadFailed: VZError.Code

The restore image failed to load.

