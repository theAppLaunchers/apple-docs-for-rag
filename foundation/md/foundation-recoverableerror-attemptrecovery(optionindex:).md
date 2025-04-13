

- Foundation
- RecoverableError
-  attemptRecovery(optionIndex:) 

Instance Method

# attemptRecovery(optionIndex:)

Attempt to recover from this error when the user selected the option at the given index. Returns true to indicate successful recovery, and false otherwise.

iOS 8.0+iPadOS 8.0+Mac Catalyst 8.0+macOS 10.10+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
func attemptRecovery(optionIndex recoveryOptionIndex: Int) -> Bool
```

**Required**

## Discussion

This entry point is used for recovery of errors handled at the “application” granularity, where nothing else in the application can proceed until the attempted error recovery completes.

