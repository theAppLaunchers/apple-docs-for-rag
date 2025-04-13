

- Swift Playgrounds
-  Previewing SwiftUI views in Swift Playgrounds 

Article

# Previewing SwiftUI views in Swift Playgrounds

Use the canvas in Swift Playgrounds to see a live preview of the SwiftUI views in your app.

## Overview

In Swift Playgrounds, you can see live Previews of your SwiftUI views just like Previews in Xcode. In an app playground, you have a default App Preview that generates from the structure that conforms to the App protocol. The canvas on the right hand side updates its title to “App Preview” when the App Preview renders.

To see live Previews, use a structure that conforms to the PreviewProvider protocol. When you create a SwiftUI view in code, the canvas displays an interactive Preview. The Preview renders live updates when you make changes to its associated file. Making small edits in a file, like changing a property value or string literal changes, causes the Preview to update instantly, while making bigger changes, like adding a new type or changing types, causes the Preview to refresh. When a Preview is available for a specific SwiftUI view, you can see that the canvas displays a page control under the current Previews. This page control allows you to switch between the App Preview and any view previews in the current file. The canvas updates its title to “Preview” when a view preview renders.

You can run your app within Swift Playgrounds. When you tap Run, Swift Playgrounds builds and displays your app so you can see what your app looks like and test its functionality. While running the app, you interact with Playgrounds App window by tapping the Swift icon in the status bar. This opens a menu with the following options:

- Restart – Restarts your app and creates a new instance.

- Stop – Stops the current running instance of your app.

- Show Project – Go back to your app playground files to look at code while your app is running.

- Show Console – See any live print statements that you may have in your code.

- Delete App Data and Restart – Deletes any cached app data and restarts your app.

## See Also

### App playgrounds

Adding a Swift package to your app playground

Extend the functionality of your app playground by finding and adding a publicly available Swift package.

Debugging an App Playground using the Console

Learn different methods to debug your code using console output.

Requesting access to capabilities for your app playground

Request access for your app to protected resources, services, or device hardware such as sensors.

Importing sample content into user app playgrounds

Learn how to bring sample code into your app playground.

