

- Bundle Resources
- Information Property List
-  WKSupportsAlwaysOnDisplay 

Property List Key

# WKSupportsAlwaysOnDisplay

A Boolean value that determines whether the system displays the app in the Always On state.

watchOS 8.0+

## Details 

Type  

boolean

## Attributes 

Default: `YES`

## Discussion

If true, the system displays the app in the Always On state when the app is the frontmost app or running an active background session. Apps compiled for watchOS 8 and later have Always On enabled by default; however, users can disable Always On for the entire device or on a per-app basis by selecting Settings \> Display & Brightness \> Always On.

For more information, see `Designing Your App for the Always On State`.

