

- ClockKit
- Deprecated articles and symbols
-  Creating complications for your watchOS app 

# Creating complications for your watchOS app

Set up and implement complications for your watchOS app.

## Overview

Complications are small interface elements that users place on the clock face.

Having your complication on an active watch face gives you the opportunity to provide useful data whenever the user glances at their watch. Users can also interact with your app by tapping on the complication and launching your app. The system also provides apps with active complications larger budgets for background refresh tasks. You can use these tasks to keep the content of your watchOS app and your complications up to date and accurate.

### Add Complications to Your App

To add complications to your watchOS app, perform the following steps:

1.  Select the data to display.

2.  Enable complications for your App.

3.  Implement your data source.

4.  Update your complications.

5.  Add placeholders for your complications.

### Select the Data to Display

Before creating a complication, decide on the data you want to display. Each watch face only provides space for a handful of complications, and users are more likely to add your complication if it provides useful and up-to-date information at a glance.

Consider the following:

Can you display your data with the available templates?  
When building a complication, you must fit your data into one of the provided templates. You can choose which template to use for each family, but for many templates, you only have a few characters or a small image. Graphic complications provide richer information using gauges and color, but you’re still limited by the amount and type of data you can display.

Do you already use notifications to convey timely information to the user?  
If you’re using notifications to deliver updates, a complication might serve as a more unobtrusive way to deliver the same data. For example, a sports app might post updated scores to a complication rather than sending notifications when the scores change.

How much data can you provide in advance?  
If possible, provide a timeline that contains all the complication updates for the near future. The complication can then use data from the timeline without requiring additional background update tasks. You can always add to or replace this timeline. However, if you update your timeline too frequently, you may exhaust your complication’s budget for background tasks and data transfers.

The system gives larger background budgets to watchOS apps with complications on the active watch face. However, it still limits the background tasks to about four tasks per hour. Alternatively, you can generate the complication data on your server, and send it to the watch using push notifications. This strategy lets you move complex and time consuming tasks off the watch; however, the system limits you to 50 complication push notifications per day. Be sure that your complications can provide useful and timely information within these constraints.

### Set Up and Design Your Complications

Before you can begin designing your complications, you need to enable support. If you’re creating a new project, you can choose to include complications in the project, and Xcode does all the work for you. However, if you want to add complications to an existing app, you may need to create and configure your complications’ data source and an asset group. For more information, see Enabling Complications for Your watchOS App.

Next, implement your app’s data source. ClockKit calls the CLKComplicationDataSource protocol’s methods to request information about the complications your app supports, and to fill the timeline of any complications on an active watch face. For more information, see Declaring complications for your app, Creating a timeline entry, and Loading future timeline events.

Finally, an effective complication must display useful information whenever the user glances at it. For information on strategies to keep your complication up to date and accurate, see Keeping your complications up to date.

### Add Placeholders

ClockKit displays placeholders for your app’s complications while the user configures a watch face. Your app can provide static images and localized templates as placeholders. For static placeholders, place images in the Complications group in your watch extension’s assets catalog. For localized templates, implement your data source’s getLocalizableSampleTemplate(for:withHandler:) method.

ClockKit uses the localizable templates whenever possible; however, it may display the static image if the template isn’t available, such as when the user first installs your app. For more information, see Adding Placeholders for Your Complication.

### Test Your Complications

To test your complications, build and install the app on the simulator or a test device. Then add the complication to an active watch face, as described in this example:

1.  Build and run the sample code project.

2.  Press the Digital Crown to return to the watch face.

3.  Firmly press the watch face to configure it, then tap Customize.

4.  Swipe left until the complications are highlighted. Select the complication you want to modify.

5.  Scroll to select your app’s complication.

6.  Press the Digital Crown again to save your changes.

For more information on configuring watch faces, see Change the watch face on your Apple Watch.

If you included complications when you created the project, Xcode automatically creates a scheme for installing and debugging your complications. By default, the scheme’s name ends in “WatchKit App (Complication)”. When you run this scheme, Xcode installs the latest version of your app and reloads your complications. You can set breakpoints in your complication’s data source to step through the loading process.

## Topics

### Configure Complications

Enabling Complications for Your watchOS App

Set up your watchOS app’s complications.

Adding Placeholders for Your Complication

Provide the placeholders that users see when adding your complication to a watch face.

## See Also

### Articles

Declaring complications for your app

Define the complications that your app supports.

Creating a timeline entry

Package your app-specific data into a template and create a timeline entry for that template.

Loading future timeline events

Preserve battery life and improve performance on the watch by providing a timeline with expected data and updates.

Keeping your complications up to date

Replace or extend the data in your complication’s timeline.

Building complications with SwiftUI

Design the appearance of a graphic complication using SwiftUI.

Displaying progress views and gauges

Add rich visual data to your SwiftUI complications with progress views and gauges.

Adding text to a complication

Use text in SwiftUI complications.

