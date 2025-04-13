

- ClockKit
- Deprecated articles and symbols
-  Declaring complications for your app 

Article

# Declaring complications for your app

Define the complications that your app supports.

## Overview

In watchOS 7 and later, use your data source’s getComplicationDescriptors(handler:) method to define the complications your app supports. In your implementation, create an array of CLKComplicationDescriptor objects, and pass this array to the method’s handler. You can update the complications by calling the reloadComplicationDescriptors() method at any time.

A complication descriptor contains a type identifier and one or more supported families. Each descriptor represents a separate complication that the user can select.

### Specify the Complication Identifiers

Your app can support multiple types of complications. For example, a weather app may support complications for `Condition`, `Temperature`, and `Precipitation`.

ClockKit uses unique strings to identify the complications. If your app has only a few complications, you can use constants for the identifiers.

```
let complicationConditionIdentifier = "Condition"
let complicationTemperatureIdentifier = "Temperature"
let complicationPrecipitationIdentifier = "PrecipitationChance"
```

Your app uses these identifiers when creating the complication descriptors for your app, and when creating timeline entries for your complications.

### Specify the Supported Families

Each complication descriptor specifies an array of families that it supports. The descriptors don’t all need to support the same families. Each descriptor can support a different subset of families, and these subsets can overlap. However, you should make sure that at least one descriptor supports each family—even if the resulting complication only acts as a launcher for your app.

To get the complete list of families, call the CLKAllComplicationFamilies function.

### Create and Return the Descriptors

After creating the type identifiers and supported families, create the descriptors for your app.

```
// Create the condition descriptor.
let conditionDescriptor = CLKComplicationDescriptor(
    identifier: complicationConditionIdentifier,
    displayName: "Weather Condition",
    supportedFamilies: mySupportedFamilies)

// Create the temperature descriptor.
let temperatureDescriptor = CLKComplicationDescriptor(
    identifier: complicationTemperatureIdentifier,
    displayName: "Temperature",
    supportedFamilies: mySupportedFamilies)

// Create the precipitation descriptor.
let precipitationDescriptor = CLKComplicationDescriptor(
    identifier: complicationPrecipitationIdentifier,
    displayName: "Percipitation",
    supportedFamilies: mySupportedFamilies)
```

Each descriptor has a localized display name that ClockKit shows when users select complications for a watch face.

After you create the descriptors, pass them to the handler from your getComplicationDescriptors(handler:) implementation.

```
// Call the handler and pass an array of descriptors.
handler([conditionDescriptor,
         temperatureDescriptor,
         precipitationDescriptor])
```

### Add Information to the Descriptors

The CLKComplicationDescriptor class provides two additional initializers: init(identifier:displayName:supportedFamilies:userActivity:) and init(identifier:displayName:supportedFamilies:userInfo:).

Use init(identifier:displayName:supportedFamilies:userActivity:) to specify an NSUserActivity object for the complication type. When the user taps the complication, ClockKit wakes your app and passes the activity object to your handle(_:) method. You can use the handle(_:) method to navigate to a particular part of your app that the activity object specifies.

Use init(identifier:displayName:supportedFamilies:userInfo:) to specify a user info dictionary with information that your data source can use when creating timeline entries.

Warning

Because the system can pass complications as part of a shared watch face, only place data in the user info dictionary that other instances of your app can use. For example, when referring to data, avoid using identifiers that can change between users—like an index into the user’s favorites list. Instead use items that remain constant across all copies of the app, like unique string identifiers.

When the user taps your complication, ClockKit includes the content of the `userInfo` parameter in the dictionary that passes to the extension delegate’s handleUserActivity(_:) method. You can also use this data to navigate to a particular part of your app.

### Dynamically Define Descriptors

The previously examples created a static set of descriptors—the app always presents the same set of complications to its users. However, you can also customize the complications for each particular user. For example, the weather app could provide `Condition`, `Temperature`, and `Precipitation` complications for each city in the user’s favorite city list.

Start by creating unique identifiers for each city and weather data combination.

```
for city in myData.favoriteCities {

    let conditionIdentifier = complicationConditionIdentifier + ": \(city.id)"
    let temperatureIdentifier = complicationTemperatureIdentifier + ": \(city.id)"
    let perceptionIdentifier = complicationPrecipitationIdentifier + ": \(city.id)"

    // Create the descriptors for the city.
    ...    
}
```

Then create the descriptors for all the identifiers. As the list of descriptors grows, it’s important to think about their order. The complications appear in the same order as the descriptors in the array. When the user configures a complication, the picker shows the first three items from the array that support the complication’s family. If there are more than three, the picker displays a More button to provide access to the additional complications.

```
// Create the descriptors for the city.
descriptors.append(CLKComplicationDescriptor(
                    identifier: conditionIdentifier,
                    displayName: "\(city.abbreviation) Weather Condition",
                    supportedFamilies: CLKComplicationFamily.allCases,
                    userInfo: [myCityIDKey: city.id,
                               myTypeIdentifierKey: conditionIdentifier]))

descriptors.append(CLKComplicationDescriptor(
                    identifier: temperatureIdentifier,
                    displayName: "\(city.abbreviation) Temperature",
                    supportedFamilies: CLKComplicationFamily.allCases,
                    userInfo: [myCityIDKey: city.id,
                               myTypeIdentifierKey: temperatureIdentifier]))

descriptors.append(CLKComplicationDescriptor(
                    identifier: perceptionIdentifier,
                    displayName: "\(city.abbreviation) Percipitation",
                    supportedFamilies: CLKComplicationFamily.allCases,
                    userInfo: [myCityIDKey: city.id,
                               myTypeIdentifierKey: perceptionIdentifier]))
```

This example also uses the descriptor’s `userInfo` property to contain a `myCityIDKey` and a `myTypeIdentifierKey` for each city. This lets you look up the city and weather data type without having to parse the complication’s `identifier` string. For an example of using the `myCityIDKey` to create a complication template, see Use Complication Data. When the user adds or removes a favorite city, you need to reload the complication descriptors according to their new favorites list.

### Reload the Descriptors

Your app can reload the descriptors at any point by calling the complication server’s reloadComplicationDescriptors() method. For example, the weather app needs to reload its descriptors when the user adds or removes cities from their favorite cities.

```
var myFavoriteCities = [City]() {
    didSet {
        CLKComplicationServer.sharedInstance().reloadComplicationDescriptors()
    }
}
```

ClockKit then calls your getComplicationDescriptors(handler:) method to load the new descriptors.

Note

If your data source removes a complication that’s already present on a watch face, ClockKit continues to display and request new timeline entries for that complication. However, the user won’t be able to add the complication to new watch faces.

### Run on Earlier Versions of watchOS

In watchOS 6 and earlier, you statically define the supported complication families in the WatchKit extension’s General tab under the Complication and Configuration settings.

Xcode then saves these settings in the extension’s `Info.plist` file.

In watchOS 7 and later, if you implement getComplicationDescriptors(handler:), the system ignores the static list of complications in the `Info.plist` file, and calls the data source’s method so that you can specify and modify the list of supported descriptors at runtime.

## See Also

### Related Documentation

Enabling Complications for Your watchOS App

Set up your watchOS app’s complications.

Adding Placeholders for Your Complication

Provide the placeholders that users see when adding your complication to a watch face.

### Articles

Creating complications for your watchOS app

Set up and implement complications for your watchOS app.

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

