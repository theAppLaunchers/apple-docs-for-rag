- USDKit  
- USDKit  
  
Framework  
  
# USDKit  
  
Author, compose, and manipulate Universal Scene Description content from Swift.  
  
iOS 27.0+ iPadOS 27.0+ Mac Catalyst 27.0+ macOS 27.0+ tvOS 27.0+ visionOS 27.0+  
  
## Overview  
  
USDKit is the Swift API for authoring, composing, and manipulating Universal Scene Description (USD) content. USD is an open scene-interchange format originated by Pixar and now stewarded by the Alliance for OpenUSD; it represents 3D scenes, assets, and animations across digital-content-creation tools and runtime engines. USDKit exposes a curated subset of OpenUSD through a hand-written, ABI-stable Swift surface.  
  
The framework centers on three core types. A USDLayer represents a single USD document — either a file on disk or an anonymous in-memory document — and serves as the unit of scene description. A USDStage assembles a hierarchy from one or more layers by applying USD’s composition rules to a root layer, producing the runtime view of a scene. Each node in that hierarchy is a USDPrim, which carries a path, attributes, relationships, references, and child primitives. Because multiple layers can define or override the same primitive, the stage composes the contributions from each layer to produce the final scene.  
  
Typical work in USDKit includes generating USD documents procedurally, extracting information from existing assets, applying bulk transformations across composed scenes, and building editors or pipeline tools. The framework also provides the supporting types that authoring depends on — type-erased value containers, interned string tokens, and transform operations — along with a RealityKit integration layer for rendering and playing composed scenes inside an entity hierarchy.  
  
## Topics  
  
### Essentials  
  
struct USDStage  
  
A composed, runtime view of a USD scene assembled from one or more layers.  
  
struct USDPrim  
  
A single node in a stage’s scene hierarchy that holds attributes, relationships, metadata, and child prims.  
  
struct USDLayer  
  
A single USD document that stores scene description in a file or in memory.  
  
### Values and tokens  
  
struct USDValue  
  
A type-erased container for a value stored in a Universal Scene Description file.  
  
protocol USDValueProtocol  
  
A type that can be wrapped in a USDValue.  
  
struct USDToken  
  
An interned, efficiently compared string that names prims, properties, and other scene-description identifiers.  
  
### Transforms  
  
struct USDTransformOperation  
  
A single transform applied to a prim, such as a translation, rotation, scale, or matrix.  
  
### RealityKit rendering and playback  
  
struct USDStageComponent  
  
A component that renders a USD stage as RealityKit entities.  
  
class USDPlayer  
  
Drives timeline playback of a USD stage and produces per-frame render data.  
  
### Render diagnostics  
  
struct USDRenderError  
  
A non-fatal error produced during USD scene processing.  
  
### Structures  
  
struct USDArray  
