

- UIKit
- App and environment
- Managing your app’s life cycle
-  Responding to memory warnings 

Article

# Responding to memory warnings

Free up memory when asked to do so by the system.

## Overview

If the system runs low on free memory and is unable to reclaim memory by terminating suspended apps, UIKit sends a low-memory warning to running apps. UIKit delivers low-memory warnings in the following ways:

- It calls the applicationDidReceiveMemoryWarning(_:) method of your app delegate.

- It calls the didReceiveMemoryWarning() method of any active UIViewController classes.

- It posts a didReceiveMemoryWarningNotification object to any registered observers.

- It delivers a warning to dispatch queues of type DISPATCH_SOURCE_TYPE_MEMORYPRESSURE.

When your app receives a low-memory warning, free up as much memory as possible, as quickly as possible. Remove references to images, media files, or any large data files that already have an on-disk representation and can be reloaded later. Remove references to any temporary objects that you no longer need. If active tasks might consume significant amounts of memory, pause dispatch queues or restrict the number of simultaneous operations that your app performs.

Important

Failure to reduce your app’s memory usage may result in your app’s termination. Therefore, consider writing any unsaved data to disk as part of your cleanup efforts.

To test your app’s response to a low-memory warning, use the Simulate Memory Warning command in iOS Simulator.

