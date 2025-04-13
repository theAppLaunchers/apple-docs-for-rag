

- WebKit
-  WKWebsiteDataRecord 

Class

# WKWebsiteDataRecord

A record of the data that a particular website stores persistently.

iOS 9.0+iPadOS 9.0+Mac Catalyst 13.1+macOS 10.11+visionOS 1.0+

``` source
@MainActor
class WKWebsiteDataRecord
```

## Overview

Use WKWebsiteDataRecord objects to discover the types of information that a website stores. Records identify the data types a website stores, but don’t identify the actual data. You might use this information to help the user manage website data. For example, Safari provides a way for users to view and remove website data. The domain name of each record contains the website’s domain name and suffix.

You don’t create WKWebsiteDataRecord objects directly. WebKit creates these records and stores them in the web view’s data store. Use the fetchDataRecords(ofTypes:completionHandler:) of that data store to retrieve the current record objects. You also use that object to remove unwanted records.

## Topics

### Getting the Record Information

var displayName: String

The display name for the data record.

### Getting the Data Type

var dataTypes: Set&lt;String>

The types of data associated with the record.

Data Store Record Types

Explore the constants that identify the types of data that websites store.

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
- Sendable

## See Also

### Web Data Management

class WKWebsiteDataStore

An object that manages cookies, disk and memory caches, and other types of data for a web view.

class WKHTTPCookieStore

An object that manages the HTTP cookies associated with a particular web view.

protocol WKURLSchemeHandler

A protocol for loading resources with URL schemes that WebKit doesn’t handle.

protocol WKURLSchemeTask

An interface that WebKit uses to request custom resources from your app.

static let readAccessURL: NSAttributedString.DocumentReadingOptionKey

The local files WebKit can access when loading content.

