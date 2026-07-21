# StateReporting  
  
- StateReporting  
-  StateReporting  
  
Framework  
  
# StateReporting  
  
Communicate your app’s state to the system to improve diagnostic actionability.  
  
iOS 27.0+ iPadOS 27.0+ Mac Catalyst 27.0+ macOS 27.0+ tvOS 27.0+ visionOS 27.0+ watchOS 27.0+  
  
## Overview  
  
StateReporting lets you define named domains and emit structured state transitions from your app. MetricKit surfaces state context in both state-aggregated and interval-level metric entries. Instruments displays transitions in the Points of Interest instrument so you can cross-reference app state against other profiling data.  
  
Each domain holds up to one active state at a time, and you can combine states across domains. For example, your game can track its graphics configuration in one domain and its game mode in another, so you can compare performance across every state combination.  
  
## Topics  
  
### Essentials  
  
Getting started with StateReporting  
  
Define reportable metadata types, obtain a state reporter for your domain, and report transitions at the right call sites in your app.  
  
### Reporting  
  
class StateReporter  
  
An object unique per domain that records state transitions and volatile metadata updates.  
  
### Defining metadata  
  
protocol ReportableMetadata  
  
A protocol for types that can supply their metadata as a dictionary of reportable values.  
  
enum ReportableMetadataValue  
  
A value in a reportable-metadata dictionary.  
  
### Metadata type macros  
  
macro ReportableMetadata()  
  
Automatically generates ReportableMetadata conformance for a type.  
  
macro ReportableMetadataKey(String)  
  
Specifies a custom key name for a property in the generated metadataDictionary.  
  
macro ReportableMetadataIgnored()  
  
Excludes a property from the generated metadataDictionary.  
