

- Apple Search Ads
-  AdGroupUpdate 

Object

# AdGroupUpdate

The response to ad group update requests.

Search Ads 2.0+

``` source
object AdGroupUpdate
```

## Properties

`automatedKeywordsOptIn`

`boolean`

The parameter for enabling and disabling Search Match. If `true`, the system automatically adds optimized keywords in addition to those you explicitly add to the ad group.

See the Enable and Disable Search Match section of Ad Groups.

`cpaGoal`

Money

The cost-per-acquisition goal.

Important

You can update the `cpaGoal` only in campaigns that use the `APPSTORE_SEARCH_RESULTS` supply source.

`defaultBidAmount`

Money

The default maximum cost-per-tap or cost-per-impression bid for the ad group.

`endTime`

`date-time`

The scheduled end date and time for the ad group, which the system determines from the ad group with the latest end time.

- The `endTime` is updatable until you reach the designated time.

- The `endTime` must be after the `startTime`.

- The `endTime` must be in UTC.

`name`

`string`

The unique name of the ad group. Responses donʼt include deleted ad groups.

`startTime`

`date-time`

The scheduled start date and time for the ad group with the earliest start time in the campaign.

- The `startTime` must be greater than the current time, and before the campaign `endTime`, if you set it.

- If you don’t set a `startTime`, the campaign defaults to the campaign request timestamp and the `startTime` is updatable until you reach the designated time.

- The `startTime` must be in UTC.

`status`

`string`

The user-controlled status to enable or pause the ad group.

Possible Values: `ENABLED, PAUSED`

`targetingDimensions`

TargetingDimensions

The targeting criteria to narrow the audience. Targeting options include age, gender, geolocation, daypart, device, and app downloaders.

## See Also

### Ad Group Request and Response Objects

object AdGroup

The response to ad group requests.

object AdGroupResponse

A container for the ad group response body.

object AdGroupListResponse

The response details of ad group requests.

