

- Kernel
- Hardware Families
- FireWire
- IOFireWireAVCUnit
-  matchPropertyTable 

# matchPropertyTable

Matching language support Match on the following properties of the unit: Vendor_ID GUID Unit_Type and available sub-units, match if the device has at least the requested number of a sub-unit type: AVCSubUnit_0 -\> AVCSubUnit_1f

``` source
virtual bool matchPropertyTable(
 OSDictionary *table); 
```

## See Also

### Miscellaneous

AVCCommand

Sends an AVC command to the device and stores the response.

AVCCommandInGeneration

Sends an AVC command to the device and stores the response. The command must complete in the specified FireWire bus generation otherwise kIOFireWireBusReset is returned.

handleClose

Overrideable method to control the open / close behaviour of an IOService.

handleOpen

Overrideable method to control the open / close behaviour of an IOService.

updateAVCCommandTimeout

By default, AVCCommands timeout 10 seconds after receiving an Interim response. This function resets the timeout of the current command to 10 seconds from the current time. Call this repeatedly for AVC commands that take a very long time to execute to prevent premature timeout.

