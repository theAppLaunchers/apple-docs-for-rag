

- Accessibility
- AccessibilitySettings
-  openSettings(for:) 

Type Method

# openSettings(for:)

Opens the Settings app to a specific section of Accessibility settings.

iOS 18.0+iPadOS 18.0+Mac Catalyst 18.0+macOS 15.0+tvOS 18.0+visionOS 2.0+watchOS 11.0+

``` source
static func openSettings(for feature: AccessibilitySettings.Feature) async throws
```

## Discussion

Some app behaviors depend on a person turning on a specific Accessibility setting on their device. You can use this method to open the Settings app to a specific Accessibility setting to help people turn it on more quickly, as shown in the following code example.

```
ContentView()
    .alert(
        "Use Personal Voice",
        isPresented: $showAlert
    ) {
        Button("Open Accessibility Settings") {
            Task {
                do {
                    try await AccessibilitySettings.openSettings(for: .personalVoiceAllowAppsToRequestToUse)
                } catch {
                    print("Error: \(error)")
                }
            }
        }
        Button("Cancel", role: .cancel) { }
    } message: {
        Text("To use this feature, turn on the Personal Voice > Allow Apps to Request to Use setting.")
    }
```

## See Also

### Opening the Settings app

enum Feature

Constants that describe specific Accessibility settings in the Settings app.

