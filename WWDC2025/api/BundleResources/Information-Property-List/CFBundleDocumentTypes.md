*   [Bundle Resources](/documentation/bundleresources)
*   [Information Property List](/documentation/bundleresources/information-property-list)
*   CFBundleDocumentTypes

Property List Key

# CFBundleDocumentTypes

The document types supported by the bundle.

iOS 2.0+iPadOS 2.0+macOS 10.0+tvOS 9.0+visionOS 1.0+watchOS 2.0+

## [Details](/documentation/BundleResources/Information-Property-List/CFBundleDocumentTypes#details)

Name

Document types

Type

array of dictionaries

## [Topics](/documentation/BundleResources/Information-Property-List/CFBundleDocumentTypes#topics)

### [Property List Keys](/documentation/BundleResources/Information-Property-List/CFBundleDocumentTypes#Property-List-Keys)

[`CFBundleTypeIconFile`](/documentation/bundleresources/information-property-list/cfbundledocumenttypes/cfbundletypeiconfile)

The icon to associate with the document type.

**Name:** Icon File Name

[`CFBundleTypeName`](/documentation/bundleresources/information-property-list/cfbundledocumenttypes/cfbundletypename)

The abstract name for the document type.

**Name:** Document Type Name

[`CFBundleTypeRole`](/documentation/bundleresources/information-property-list/cfbundledocumenttypes/cfbundletyperole)

The app’s role with respect to the document type.

**Name:** Role

[`LSHandlerRank`](/documentation/bundleresources/information-property-list/cfbundledocumenttypes/lshandlerrank)

The ranking of this app among apps that declare themselves as editors or viewers of the given file type.

**Name:** Handler rank

[`LSItemContentTypes`](/documentation/bundleresources/information-property-list/cfbundledocumenttypes/lsitemcontenttypes)

The document file types the app supports.

**Name:** Document Content Type UTIs

[`LSTypeIsPackage`](/documentation/bundleresources/information-property-list/cfbundledocumenttypes/lstypeispackage)

A Boolean value indicating whether the document is distributed as a bundle.

**Name:** Document is a package or bundle

[`NSDocumentClass`](/documentation/bundleresources/information-property-list/cfbundledocumenttypes/nsdocumentclass)

The subclass used to create instances of this document.

**Name:** Cocoa NSDocument Class

[`NSExportableTypes`](/documentation/bundleresources/information-property-list/cfbundledocumenttypes/nsexportabletypes)

The file types that this document can be exported to.

**Name:** Exportable Type UTIs

## [See Also](/documentation/BundleResources/Information-Property-List/CFBundleDocumentTypes#see-also)

### [Documents](/documentation/BundleResources/Information-Property-List/CFBundleDocumentTypes#Documents)

[`UISupportsDocumentBrowser`](/documentation/bundleresources/information-property-list/uisupportsdocumentbrowser)

A Boolean value indicating whether the app is a document-based app.

**Name:** Supports Document Browser

[`LSSupportsOpeningDocumentsInPlace`](/documentation/bundleresources/information-property-list/lssupportsopeningdocumentsinplace)

A Boolean value indicating whether the app may open the original document from a file provider, rather than a copy of the document.

**Name:** Supports opening documents in place

[`NSDownloadsUbiquitousContents`](/documentation/bundleresources/information-property-list/nsdownloadsubiquitouscontents)

A Boolean value that indicates whether the system should download documents before handing them over to the app.