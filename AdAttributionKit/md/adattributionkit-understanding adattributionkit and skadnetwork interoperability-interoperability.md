

- AdAttributionKit
-  Understanding AdAttributionKit and SKAdNetwork interoperability 

Article

# Understanding AdAttributionKit and SKAdNetwork interoperability

Learn how attribution APIs interact to deliver ad impressions.

## Overview

AdAttributionKit and SKAdNetwork are frameworks that enable ad attribution and user engagement measurement for conversions. AdAttributionKit works with both the App Store and alternative app marketplaces, while SKAdNetwork works specifically with the App Store.

## Update conversion values independently

The update API to call depends on the framework your ad network is using, although you can use both APIs:

If your framework is integrated with AdAttributionKit, use the updateConversionValue(_:coarseConversionValue:lockPostback:) or updateConversionValue(_:lockPostback:) API methods. If your framework is integrated with SKAdNetwork, call the updatePostbackConversionValue(_:coarseValue:lockWindow:completionHandler:) or updatePostbackConversionValue(_:coarseValue:completionHandler:) API methods.

If your framework is integrated with both AdAttributionKit and SKAdNetwork, call APIs from both. If your app doesn’t have any pending postbacks — for instance because a person hasn’t seen an ad for your app — the system ignores calls to both AdAttributionKit and SKAdNetwork. Additionally, `.adattributionkit` and `.skadnetwork` ad network IDs are compatible across both AdAttributionKit and SKAdNetwork, so you don’t need a specific ad network ID for one or the other.

## Understand how the system determines attribution

If an app has both AdAttributionKit and SKAdNetwork impressions, the system sorts both of them and decides the winner. Only one impression can win for a conversion, whether it comes from AdAttributionKit or SKAdNetwork. If a person sees more than one advertisement, the attribution goes to the ad the person most recently tapped. If a person doesn’t tap any ads, attribution goes to the ad a person most recently viewed.

The system sorts the impressions based on the following criteria:

- Whether they are click-through or view-through. Click-through ads always take precedence over view-through ads.

- For impressions, in each click-through or view-through group, the system sorts them based on their timestamp.

- The system considers a maximum of six impressions for any conversion.

## See Also

### Essentials

Presenting ads in your app

Render different ad styles in your app.

Receiving ad attributions and postbacks

Understand timeframes and priorities for ad impressions that result in ad attributions, and how impressions qualify for postbacks.

Identifying conversion values with conversion tags

Use conversion tags to identify and update specific postbacks when you have overlapping conversion windows.

