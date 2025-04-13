

- SwiftUI
- View
-  presentationPreventsAppTermination(\_:) 

Instance Method

# presentationPreventsAppTermination(\_:)

Whether a presentation prevents the app from being terminated/quit by the system or app termination menu item.

macOS 15.4+

``` source
nonisolated
func presentationPreventsAppTermination(_ prevents: Bool?) -> some View
```

## Discussion

SwiftUI uses the buttons in a sheet’s toolbar to determine whether a particular sheet should block termination by default. If there is a singular toolbar item with the confirmationAction or the cancellationAction placement and no other toolbar items, the sheet will not prevent termination by default.

Use this modifier to specify whether a sheet should prevent app termination. Pass `nil` to explicitly request the automatic behavior/for the inert version of this modifier. Non-nil values will override `nil`, and `true` takes precedence over `false`.

Use this modifier within the `content` argument to `View/sheet`

```
struct LaunchScreen: View {
  @State private var presentLogin = false
  var body: some View {
    HomeView()
      .sheet(isPresented: $presentLogin) {
        LoginView()
          // explicitly allow app termination because the
          // default behavior would resolve to `true`.
          .presentationPreventsAppTermination(false)
          .toolbar {
            ToolbarItem(placement: .cancellationAction) {
              Button("Cancel") { presentLogin = false }
            }
            ToolbarItem(placement: .confirmationAction) {
              Button("Login") {
                // Attempt login...
                presentLogin = false
              }
            }
          }
        }
    }
}
```

