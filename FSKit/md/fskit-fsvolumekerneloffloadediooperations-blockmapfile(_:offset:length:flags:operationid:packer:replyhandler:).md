

- FSKit
- FSVolumeKernelOffloadedIOOperations
-  blockmapFile(\_:offset:length:flags:operationID:packer:replyHandler:) 

Instance Method

# blockmapFile(\_:offset:length:flags:operationID:packer:replyHandler:)

Maps a file’s disk space into extents, allowing the kernel to perform I/O with that space.

macOS 15.4+

``` source
func blockmapFile(
    _ file: FSItem,
    offset: off_t,
    length: Int,
    flags: FSBlockmapFlags,
    operationID: FSOperationID,
    packer: FSExtentPacker,
    replyHandler reply: @escaping ((any Error)?) -> Void
)
```

``` source
func blockmapFile(
    _ file: FSItem,
    offset: off_t,
    length: Int,
    flags: FSBlockmapFlags,
    operationID: FSOperationID,
    packer: FSExtentPacker
) async throws
```

**Required**

## Parameters 

`file`  

The file for which to map disk space.

`offset`  

The starting logical offset of the range to be mapped (in bytes).

`length`  

The length of the range to be mapped (in bytes).

`flags`  

Flags that affect the behavior of the blockmap operation.

`operationID`  

A unique identifier of the blockmap call. Any value other than `0` (Objective-C) or unspecified (Swift) indicates the beginning of an I/O operation. A value of `0` or unspecified indicates the kernel maps the file without performing I/O. In this case, FSKit doesn’t perform a corresponding call to completeIO(for:offset:length:status:flags:operationID:replyHandler:).

`packer`  

An extent packer you use to pack the requested range of the file’s allocated disk space. FSKit sends all of the packed extents to the kernel when it invokes `reply`.

`reply`  

A block or closure to indicate success or failure. If mapping fails, pass an error as the one parameter to the reply handler. If mapping succeeds, pass `nil`. For an `async` Swift implementation, there’s no reply handler; simply throw an error or return normally.

## Discussion

FSKit calls this method when the kernel needs to get a mapping of logical-to-physical offsets of the file’s data. This call may occur as part of an I/O operation on the file, or just to get the mapping as part of a `fcntl(F_LOG2PHYS)` system call. In the case of an I/O operation on the file, `operationID` has a nonzero value; a future call to completeIO(for:offset:length:status:flags:operationID:replyHandler:) uses the same `operationID` to indicate which operation it completes. In the case of a `fcntl(F_LOG2PHYS)` system call, the `operationID` parameter is `0` (Objective-C) or unspecified (Swift). In both cases the kernel retains the mapping, and it may perform I/O to this range (or a part of it) at any time.

If satisfying a blockmap request requires more extents than `packer` can handle, FSKit makes additional calls to this method with the same operation ID to collect the remainder.

## See Also

### Performing mapped I/O

struct FSBlockmapFlags

Flags that describe the behavior of a blockmap operation.

func completeIO(for: FSItem, offset: off_t, length: Int, status: any Error, flags: FSCompleteIOFlags, operationID: FSOperationID, replyHandler: ((any Error)?) -> Void)

Completes an I/O operation for a given file.

**Required**

struct FSCompleteIOFlags

Flags that describe the behavior of an I/O completion operation.

