

- Vision
- VNImageRequestHandler
-  perform(\_:) 

Instance Method

# perform(\_:)

Schedules Vision requests to perform.

iOS 11.0+iPadOS 11.0+Mac Catalyst 13.1+macOS 10.13+tvOS 11.0+visionOS 1.0+

``` source
func perform(_ requests: [VNRequest]) throws
```

## Parameters 

`requests`  

An array of Vision requests to perform.

## Discussion

The function returns after all requests have either completed or failed. Check individual requests and errors for their respective successes and failures.

