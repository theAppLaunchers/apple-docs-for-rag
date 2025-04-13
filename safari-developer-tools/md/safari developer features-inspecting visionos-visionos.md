

- Safari Developer Features
-  Inspecting visionOS 

Article

# Inspecting visionOS

Inspect webpages, service workers, extensions, and content inside apps in visionOS from a Mac on the same network.

## Overview

Web content in visionOS is inspectable when you connect the device to a Mac. You can also use simulators on a Mac with Apple silicon to test your webpages and apps without a physical device. To learn more about device simulators, see Installing Xcode and Simulators.

## Enable inspecting your device from a Mac on the same network

To inspect web content on a visionOS device, you must enable Web Inspector.

1.  On your visionOS device, open the **Settings** app.

2.  Go to **Apps** \> **Safari**.

3.  Scroll down to **Advanced**.

4.  Enable the **Web Inspector** toggle.

To allow inspecting without a physical wired connection to your Mac, you can pair your visionOS device over the network:

1.  Make sure both your Mac and device are connected to the same network. The Wi-Fi network must be compatible with Bonjour.

2.  On your visionOS device, open **Settings**, then choose **General** \> **Remote Devices**. While this screen is visible, your device is available for pairing from any Mac on the network.

3.  On your Mac, go to the **Develop** menu in Safari and find your device in the list.

4.  From the device’s submenu, choose **Use for Development**.

5.  Enter the six-digit PIN code shown on the device into the PIN field shown on your Mac.

Once paired, you can inspect content on the visionOS device like any other device. In Safari, the device appears in the Develop menu.

Alternatively, you can also pair with the device using Xcode.

### visionOS simulators

Simulators come with **Web Inspector** already enabled. The Develop menu lists currently booted simulators just like connected devices.

## Inspect webpages

Webpages you open in Safari in visionOS appear in a submenu for the connected device of the **Develop** menu of Safari on a connected Mac. Safari groups webpages and other content by app, making finding the webpage you want to inspect easier.

Find the webpage you want to inspect, then select it to open a new Web Inspector window. This window continues inspecting the tab you started inspecting, including across navigations. If you close the tab in visionOS, the Web Inspector window disappears.

For webpages, some additional options are available only while inspecting a connected device or a simulator to allow you to override the user agent, disable cross-origin restrictions, disable site-specific quirks, and more. See Device Settings.

## Inspect service workers

Service Workers are shared between webpages and don’t necessarily belong to any individual webpage. For this reason, they are inspectable separately from webpages in Safari.

You can only inspect service workers that are currently running. To inspect service workers, open the **Develop** menu, find the menu item for the visionOS device you want to inspect and select them from the **Service Workers** section near the bottom of the menu. This section doesn’t appear if there aren’t any service workers currently running.

## Inspect extensions

Extensions can run scripts or create webpages in several places, and how you inspect them varies depending on the content. Learn more about debugging web extensions…

### Content scripts

To debug the scripts that web extensions inject into webpages, first inspect the webpage. Open Web Inspector, then click the Sources tab and select your content script file from the Extension Scripts folder at the lower left. Select your extension’s execution context using the selector in the lower-right corner of the inspector. Set breakpoints by clicking the gutter with line numbers in the source view. Inspect other source files for your extension, such as style sheets, in the Sources area at the lower left.

### Background scripts

To debug background scripts, open the **Develop** menu, find the menu item for the device you want to inspect, and then find the item with the name of the extension, “**Extension Background Page**”, and the filename of the background script.

### Toolbar pop-up

To debug your extension’s pop-up, open your pop-up on the device. From the **Develop** menu, find the menu item for the device you want to inspect, and then find the item with the name of the extension, “**Extension Pop-up Page**”, and the filename of the pop-up’s HTML.

## Inspect JavaScript and webpages in apps

You can make WKWebViews and JSContexts in apps inspectable, allowing anyone who enables **Web Inspector** on the device to inspect them. Content you can inspect appears in a submenu for the connected device of the **Develop** menu of Safari on a connected Mac. Safari separates webpages and JavaScript contexts by app, making finding the content you want to inspect easier.

Learn more about Enabling inspecting content in your apps.

## See Also

### Inspecting content

Inspecting Safari on macOS

Inspect webpages, Service Workers, and extensions in Safari on macOS.

Inspecting iOS and iPadOS

Inspect webpages, Service Workers, Home Screen web apps, extensions, and content inside apps on iOS and iPadOS devices and simulators from a connected Mac.

Inspecting tvOS

Inspect JavaScript and TVML content on tvOS from a Mac on the same network.

Enabling inspecting content in your apps

Enable the inspection of webpages and JavaScript in apps you develop when inspected from a connected Mac.

