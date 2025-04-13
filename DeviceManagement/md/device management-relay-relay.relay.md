

- Device Management
- Relay
-  Relay.Relay 

Device Management Profile

# Relay.Relay

A dictionary that describes a relay server.

iOS 17.0+iPadOS 17.0+macOS 14.0+tvOS 17.0+visionOS 1.0+Device Assignment ServicesVPP License Management

``` source
object Relay.Relay
```

## Properties

`AdditionalHTTPHeaderFields`

Relay.Relay.AdditionalHTTPHeaderFields

A dictionary that contains custom HTTP header keys and values to add to each request. The dictionary key name represents the HTTP header field name to use, and the dictionary value is the string to use as the HTTP header field value.

`HTTP2RelayURL`

`string`

The URL or URI template, as defined in RFC 9298, of a relay server that’s reachable using HTTP/2 and supports proxying TCP and UDP using the CONNECT method.

Each relay needs to include either `HTTP2RelayURL` or `HTTP3RelayURL`, or it can include both.

`HTTP3RelayURL`

`string`

The URL or URI template, as defined in RFC 9298, of a relay server that’s reachable using HTTP/3 and supports proxying TCP and UDP using the CONNECT method.

Each relay needs to include either `HTTP2RelayURL` or `HTTP3RelayURL`, or it can include both.

`PayloadCertificateUUID`

`string`

The UUID that points to an identity certificate payload, which the system uses to authenticate the user to the relay server.

`RawPublicKeys`

`[data]`

An array of raw public keys that the system uses to authenticate the server during a TLS handshake. The server needs to use one of the keys in the handshake to authenticate.

If this array is empty, the system uses the default TLS trust evaluation.

## Topics

### Additional header fields

object Relay.Relay.AdditionalHTTPHeaderFields

A custom HTTP header key field name.

