

- Core Services
- Apple Events
-  AECreateAppleEvent(\_:\_:\_:\_:\_:\_:) 

Function

# AECreateAppleEvent(\_:\_:\_:\_:\_:\_:)

Creates an Apple event with several important attributes but no parameters.

macOS 10.0+

``` source
func AECreateAppleEvent(
    _ theAEEventClass: AEEventClass,
    _ theAEEventID: AEEventID,
    _ target: UnsafePointer!,
    _ returnID: AEReturnID,
    _ transactionID: AETransactionID,
    _ result: UnsafeMutablePointer!
) -> OSErr
```

## Parameters 

`theAEEventClass`  

The event class of the Apple event to create. This parameter becomes accessible through the `keyEventClassAttr` attribute of the Apple event. Some event classes are described in Event Class Constants. See AEEventClass.

`theAEEventID`  

The event ID of the Apple event to create. This parameter becomes accessible through the `keyEventIDAttr `attribute of the Apple event. Some event IDs are described in Event ID Constants. See AEEventID.

`target`  

A pointer to an address descriptor. Before calling `AECreateAppleEvent`, you set the descriptor to identify the target (or server) application for the Apple event. This parameter becomes accessible through the `keyAddressAttr` attribute of the Apple event. See AEAddressDesc.

`returnID`  

The return ID for the created Apple event. If you pass a value of `kAutoGenerateReturnID`, the Apple Event Manager assigns the created Apple event a return ID that is unique to the current session. If you pass any other value, the Apple Event Manager assigns that value for the ID. This parameter becomes accessible through the `keyReturnIDAttr` attribute of the Apple event. The return ID constant is described in ID Constants for the AECreateAppleEvent Function. See AEReturnID.

`transactionID`  

The transaction ID for this Apple event. A transaction is a sequence of Apple events that are sent back and forth between the client and server applications, beginning with the client’s initial request for a service. All Apple events that are part of a transaction must have the same transaction ID. You can specify the `kAnyTransactionID` constant if the Apple event is not one of a series of interdependent Apple events. This parameter becomes accessible through the `keyTransactionIDAttr` attribute of the Apple event. This transaction ID constant is described in ID Constants for the AECreateAppleEvent Function. See AETransactionID.

`result`  

A pointer to an Apple event. On successful return, the new Apple event. On error, a null descriptor (one with descriptor type `typeNull`). If the function returns successfully, your application should call the AEDisposeDesc(_:) function to dispose of the resulting Apple event after it has finished using it. See the AppleEvent data type.

## Return Value

A result code. See Result Codes.

## Discussion

The `AECreateAppleEvent `function creates an empty Apple event. You can add parameters to the Apple event after you create it with the functions described in Apple Event Manager.

### Version-Notes

Thread safe starting in OS X v10.2.

