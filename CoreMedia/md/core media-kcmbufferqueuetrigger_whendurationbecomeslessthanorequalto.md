

- Core Media
-  kCMBufferQueueTrigger_WhenDurationBecomesLessThanOrEqualTo 

Global Variable

# kCMBufferQueueTrigger_WhenDurationBecomesLessThanOrEqualTo

Trigger fires when queue duration becomes less than or equal to the specified duration.

iOSiPadOSMac CatalystmacOStvOSvisionOSwatchOS

``` source
var kCMBufferQueueTrigger_WhenDurationBecomesLessThanOrEqualTo: CMBufferQueueTriggerCondition { get }
```

## See Also

### Constants

var kCMBufferQueueTrigger_WhenDurationBecomesLessThan: CMBufferQueueTriggerCondition

Trigger fires when queue duration becomes less than the specified duration.

var kCMBufferQueueTrigger_WhenDurationBecomesGreaterThan: CMBufferQueueTriggerCondition

Trigger fires when queue duration becomes greater than the specified duration.

var kCMBufferQueueTrigger_WhenDurationBecomesGreaterThanOrEqualTo: CMBufferQueueTriggerCondition

Trigger fires when queue duration becomes greater than or equal to the specified duration.

var kCMBufferQueueTrigger_WhenMinPresentationTimeStampChanges: CMBufferQueueTriggerCondition

Trigger fires when the minimum presentation timestamp changes (triggerDuration is ignored).

var kCMBufferQueueTrigger_WhenMaxPresentationTimeStampChanges: CMBufferQueueTriggerCondition

Trigger fires when the maximum presentation timestamp changes (triggerDuration is ignored).

var kCMBufferQueueTrigger_WhenDataBecomesReady: CMBufferQueueTriggerCondition

Trigger fires when next dequeueable buffer becomes ready (that is, CMBufferQueueDequeueIfDataReady(_:) will now succeed). (triggerDuration is ignored.)

var kCMBufferQueueTrigger_WhenEndOfDataReached: CMBufferQueueTriggerCondition

Trigger fires when CMBufferQueueIsAtEndOfData’s condition becomes true. (triggerDuration is ignored.)

var kCMBufferQueueTrigger_WhenReset: CMBufferQueueTriggerCondition

Trigger fires when CMBufferQueueReset called. (triggerDuration is ignored.)

var kCMBufferQueueTrigger_WhenBufferCountBecomesLessThan: CMBufferQueueTriggerCondition

Trigger fires when buffer count becomes less than the specified threshold number.

var kCMBufferQueueTrigger_WhenBufferCountBecomesGreaterThan: CMBufferQueueTriggerCondition

Trigger fires when buffer count becomes \> the specified threshold number.

var kCMBufferQueueTrigger_WhenDurationBecomesGreaterThanOrEqualToAndBufferCountBecomesGreaterThan: CMBufferQueueTriggerCondition

