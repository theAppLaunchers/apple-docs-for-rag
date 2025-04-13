

- DeviceActivity
- DeviceActivityEvent
-  init(applications:categories:webDomains:threshold:) 

Initializer

# init(applications:categories:webDomains:threshold:)

Creates a new event.

iOS 15.0+iPadOS 15.0+Mac Catalyst 15.0+

``` source
init(
    applications: Set = [],
    categories: Set = [],
    webDomains: Set = [],
    threshold: DateComponents
)
```

## Parameters 

`applications`  

An optional list of applications to include in the event. A small subset of popular App Store apps have known associated web domains that get included implicitly. For example, an event that includes an app implicitly includes usage of the app’s web domain.

`categories`  

An optional list of categories to include in the event.

`webDomains`  

An optional list of web domains to include in the event. Some web domains have associated apps included implicitly.

`threshold`  

The amount of time that results in a callback to a DeviceActivityMonitor.

## Discussion

An application’s extension receives a callback once the combination of specified applications, categories, and webDomains have been in use longer than the event’s threshold within the activity’s scheduled interval. If your app didn’t specify any `applications`, `categories`, or `webDomains`, the event includes all `applications`, `categories`, and `web domains`.

Important

When your app calls startMonitoring(_:during:events:) and the event’s schedule is active, the system will only consider the person’s device activity when it starts monitoring the event.

## See Also

### Creating an Event

struct Name

The unique name of an event.

var includesAllActivity: Bool

A Boolean value that indicates whether the event includes all applications, categories, and web domains.

