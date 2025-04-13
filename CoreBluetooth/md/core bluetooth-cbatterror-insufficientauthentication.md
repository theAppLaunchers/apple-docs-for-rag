

- Core Bluetooth
- CBATTError
-  insufficientAuthentication 

Type Property

# insufficientAuthentication

Reading or writing the attribute’s value failed for lack of authentication.

iOS 5.0+iPadOS 5.0+Mac Catalyst 13.0+macOS 10.10+tvOS 9.0+visionOS 1.0+watchOS 4.0+

``` source
static var insufficientAuthentication: CBATTError.Code { get }
```

## Discussion

This error indicates you must authenticate before reading or writing the attribute’s value.

## See Also

### Error Codes

static var success: CBATTError.Code

The ATT command or request successfully completed.

static var invalidHandle: CBATTError.Code

The attribute handle is invalid on this peripheral.

static var readNotPermitted: CBATTError.Code

The permissions prohibit reading the attribute’s value.

static var writeNotPermitted: CBATTError.Code

The permissions prohibit writing the attribute’s value.

static var invalidPdu: CBATTError.Code

The attribute Protocol Data Unit (PDU) is invalid.

static var requestNotSupported: CBATTError.Code

The attribute server doesn’t support the request received from the client.

static var invalidOffset: CBATTError.Code

The specified offset value was past the end of the attribute’s value.

static var insufficientAuthorization: CBATTError.Code

Reading or writing the attribute’s value failed for lack of authorization.

static var prepareQueueFull: CBATTError.Code

The prepare queue is full, as a result of there being too many write requests in the queue.

static var attributeNotFound: CBATTError.Code

The attribute wasn’t found within the specified attribute handle range.

static var attributeNotLong: CBATTError.Code

The ATT read blob request can’t read or write the attribute.

static var insufficientEncryptionKeySize: CBATTError.Code

The encryption key size used for encrypting this link is insufficient.

static var invalidAttributeValueLength: CBATTError.Code

The length of the attribute’s value is invalid for the intended operation.

static var unlikelyError: CBATTError.Code

The ATT request encountered an unlikely error and wasn’t completed.

static var insufficientEncryption: CBATTError.Code

Reading or writing the attribute’s value failed for lack of encryption.

