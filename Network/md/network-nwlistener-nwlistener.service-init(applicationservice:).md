

- Network
- NWListener
- NWListener.Service
-  init(applicationService:) 

Initializer

# init(applicationService:)

Creates a listener for apps that listen for connections from a network device picker.

iOS 16.0+iPadOS 16.0+Mac Catalyst 16.0+macOS 13.0+tvOS 16.0+visionOS 1.0+watchOS 9.0+

``` source
init(applicationService: String)
```

## Parameters 

`applicationService`  

The name of the application service. This must match the name passed to the network device picker.

## Discussion

Use this initializer to setup a listener for application services.

Apps that register as advertising an application service should always have a listener waiting for a local connection. The system launches your app when the user selects the current device in a DevicePicker or DDDevicePickerViewController. Create the listener as soon as your app launches, so that your app can connect with the requesting device.

