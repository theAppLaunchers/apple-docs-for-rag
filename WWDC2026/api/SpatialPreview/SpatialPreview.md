- SpatialPreview  
- Spatial Preview  
  
Framework  
  
# Spatial Preview  
  
Preview spatial content from a macOS app on a connected visionOS device.  
  
macOS 27.0+ visionOS 27.0+  
  
Overview  
  
Use Spatial Preview to work with spatial content from a macOS app to a connected visionOS device in real time. The framework centers on two abstractions: SpatialPreviewEndpoint, which identifies the target visionOS device, and SpatialPreviewSession, which manages the active preview connection and the flow of content. The USDPreviewSession and DocumentPreviewSession objects adopt SpatialPreviewSession and support visionOS previews of Universal Scene Description (USD) content and general file content, respectively. USDKit is recommended for Spatial Preview because it works without any additional setup. If you want to use your own OpenUSD library, see the documentation below on how to bridge OpenUSD to USDKit.  
  
## Topics  
  
### Essentials  
  
Working with content from your Mac app using Spatial Preview  
  
Send and update documents, and work with 3D content live from your macOS app to a visionOS device through the Spatial Preview framework.  
  
Bridging an application’s custom USD runtime to Spatial Preview  
  
Sync edits between an application with its own OpenUSD runtime and a Spatial Preview session using a shared USDLayer as the exchange mechanism.  
  
### Nearby devices  
  
struct SpatialPreviewEndpoint  
  
An endpoint representing a visionOS device you can connect to for spatial preview.  
  
struct SpatialPreviewDevicePicker  
  
Presents nearby companion devices and allows the user to make a selection.  
  
class ConnectedSpatialEndpointObserver  
  
An observer that provides access to the endpoint for a device connected via Mac Virtual Display.  
  
### Preview sessions  
  
protocol SpatialPreviewSession  
  
A session that manages the lifecycle and connection state of a spatial preview on a visionOS device.  
  
class DocumentPreviewSession  
  
A session that streams document content to a connected visionOS device for spatial preview.  
  
class USDPreviewSession  
  
A session that enables you to present the contents of a Universal Scene Description (USD) stage.  
  
### Session state and errors  
  
enum SpatialPreviewSessionState  
  
Indicates the state of the session and the health of the underlying connection.  
  
enum SpatialPreviewSessionError  
  
struct UnavailableError  
  
An error thrown when accessing the endpoint property while no Mac Virtual Display device is available.  
  
enum Error  
  
Errors that can occur during a USD preview session  
  
enum Event  
  
Events emitted during a USD preview session  
