

- ClassKit
- Enabling ClassKit in your app
-  Testing your ClassKit app during development 

Article

# Testing your ClassKit app during development

Use development mode to test your app without a Managed Apple ID.

## Overview

When you distribute your ClassKit-enabled app through the App Store, it runs in production mode. In this mode, ClassKit shares data with Schoolwork on the device, and also with other devices through iCloud—for example, so that assignments made on a teacher’s device can be transmitted to students’ devices, or so that progress reported by a student returns to the teacher that made the assignment. To define these roles and enable these connections, users must be signed in to devices with Managed Apple IDs issued by an educational institution enrolled in Apple School Manager.

During development, you might not have access to users with Managed Apple IDs. Instead, you run your app in development mode. In this mode, which Xcode enables by default, you manually set the user’s role in your device Settings, and all ClassKit data remains stored locally on your device. Nothing is sent to iCloud, and so a Managed Apple ID isn’t required. However, the ClassKit API behaves just as it does in production mode, so that you can test your ClassKit adoption.

Note

You can’t test ClassKit behavior in Simulator because Schoolwork isn’t available in that environment. Instead, test your ClassKit adoption on real iOS devices with the Schoolwork app installed.

### Choose a role in the ClassKit developer settings

After you install Schoolwork on an iOS device, new developer settings appear for controlling ClassKit development mode behavior. Go to Settings \> Developer on the device and choose ClassKit API.

In the view that appears, choose either a teacher or student role for the device. The role you choose changes how ClassKit routes data, as described in About ClassKit and user roles.

You can switch back and forth between the teacher and student roles as needed. For example, begin as a teacher and run your app to establish your assignable content. Then create an assignment with Schoolwork. Next, switch to student mode and complete the assignment in your app. Finally, switch back to teacher mode to see the reported student progress. If you want to start over, tap Reset Development Data, shown just underneath the role selection in the screenshot above, to purge the student and teacher databases.

If you later want to test with real managed accounts, as described in Optionally, test in production mode with managed Apple IDs below, exit development mode by returning to the Off setting.

### Flush cached ClassKit data after changing roles

Because development mode stores teacher and student data in their own dedicated database on a single device, it’s important to flush any cached ClassKit data from memory after you change roles. Otherwise, you might be working with cached items from the teacher’s database after changing to the student role, or vice versa. This results in undefined behavior.

The easiest way to flush data is to restart your app, forcing ClassKit to reload or recreate data when you begin operating in the new role, rather than relying on possibly stale data in memory.

### Optionally, test in production mode with managed Apple IDs

You can fully qualify your ClassKit adoption using development mode, as explained above. But if you do need to launch your app from Xcode in an environment where users are logged in with Managed Apple IDs, you can choose production mode manually.

When you enable the ClassKit capability in Xcode for your app, Xcode adds a `ClassKit Environment` entitlement to the build and sets its value to `development`. This entitlement value enables ClassKit and opts your app in to ClassKit’s development features by default. As part of the App Store submission process, Xcode automatically changes the entitlement’s value to `production`, which deactivates development mode behavior for instances of the app distributed through the App Store.

To override this behavior and choose production mode during development, modify the entitlement manually by opening your app’s entitlements file and setting the ClassKit entitlement’s value to `production`:

From your app’s point of view, the ClassKit API behaves exactly the same in production mode as it did in development mode, but the framework only interacts with Schoolwork and the network if you sign in to the device with a Managed Apple ID. If you don’t sign in with a Managed Apple ID in production mode, ClassKit treats you as an unmanaged user, silently dropping any data you report through the API. Similarly, ClassKit drops data unless your school’s IT administrator enables student progress in Apple School Manager, as described in Use Schoolwork to manage student progress in Apple School Manager.

Important

If you choose production mode in your app’s entitlements, make sure to disable ClassKit development mode on your development devices. In Settings, choose Developer \> ClassKit API \> Off. Otherwise, ClassKit keeps all data on the device, regardless of your app’s settings.

