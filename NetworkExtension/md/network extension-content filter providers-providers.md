

- Network Extension
-  Content filter providers 

API Collection

# Content filter providers

Create an on-device network content filter.

## Overview

An on-device network content filter examines user network content as it passes through the network stack and determines if it should block that content or allow it to pass on to its final destination. You might create a content filter and sell it to organizations, like schools and businesses, that want to prevent users from accessing specific Internet content.

A content filter consists of two providers that work in close cooperation:

- A filter data provider receives user network content and examines that content to determine whether to block or allow it.

- A filter control provider passes configuration information to the filter data provider to allow that provider to do its job.

This separation exists to guarantee user privacy. The filter data provider runs in a very restrictive sandbox that prevents user network content from escaping that provider. The filter control provider has a less restrictive sandbox but doesn’t have access to user network content. By combining these providers, your content filter has access to the network but can’t use that access to export user network content.

For example, your filter control provider might download a set of filtering rules and save them to a shared app group. Your filter data provider has *read-only* access to that app group, allowing it use those rules to filter content but still preventing it from exporting user network content.

For detailed information about content filter provider deployment options, see TN3134: Network Extension provider deployment.

Note

When a VPN configuration is active, connections use the VPN instead of iCloud Private Relay. Network Extension providers also don’t use iCloud Private Relay.

## Topics

### Essentials

Network Extensions Entitlement

The APIs an app can use to customize networking features.

### Data and control providers

class NEFilterDataProvider

The principal class for a filter data provider extension.

class NEFilterControlProvider

The principal class for a filter control provider extension.

class NEFilterPacketProvider

A filter provider that evaluates network packets and decides whether to block, allow, or delay the packets.

class NEFilterProvider

An abstract base class shared by content filters.

### Flow handling

class NEFilterFlow

The abstract base class for types that represent flows of network data.

class NEFilterBrowserFlow

A flow of network data, originating from a WebKit-based browser, that the filter examines.

class NEFilterSocketFlow

A flow of network data that the filter examines.

class NEFilterNewFlowVerdict

The result from a filter data provder after the initial examination of a flow.

class NEFilterDataVerdict

The result from a filter data provder for subsequent chunks of data on a flow.

class NEFilterControlVerdict

The result from a filter control provider.

class NEFilterRemediationVerdict

The result from a filter data provider after the user requests remediation for a blocked flow.

class NEFilterVerdict

The abstract base class for filter verdict classes.

class NEFilterReport

The report of the data provider’s action on a flow.

### Filter configuration

class NEFilterManager

An object to create and manage a content filter’s configuration.

class NEFilterProviderConfiguration

Configuration parameters for a content filter.

## See Also

### Content filters

Filtering Network Traffic

Use the Network Extension framework to allow or deny network connections.

