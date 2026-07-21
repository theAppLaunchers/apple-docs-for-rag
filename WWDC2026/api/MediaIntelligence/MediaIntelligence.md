# MediaIntelligence  
  
- MediaIntelligence  
-  Media Intelligence  
  
Framework  
  
# Media Intelligence  
  
Analyze video content and group faces in images using on-device machine learning.  
  
iOS 27.0+ iPadOS 27.0+ Mac Catalyst 27.0+ macOS 27.0+ tvOS 27.0+ visionOS 27.0+  
  
## Overview  
  
Media Intelligence provides on-device algorithms to analyze image and video content. Use it in video editors, photo organizers, and other media apps to add intelligence features without building the underlying analysis pipeline yourself.  
  
For images, FaceGroupAnalyzer detects faces in a collection of image assets and groups matching faces into entities, each representing a unique person. You can then query the analyzer to retrieve faces by asset, entity, or face ID, and use the results to build features like person-based photo organization or face search.  
  
For video, VideoAnalyzer accepts one or more analysis requests for a specified asset and returns results for each. Use HighlightAnalysisRequest to identify the most engaging segments of a video clip, or use KeyFrameAnalysisRequest to select a keyframe that represents the overall theme of the video. Both requests run in-process on the device, with no data leaving the system.  
  
## Topics  
  
### Image analysis  
  
Detecting and grouping faces in images  
  
Organize photos by person using on-device face detection.  
  
class FaceGroupAnalyzer  
  
An object that detects faces in images and groups them by person.  
  
struct MediaIntelligenceImageAsset  
  
An image asset to analyze.  
  
### Video analysis  
  
Finding the best moments in a video  
  
Identify keyframes and highlight segments using on-device analysis.  
  
class VideoAnalyzer  
  
An object that analyzes video assets for highlights and key frames.  
  
struct MediaIntelligenceVideoAsset  
  
A video asset to analyze.  
  
class HighlightAnalysisRequest  
  
A request that identifies the most engaging segments of a video.  
  
class KeyFrameAnalysisRequest  
  
A request that identifies the best representative frame of a video.  
  
### Errors  
  
enum MediaIntelligenceError  
  
An error that indicates a media analysis operation failed.  
