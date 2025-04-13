

- Device Management
- ContentCachingInformationResponse
-  ContentCachingInformationResponse.StatusResponse 

Device Management Command

# ContentCachingInformationResponse.StatusResponse

A dictionary that contains the status of content caching on a device.

macOS 10.15.4+Device Assignment ServicesVPP License Management

``` source
object ContentCachingInformationResponse.StatusResponse
```

## Properties

`Activated`

`boolean`

If `true`, the device has enabled content caching. Enabling content caching doesn’t guarantee service. See the `Active` key for the readiness of content caching to serve requests.

Default: `false`

`Active`

`boolean`

If `true`, content caching is ready to serve requests.

Default: `false`

`ActualCacheUsed`

`integer`

The actual amount of disk space, in bytes, that cached content uses. See related values `CacheUsed` and `PersonalCacheUsed`.

`Alerts`

`[`ContentCachingInformationResponse.StatusResponse.AlertsItem`]`

An array that contains the error conditions the content cache detected that aren’t related to peer filter ranges, parent content caches, or peer content caches.

See `AlertsForPeerFilterRanges` for errors related to peer filter ranges.

See `Parents` and `Peers` for errors related to parent and peer content caches.

To display these alerts on the device, set `DisplayAlerts` to `true` in the installed ContentCaching profile.

`AlertsForPeerFilterRanges`

ContentCachingInformationResponse.StatusResponse.AlertsForPeerFilterRanges

The error conditions the content cache detected in the `PeerFilterRanges` in the installed `com.apple.AssetCache.managed` payload.

To display these alerts on the device, set `DisplayAlerts` to `true` in the installed ContentCaching profile.

`CacheDetails`

ContentCachingInformationResponse.StatusResponse.CacheDetails

The amount of disk space that various categories of cached content use. Apple defines these categories and they’re subject to change.

`CacheFree`

`integer`

The amount of disk space, in bytes, available to the content cache.

`CacheLimit`

`integer`

The maximum amount of disk space, in bytes, available to the content cache. A value of `0` indicates an unlimited amount. This value corresponds to `CacheLimit` in the installed ContentCaching profile.

`CacheStatus`

`string`

The level of cache pressure. `LowSpace` means cache pressure is high.

Possible Values: `LOWSPACE, OK`

`CacheUsed`

`integer`

The amount of disk space, in bytes, cached content uses. Content caching allocates space in its cache for entire files even when it stores only part of those files in its cache.

`DataMigrationCompleted`

`boolean`

If `true`, the content cache finished moving from one volume to another.

Default: `false`

`DataMigrationError`

ContentCachingInformationResponse.StatusResponse.DataMigrationError

The error that occurred while the content cache moved from one volume to another.

`DataMigrationProgress`

`number`

A floating-point number between `0.0` and `1.0` that indicates the percentage of progress in moving the content cache from one volume to another. A value of `1.0` indicates that the content cache has fully migrated.

Minimum: `0`

Maximum: `1`

`MaxCachePressureLast1Hour`

`number`

A floating-point number between `0.0` and `1.0` that represents how often the cache needed more disk space over the last hour of operation. A lower value is better.

Minimum: `0`

Maximum: `1`

`Parents`

`[`ContentCachingInformationResponse.StatusResponse.ParentsItem`]`

An array of dictionaries that describes parent content caches.

`Peers`

`[`ContentCachingInformationResponse.StatusResponse.PeersItem`]`

An array of dictionaries that describes peer content caches.

`PersonalCacheFree`

`integer`

The amount of disk space, in bytes, available to the content cache for personal iCloud content.

`PersonalCacheLimit`

`integer`

The maximum amount of disk space, in bytes, available to the content cache for personal iCloud content. A value of `0` indicates an unlimited amount.

`PersonalCacheUsed`

`integer`

The amount of disk space, in bytes, available to the content cache for personal iCloud content.

`Port`

`integer`

The IP port number the content cache listens to for requests from clients, peers, and children.

`PrivateAddresses`

`[string]`

An array of the content cache’s local IP addresses.

`PublicAddress`

`string`

The public IP address of the content cache.

`RegistrationError`

`string`

If present, the reason the content cache failed to register itself with Apple.

`RegistrationResponseCode`

`integer`

If present, the HTTP response code the content cache received when it failed to register itself with Apple.

`RegistrationStarted`

`date`

The date when the content cache began registering itself with Apple. This value is only available during registration attempts.

`RegistrationStatus`

`integer`

The status of the content cache’s registration with Apple, which is one of the following values:

- `-1:` Failed

- `0:` Pending

- `1:` Succeeded

Possible Values: `-1, 0, 1`

`RestrictedMedia`

`boolean`

If `true`, a restriction prevents caching of certain content types.

Default: `false`

`ServerGUID`

`string`

The unique identifier of the content cache.

`StartupStatus`

`string`

The status of the content cache’s registration with Apple.

Possible Values: `FAILED, MIGRATING_DATA, OK, PENDING`

`TetheratorStatus`

`integer`

The status of tethered caching, which is content caching with a shared internet connection, which is one of the following values:

- `-1:` Unknown

- `0:` Disabled

- `1:` Enabled

Possible Values: `-1, 0, 1`

`TotalBytesAreSince`

`date`

The start date to use when collecting data for the other `TotalBytes` values.

`TotalBytesDropped`

`integer`

The amount of data, in bytes, that the content cache downloaded, but couldn’t add to its cache, since the `TotalBytesAreSince` date.

`TotalBytesImported`

`integer`

The amount of data, in bytes, that the content cache received since the `TotalBytesAreSince` date.

`TotalBytesReturnedToChildren`

`integer`

The amount of data, in bytes, that the content cache served to its child content cache since the `TotalBytesAreSince` date.

`TotalBytesReturnedToClients`

`integer`

The amount of data, in bytes, that the content cache served to client iOS, macOS, and tvOS devices since the `TotalBytesAreSince` date.

`TotalBytesReturnedToPeers`

`integer`

The amount of data, in bytes, that the content cache served to peer content caches since the `TotalBytesAreSince` date.

`TotalBytesStoredFromOrigin`

`integer`

The amount of data, in bytes, that the content cache saved from the internet since the `TotalBytesAreSince` date.

`TotalBytesStoredFromParents`

`integer`

The amount of data, in bytes, that the content cache saved from parent content caches since the `TotalBytesAreSince` date.

`TotalBytesStoredFromPeers`

`integer`

The amount of data, in bytes, that the content cache saved from peer content caches since the `TotalBytesAreSince` date.

## Topics

### Response Dictionaries

object ContentCachingInformationResponse.StatusResponse.AlertsItem

A dictionary that describes an alert from the content cache.

object ContentCachingInformationResponse.StatusResponse.CacheDetails

A dictionary that describes disk space the content cache uses.

object ContentCachingInformationResponse.StatusResponse.DataMigrationError

A dictionary that describes a data migration error.

object ContentCachingInformationResponse.StatusResponse.ParentsItem

A dictionary that describes a parent content cache.

object ContentCachingInformationResponse.StatusResponse.PeersItem

A dictionary that describes a peer content cache.

object ContentCachingInformationResponse.StatusResponse.AlertsForPeerFilterRanges

A dictionary that contains alerts for peer filter ranges.

## See Also

### Commands

object ContentCachingInformationResponse.ErrorChainItem

A dictionary that describes an error chain item.

