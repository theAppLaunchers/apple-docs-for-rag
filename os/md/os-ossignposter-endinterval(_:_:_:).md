

- os
- OSSignposter
-  endInterval(\_:\_:\_:) 

Instance Method

# endInterval(\_:\_:\_:)

Ends a signposted interval and attaches the specified message.

iOS 15.0+iPadOS 15.0+Mac CatalystmacOS 12.0+tvOS 15.0+visionOSwatchOS 8.0+

``` source
func endInterval(
    _ name: StaticString,
    _ state: OSSignpostIntervalState,
    _ message: SignpostMetadata
)
```

## Parameters 

`name`  

The signpost’s name.

`state`  

The returned interval state from the matching begin call.

`message`  

The interpolated string that the signposter attaches to the signpost. Each of the message’s interpolations can specify individual formatting and privacy options. For more information, see Message Argument Formatters.

## Discussion

Important

Don’t create an instance of SignpostMetadata. Instead, provide an interpolated string as the `message` parameter and the system converts it automatically.

The signposter uses interval state to enforce the following runtime assertions:

- Multiple end calls don’t consume the same interval state.

- The begin call and end call use the same name.

- The begin call and end call emit signposts to the same underlying log.

- You don’t use the exclusive signpost ID for intervals that cross process boundaries.

In debug builds, any assertion failures result in a crash. In production builds, your app continues to run and, instead, the signposter attaches an error message to the interval’s closing signpost.

If you don’t have access to the returned interval state from the corresponding begin call, or the cost you incur when serializing the state to pass between processes is unacceptable, recreate the interval state by passing the interval’s signpost ID to beginState(id:). For more information about serializing interval state, see OSSignpostIntervalState.

Important

Recreating interval state using the beginState(id:) method bypasses runtime assertions that check for consistency between the beginning and the end of a signposted interval.

The following example shows how to recreate interval state in a scope other than the one that includes the begin call, and also demonstrates the use of message interpolation:

```
// A closure that represents a process in the context of this example.
let processA: (String) -> OSSignpostID = { account in
    // Create a signposter that uses the default subsystem.
    let signposter = OSSignposter()

    // Generate a signpost ID to associate with the signposted interval.
    let signpostID = signposter.makeSignpostID()

    // Begin a signposted interval and attach a message that securely
    // interpolates sensitive data.
    let _ = signposter.beginInterval("Fetch Purchases", id: signpostID,
        "Account: \(account, privacy: .sensitive(mask: .hash))")

    // Return the signpost ID to the caller.
    return signpostID
}

// Another closure representing a different process.
let processB: (OSSignpostID, Int) -> Void = { signpostID, count in
    // Create a signposter that uses the same subsystem as
    // the original, which, in this case, is the default.
    let signposter = OSSignposter()

    // Recreate the interval state using the provided signpost ID.
    let state = OSSignpostIntervalState.beginState(id: signpostID)

    // End the signposted interval using the recreated state and 
    // attach a message that interpolates a value using custom 
    // alignment.
    signposter.endInterval("Fetch Purchases", state,
        "Fetched \(count, align: .right(columns: 6)) purchases.")
}

// Execute the two closures.
let signpostID = processA("123456768")
processB(signpostID, 49)
```

## See Also

### Stopping a Signposted Interval

func endInterval(StaticString, OSSignpostIntervalState)

Ends the signposted interval that corresponds to the specified name and state.

