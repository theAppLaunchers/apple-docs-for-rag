

- Core Foundation
-  kCFStreamErrorDomainSOCKS 

Global Variable

# kCFStreamErrorDomainSOCKS

The error code is a SOCKS proxy error.

iOS 2.0+iPadOS 2.0+Mac Catalyst 13.1+macOS 10.0+tvOSvisionOS 1.0+watchOS 2.0+

``` source
let kCFStreamErrorDomainSOCKS: Int32
```

## See Also

### Constants

let kCFStreamErrorDomainNetDB: Int32

The error code is an error code defined in \`netdb.h\`.

let kCFStreamErrorDomainNetServices: Int32

The error code is a \`CFNetService\` error code. For details, see the \[\`CFNetServicesError\`\](doc://com.apple.cfnetwork/documentation/CFNetwork/CFNetServicesError) enumeration.

let kCFStreamErrorDomainMach: Int32

The error code is a Mach error code defined in \`mach/error.h\`.

let kCFStreamErrorDomainFTP: Int32

The error code is an FTP error code.

let kCFStreamErrorDomainHTTP: Int32

The error code is an HTTP error code.

let kCFStreamErrorDomainSystemConfiguration: Int32

The error code is a system configuration error code as defined in \`System/ConfigurationSystemConfiguration.h\`.

let kCFStreamErrorDomainWinSock: CFIndex

When running CFNetwork code on Windows, this domain returns error codes associated with the underlying TCP/IP stack. You should also note that non-networking errors such as \`ENOMEM\` are delivered through the POSIX domain. See the header \`winsock2.h\` for relevant error codes.

let kCFStreamErrorDomainSSL: Int32

The error code is an SSL error code as defined in `Security/SecureTransport.h`.

