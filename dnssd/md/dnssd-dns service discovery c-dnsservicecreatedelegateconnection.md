

- dnssd
- DNS Service Discovery C
-  DNSServiceCreateDelegateConnection 

Article

# DNSServiceCreateDelegateConnection

Create a delegate connection to the daemon allowing efficient registration of multiple individual records.

## Overview

```
DNSServiceErrorType DNSServiceCreateDelegateConnection (
   DNSServiceRef *sdRef,
   int32_t pid,
   uuid_t uuid
);
```

## Parameters

**sdRef**

A pointer to an uninitialized DNSServiceRef. Deallocating the reference (via DNSServiceRefDeallocate()) severs the connection and deregisters all records registered on this connection.

**pid**

Process ID of the delegate

**uuid**

UUID of the delegate

Note that only one of the two arguments (pid or uuid) can be specified. If pid is zero, uuid will be assumed to be a valid value; otherwise pid will be used.

## Return Value

Returns kDNSServiceErr_NoError on success, otherwise returns an error code indicating the specific failure that occurred (in which case the DNSServiceRef is not initialized). kDNSServiceErr_NotAuth is returned to indicate that the calling process does not have entitlements to use this API.

## See Also

### TXT Record Parsing Functions

func DNSServiceSetDispatchQueue(DNSServiceRef!, dispatch_queue_t!) -> DNSServiceErrorType

Allows you to schedule a DNSServiceRef on a serial dispatch queue for receiving asynchronous callbacks.

func TXTRecordContainsKey(UInt16, UnsafeRawPointer!, UnsafePointer&lt;CChar>!) -> Int32

Allows you to determine if a given TXT Record contains a specified key.

func TXTRecordGetCount(UInt16, UnsafeRawPointer!) -> UInt16

Returns the number of keys stored in the TXT Record.

func TXTRecordGetItemAtIndex(UInt16, UnsafeRawPointer!, UInt16, UInt16, UnsafeMutablePointer&lt;CChar>!, UnsafeMutablePointer&lt;UInt8>!, UnsafeMutablePointer&lt;UnsafeRawPointer?>!) -> DNSServiceErrorType

Allows you to retrieve a key name and value pointer, given an index into a TXT Record.

func TXTRecordGetValuePtr(UInt16, UnsafeRawPointer!, UnsafePointer&lt;CChar>!, UnsafeMutablePointer&lt;UInt8>!) -> UnsafeRawPointer!

Allows you to retrieve the value for a given key from a TXT Record.

