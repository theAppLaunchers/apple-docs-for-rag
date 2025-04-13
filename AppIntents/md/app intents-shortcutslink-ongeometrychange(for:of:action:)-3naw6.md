

- App Intents
- ShortcutsLink
-  onGeometryChange(for:of:action:) 

Instance Method

# onGeometryChange(for:of:action:)

Adds an action to be performed when a value, created from a geometry proxy, changes.

AppIntentsSwiftUIiOS 18.0+iPadOS 18.0+Mac Catalyst 18.0+macOS 15.0+tvOS 18.0+visionOS 1.0+watchOS 10.0+

``` source
@preconcurrency nonisolated
func onGeometryChange(
    for type: T.Type,
    of transform: @escaping (GeometryProxy) -> T,
    action: @escaping (T, T) -> Void
) -> some View where T : Equatable, T : Sendable
```

## Parameters 

`type`  

The type of value transformed from a geometry proxy.

`transform`  

A closure that transforms a `GeometryProxy` to your type.

`action`  

A closure to run when the transformed data changes.

`oldValue`  

The old value that failed the comparison check.

`newValue`  

The new value that failed the comparison check.

## Discussion

The geometry of a view can change frequently, especially if the view is contained within a `ScrollView` and that scroll view is scrolling.

You should avoid updating large parts of your app whenever the scroll geometry changes. To aid in this, you provide two closures to this modifier:

- transform: This converts a value of `GeometryProxy` to your own data type.

- action: This provides the data type you created in `of` and is called whenever the data type changes.

For example, you can use this modifier to know how much of a view is visible on screen. In the following example, the data type you convert to is a `Bool` and the action is called whenever the `Bool` changes.

```
ScrollView(.horizontal) {
    LazyHStack {
         ForEach(videos) { video in
             VideoView(video)
         }
     }
 }

struct VideoView: View {
    var video: VideoModel

    var body: some View {
        VideoPlayer(video)
            .onGeometryChange(for: Bool.self) { proxy in
                let frame = proxy.frame(in: .scrollView)
                let bounds = proxy.bounds(of: .scrollView) ?? .zero
                let intersection = frame.intersection(
                    CGRect(origin: .zero, size: bounds.size))
                let visibleHeight = intersection.size.height
                return (visibleHeight / frame.size.height) > 0.75
             } action: { isVisible in
                video.updateAutoplayingState(
                    isVisible: isVisible)
            }
    }
}
```

