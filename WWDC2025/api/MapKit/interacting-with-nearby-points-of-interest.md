*   [MapKit](/documentation/mapkit)
*   [MapKit for AppKit and UIKit](/documentation/mapkit/mapkit-for-appkit-and-uikit)
*   Interacting with nearby points of interest

Sample Code

# Interacting with nearby points of interest

Provide automatic search completions for a partial search query, search the map for relevant locations nearby, and retrieve details for selected points of interest.

[Download](https://docs-assets.developer.apple.com/published/97c441e2ff4d/InteractingWithNearbyPointsOfInterest.zip)

iOS 18.0+iPadOS 18.0+visionOS 2.2+Xcode 16.2+

## [Overview](/documentation/MapKit/interacting-with-nearby-points-of-interest#Overview)

This sample code project demonstrates how to programmatically search for map-based addresses and points of interest using a natural language string, and how to get more information about points of interest that a person selects on the map. The search results center around the locations visible in the map view.

### [Request search completions](/documentation/MapKit/interacting-with-nearby-points-of-interest#Request-search-completions)

[`MKLocalSearchCompleter`](/documentation/mapkit/mklocalsearchcompleter) retrieves autocomplete suggestions for a partial search query within a map region. A person can type “cof”, and a search completion suggests “coffee” as the query string. As the person types a query into a search bar, the sample app updates the query. In SwiftUI, the sample creates the search field using the [`searchable(text:placement:prompt:)`](/documentation/SwiftUI/View/searchable\(text:placement:prompt:\)) modifier.

```

```
.searchable(text: $searchQuery, placement: .navigationBarDrawer(displayMode: .always), prompt: searchPrompt)
```

```

As someone types a query into a search bar, the sample app updates the [`queryFragment`](/documentation/mapkit/mklocalsearchcompleter/queryfragment) for the search completion through the `searchQuery` binding.

```swift

```swift
/// Ask for completion suggestions based on the query text.
```swift
```swift
func provideCompletionSuggestions(for query: String) {
```
```
    /**
     Configure the search to return completion results based only on the options in the app. For example,
     someone can configure the app to exclude specific point-of-interest categories, or to only return results for addresses.
     */
    searchCompleter?.resultTypes = mapConfiguration.resultType.completionResultType
    searchCompleter?.regionPriority = mapConfiguration.regionPriority.localSearchRegionPriority
    if mapConfiguration.resultType == .pointsOfInterest {
        searchCompleter?.pointOfInterestFilter = mapConfiguration.pointOfInterestOptions.filter
    } else if mapConfiguration.resultType == .addresses {
        searchCompleter?.addressFilter = mapConfiguration.addressOptions.filter
    }
    
    searchCompleter?.region = mapConfiguration.region
    searchCompleter?.queryFragment = query
}
```

```

### [Receive completion results](/documentation/MapKit/interacting-with-nearby-points-of-interest#Receive-completion-results)

Completion results represent fully formed query strings based on the query fragment someone types. The sample app uses completion results to populate UI elements to quickly fill in a search query. The app receives the latest completion results as an array of [`MKLocalSearchCompletion`](/documentation/mapkit/mklocalsearchcompletion) objects by adopting the [`MKLocalSearchCompleterDelegate`](/documentation/mapkit/mklocalsearchcompleterdelegate) protocol.

```swift

```swift
nonisolated func completerDidUpdateResults(_ completer: MKLocalSearchCompleter) {
    Task { @MainActor in
        /**
         As a person types, new completion suggestions continuously return to this method. Update the property storing the current
         results, so that the app UI can observe the change and display the updated suggestions.
         */
        let suggestedCompletions = completer.results
        resultStreamContinuation?.yield(suggestedCompletions)
    }
}
```

```

The app uses an [`AsyncStream`](/documentation/Swift/AsyncStream) to deliver the completion results to the UI, which the `SidebarView` stores in its `searchCompletions` property. The app displays the search suggestions with the [`searchSuggestions(_:)`](/documentation/SwiftUI/View/searchSuggestions\(_:\)) modifier, which takes a binding to the `searchCompletions` property.

```swift

```swift
.searchSuggestions {
    // Treat each `MKMapItem` object as unique, using `\.self` for the identity. The `identifier` property of `MKMapItem`
    // is an optional value, and the meaning of the identifier for `MKMapItem` doesn't have the same semantics as
    // the `Identifable` protocol that `ForEach` requires.
    ForEach($searchCompletions, id: \.self) { completion in
        SearchCompletionItemView(completion: completion.wrappedValue)
        .onTapGesture {
            convertSearchCompletionToSearchResults(completion.wrappedValue)
        }
    }
}
```

```

### [Highlight the relationship of a query fragment to the suggestion](/documentation/MapKit/interacting-with-nearby-points-of-interest#Highlight-the-relationship-of-a-query-fragment-to-the-suggestion)

Within the UI elements that represent each query result, the sample code uses the [`titleHighlightRanges`](/documentation/mapkit/mklocalsearchcompletion/titlehighlightranges) on an `MKLocalSearchCompletion` to show how the query someone enters relates to the suggested result. For example, the following code applies a highlight with [`NSAttributedString`](/documentation/Foundation/NSAttributedString):

```swift

```swift
private func createHighlightedString(text: String, rangeValues: [NSValue]) -> NSAttributedString {
    let attributes = [NSAttributedString.Key.backgroundColor: UIColor(named: "suggestionHighlight")!]
    let highlightedString = NSMutableAttributedString(string: text)
    // Each `NSValue` wraps an `NSRange` that functions as a style attribute's range with `NSAttributedString`.
    let ranges = rangeValues.map { $0.rangeValue }
    for range in ranges {
        highlightedString.addAttributes(attributes, range: range)
    }
    return highlightedString
}
```

```

### [Search for map items](/documentation/MapKit/interacting-with-nearby-points-of-interest#Search-for-map-items)

An `MKLocalSearch.Request` takes either an `MKLocalSearchCompletion` or a natural language query string, and returns an array of [`MKMapItem`](/documentation/mapkit/mkmapitem) objects. Each `MKMapItem` represents a geographic location, like a specific address, that matches the search query. The sample code asynchronously retrieves the array of `MKMapItem` objects by calling [`start(completionHandler:)`](/documentation/mapkit/mklocalsearch/start\(completionhandler:\)) on [`MKLocalSearch`](/documentation/mapkit/mklocalsearch).

```swift
```swift
```swift
```swift
```swift
```swift
let search = MKLocalSearch(request: request)
```
```
currentSearch = search
defer {
    // After the search completes, the reference is no longer needed.
    currentSearch = nil
}
```swift
```swift
var results: [MKMapItem]
```
```
do {
    let response = try await search.start()
    results = response.mapItems
} catch let error {
    searchLogging.error("Search error: \(error.localizedDescription)")
    results = []
}
```
```
```
```

### [Allow someone to select points of interest on the map](/documentation/MapKit/interacting-with-nearby-points-of-interest#Allow-someone-to-select-points-of-interest-on-the-map)

If a person is exploring the map, they can get information for a point of interest by tapping it. To provide these interactions, the sample code enables selectable map features as follows:

```

```
// Use the standard map style, with an option to display specific point-of-interest categories.
.mapStyle(.standard(pointsOfInterest: mapModel.searchConfiguration.pointOfInterestOptions.categories))
// Only allow selection for points of interest, and disable selection of other labels, like city names.
.mapFeatureSelectionDisabled { feature in
    feature.kind != MapFeature.FeatureKind.pointOfInterest
}
/*
 The selection accessory allows people to tap on map features and get more detailed information, which displays
 as either a sheet or a callout according to the `style` parameter. Along with the `selection` binding, this determines
 which feature to display additional information for.
 
 This modifier differs from the `mapItemDetailSelectionAccessory(:_) modifier, which enables the same selection
 behaviors on annotations that the app adds to `Map` for search results.
 */
.mapFeatureSelectionAccessory(.automatic)
```

```

When someone taps a point of interest, the system presents the map item’s details, including information like a phone number, business hours, and buttons to start navigation to the location using Apple Maps. The system presents the information using the style that the `mapFeatureSelectionAccessory(_:)` modifier configures. The sample app uses the [`automatic`](/documentation/mapkit/mapitemdetailselectionaccessorystyle/automatic) style, but the [`MapItemDetailSelectionAccessoryStyle`](/documentation/mapkit/mapitemdetailselectionaccessorystyle) structure offers several other options.

### [Persist and retrieve map items](/documentation/MapKit/interacting-with-nearby-points-of-interest#Persist-and-retrieve-map-items)

If someone is exploring the map, they may want the app to store places they looked at so that they can come back to them later, including across app launches. `MKMapItem` has an [`identifier`](/documentation/mapkit/mkmapitem/identifier-swift.property) property, which the app stores in its `VisitedPlace` model using `SwiftData`.

```swift

```swift
guard let identifier = mapItem.identifier else { return }
```swift
```swift
let visit = VisitedPlace(id: identifier.rawValue)
```
```
```

```

When the app launches, it retrieves the history of visited locations from SwiftData. To get the `MKMapItem` from the previously stored identifier, the app creates an [`MKMapItemRequest`](/documentation/mapkit/mkmapitemrequest) with the stored identifier and calls [`getMapItem(completionHandler:)`](/documentation/mapkit/mkmapitemrequest/getmapitem\(completionhandler:\)).

```swift

```swift
@MainActor
```swift
```swift
func convertToMapItem() async -> MKMapItem? {
```
```
    guard let identifier = MKMapItem.Identifier(rawValue: id) else { return nil }
    let request = MKMapItemRequest(mapItemIdentifier: identifier)
    var mapItem: MKMapItem? = nil
    do {
        mapItem = try await request.mapItem
    } catch let error {
        let logger = Logger(subsystem: Bundle.main.bundleIdentifier!, category: "Map Item Requests")
        logger.error("Getting map item from identifier failed. Error: \(error.localizedDescription)")
    }
    return mapItem
}
```

```

## [See Also](/documentation/MapKit/interacting-with-nearby-points-of-interest#see-also)

### [Local search](/documentation/MapKit/interacting-with-nearby-points-of-interest#Local-search)

```swift
```swift
```swift
```swift
enum MKLocalSearchRegionPriority
```
```

A value that indicates the importance of the configured region.
```
```swift
```swift
```swift
struct ResultType
```
```

Options that indicate types of search results.
```
```swift
```swift
```swift
class MKLocalSearch
```
```

A utility object for initiating map-based searches and processing the results.
```
```swift
```swift
```swift
struct Options
```
```

A structure that contains options for filtering results in a search.
```
```swift
```swift
```swift
class MKAddressFilter
```
```

An object that filters which address options to include or exclude in search results.
```
```swift
```swift
```swift
struct ResultType
```
```

Options that indicate types of search completions.
```
```swift
```swift
```swift
class MKLocalSearchCompleter
```
```

A utility object for generating a list of completion strings based on a partial search string that you provide.
```
```swift
```swift
```swift
class MKLocalSearchCompletion
```
```

A fully formed string that completes a partial string.
```
```swift
```swift
```swift
class MKLocalPointsOfInterestRequest
```
```

A structured request to use when searching for points of interest.
```
```