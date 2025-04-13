

- WatchKit
- WKInterfaceTimer
-  start() 

Instance Method

# start()

Begins updates to the timer’s display.

watchOS 2.0+

``` source
func start()
```

## Discussion

After setting the target date for the timer, call this method to begin updating the timer object’s displayed text. Further updates to the timer occur automatically on the user’s Apple Watch, without the need for you to do anything else.

This method does not actually affect the actual timer value. The timer begins counting when you set the target date using the setDate(_:) method. This method tells WatchKit to start updating the label containing the timer’s value.

## See Also

### Starting and Stopping the Timer

func stop()

Stops updates to the timer’s display.

