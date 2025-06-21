Framework

# Core Spotlight

Add search capabilities to your app, and index your content so people can find it from Spotlight and Safari.

iOS 9.0+iPadOS 9.0+Mac Catalyst 13.0+macOS 10.13+visionOS 1.0+

## [Overview](/documentation/CoreSpotlight#overview)

Help people access activities and items within your app by adding details about those items to a Core Spotlight index. The framework provides APIs to add your content to an index, and search for items in that index. You decide what content makes sense to index, but typically you index anything that someone might look for in your app. For example, you might index photos, contacts, the items someone purchased, or data they see in your interface. You can then use Core Spotlight to search for your indexed content and display those results in your app.

Your app is responsible for indexing your app’s content and maintaining those indexes. You can index content when your app runs, or provide an app extension to index content when the system requests it. You can index any content your app manages, including files and other content that your app isn’t currently displaying. The indexes you create using Core Spotlight remain on device, and are private to the owner of the device. Devices don’t share indexed data with Apple, or synchronize that data with the person’s other devices.

In addition to indexing content, iOS provides additional strategies for making your app’s content searchable:

*   Use the search-related properties of [`NSUserActivity`](/documentation/Foundation/NSUserActivity) to add items to the on-device index, with the option to identify the items as eligible for public indexing. Learn more about [`NSUserActivity`](/documentation/Foundation/NSUserActivity) in [Index Activities and Navigation Points](https://developer.apple.com/library/content/documentation/General/Conceptual/AppSearch/Activities.html#//apple_ref/doc/uid/TP40016308-CH6-SW1).
    
*   Use web markup to index content on your web server in Apple’s server-side index, which makes the data available to all iOS users in Spotlight and Safari search results. For more information, see [Mark Up Web Content](https://developer.apple.com/library/content/documentation/General/Conceptual/AppSearch/WebContent.html#//apple_ref/doc/uid/TP40016308-CH8-SW1) in [App Search Programming Guide](https://developer.apple.com/library/content/documentation/General/Conceptual/AppSearch/index.html).
    

## [Topics](/documentation/CoreSpotlight#topics)

### [Essentials](/documentation/CoreSpotlight#Essentials)

[

Adding your app’s content to Spotlight indexes](/documentation/corespotlight/adding-your-app-s-content-to-spotlight-indexes)

Create a description for your app’s content and add it to a Spotlight index to make it searchable.

[

Enabling Apple Intelligence summarization and prioritization](/documentation/corespotlight/enable-apple-intelligence-summaries)

Summarize and prioritize app content using Spotlight extensions.

### [Searchable items](/documentation/CoreSpotlight#Searchable-items)

```swift
```swift
```swift
```swift
class CSSearchableItem
```
```

The details of your app-specific content that someone might search for on their devices.
```
```swift
```swift
```swift
class CSSearchableItemAttributeSet
```
```

The detailed metadata for a searchable item.
```
```swift
```swift
```swift
class CSCustomAttributeKey
```
```

A key associated with a custom attribute for a searchable item.
```
```swift
```swift
```swift
class CSLocalizedString
```
```

An object that displays localized text in search results related to your app.
```
```swift
```swift
```swift
class CSPerson
```
```

An object that represents a person in the context of search results.
```
```

### [Indexes](/documentation/CoreSpotlight#Indexes)

```swift
```swift
```swift
```swift
class CSSearchableIndex
```
```

An on-device index for your app’s searchable content.
```
```swift
```swift
```swift
protocol CSSearchableIndexDelegate
```
```

A protocol that defines methods a delegate object or app extension uses to handle communication from the on-device index.
```
```

### [Spotlight app extensions](/documentation/CoreSpotlight#Spotlight-app-extensions)

[

Regenerating your app’s indexes on demand](/documentation/corespotlight/regenerating-your-app-s-indexes-on-demand)

Create an app extension to maintain your app’s indexes and regenerate them as needed.

```swift
```swift
```swift
class CSIndexExtensionRequestHandler
```
```

An interface that implements an index-maintenance app extension.
```
```swift
```swift
```swift
class CSImportExtension
```
```

An object that provides searchable attributes for file types that the app supports.
```

### [Queries](/documentation/CoreSpotlight#Queries)

[

Building a search interface for your app](/documentation/corespotlight/building-a-search-interface-for-your-app)

Add a search interface to your app to execute Spotlight queries and offer suggested text completions.

[

Searching for information in your app](/documentation/corespotlight/searching-for-information-in-your-app)

Search for app-specific content and refine search results using predicates and filters.

```swift
```swift
```swift
class CSUserQuery
```
```

A type you use to initiate searches from your interface and offer suggested text completions.
```
```swift
```swift
```swift
class CSUserQueryContext
```
```

The configuration details to apply to a user query.
```
```swift
```swift
```swift
class CSSearchQuery
```
```

A type you use to programmatically search the indexed app content.
```
```swift
```swift
```swift
class CSSearchQueryContext
```
```

The behavior configuration to use for a search query.
```
```swift
```swift
```swift
class CSSuggestion
```
```

The kind of suggestion to use in a query.
```

### [Errors](/documentation/CoreSpotlight#Errors)

```swift
```swift
```swift
```swift
struct CSIndexError
```
```

Index errors returned by Core Spotlight.
```
```swift
```swift
```swift
struct CSSearchQueryError
```
```

Search query errors returned by Core Spotlight.
```

[

API Reference

CSIndex Errors](/documentation/corespotlight/csindex-errors)

Index error codes and error domain.

[

API Reference

CSSearchQuery Errors](/documentation/corespotlight/cssearchquery-errors)

Search query error codes and error domain.
```

### [Version](/documentation/CoreSpotlight#Version)

```swift
```swift
```swift
```swift
var CoreSpotlightAPIVersion: Int32
```
```

The API version number for Core Spotlight.
```
```