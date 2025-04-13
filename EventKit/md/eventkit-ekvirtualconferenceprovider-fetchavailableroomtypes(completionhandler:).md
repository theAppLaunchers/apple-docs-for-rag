

- EventKit
- EKVirtualConferenceProvider
-  fetchAvailableRoomTypes(completionHandler:) 

Instance Method

# fetchAvailableRoomTypes(completionHandler:)

Provides an array of room types where events take place.

iOS 15.0+iPadOS 15.0+Mac Catalyst 15.0+macOS 12.0+visionOS 1.0+watchOS 8.0+

``` source
func fetchAvailableRoomTypes(completionHandler: @escaping ([EKVirtualConferenceRoomTypeDescriptor]?, (any Error)?) -> Void)
```

``` source
func fetchAvailableRoomTypes() async throws -> [EKVirtualConferenceRoomTypeDescriptor]
```

## Parameters 

`completionHandler`  

A completion handler that you call after you determine the available rooms. If you provide an array with one or more room type descriptors, pass `nil` for the error parameter. Conversely, if you provide an error object, pass `nil` for the array parameter.

## Discussion

Concurrency Note

You can call this method from synchronous code using a completion handler, as shown on this page, or you can call it as an asynchronous method that has the following declaration:

```
func fetchAvailableRoomTypes() async throws -> [EKVirtualConferenceRoomTypeDescriptor]
```

For information about concurrency and asynchronous code in Swift, see Calling Objective-C APIs Asynchronously.

Your virtual conference provider implements this method to provide the list of rooms where users schedule events using your service. Create an instance of EKVirtualConferenceRoomTypeDescriptor for each room that’s available for users to schedule events in.

```
override func fetchAvailableRoomTypes(completionHandler: @escaping ([EKVirtualConferenceRoomTypeDescriptor]?, Error?) -> Void) {
    // Create two rooms, one for the user's personal room and a
    // second room for team events.
    let personalRoom = EKVirtualConferenceRoomTypeDescriptor(
        title: "Maria's Personal Room",
        identifier: "personal-room"
    )
    let teamRoom = EKVirtualConferenceRoomTypeDescriptor(
        title: "Team Room",
        identifier: "team-room"
    )

    // Call the completion handler with an array that contains
    // both rooms.
    let allRooms = [personalRoom, teamRoom]
    completionHandler(allRooms, nil)
}
```

If your virtual conference provider is unable to provide any room types, call the completion handler with `nil` for the array and an error that describes why rooms aren’t available.

Users choose one of the room type descriptors when adding an event to their calendar. To complete the process of adding the event, EventKit calls fetchVirtualConference(identifier:completionHandler:) and passes the room type descriptor that the user selects.

