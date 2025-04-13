

- UIKit
- Protecting the User’s Privacy
-  Encrypting Your App’s Files 

Article

# Encrypting Your App’s Files

Protect the user’s data in iOS by encrypting it on disk.

## Overview

Data protection is an iOS feature that you use to secure your app’s files and prevent unauthorized access to them. Data protection is enabled automatically when the user sets an active passcode for the device. You read and write your files normally, but the system encrypts and decrypts your content behind the scenes. The encryption and decryption processes are automatic and hardware accelerated.

You specify the level of data protection that you want to apply to each of your files. There are four levels available, each of which determines when you may access the file. If you do not specify a protection level when creating a file, iOS applies the default protection level automatically.

- **No protection.** The file is always accessible.

- **Complete until first user authentication.** (Default) The file is inaccessible until the first time the user unlocks the device. After the first unlocking of the device, the file remains accessible until the device shuts down or reboots.

- **Complete unless open.** You can open existing files only when the device is unlocked. If you have a file already open, you may continue to access that file even after the user locks the device. You can also create new files and access them while the device is locked or unlocked.

- **Complete.** The file is accessible only when the device is unlocked.

To create and encrypt a new file in one step, construct a data object with the file’s contents and call the write(to:options:) method. When calling the method, specify the data protection option that you want applied to the file. The following code shows an example of how to write out the contents of a Data instance to a file and encrypt it using the complete protection level.

```
do {
   try data.write(to: fileURL, options: .completeFileProtection)
}
catch {
   // Handle errors.
}
```

To change the data protection level of an existing file, use the setResourceValue(_:forKey:) method of NSURL. When calling this method, assign the new data protection option to the fileProtectionKey resource key. The following code shows an example that adds this key to an existing file.

```
do {
   try (fileURL as NSURL).setResourceValue( 
                  URLFileProtection.complete,
                  forKey: .fileProtectionKey)
}
catch {
   // Handle errors.
}
```

### Manage Your Access to Encrypted Files

Depending on a file’s protection level, attempts to read or write its contents could fail when the user subsequently locks the device. To ensure that your app is able to access files, do the following:

- Choose the right data protection level for your needs.

- Use the app delegate’s applicationProtectedDataWillBecomeUnavailable(_:) and applicationProtectedDataDidBecomeAvailable(_:) methods to close and reopen files with the completeFileProtection level.

Assign the complete protection level to files that your app accesses only when it is in the foreground. If your app supports background capabilities, such as handling location updates, assign a different protection level for files that you might access while in the background. For example, a fitness app might use the complete unless open protection level on a file that it uses to log location events in the background.

Files containing personal information about the user, or files created directly by the user, always warrant the strongest level of protection. Assign the complete protection level to user data files and manage access to those files using the app delegate methods. The app delegate methods give you time to close the files before they become inaccessible to your app.

## See Also

### Supporting Privacy

Requesting access to protected resources

Provide a purpose string that explains to a person why you need access to protected resources on their device.

