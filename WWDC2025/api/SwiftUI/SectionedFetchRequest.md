*   [SwiftUI](/documentation/swiftui)
*   SectionedFetchRequest

Structure

# SectionedFetchRequest

A property wrapper type that retrieves entities, grouped into sections, from a Core Data persistent store.

iOS 15.0+iPadOS 15.0+Mac Catalyst 15.0+macOS 12.0+tvOS 15.0+visionOS 1.0+watchOS 8.0+

```swift
```swift
```swift
```swift
```swift
```swift
```swift

```swift
@[`MainActor`](/documentation/Swift/MainActor) @propertyWrapper @preconcurrency
struct SectionedFetchRequest<SectionIdentifier, Result> where SectionIdentifier : [`Hashable`](/documentation/Swift/Hashable), Result : [`NSFetchRequestResult`](/documentation/CoreData/NSFetchRequestResult)
```

```
```
```
```
```
```
```

## [Overview](/documentation/SwiftUI/SectionedFetchRequest#overview)

Use a `SectionedFetchRequest` property wrapper to declare a [`SectionedFetchResults`](/documentation/swiftui/sectionedfetchresults) property that provides a grouped collection of Core Data managed objects to a SwiftUI view. If you don’t need sectioning, use [`FetchRequest`](/documentation/swiftui/fetchrequest) instead.

Configure a sectioned fetch request with an optional predicate and sort descriptors, and include a `sectionIdentifier` parameter to indicate how to group the fetched results. Be sure that you choose sorting and sectioning that work together to avoid discontiguous sections. For example, you can request a list of earthquakes, composed of `Quake` managed objects that the [Loading and Displaying a Large Data Feed](/documentation/swiftui/loading_and_displaying_a_large_data_feed) sample code project defines to store earthquake data, sorted by time and grouped by date:

```swift

```swift
@SectionedFetchRequest<String, Quake>(
    sectionIdentifier: \.day,
    sortDescriptors: [SortDescriptor(\.time, order: .reverse)]
)
private var quakes: SectionedFetchResults<String, Quake>
```

```

Always declare properties that have a sectioned fetch request wrapper as private. This lets the compiler help you avoid accidentally setting the property from the memberwise initializer of the enclosing view.

The request infers the entity type from the `Result` type that you specify, which is `Quake` in the example above. Indicate a `SectionIdentifier` type to declare the type found at the fetched object’s `sectionIdentifier` key path. The section identifier type must conform to the [`Hashable`](/documentation/Swift/Hashable) protocol.

The example above depends on the `Quake` type having a `day` property that’s either a stored or computed string. Be sure to mark any computed property with the `@objc` attribute for it to function as a section identifier. For best performance with large data sets, use stored properties.

The sectioned fetch request and its results use the managed object context stored in the environment, which you can access using the [`managedObjectContext`](/documentation/swiftui/environmentvalues/managedobjectcontext) environment value. To support user interface activity, you typically rely on the [`viewContext`](/documentation/CoreData/NSPersistentContainer/viewContext) property of a shared [`NSPersistentContainer`](/documentation/CoreData/NSPersistentContainer) instance. For example, you can set a context on your top-level content view using a shared container that you define as part of your model:

```

```
ContentView()
    .environment(
        \.managedObjectContext,
        QuakesProvider.shared.container.viewContext)
```

```

When you need to dynamically change the section identifier, predicate, or sort descriptors, access the request’s [`SectionedFetchRequest.Configuration`](/documentation/swiftui/sectionedfetchrequest/configuration) structure, either directly or with a binding.

## [Topics](/documentation/SwiftUI/SectionedFetchRequest#topics)

### [Creating a fetch request](/documentation/SwiftUI/SectionedFetchRequest#Creating-a-fetch-request)

[`init(sectionIdentifier:sortDescriptors:predicate:animation:)`](/documentation/swiftui/sectionedfetchrequest/init\(sectionidentifier:sortdescriptors:predicate:animation:\))

Creates a sectioned fetch request based on a section identifier, a predicate, and reference type sort parameters.

[`init(entity: NSEntityDescription, sectionIdentifier: KeyPath<Result, SectionIdentifier>, sortDescriptors: [NSSortDescriptor], predicate: NSPredicate?, animation: Animation?)`](/documentation/swiftui/sectionedfetchrequest/init\(entity:sectionidentifier:sortdescriptors:predicate:animation:\))

Creates a sectioned fetch request for a specified entity description, based on a section identifier, a predicate, and sort parameters.

### [Creating a fully configured fetch request](/documentation/SwiftUI/SectionedFetchRequest#Creating-a-fully-configured-fetch-request)

[`init(fetchRequest: NSFetchRequest<Result>, sectionIdentifier: KeyPath<Result, SectionIdentifier>, animation: Animation?)`](/documentation/swiftui/sectionedfetchrequest/init\(fetchrequest:sectionidentifier:animation:\))

Creates a fully configured sectioned fetch request that uses the specified animation when updating results.

[`init(fetchRequest: NSFetchRequest<Result>, sectionIdentifier: KeyPath<Result, SectionIdentifier>, transaction: Transaction)`](/documentation/swiftui/sectionedfetchrequest/init\(fetchrequest:sectionidentifier:transaction:\))

Creates a fully configured sectioned fetch request that uses the specified transaction when updating results.

### [Configuring a request dynamically](/documentation/SwiftUI/SectionedFetchRequest#Configuring-a-request-dynamically)

```swift
```swift
```swift
```swift
struct Configuration
```
```

The request’s configurable properties.
```
```swift
```swift
```swift
var projectedValue: Binding<SectionedFetchRequest<SectionIdentifier, Result>.Configuration>
```
```

A binding to the request’s mutable configuration properties.
```
```

### [Getting the fetched results](/documentation/SwiftUI/SectionedFetchRequest#Getting-the-fetched-results)

```swift
```swift
```swift
```swift
func update()
```
```

Updates the fetched results.
```
```swift
```swift
```swift
var wrappedValue: SectionedFetchResults<SectionIdentifier, Result>
```
```

The fetched results of the fetch request.
```
```

### [Default Implementations](/documentation/SwiftUI/SectionedFetchRequest#Default-Implementations)

[

API Reference

DynamicProperty Implementations](/documentation/swiftui/sectionedfetchrequest/dynamicproperty-implementations)

## [Relationships](/documentation/SwiftUI/SectionedFetchRequest#relationships)

### [Conforms To](/documentation/SwiftUI/SectionedFetchRequest#conforms-to)

*   [`Copyable`](/documentation/Swift/Copyable)
*   [`DynamicProperty`](/documentation/swiftui/dynamicproperty)
    
    Conforms when `SectionIdentifier` conforms to `Hashable` and `Result` conforms to `NSFetchRequestResult`.
    

## [See Also](/documentation/SwiftUI/SectionedFetchRequest#see-also)

### [Accessing Core Data](/documentation/SwiftUI/SectionedFetchRequest#Accessing-Core-Data)

[

Loading and Displaying a Large Data Feed](/documentation/swiftui/loading_and_displaying_a_large_data_feed)

Consume data in the background, and lower memory use by batching imports and preventing duplicate records.

```swift
```swift
```swift
var managedObjectContext: NSManagedObjectContext
```
```
```
```swift
```swift
```swift
struct FetchRequest
```
```

A property wrapper type that retrieves entities from a Core Data persistent store.
```
```swift
```swift
```swift
struct FetchedResults
```
```

A collection of results retrieved from a Core Data store.
```
```swift
```swift
```swift
struct SectionedFetchResults
```
```

A collection of results retrieved from a Core Data persistent store, grouped into sections.
```