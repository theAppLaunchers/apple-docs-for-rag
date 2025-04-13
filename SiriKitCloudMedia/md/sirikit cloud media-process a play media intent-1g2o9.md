

- SiriKit Cloud Media
-  Process a Play Media Intent 

Web Service Endpoint

# Process a Play Media Intent

Interpret the user’s request to play a media item, and provide instructions to access a corresponding playback queue.

SiriKit Cloud Media 1.0.2+

## URL

``` source
POST https://cloudextension-testservice.local/api/intent/playMedia
```

## Header Parameters

`Accept-Language`

`string`

 (Required) 

The client’s current user interface language. Respond with localized content for this language, if available.

`Request-Timeout`

`uint32`

 (Required) 

An approximate deadline, in seconds, for processing this real-time user request. The Session object provides the exact deadline for handling an intent.

Minimum: `1`

`User-Agent`

`string`

 (Required) 

The extension protocol running on the client. This is an RFC 7231-compliant string that contains the product name *AppleCloudExtension* and the SiriKit Extension library version running on the client.

Maximum length: `250`

Value: `/AppleCloudExtension/([0-9]+\.[0-9]+\.[0-9]+) *.*/`

`x-applecloudextension-retry-count`

`uint32`

The number of previous requests from the client. The client omits this header on the first attempt.

Minimum: `1`

`x-applecloudextension-session-id`

`string`

 (Required) 

A constant session identifier to include in each request and response. Respond to each request with the session ID the client sends in that request.

Minimum length: `1`

Maximum length: `128`

## HTTP Body

`[`PlayMediaIntentHandlingInvocation`]`

An array of intents to play media.

Content-Type: application/json

## Response Codes

` 200 ``OK`

`[`PlayMediaIntentHandlingInvocationResponse`]`

`OK`

The request is successful.

Content-Type: application/json

## Discussion

Processing a play media request requires a few steps:

- Resolve the intended media item.

- Resolve any playback customizations, such as repeat mode.

- Handle the intent.

- Provide a playback queue.

You can improve the overall response time to the user’s request by providing a response for resolving any playback customizations, and handling the intent alongside your response to the request to resolve the intended media item. This allows the client to skip subsequent requests when you can resolve each parameter successfully. If your service responds with a disambiguation, confirmation, or failure, the client disregards the pre-emptive responses, and sends the subsequent intent-processing requests.

## Topics

### Processing a Play Media Intent

object PlayMediaIntent

An object that describes the user’s request to play a media item.

object PlayMediaIntentHandlingInvocation

A request to process a play media intent.

type PlayMediaIntentHandlingInvocationResponse

The service’s response to a request to process a play media intent.

### Resolving a Media Item

object PlayMediaIntentHandlingResolveMediaItemsInvocationResponse

Your service’s response to a request to resolve media items in a play media intent.

object PlayMediaMediaItemResolutionResult

A media item that matches a play media intent, or information about why your service can’t provide a media item.

type PlayMediaMediaItemUnsupportedReason

Reasons the media service can’t play the media item.

### Handling a Play Media Intent

object PlayMediaIntentHandlingHandleInvocationResponse

Your service’s response to a request to handle a fully resolved play media intent.

object PlayMediaIntentResponse

A structure that contains a response code indicating how your service handles a play media intent.

type PlayMediaIntentResponseCode

Codes your service can return when handling a play media intent.

### Resolving the Intended Repeat Mode

object PlayMediaIntentHandlingResolvePlaybackRepeatModeInvocationResponse

Your service’s response to a request to resolve the repeat mode in a play media intent.

object PlayMediaIntentHandlingResolvePlaybackRepeatModeInvocationResponse.Result

The result of resolving the repeat mode for a play media intent.

object PlaybackRepeatModeResolutionResult

Information about whether your service can identify the specified repeat mode.

type PlaybackRepeatMode

The possible repeat modes for a media queue.

### Resolving the Intended Queue Location

object PlayMediaIntentHandlingResolvePlaybackQueueLocationInvocationResponse

Your service’s response to a request to resolve the queue location in a play media intent.

object PlaybackQueueLocationResolutionResult

Information about whether your service can resolve the specified queue location.

type PlaybackQueueLocation

Possible locations in a playback queue to insert a media item.

### Resuming Playback

object PlayMediaIntentHandlingResolveResumePlaybackInvocationResponse

Your service’s response to a request to resolve whether a play media intent resumes the current playback queue.

### Shuffling Playback

object PlayMediaIntentHandlingResolvePlayShuffledInvocationResponse

Your service’s response to a request to resolve whether a play media intent requests a shuffled queue.

## See Also

### Media Play Queues

Get a Media Queue

Provide a playback queue from a successfully processed play media intent.

