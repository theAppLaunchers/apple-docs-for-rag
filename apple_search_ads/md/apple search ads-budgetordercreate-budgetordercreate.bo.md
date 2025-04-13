

- Apple Search Ads
- BudgetOrderCreate
-  BudgetOrderCreate.Bo 

Object

# BudgetOrderCreate.Bo

The response to a request to create a budget order.

Search Ads 4.11+

``` source
object BudgetOrderCreate.Bo
```

## Properties

`billingEmail`

`string`

The billing email.

`budget`

Money

The total budget amount available for the budget order.

`clientName`

`string`

The advertiser or product. This is a requirement for agency-type accounts.

`endDate`

`date-time`

The scheduled end date and time for the budget order in the format of `yyyy-mm-dd’T’HH:MM:SS.SSS`.

`name`

`string`

The name of the budget order, which is unique within an organization.

`orderNumber`

`string`

A purchase order number. This is a requirement for agency-type accounts.

`primaryBuyerEmail`

`string`

The primary buyer’s email address.

`primaryBuyerName`

`string`

The primary buyer’s name.

`startDate`

`date-time`

The scheduled start date and time for the budget order in the format of `yyyy-mm-dd’T’HH:MM:SS.SSS`.

`supplySources`

`[string]`

The supply source of ads to use in a budget order and a campaign. See SupplySource for enum descriptions and validations.

Possible Values: `APPSTORE_PRODUCT_PAGES_BROWSE, APPSTORE_SEARCH_RESULTS, APPSTORE_SEARCH_TAB, APPSTORE_TODAY_TAB`

