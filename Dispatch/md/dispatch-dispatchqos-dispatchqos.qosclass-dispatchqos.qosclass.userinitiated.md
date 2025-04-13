

- Dispatch
- DispatchQoS
- DispatchQoS.QoSClass
-  DispatchQoS.QoSClass.userInitiated 

Case

# DispatchQoS.QoSClass.userInitiated

The quality-of-service class for tasks that prevent the user from actively using your app.

iOS 8.0+iPadOS 8.0+Mac CatalystmacOS 10.10+tvOSvisionOSwatchOS

``` source
case userInitiated
```

## Discussion

User-initiated tasks are second only to user-interactive tasks in their priority on the system. Assign this class to tasks that provide immediate results for something the user is doing, or that would prevent the user from using your app. For example, you might use this quality-of-service class to load the content of an email that you want to display to the user.

## See Also

### Getting the Quality-of-Service Class

case userInteractive

The quality-of-service class for user-interactive tasks, such as animations, event handling, or updating your app’s user interface.

case `default`

The default quality-of-service class.

case utility

The quality-of-service class for tasks that the user does not track actively.

case background

The quality-of-service class for maintenance or cleanup tasks that you create.

case unspecified

The absence of a quality-of-service class.

