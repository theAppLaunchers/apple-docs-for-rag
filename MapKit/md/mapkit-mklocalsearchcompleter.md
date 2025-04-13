

- MapKit
-  MKLocalSearchCompleter 

Class

# MKLocalSearchCompleter

A utility object for generating a list of completion strings based on a partial search string that you provide.

iOS 9.3+iPadOS 9.3+Mac Catalyst 13.1+macOS 10.11.4+tvOS 9.2+visionOS 1.0+

``` source
class MKLocalSearchCompleter
```

## Overview

You use an MKLocalSearchCompleter object to retrieve auto-complete suggestions for your own map-based search controls. As the user types text, you feed the current text string into the search completer object, which delivers possible string completions that match locations or points of interest.

You create and configure MKLocalSearchCompleter objects yourself. You must always assign a delegate object to the search completer so that you can receive the search results that it generates. Specify a search region to restrict results to a designated area. The following code shows a simple example of a view controller that stores the MKLocalSearchCompleter object in a property. The view controller itself acts as the delegate for the completer and the view controller uses the region associated with an MKMapView object that’s part of the view controller’s interface. Completer objects are long-lived objects, so you can store strong references to them and reuse them later in your code.

Listing 1. Creating and configuring a search completer

- Swift
- Objective-C

```
override func viewDidLoad() {
    super.viewDidLoad()

    completer = MKLocalSearchCompleter()
    completer.delegate = self

    // Limit search results to the map view's current region.
    completer.region = myMapView.region
}
```

```
- (void)viewDidLoad {
   [super viewDidLoad];

   self.completer = [[MKLocalSearchCompleter alloc] init];
   self.completer.delegate = self;

   // Limit search results to the map view's current region.
   self.completer.region = self.myMapView.region;
}
```

Update the value of the completer’s queryFragment property to begin a search query. You can update this property in real time as the user types new characters into a text field because the completer object waits a short amount of time for the query string to stabilize. When modifications to the query string stop, the completer initiates a new search and returns the results to your delegate as an array of MKLocalSearchCompletion objects.

## Topics

### Receiving the search results

var delegate: (any MKLocalSearchCompleterDelegate)?

The object that receives the completion results.

protocol MKLocalSearchCompleterDelegate

Methods the delegate calls with search completion data.

### Specifying the query attributes

var addressFilter: MKAddressFilter?

A filter that lists which address options to include or exclude in search results.

var queryFragment: String

The search string that you want completions for.

var region: MKCoordinateRegion

The region that defines the geographic scope of the search.

var regionPriority: MKLocalSearchRegionPriority

A value that indicates the importance of the configured region.

var resultTypes: MKLocalSearchCompleter.ResultType

The types of search completions to include.

var pointOfInterestFilter: MKPointOfInterestFilter?

A filter that lists point of interest categories to include or exclude in the search.

var filterType: MKLocalSearchCompleter.FilterType

The filter options for the search results.

Deprecated

enum FilterType

Constants indicating the types of search completions to return.

Deprecated

struct ResultType

Options that indicate types of search completions.

### Canceling the query

func cancel()

Cancels an in-progress search operation.

var isSearching: Bool

A Boolean value that indicates whether a search operation is in progress.

### Getting the current query results

var results: [MKLocalSearchCompletion]

The most recently received search completions.

## Relationships

### Inherits From

- NSObject

### Conforms To

- CVarArg
- CustomDebugStringConvertible
- CustomStringConvertible
- Equatable
- Hashable
- NSObjectProtocol

## See Also

### Local search

Interacting with nearby points of interest

Provide automatic search completions for a partial search query, search the map for relevant locations nearby, and retrieve details for selected points of interest.

enum MKLocalSearchRegionPriority

A value that indicates the importance of the configured region.

struct ResultType

Options that indicate types of search results.

class MKLocalSearch

A utility object for initiating map-based searches and processing the results.

struct Options

A structure that contains options for filtering results in a search.

class MKAddressFilter

An object that filters which address options to include or exclude in search results.

struct ResultType

Options that indicate types of search completions.

class MKLocalSearchCompletion

A fully formed string that completes a partial string.

class MKLocalPointsOfInterestRequest

A structured request to use when searching for points of interest.

