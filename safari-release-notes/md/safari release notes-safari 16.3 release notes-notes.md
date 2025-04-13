

- Safari Release Notes
-  Safari 16.3 Release Notes 

Article

# Safari 16.3 Release Notes

Released January 23, 2023 — Version 16.3 (18614.4.6)

## Overview

Safari 16.3 is available for macOS Big Sur, macOS Monterey, macOS Ventura, iPadOS 16.3, and iOS 16.3.

### CSS

#### Resolved Issues

- Fixed `MediaQueryList.matches` to update the parent document layout for viewport-dependent media queries.

- Fixed transfers of min and max sizes for CSS `aspect-ratio` to be constrained by defined sizes.

- Fixed `gap` to be accounted for by using the unclamped subgrid track sizes to compute track positions.

- Fixed calculating block size to use the correct box-sizing.

- Fixed the transferred `min` and `max` sizes to be constrained by defined sizes.

- Fixed: Use intrinsic ratio of replaced elements when computing flex sizes.

- Fixed negative content sizes when using `box-sizing: border-box` with border and padding.

- Fixed setting `scrollTop` on a fixed element with overflow breaking scrolling on a page with `overscroll-behavior: none`.

### Rendering

#### Resolved Issues

- Fixed replaced elements with aspect ratio and size in one dimension to respect the min and max constraints in the opposite dimension.

### Web API

#### Resolved Issues

- Fixed decompressing content downloaded via `fetch()` with `Content-Encoding: gzip` set.

- Fixed downloads served from a service worker that uses preload.

- Fixed: Added an error event when link preload fails synchronously.

- Fixed Cross-Origin-Embedder-Policy incorrectly blocking scripts.

- Fixed Authorization header used for subsequent 301 redirects when the request header changes.

- Fixed showing a dialog element when the target is a shadow host with a focus delegates.

### Content Security Policy

#### New Features

- Added support for the `prefetch-src` directive.

#### Resolved Issues

- Fixed: Check for `strict-dynamic` in `script-src` and `default-src` directives.

- Fixed: Added an error event when Content Security Policy blocks inline stylesheets.

### Media

#### Resolved Issues

- Fixed web audio becoming garbled with switching from speakers to headphones.

- Fixed video track’s size settings in the second MediaStream created when the `aspectRatio` constraint is applied.

- Fixed showing Media Session API artwork.

- Fixed “A MediaStreamTrack ended due to a capture failure” error when selecting bluetooth headphones as an audio input device.

- Fixed WebVTT styles to apply with in-band tracks.

- Fixed alternate VPx codec names to support `vp8.0` and `vp9.0`.

### SVG

#### Resolved Issues

- Fixed MouseClick `offsetX` and `offsetY` on a foreign object in an SVG to be relative to the element rather than relative to the SVG container.

## See Also

### Version 16

Safari 16.6 Release Notes

Released July 24, 2023 — Version 16.6 (18615.3.12)

Safari 16.5 Release Notes

Released May 18, 2023 — Version 16.5 (18615.2.9)

Safari 16.4 Release Notes

Released March 27, 2023 — Version 16.4 (18615.1.26)

Safari 16.2 Release Notes

Released December 13, 2022 — Version 16.2 (18614.3.7)

Safari 16.1 Release Notes

Released October 24, 2022 — Version 16.1 (18614.2.9)

Safari 16 Release Notes

Released September 12, 2022 — Version 16 (18614.1.25)

