

- Group Activities
-  Joining and managing a shared activity 

Article

# Joining and managing a shared activity

Configure the session when a SharePlay activity starts, and handle events that occur during the lifetime of the activity.

## Overview

When one person in a group starts an activity, other people’s devices display system UI to prompt them to join that activity. When each person joins, the system prepares a GroupSession object for the activity and delivers it to their app. Your app uses that session object to:

- Prepare any required UI.

- Start the activity, monitor its state, and respond to changes.

- Synchronize activity-related information.

For information about how to define activities, see Defining your app’s SharePlay activities. For information about how to start activities, see Presenting SharePlay activities from your app’s UI.

### Join an activity from a background task

Activities can start at any time, so you need to set up an asynchronous handler in your app to listen for when they start. After a participant joins an activity, the system creates a GroupSession object and delivers it to the sessions property of the GroupActivity type you defined. Monitor the sessions property from an asynchronous handler, and process new session objects when they become available.

Configure separate asynchronous handlers for each of your app’s activity types, and use each one to receive new sessions for their activity. In SwiftUI, create your handler by adding the task(priority:_:) modifier to the view containing the UI for the activity, as shown in the example below. Inside the block for the task modifier, wait on the activity’s sessions property using a `for..in` loop. The sessions property contains an AsyncSequence type, which wakes up the task and executes your code when a new session arrives. Use your code to begin the activity in your app.

```
struct ContentView: View {

    var body: some View {
        VStack {
            MyCustomView()
            MyOtherCustomView()
        }
        .task {
            for await session in MyActivity.sessions() {
                // Perform any app-specific tasks...

                // Join the session.
                session.join
            }
        }
    }
}
```

If you’re not using SwiftUI, handle the arrival of sessions using a Task block, as shown in the following example. This block offers the same behavior as the SwiftUI task modifier, and you use it in similar ways. When a new session arrives, update your app’s UI to reflect the current activity, or perform any other tasks you need to prepare for the activity.

```
// Process an asynchronously delivered session.
var task = Task {
    for await session in DrawTogether.sessions() {

        // Perform any app-specific tasks...

        // Join the session.
        session.join()
    }
}
```

Save a reference to any sessions you receive asynchronously and remove those references when the session state changes to GroupSession.State.invalidated(reason:). The system delivers one new session for each joined activity. When the state of the session changes, or when other properties change, the system updates the already delivered session. To detect updates while the session is active, add subscribers to the properties of the GroupSession object.

### Prepare your app’s interface

When your app receives a GroupSession object, start preparing your app’s UI immediately. The activity doesn’t start until you call the join method of the session object you received. However, don’t call that method until you’re ready to display the UI for the activity itself. If your app needs to collect login credentials or download content before starting the activity, present the UI for those tasks and wait for them to complete before you call the join method.

After you join an activity, update your UI as needed to reflect relevant information. In particular:

- Provide a way for people to see who joined the activity, and who hasn’t joined. Some people might not join an activity right away, because they don’t have the app or are doing something else. Keeping everyone informed lets them know who’s aware of the activity details.

- Provide visual cues when someone makes a change, and optionally display information about who made the change. For example, annotate the change temporarily with the person’s identity, or add app-specific messages to the conversation.

- Support people navigating away from an activity but staying on the group FaceTime call or Messages conversation. For activities that involve video playback, support Picture in Picture to continue playback even when someone changes apps.

- Make sure app-specific controls are easy to access.

### Join the session to start the activity

When your app has everything it needs and is ready to start the activity, call the join() method of the GroupSession object. The join() method asks the system to start the activity in your app.  
Even after you call this method, the session remains in the GroupSession.State.waiting state until the system establishes a connection to the activity.

If your call to join() is successful, the system changes the state of the session to GroupSession.State.joined and begins sending information to and from the current device. If you tried to synchronize data after calling join(), but before the system completed the request, those requests remain queued until your session enters the GroupSession.State.joined state. After successfully joining the session, the system expects you to handle session-related changes and messages. For information about how to send messages between participants, see Synchronizing data during a SharePlay activity.

### Accommodate people who arrive late to the session

Participants join activities separately, and people can join immediately or after a delay. If participants need to download your app, or don’t see the invitation to join the activity, they might arrive several minutes after others. If your activity manages state information that all participants require, devise a way to deliver that information to someone who arrives late. For example, a whiteboard app needs to deliver the current whiteboard content to any late joiners.

Consider the experience for people who arrive late to an activity, and plan for it when implementing your activity support. You might create a lobby interface where participants wait until everyone is present, or you might define custom messages to let people catch up with the rest of the group. Choose an experience that makes sense for your app, and remember that every participant is equal in a SharePlay activity. There’s no single activity owner who controls the experience.

To determine when new participants join the session, monitor the activeParticipants property of the session using a separate task. When the list of participants changes, compare the new list with a saved copy your app maintains. When you detect new participants, update them with the current state of the activity.

```
Task {
    for try await updatedParticipants in session.$activeParticipants.values {
        for participant in updatedParticipants {
            // Compare the current list to a saved version you maintain.
        }
    }
}
```

### End the activity for one or more participants

The GroupSession object contains methods to end the session for the current participant or the entire group. When designing your UI, make it clear which option someone is choosing, and call the correct method in response.

When a participant quits your app, switches to a different app, or navigates away from your app’s activity-related UI, call leave() to end the activity for that participant. Other participants remain engaged in the activity until they leave or until someone ends the activity for everyone.

When a participant leaves an activity, the system moves their session to the GroupSession.State.invalidated(reason:) state and stops the flow of information between their device and the rest of the group. When the session moves to this state, it’s safe to discard the session object itself and perform any activity-related cleanup. If the person is still active on the FaceTime call or Messages conversation and rejoins the activity later, the system delivers a new session object to your app.

When you want to end the activity for everyone, call the end() method. This method invalidates the sessions for all participants. Make sure any buttons or UI that calls this method makes it clear that the activity ends for everyone. The session also ends when everyone leaves the activity.

## See Also

### Session management

Drawing content in a group session

Invite your friends to draw on a shared canvas while on a FaceTime call.

class GroupSession

A session for an in-progress activity that synchronizes content among participant devices.

protocol CustomMessageIdentifiable

A type that assigns a custom ID string to messages you send to other devices.

struct Participant

An active participant in a group session.

