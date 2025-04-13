

- App Store Receipts
- responseBody
-  responseBody.Latest_receipt_info Deprecated

Object

# responseBody.Latest_receipt_info

An array that contains all in-app purchase transactions.

App Store Receipts 1.0–1.7Deprecated

## Properties

`app_account_token`

app_account_token

Deprecated 

The appAccountToken associated with this transaction. This field is only present if your app supplied an appAccountToken(_:) or provided a UUID for the applicationUsername property when the user made the purchase.

`cancellation_date`

`string`

Deprecated 

The time the App Store refunded a transaction or revoked it from Family Sharing, in a date-time format similar to the ISO 8601. This field is present only for refunded or revoked transactions.

`cancellation_date_ms`

cancellation_date_ms

Deprecated 

The time the App Store refunded a transaction or revoked it from Family Sharing, in UNIX epoch time format, in milliseconds. This field is present only for refunded or revoked transactions. Use this time format for processing dates.

`cancellation_date_pst`

`string`

Deprecated 

The time the App Store refunded a transaction or revoked it from Family Sharing, in Pacific Standard Time. This field is present only for refunded or revoked transactions.

`cancellation_reason`

`string`

Deprecated 

The reason for a refunded or revoked transaction. A value of `1` indicates that the customer canceled their transaction due to an actual or perceived issue within your app. A value of `0` indicates that the transaction was canceled for another reason; for example, if the customer made the purchase accidentally.

Possible Values: `1, 0`

`expires_date`

`string`

Deprecated 

The time an auto-renewable subscription expires or when it will renew, in a date-time format similar to the ISO 8601.

`expires_date_ms`

expires_date_ms

Deprecated 

The time an auto-renewable subscription expires or when it will renew, in UNIX epoch time format, in milliseconds. Use this time format for processing dates.

`expires_date_pst`

`string`

Deprecated 

The time an auto-renewable subscription expires or when it will renew, in Pacific Standard Time.

`in_app_ownership_type`

in_app_ownership_type

Deprecated 

A value that indicates whether the user is the purchaser of the product or is a family member with access to the product through Family Sharing.

`is_in_intro_offer_period`

`string`

Deprecated 

An indicator of whether an auto-renewable subscription is in the introductory price period. See is_in_intro_offer_period for more information.

Possible Values: `true, false`

`is_trial_period`

is_trial_period

Deprecated 

An indicator of whether an auto-renewable subscription is in the free trial period.

`is_upgraded`

`string`

Deprecated 

An indicator that an auto-renewable subscription has been canceled due to an upgrade. This field is only present for upgrade transactions.

Value: `true`

`offer_code_ref_name`

offer_code_ref_name

Deprecated 

The reference name of a subscription offer that you configured in App Store Connect. This field is present when a customer redeems a subscription offer code. For more information about offer codes, see Set Up Offer Codes, and Implementing offer codes in your app.

`original_purchase_date`

`string`

Deprecated 

The time of the original app purchase, in a date-time format similar to ISO 8601.

`original_purchase_date_ms`

`string`

Deprecated 

The time of the original app purchase, in UNIX epoch time format, in milliseconds. Use this time format for processing dates. For an auto-renewable subscription, this value indicates the date of the subscription’s initial purchase. The original purchase date applies to all product types and remains the same in all transactions for the same product ID. This value corresponds to the original transaction’s transactionDate property in StoreKit.

`original_purchase_date_pst`

`string`

Deprecated 

The time of the original app purchase, in Pacific Standard Time.

`original_transaction_id`

original_transaction_id

Deprecated 

The transaction identifier of the original purchase.

`product_id`

`string`

Deprecated 

The unique identifier of the product purchased. You provide this value when creating the product in App Store Connect, and it corresponds to the productIdentifier property of the SKPayment object stored in the transaction’s payment property.

`promotional_offer_id`

promotional_offer_id

Deprecated 

The identifier of the subscription offer redeemed by the user.

`purchase_date`

`string`

Deprecated 

The time the App Store charged the user’s account for a purchased or restored product, or the time the App Store charged the user’s account for a subscription purchase or renewal after a lapse, in a date-time format similar to ISO 8601.

`purchase_date_ms`

`string`

Deprecated 

For consumable, non-consumable, and non-renewing subscription products, the time the App Store charged the user’s account for a purchased or restored product, in the UNIX epoch time format, in milliseconds. For auto-renewable subscriptions, the time the App Store charged the user’s account for a subscription purchase or renewal after a lapse, in the UNIX epoch time format, in milliseconds. Use this time format for processing dates.

`purchase_date_pst`

`string`

Deprecated 

The time the App Store charged the user’s account for a purchased or restored product, or the time the App Store charged the user’s account for a subscription purchase or renewal after a lapse, in Pacific Standard Time.

`quantity`

`string`

Deprecated 

The number of consumable products purchased. This value corresponds to the quantity property of the SKPayment object stored in the transaction’s payment property. The value is usually `1` unless modified with a mutable payment. The maximum value is `10`.

`subscription_group_identifier`

`string`

Deprecated 

The identifier of the subscription group to which the subscription belongs. The value for this field is identical to the subscriptionGroupIdentifier property in SKProduct.

`web_order_line_item_id`

`string`

Deprecated 

A unique identifier for purchase events across devices, including subscription-renewal events. This value is the primary key for identifying subscription purchases.

`transaction_id`

transaction_id

Deprecated 

A unique identifier for a transaction such as a purchase, restore, or renewal.

