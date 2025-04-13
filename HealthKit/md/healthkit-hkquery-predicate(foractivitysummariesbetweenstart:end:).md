

- HealthKit
- HKQuery
-  predicate(forActivitySummariesBetweenStart:end:) 

Type Method

# predicate(forActivitySummariesBetweenStart:end:)

Returns a predicate for matching all the activity summaries that fall between the days identified by the start and end date components.

iOS 9.3+iPadOS 9.3+Mac Catalyst 13.0+macOS 13.0+visionOS 1.0+watchOS 2.2+

``` source
class func predicate(
    forActivitySummariesBetweenStart startDateComponents: DateComponents,
    end endDateComponents: DateComponents
) -> NSPredicate
```

## Parameters 

`startDateComponents`  

Date components that uniquely identify the start day as perceived by the user. This day may be longer or shorter than 24 hours (for example, if the user traveled across time zones).

The date components must have a valid calendar property.

`endDateComponents`  

Date components that uniquely identify the end day as perceived by the user. This day may be longer or shorter than 24 hours (for example, if the user traveled across time zones).

The date components must have a valid calendar property.

## Return Value

A predicate for matching activity summaries spanning a range of days.

## Discussion

Use this convenience method to create a predicate that matches activity summaries that fall between the specified days. The following sample uses both the convenience method and a predicate format string to create equivalent predicates.

- Swift
- Objective-C

```
let forDays =
    HKQuery.predicateForActivitySummariesBetweenStartDateComponents(startDateComponents, endDateComponents: endDateComponents)
let explicitForDays =
    NSPredicate(format: "%K >= %@ AND %K 

```
NSPredicate *forDay =
[HKQuery HKQuery.predicateForActivitySummariesBetweenStartDateComponents: startDateComponents endDateComponents:endDateComponents];

NSPredicate *explicitforDay =
[NSPredicate predicateWithFormat:@"%K >= %@ AND %K 

## See Also

### Related Documentation

let HKPredicateKeyPathDateComponents: String

The key path for accessing an activity summary’s date components.

### Creating activity summary predicates

class func predicateForActivitySummary(with: DateComponents) -> NSPredicate

Returns a predicate that matches the activity summary for the specified day.

