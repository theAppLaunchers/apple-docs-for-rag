

- Combine
- Publishers
- Publishers.Output
-  combineLatest(\_:\_:) 

Instance Method

# combineLatest(\_:\_:)

Subscribes to two additional publishers and publishes a tuple upon receiving output from any of the publishers.

iOS 13.0+iPadOS 13.0+Mac Catalyst 13.0+macOS 10.15+tvOS 13.0+visionOS 1.0+watchOS 6.0+

``` source
func combineLatest(
    _ publisher1: P,
    _ publisher2: Q
) -> Publishers.CombineLatest3 where P : Publisher, Q : Publisher, Self.Failure == P.Failure, P.Failure == Q.Failure
```

## Parameters 

`publisher1`  

A second publisher to combine with the first publisher.

`publisher2`  

A third publisher to combine with the first publisher.

## Return Value

A publisher that receives and combines elements from this publisher and two other publishers.

## Discussion

Use combineLatest(_:_:) when you want the downstream subscriber to receive a tuple of the most-recent element from multiple publishers when any of them emit a value. To combine elements from multiple publishers, use zip(_:_:) instead. To receive just the most-recent element from multiple publishers rather than tuples, use merge(with:_:).

Tip

The combined publisher doesn’t produce elements until each of its upstream publishers publishes at least one element.

The combined publisher passes through any requests to *all* upstream publishers. However, it still obeys the demand-fulfilling rule of only sending the request amount downstream. If the demand isn’t unlimited, it drops values from upstream publishers. It implements this by using a buffer size of 1 for each upstream, and holds the most-recent value in each buffer.

All upstream publishers need to finish for this publisher to finish. If an upstream publisher never publishes a value, this publisher never finishes.

In this example, three instances of PassthroughSubject emit values; as combineLatest(_:_:) receives input from any of the upstream publishers, it combines the latest value from each publisher into a tuple and publishes it:

```
let pub = PassthroughSubject()
let pub2 = PassthroughSubject()
let pub3 = PassthroughSubject()

cancellable = pub
    .combineLatest(pub2, pub3)
    .sink { print("Result: \($0).") }

pub.send(1)
pub.send(2)
pub2.send(2)
pub3.send(9)

pub.send(3)
pub2.send(12)
pub.send(13)
pub3.send(19)

// Prints:
//  Result: (2, 2, 9).
//  Result: (3, 2, 9).
//  Result: (3, 12, 9).
//  Result: (13, 12, 9).
//  Result: (13, 12, 19).
```

If any of the combined publishers terminates with a failure, this publisher also fails.

## See Also

### Collecting and Republishing the Latest Elements from Multiple Publishers

func combineLatest&lt;P, T>(P, (Self.Output, P.Output) -> T) -> Publishers.Map&lt;Publishers.CombineLatest&lt;Self, P>, T>

Subscribes to an additional publisher and invokes a closure upon receiving output from either publisher.

func combineLatest&lt;P>(P) -> Publishers.CombineLatest&lt;Self, P>

Subscribes to an additional publisher and publishes a tuple upon receiving output from either publisher.

func combineLatest&lt;P, Q, T>(P, Q, (Self.Output, P.Output, Q.Output) -> T) -> Publishers.Map&lt;Publishers.CombineLatest3&lt;Self, P, Q>, T>

Subscribes to two additional publishers and invokes a closure upon receiving output from any of the publishers.

func combineLatest&lt;P, Q, R, T>(P, Q, R, (Self.Output, P.Output, Q.Output, R.Output) -> T) -> Publishers.Map&lt;Publishers.CombineLatest4&lt;Self, P, Q, R>, T>

Subscribes to three additional publishers and invokes a closure upon receiving output from any of the publishers.

func combineLatest&lt;P, Q, R>(P, Q, R) -> Publishers.CombineLatest4&lt;Self, P, Q, R>

Subscribes to three additional publishers and publishes a tuple upon receiving output from any of the publishers.

