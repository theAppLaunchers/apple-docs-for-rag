

- Core Motion
- CMMovementDisorderManager
-  monitorKinesiasExpirationDate() 

Instance Method

# monitorKinesiasExpirationDate()

Returns the expiration date for the most recent monitoring period.

watchOS 5.0+

``` source
func monitorKinesiasExpirationDate() -> Date?
```

## Return Value

The current expiration date, or `nil` if you have not yet begun monitoring.

## Discussion

This date is set when you call the monitorKinesias(forDuration:) method. You can extend the date by calling monitorKinesias(forDuration:) again; however, you can’t shorten the monitoring duration.

You can use the expiration date to determine whether you are currently monitoring the user.

```
guard let experiationDate = movementDisorderManager.monitorKinesiasExpirationDate() else {
    // You haven't started monitoring the user.
    return
}

if experiationDate > Date() {
    // Currently monitoring the user.
} else {
    // The monitoring period has ended.
}
```

## See Also

### Recording Movement Disorders

func monitorKinesias(forDuration: TimeInterval)

Calculate and store tremor and dyskinetic symptom results for the duration of the specified time interval.

