*   [Metal](/documentation/metal)
*   [MTLDevice](/documentation/metal/mtldevice)
*   makeIOHandle(url:compressionMethod:) Deprecated

Instance Method

# makeIOHandle(url:compressionMethod:)

Creates an input/output file handle instance that represents a compressed file at a URL.

iOS 16.0–17.0DeprecatediPadOS 16.0–17.0DeprecatedMac Catalyst 16.0–17.0DeprecatedmacOS 13.0–14.0DeprecatedtvOS 16.0–17.0DeprecatedvisionOS 1.0–1.0Deprecated

```swift
```swift
```swift
```swift
```swift
```swift
```swift
```swift
func makeIOHandle(
    url: [`URL`](/documentation/Foundation/URL),
    compressionMethod: [`MTLIOCompressionMethod`](/documentation/metal/mtliocompressionmethod)
) throws -> any [`MTLIOFileHandle`](/documentation/metal/mtliofilehandle)
```
```
```
```
```
```
```
```

**Required**

Deprecated

Use [`makeIOFileHandle(url:compressionMethod:)`](/documentation/metal/mtldevice/makeiofilehandle\(url:compressionmethod:\)) instead.

## [Parameters](/documentation/Metal/MTLDevice/makeIOHandle\(url:compressionMethod:\)#parameters)

`url`

A location URL to a compressed file in the file system.

`compressionMethod`

The file’s compression format.

## [Return Value](/documentation/Metal/MTLDevice/makeIOHandle\(url:compressionMethod:\)#return-value)

A new [`MTLIOFileHandle`](/documentation/metal/mtliofilehandle) instance if the method completes successfully; otherwise Swift throws an error and Objective-C returns `nil`.

## [Discussion](/documentation/Metal/MTLDevice/makeIOHandle\(url:compressionMethod:\)#discussion)

For information about using input/output command queues and file handles, see [Resource Loading](/documentation/metal/resource-loading).

## [See Also](/documentation/Metal/MTLDevice/makeIOHandle\(url:compressionMethod:\)#see-also)

### [Creating I/O File Handles](/documentation/Metal/MTLDevice/makeIOHandle\(url:compressionMethod:\)#Creating-IO-File-Handles)

```swift
```swift
```swift
```swift
func makeIOFileHandle(url: URL) throws -> any MTLIOFileHandle
```
```

Creates an input/output file handle instance that represents a file at a URL.

**Required**
```
```swift
```swift
```swift
func makeIOFileHandle(url: URL, compressionMethod: MTLIOCompressionMethod) throws -> any MTLIOFileHandle
```
```

Creates an input/output file handle instance that represents a compressed file at a URL.

**Required**
```
```swift
```swift
```swift
func makeIOHandle(url: URL) throws -> any MTLIOFileHandle
```
```

Creates an input/output file handle instance that represents a file at a URL.

**Required**

Deprecated
```
```