

- RealityKit
- Model3DPlaceholderContent
-  onGeometryChange3D(for:of:action:) 

Instance Method

# onGeometryChange3D(for:of:action:)

Returns a new view that arranges to call `action(oldValue, newValue)` whenever the value computed by `value(proxy)` changes, where `proxy` provides access to the view’s 3D geometry properties.

RealityKitSwiftUIvisionOS 2.0+

``` source
@MainActor @preconcurrency
func onGeometryChange3D(
    for type: T.Type,
    of transform: @escaping (GeometryProxy3D) -> T,
    action: @escaping (T, T) -> Void
) -> some View where T : Equatable
```

