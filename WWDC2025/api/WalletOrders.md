Web Service

# Wallet Orders

Create, distribute, and update orders in Wallet.

iOS 16.0+iPadOS 16.0+macOS 13.0+

## [Overview](/documentation/WalletOrders#overview)

Use Wallet Orders to give users the ability to track and manage their purchases in Wallet. You can donate an order to Wallet seamlessly through Apple Pay after payment authorization.

To give people the ability to track their orders in Wallet, you need to:

*   Add order details to the payment authorization result.
    
*   Build an order package and provide access through your web service.
    
*   Update the order when the order’s state has changed.
    

## [Topics](/documentation/WalletOrders#topics)

### [Essentials](/documentation/WalletOrders#Essentials)

[

Creating the source for an order](/documentation/walletorders/creating-the-source-for-an-order)

Define an order by creating the directory structure, and adding source files and images.

[

Building a distributable order package](/documentation/walletorders/building-a-distributable-order-package)

Prepare an order for distribution by building, signing, and compressing the source files.

[`Retrieve the registrations for a device`](/documentation/walletorders/retrieve-the-registrations-for-a-device)

Retrieves the identifiers of the orders that the device registered for.

[`Retrieve the latest version of an order`](/documentation/walletorders/retrieve-the-latest-version-of-an-order)

Retrieves the latest signed and compressed version of an order.

[`object Order`](/documentation/walletorders/order)

The order’s details, including information about the products or services rendered, customer service, and fulfillment.

[

Example Order Packages](/documentation/walletorders/example-order-packages)

Edit, build, and add example order packages to Wallet.

### [Notifications](/documentation/WalletOrders#Notifications)

[`Register a device for update notifications`](/documentation/walletorders/register-a-device-for-update-notifications)

Registers a device to receive update notifications for an order.

[`Unregister a device from update notifications`](/documentation/walletorders/unregister-a-device-from-update-notifications)

Unregisters a device from receiving update notifications for an order.

[`object PushToken`](/documentation/walletorders/pushtoken)

The push token APNS uses to send update notifications to the device.

### [Message logs](/documentation/WalletOrders#Message-logs)

[`Receive log messages`](/documentation/walletorders/receive-log-messages)

Records log messages on your server.

[`object LogEntries`](/documentation/walletorders/logentries)

An array of log messages.