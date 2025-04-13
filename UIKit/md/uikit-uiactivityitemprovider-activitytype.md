

- UIKit
- UIActivityItemProvider
-  activityType 

Instance Property

# activityType

The type of the activity object that is expecting the data.

iOS 6.0+iPadOS 6.0+Mac Catalyst 13.1+visionOS 1.0+

``` source
var activityType: UIActivity.ActivityType? { get }
```

## Discussion

The value of this property is `nil` until the user selects an activity. At that time, the value is set and the provider object is submitted to a queue for execution. Thus, you should access this value only after your object’s item method is called.

## See Also

### Accessing the provider attributes

var item: Any

Generates and returns the actual data-bearing object.

var placeholderItem: Any?

The placeholder object you specified at initialization time.

