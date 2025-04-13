

- Security
-  SSLGetDiffieHellmanParams(\_:\_:\_:) Deprecated

Function

# SSLGetDiffieHellmanParams(\_:\_:\_:)

Retrieves the Diffie-Hellman parameters for a given context.

macOS 10.2–10.15Deprecated

``` source
func SSLGetDiffieHellmanParams(
    _ context: SSLContext,
    _ dhParams: UnsafeMutablePointer,
    _ dhParamsLen: UnsafeMutablePointer
) -> OSStatus
```

Deprecated

No longer supported. Use Network.framework.

## Parameters 

`context`  

An SSL session context reference.

`dhParams`  

On return, points to a buffer containing the Diffie-Hellman parameter block in Open SSL DER format.The returned data is not copied and belongs to the SSL session context reference; therefore, you cannot modify the data and it is released automatically when you dispose of the context.

`dhParamsLen`  

On return, points to the length of the buffer pointed to by the `dhParams` parameter.

## Return Value

A result code. See Secure Transport Result Codes.

## Discussion

This function returns the parameter block specified in an earlier call to the SSLSetDiffieHellmanParams(_:_:_:) function. If that function was never called, the `dhParams` parameter returns `NULL` and the `dhParamsLen` parameter returns `0`.

