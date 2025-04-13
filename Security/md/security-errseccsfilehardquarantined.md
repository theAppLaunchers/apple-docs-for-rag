

- Security
-  errSecCSFileHardQuarantined 

Global Variable

# errSecCSFileHardQuarantined

File open or execution not allowed.

Mac Catalyst 13.0+macOS 10.0+

``` source
var errSecCSFileHardQuarantined: OSStatus { get }
```

## Discussion

File has quarantine flags indicating that it should not be opened or executed under any circumstances. This usually occurs because the file was downloaded by a sandboxed application that does not have file download entitlements.

