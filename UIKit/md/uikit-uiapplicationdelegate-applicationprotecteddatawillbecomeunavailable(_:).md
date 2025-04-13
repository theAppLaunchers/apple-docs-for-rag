

- UIKit
- UIApplicationDelegate
-  applicationProtectedDataWillBecomeUnavailable(\_:) 

Instance Method

# applicationProtectedDataWillBecomeUnavailable(\_:)

Tells the delegate that the protected files are about to become unavailable.

iOS 4.0+iPadOS 4.0+Mac Catalyst 13.1+tvOSvisionOS 1.0+

``` source
@MainActor
optional func applicationProtectedDataWillBecomeUnavailable(_ application: UIApplication)
```

## Parameters 

`application`  

Your singleton app object.

## Mentioned in 

Encrypting Your App’s Files

## Discussion

On a device that uses content protection, protected files are stored in an encrypted form and made available only at certain times, usually when the device is unlocked. This notification lets your app know that the device is about to be locked and that any protected files it is currently accessing might become unavailable shortly.

If your app is currently accessing a protected file, you can use this method to release any references to that file. Although it is not an error to access the file while the device is locked, any attempts to do so will fail. Therefore, if your app depends on the file, you might want to take steps to avoid using that file while the device is locked.

## See Also

### Responding to environment changes

func applicationProtectedDataDidBecomeAvailable(UIApplication)

Tells the delegate that protected files are available now.

func applicationDidReceiveMemoryWarning(UIApplication)

Tells the delegate when the app receives a memory warning from the system.

func applicationSignificantTimeChange(UIApplication)

Tells the delegate when there is a significant change in the time.

class let protectedDataDidBecomeAvailableNotification: NSNotification.Name

A notification that posts when the protected files become available for your code to access.

class let protectedDataWillBecomeUnavailableNotification: NSNotification.Name

A notification that posts shortly before protected files are locked down and become inaccessible.

class let didReceiveMemoryWarningNotification: NSNotification.Name

A notification that posts when the app receives a warning from the operating system about low memory availability.

class let significantTimeChangeNotification: NSNotification.Name

A notification that posts when there’s a significant change in time.

