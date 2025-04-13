

- BrowserEngineKit
- BEScrollViewDelegate
-  scrollView(\_:handle:completion:) 

Instance Method

# scrollView(\_:handle:completion:)

Handles a scroll update, optionally stopping the scroll view from reacting.

iOS 17.4+iPadOS 17.4+tvOS 17.4+visionOS 1.1+

``` source
@MainActor
optional func scrollView(
    _ scrollView: BEScrollView,
    handle scrollUpdate: BEScrollViewScrollUpdate,
    completion: @escaping (Bool) -> Void
)
```

``` source
@MainActor
optional func scrollView(
    _ scrollView: BEScrollView,
    handle scrollUpdate: BEScrollViewScrollUpdate
) async -> Bool
```

## Parameters 

`scrollView`  

The BEScrollView object that receives the scroll update.

`scrollUpdate`  

Information about the scroll update. You need to retrieve the information from this object immediately on the main thread when the system calls your delegate method, otherwise the values may change.

`completion`  

A block that you call when you finish processing the scroll update. Pass `true` as the parameter if you handled the scroll event and the scroll view doesn’t need to react to it; `false` otherwise.

## Overview

When you implement this method, your `BEScrollViewDelegate` receives scroll updates before its delegating scroll view handles them.

The system calls this delegate method on the main queue. Retrieve information from the `scrollUpdate` on the main queue, then process the update asynchronously. Finally, call the `completion` block asynchronously on the main queue, passing `true` as the parameter to stop the scroll view from handling the scroll event; `false` otherwise.

Important

Schedule completion blocks on the main queue in the same order in which you receive scroll updates.

