

- Dispatch
- DispatchSourceProtocol
-  setRegistrationHandler(handler:) 

Instance Method

# setRegistrationHandler(handler:)

Sets the registration handler work item for the dispatch source.

iOS 8.0+iPadOS 8.0+Mac CatalystmacOS 10.10+tvOSvisionOSwatchOS

``` source
func setRegistrationHandler(handler: DispatchWorkItem)
```

## Parameters 

`handler`  

The event handler block to submit to the source’s target queue.

## Discussion

The registration handler (if specified) is submitted to the source’s target queue as soon as the source has been fully set up and is ready to start delivering events. The set up of a dispatch source’s underlying event-delivery mechanism occurs asynchronously.

Installing a registration handler is a way to be notified when that set up is complete and the dispatch source is ready to start delivering events. After your operation handler is executed, the dispatch source uninstalls it. As such, registration handlers are executed only once after you resume the dispatch source. If you set a registration handler on a dispatch source that is already set-up and running, the handler is invoked immediately.

## See Also

### Installing Event Handlers

func setEventHandler(handler: DispatchWorkItem)

Sets the event handler work item for the dispatch source.

func setEventHandler(qos: DispatchQoS, flags: DispatchWorkItemFlags, handler: Self.DispatchSourceHandler?)

func setRegistrationHandler(qos: DispatchQoS, flags: DispatchWorkItemFlags, handler: Self.DispatchSourceHandler?)

typealias DispatchSourceHandler

