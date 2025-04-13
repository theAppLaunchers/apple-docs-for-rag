

- XCTest
- XCTIssueReference
-  init(type:compactDescription:detailedDescription:sourceCodeContext:associatedError:attachments:) 

Initializer

# init(type:compactDescription:detailedDescription:sourceCodeContext:associatedError:attachments:)

Creates an issue for a test failure, with descriptions, source code location, error, and attachments.

``` source
init(
    type: XCTIssueReference.IssueType,
    compactDescription: String,
    detailedDescription: String?,
    sourceCodeContext: XCTSourceCodeContext,
    associatedError: (any Error)?,
    attachments: [XCTAttachment]
)
```

## Parameters 

`type`  

A value for classifying an issue that occurs during testing.

`compactDescription`  

A concise description of the issue that doesn’t include transient data and is suitable for use in test run summaries and for aggregation of results across multiple test runs.

`detailedDescription`  

A detailed description of the issue that may include transient data, such as numbers, object identifiers, and timestamps, to help diagnose the issue.

`sourceCodeContext`  

The source code location for the issue, including the filename, line number, and call stack.

`associatedError`  

An optional error to associate with a test issue.

`attachments`  

An array of data that augments a test issue, such as files, images, screenshots, data blobs, or ZIP files.

## See Also

### Initializers

convenience init(type: XCTIssueReference.IssueType, compactDescription: String)

Creates an issue with a compact description for a test failure.

