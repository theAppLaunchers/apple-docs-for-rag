

- SMS and Call Reporting
-  Understanding how Live Caller ID Lookup preserves privacy 

Article

# Understanding how Live Caller ID Lookup preserves privacy

Use Live Caller ID Lookup to protect user privacy by hiding the client’s IP address, using anonymous authentication, and hiding the incoming phone number.

## Overview

The Live Caller ID Lookup feature allows you to check incoming calls against your server for known spam numbers while preserving user privacy. When someone’s device receives a phone call, the system communicates with your back-end server to retrieve caller ID and blocking information, and then displays that information on the incoming call screen and in the device’s recent calls.

Apple’s implementation of Live Caller ID Lookup upholds user privacy while providing useful information. It does this by:

- Hiding the client’s IP address using Apple’s Oblivious HTTP.

- Using anonymous authentication with the Privacy Pass protocol.

- Hiding the incoming number by using keyword private information retrieval (KPIR).

### Hide the client’s IP address

Live Caller ID Lookup hides identifiable information using Apple’s Oblivious HTTP.

The Oblivious HTTP routes requests through two relays hosted by different parties. The first relay removes the client’s IP address from the incoming request and can’t see the destination address. A third-party provider hosts the second relay. This removes the IP address before it reaches the server.

### Use anonymous authentication

Live Caller ID Lookup uses the Privacy Pass protocol, which requires you to authenticate the users who register with the service without sharing their identity or linking the client’s identity to the query. First, your on-device app authenticates the client using a temporary ID and receives a long-term token (user token). Then, the app hands this token to the on-device system. From there, the system runs multiple round protocols with your server, and receives several private tokens that it can use to make authenticated anonymous queries.

Your server doesn’t learn which user token the system has. Additionally, your on-device, client-side app only participates in the initial authentication. The client-side app doesn’t know the private tokens and query phone numbers because the system controls them. This ensures authentication while preserving privacy.

### Hide the incoming number

Apple’s Oblivious HTTP and Privacy Pass hide the client’s identity from your server. However, they don’t hide the query itself. Live Caller ID Lookup uses KPIR to hide client queries. KPIR is a cryptographic protocol that calls the server to fetch data corresponding to a particular keyword from the hosted database without revealing the keyword to the server. Implementing the Live Caller ID Lookup feature requires the service provider to run a KPIR server on its database and handle all of the client’s KPIR encrypted queries. For more information, see the Live Caller ID Lookup example.

## See Also

### Live Caller ID Lookup

Formatting data for blocking and identity information

Set up your PIR payload for call blocking and identity information.

Setting up the HTTP endpoints for Live Caller ID Lookup

Connect the on-device system to your server.

Getting up-to-date calling and blocking information for your app

Implement the Live Caller ID Lookup app extension to provide call-blocking and identity services.

protocol LiveCallerIDLookupProtocol

Information the system uses to query the app extension for context.

protocol LiveCallerIDLookupExtensionConfiguration

An object that allows the system to query the app extension.

struct LiveCallerIDLookupExtensionContext

The information the system uses for configuration.

enum CallLookupExtensionStatus

Returns a value with the current state of the app extension.

class LiveCallerIDLookupManager

The entry point that provides access to a collection of functions that help manage the state of the Live Caller ID Lookup app extension.

