

- Core ML
- MLTask
-  resume() 

Instance Method

# resume()

Begins or resumes a machine learning task.

iOS 13.0+iPadOS 13.0+Mac Catalyst 13.1+macOS 10.15+tvOS 14.0+visionOS 1.0+watchOS 6.0+

``` source
func resume()
```

## Discussion

Use this method to start a task for the first time or resumes a task that has paused. Tasks pause when they notify your app’s progress handlers, such as those you provide to an MLUpdateProgressHandlers instance.

## See Also

### Starting and Stopping a Task

func cancel()

Cancels a machine learning task before it completes.

