

- MediaExtension
-  RAW processor entitlement 

Article

# RAW processor entitlement

Include an entitlement to indicate your extension is a MediaExtension RAW processor.

## Overview

MediaExtension RAW processors must include an special entitlement key with a Boolean value set to true. This entitlement is the same as for MediaExtension video decoders, since RAW processors always work in conjunction with a corresponding video decoder. To add the entitlement key in Xcode, follow these steps:

1.  Select the build target for your format reader extension

2.  Go to the Signing & Capabilities tab

3.  Click + to add a new capability

4.  Choose Media Extension Video Decoder from the list

The entitlement key is `com.apple.developer.mediaextension.videodecoder` and it must have a Boolean value set to true. A developer provisioning profile will be needed to use this entitlement.

## See Also

### RAW processors

protocol MERAWProcessor

A protocol that defines the requirements for a RAW processor.

protocol MERAWProcessorExtension

A protocol that defines a factory to create RAW processors for a codec type that the extension implements.

class MERAWProcessorPixelBufferManager

Describes pixel buffer requirements and creates new pixel buffers.

class MERAWProcessingParameter

An object for the RAW processor to describe each processing parameter the processor exposes.

enum MERAWProcessorNotification

Notifications that indicate a RAW processor state change.

RAW processor property list dictionary

Include a property list dictionary to describe a RAW processor.

