

- Safari Developer Features
-  Adding additional simulators 

Article

# Adding additional simulators

Add simulators for different devices and iOS versions to use for web development.

## Overview

A Simulator runtime is an OS package that Simulator loads when booting a device, which is specific to a particular OS and version. Simulator runtimes are then used by numerous different Simulators with different device types, like iPhone 16 or iPad Pro.

If you want to test on another platform or OS version, you need to add the Simulator runtime for that platform, and then create a new Simulator.

## Install and uninstall Simulator runtimes

### Adding a Simulator runtime

1.  In Xcode, from the menu bar, choose **Xcode** \> **Settings…**.

2.  Go to the **Components** tab.

3.  The Platform Support section shows the latest versions of available platform and Simulator runtimes. Click the **Get** button next to the one you need.

4.  If you need a previously released Simulator runtime, click the Add button (**+**) in the lower left corner, and then select a platform to view a list of available versions.

5.  Select a version and click **Download & Install**.

### Removing a Simulator runtime

To recover storage space from unused Simulator runtimes:

1.  In Xcode, from the menu bar, choose **Xcode** \> **Settings…**.

2.  Go to the **Components** tab.

3.  Select the Simulator runtime you wish to remove.

4.  Click the Delete button (**–**) in the lower left corner.

5.  Click **Delete** in the confirmation dialog.

## Add and remove Simulators

### Adding a Simulator

1.  In Xcode, from the menu bar, choose **Window** \> **Devices and Simulators**.

2.  Choose **Simulators** at the top of the sidebar.

3.  Click the Add button (**+**) in the lower left corner.

4.  Choose a **Device Type** and **OS Version** for your simulator, and optionally provide it with a name.

5.  Click **Create** to create the new simulator.

### Removing a Simulator

1.  In Xcode, from the menu bar, choose **Window** \> **Devices and Simulators**.

2.  Choose **Simulators** at the top of the sidebar.

3.  Control-click on the Simulator you wish to remove.

4.  Choose **Delete** from the pop-up menu.

5.  Click **Delete** in the confirmation dialog.

Tip

Simulators can also be managed from the terminal.

## See Also

### Simulators

Installing Xcode and Simulators

Install simulators to use for web development.

