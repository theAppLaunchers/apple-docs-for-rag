

- App Store Server API
-  HistoryResponse 

Object

# HistoryResponse

A response that contains the customer’s transaction history for an app.

App Store Server API 1.0+

``` source
object HistoryResponse
```

## Properties

`appAppleId`

appAppleId

The app’s identifier in the App Store.

`bundleId`

bundleId

The bundle identifier of the app.

`environment`

environment

The server environment in which you’re making the request, whether sandbox or production.

`hasMore`

hasMore

A Boolean value that indicates whether the App Store has more transactions than it returns in this response. If the value is `true`, use the `revision` token to request the next set of transactions.

`revision`

revision

A token you use in a query to request the next set of transactions from the endpoint.

`signedTransactions`

`[`JWSTransaction`]`

An array of in-app purchase transactions for the customer, signed by Apple, in JSON Web Signature (JWS) format.

## Discussion

The Get Transaction History endpoint returns the HistoryResponse. This response contains results for all in-app purchase product types: auto-renewable subscriptions, non-renewing subscriptions, non-consumables, and consumables. The result includes transactions in any state, including transactions that are refunded or revoked, and transactions that the app has or hasn’t marked as finished.

The history response returns a maximum of 20 transactions per response. If your customer has more than 20 in-app transactions, the hasMore value is `true`. Each response includes a revision value. Call Get Transaction History again with the `revision` token in the query to receive the next set of transactions; use the same query parameters for each subsequent call that includes `revision`. When the App Store has no more transactions to send, the `hasMore` value is `false`.

If a customer upgrades a subscription or the App Store revokes an in-app purchase while you’re receiving transaction history, the App Store updates the relevant transaction. If the response is sorted in `ASCENDING` order, you receive the transaction again, with updated data.

Note

The Get Transaction History V1 endpoint also returns the HistoryResponse, however, it doesn’t include consumable in-app purchases that the app has marked as finished. Use Get Transaction History instead.

## Topics

### Response data types

type appAppleId

The unique identifier of an app in the App Store.

type bundleId

The bundle identifier of an app.

type environment

The server environment, either sandbox or production.

type hasMore

A Boolean value indicating whether the App Store has more transaction data.

type revision

A token you use in a query to request the next set of transactions for the customer.

type JWSTransaction

Transaction information signed by the App Store, in JSON Web Signature (JWS) Compact Serialization format.

## See Also

### In-app purchase history

Get Transaction History

Get a customer’s in-app purchase transaction history for your app.

Get Transaction History V1

Get a customer’s in-app purchase transaction history for your app, except finished consumable in-app purchases.

Deprecated

