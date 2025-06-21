*   [Bundle Resources](/documentation/bundleresources)
*   [Information Property List](/documentation/bundleresources/information-property-list)
*   [UIApplicationSceneManifest](/documentation/bundleresources/information-property-list/uiapplicationscenemanifest)
*   UIApplicationSupportsTabbedSceneCollection

Property List Key

# UIApplicationSupportsTabbedSceneCollection

A Boolean value indicating whether an app built with Mac Catalyst supports automatic tabbing mode.

Mac Catalyst 15.0+

## [Details](/documentation/BundleResources/Information-Property-List/UIApplicationSceneManifest/UIApplicationSupportsTabbedSceneCollection#details)

Name

Supports Tabbed Scene Collection

Type

boolean

## [Attributes](/documentation/BundleResources/Information-Property-List/UIApplicationSceneManifest/UIApplicationSupportsTabbedSceneCollection#attributes)

Default: `YES`

## [Discussion](/documentation/BundleResources/Information-Property-List/UIApplicationSceneManifest/UIApplicationSupportsTabbedSceneCollection#Discussion)

By default, the tabbing mode for an app built with Mac Catalyst that support multiple scenes is [`NSWindow.TabbingMode.automatic`](/documentation/AppKit/NSWindow/TabbingMode-swift.enum/automatic). Starting with macOS 12, you can disable this behavior by adding the [`UIApplicationSupportsTabbedSceneCollection`](/documentation/bundleresources/information-property-list/uiapplicationscenemanifest/uiapplicationsupportstabbedscenecollection) key with a value of [`false`](/documentation/swift/false) to the [`UIApplicationSceneManifest`](/documentation/bundleresources/information-property-list/uiapplicationscenemanifest) key in your app’s `Info.plist` file.

## [See Also](/documentation/BundleResources/Information-Property-List/UIApplicationSceneManifest/UIApplicationSupportsTabbedSceneCollection#see-also)

### [Multiple windows](/documentation/BundleResources/Information-Property-List/UIApplicationSceneManifest/UIApplicationSupportsTabbedSceneCollection#Multiple-windows)

[`UIApplicationSupportsMultipleScenes`](/documentation/bundleresources/information-property-list/uiapplicationscenemanifest/uiapplicationsupportsmultiplescenes)

A Boolean value indicating whether the app supports two or more scenes simultaneously.

**Name:** Enable Multiple Windows