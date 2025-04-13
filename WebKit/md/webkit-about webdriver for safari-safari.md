

- WebKit
-  About WebDriver for Safari 

Article

# About WebDriver for Safari

Enhance testing of your web content using Safari’s enhancements to WebDriver.

## Overview

WebDriver, Selenium’s cross-platform, cross-browser API, automates testing of web content interactions on all major platforms and browsers, without requiring browser-specific code. Use WebDriver to write robust, comprehensive tests and run them against any browser that has a WebDriver-compliant driver. Safari’s driver is called `safaridriver` and has a preset available in most Selenium client libraries. You can write tests in Python, Java, PHP, JavaScript, and any other language whose library is compatible with the W3C WebDriver protocol.

WebDriver is a REST API. It hosts a local web server that accepts REST-style HTTP requests, so it can accept automation commands from a wide variety of test setups.

To support WebDriver without sacrificing a user’s privacy or security, Safari’s driver provides extra safeguards to ensure that test execution is isolated from normal browsing data and from other test runs. The driver is available in Safari 10 or later.

### Isolated Automation Windows

Test execution is confined to special automation windows that are isolated from normal browsing windows, user settings, and preferences. You can recognize these windows by their orange Smart Search field. Like a private browsing session, an automation session always starts from a clean slate. It can’t access Safari’s browsing history, AutoFill data, or other sensitive information available in a normal browsing session. These isolated sessions also help to ensure that tests are unaffected by a previous test session’s persistent state.

### Glass Panes

To prevent any attempts to interact with the window or web content during a test, Safari installs a transparent “glass pane” over the automation windows while the browser is being used for WebDriver testing. This pane catches any stray interactions (mouse, keyboard, resizing, and so on) that could affect the automation window. If a running test gets stuck, you can interrupt it by “breaking” the glass pane and stopping the session. When an automation session is interrupted, the test’s connection to the browser is permanently severed, and the automation window remains open for further inspection, until closed manually.

### Web Inspector and WebDriver

You can use Web Inspector during and after the execution of a WebDriver test. Web Inspector features such as console logging, the Elements tab, and the script debugger are fully functional when running WebDriver tests. Choose the Develop \> Show Web Inspector menu item (shortcut: ⌥⌘I) to launch Web Inspector while a test is running.

### WebDriver Commands for Debugging

You can specify some WebDriver capabilities in a New Session request to assist debugging:

- `safari:automaticInspection`—When passed the `safari:automaticInspection` capability in a New Session request, `safaridriver` preloads the Web Inspector and JavaScript debugger in the background. To pause test execution and bring up Web Inspector’s Debugger tab, evaluate a `debugger;` statement in the test page.

- `safari:automaticProfiling`—When passed the `safari:automaticProfiling` capability in a New Session request, `safaridriver` preloads Web Inspector and starts a timeline recording in the background. Open the Timelines tab in Web Inspector to see the captured timeline recording in its entirety.

### One Session at a Time, to Mimic User Interaction

Only one Safari browser instance can be active at any given time, and only one WebDriver session at a time can be attached to the browser instance. These constraints ensure that the simulated behavior (mouse, keyboard, touch, and so forth) accurately reflects what a user can do in a macOS windowing environment and prevents tests from competing with each other for window and keyboard focus.

## See Also

### WebDriver

macOS WebDriver Commands for Safari 11.1 and earlier

Test your web content using the WebDriver commands supported by Safari 11.1 and earlier.

macOS WebDriver Commands for Safari 12 and later

Test your web content using the WebDriver commands supported by Safari 12 and later.

Testing with WebDriver in Safari

Enable WebDriver and run a test.

