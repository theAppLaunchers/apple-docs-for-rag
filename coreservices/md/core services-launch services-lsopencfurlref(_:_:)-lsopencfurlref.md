

- Core Services
- Launch Services
-  LSOpenCFURLRef(\_:\_:) 

Function

# LSOpenCFURLRef(\_:\_:)

Opens an item for a URL in the default manner in its preferred app.

macOS 10.0+

``` source
func LSOpenCFURLRef(
    _ inURL: CFURL,
    _ outLaunchedURL: UnsafeMutablePointer?>?
) -> OSStatus
```

## Parameters 

`inURL`  

A Core Foundation URL reference designating the item to open; see the *CFURL Reference* in the Core Foundation Reference Documentation for a description of the `CFURLRef` data type.

`outLaunchedURL`  

A pointer to a Core Foundation URL reference that, on return, will identify the app launched. Pass `NULL` if this information is unimportant.

Despite the absence of the word `Copy` in its name, this function retains the URL reference object on your behalf; you are responsible for releasing this object.

## Return Value

A result code; see Result Codes.

## Discussion

The designated item is opened in the default manner, as if it had been opened with the `LSOpenFromURLSpec` function with a launch specification specifying the launch flag `kLSLaunchDefaults`: that is, asynchronously, and with the remaining launch parameters taken from the application’s information property list. For greater control, call `LSOpenFromURLSpec` directly. See LSLaunchFlags for more information about launch flags.

If the item URL’s scheme is `file` (designating either a file or a directory), the selection of the preferred application is based on the designated item’s filename extension, file type, and creator signature; otherwise, it is based on the URL scheme (such as `http`, `ftp`, or `mailto`). The application is launched or activated, as required, and sent an appropriate Apple event depending on the circumstances:

- If the URL’s scheme is `file` and it designates a document, the document’s preferred application is launched (or activated if it is already running).

  - If the application claims to accept `file` URLs, it is sent a `'GURL'` (“get URL”) Apple event containing the item’s URL.

  - If the application does not claim to accept `file` URLs, it is sent an `'odoc'` (“open document”) Apple event identifying the document to open.

- If the URL’s scheme is `file` and it designates an application:

  - If the application is not already running, it is launched and sent an `'oapp'` (“open application”) Apple event.

  - If the application is already running, it is activated and sent an `'rapp'` (“reopen application”) Apple event.

- If the URL has a scheme other than `file`, the scheme’s preferred application is launched (or activated if it is already running) and sent a `'GURL'` (“get URL”) Apple event containing the item’s URL.

As of macOS 10.4 and later, launchApplication(at:options:configuration:) is the preferred way of opening a URL.

### Version-Notes

Thread-safe since Mac OS version 10.2.

## See Also

### Opening Items

func LSOpenFromURLSpec(UnsafePointer&lt;LSLaunchURLSpec>, UnsafeMutablePointer&lt;Unmanaged&lt;CFURL>?>?) -> OSStatus

Opens one or more items for a URL in the preferred apps or a designated app.

struct LSLaunchURLSpec

The specification for launching an app, opening items, or both, along with related information.

class LSSharedFileList

A persistent list of file-system objects.

class LSSharedFileListItem

A file-system object in the shared file list.

