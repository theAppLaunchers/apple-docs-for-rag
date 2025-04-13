

- IOBluetooth UI
- IOBluetoothDeviceSelectorController
-  beginSheetModal(for:modalDelegate:didEnd:contextInfo:) 

Instance Method

# beginSheetModal(for:modalDelegate:didEnd:contextInfo:)

Runs the device selector panel as a sheet on the target window.

macOS 10.2+

``` source
@MainActor
func beginSheetModal(
    for sheetWindow: NSWindow!,
    modalDelegate: Any!,
    didEnd didEndSelector: Selector!,
    contextInfo: UnsafeMutableRawPointer!
) -> IOReturn
```

## Parameters 

`sheetWindow`  

NSWindow to attach the device selector panel to as a sheet.

`modalDelegate`  

Delegate object that gets sent the didEndSelector when the sheet modal session is finished.

`didEndSelector`  

Selector sent to the modalDelegate when the sheet modal session is finished.

`contextInfo`  

User-definied value passed to the modalDelegate in the didEndSelector.

## Return Value

Returns kIOReturnSuccess if the sheet modal session was started.

## Discussion

This function works the same way as -\[NSApplication beginSheet:modalForWindow:modalDelegate:didEndSelector:contextInfo:\]. The didEndSelector has a similar prototype as in NSApplication except that the first argument is the IOBluetoothDeviceSelectorController object instead of the window: -(void)sheetDidEnd:(IOBluetoothDeviceSelectorController \*)controller returnCode:(int)returnCode contextInfo:(void \*)contextInfo. The returnCode parameter will either be kIOBluetoothUISuccess or kIOBluetoothUIUserCancelledErr as described in -runModal.

NOTE: This method is only available in macOS 10.2.4 (Bluetooth v1.1) or later.

## See Also

### Instance Methods

func addAllowedUUID(IOBluetoothSDPUUID!)

Adds a UUID to the list of UUIDs that are used to validate the user’s selection.

func addAllowedUUIDArray([Any]!)

Adds an array of UUIDs to the list of UUIDs that are used to validate the user’s selection.

func clearAllowedUUIDs()

Resets the controller back to the default state where it will accept any device the user selects.

func getCancel() -> String!

Returns the title of the default/cancel button in the device selector panel.

func getDescriptionText() -> String!

Returns the description text that appears in the device selector panel.

func getHeader() -> String!

Returns the header text that appears in the device selector panel.

func getOptions() -> IOBluetoothServiceBrowserControllerOptions

Returns the option bits that control the panel’s behavior.

func getPrompt() -> String!

Returns the title of the default/select button in the device selector panel.

func getResults() -> [Any]!

Returns the result of the user’s selection.

func getSearchAttributes() -> UnsafePointer&lt;IOBluetoothDeviceSearchAttributes>!

Returns the search attributes that control the panel’s search/inquiry behavior.

func getTitle() -> String!

Returns the title of the device selector panel.

func runModal() -> Int32

Runs the device selector panel in a modal session to allow the user to select a Bluetooth device.

func setCancel(String!)

Sets the title of the default/cancel button in the device selector panel.

func setDescriptionText(String!)

Sets the description text that appears in the device selector panel.

func setHeader(String!)

Sets the header text that appears in the device selector panel.

