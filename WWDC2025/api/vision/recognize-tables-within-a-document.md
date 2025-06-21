*   [Vision](/documentation/vision)
*   Recognizing tables within a document Beta

Sample Code

# Recognizing tables within a document

Scan a document containing a contact table and extract the content within the table in a formatted way.

[Download](https://docs-assets.developer.apple.com/published/ac3602c841c7/RecognizingTablesWithinADocument.zip)

iOS 26.0+BetaiPadOS 26.0+BetaXcode 26.0+Beta

## [Overview](/documentation/Vision/recognize-tables-within-a-document#Overview)

Note

This sample code project is associated with WWDC25 session 272: [Reading documents using Vision](https://developer.apple.com/videos/play/wwdc2025/272).

### [Configure the sample code project](/documentation/Vision/recognize-tables-within-a-document#Configure-the-sample-code-project)

Because this sample app requires camera access, you’ll need to build and run this sample on a device. The first time you run this sample on device, you need to grant the app access to the camera. In the sample project’s `assets` folder, open the `sampleDocuments.png` file and use the rear camera on iPad or iPhone. Optionally, if you have access to a printer, print this file and try scanning it with your device.

## [See Also](/documentation/Vision/recognize-tables-within-a-document#see-also)

### [Text detection](/documentation/Vision/recognize-tables-within-a-document#Text-detection)

[

Locating and displaying recognized text](/documentation/vision/locating-and-displaying-recognized-text)

Perform text recognition on a photo using the Vision framework’s text-recognition request.

```swift
```swift
```swift
struct RecognizeDocumentsRequest
```
```

An image-analysis request to scan an image of a document and provide information about its structure.

Beta
```
```swift
```swift
```swift
struct DocumentObservation
```
```

Information about the sections of content that an image-analysis request detects in a document.

Beta
```
```swift
```swift
```swift
struct DetectTextRectanglesRequest
```
```

An image-analysis request that finds regions of visible text in an image.
```
```swift
```swift
```swift
struct RecognizeTextRequest
```
```

An image-analysis request that recognizes text in an image.
```

Beta Software

This documentation contains preliminary information about an API or technology in development. This information is subject to change, and software implemented according to this documentation should be tested with final operating system software.

[Learn more about using Apple's beta software](https://developer.apple.com/support/beta-software/)