

- CloudKit
-  Designing and Creating a CloudKit Database 

Article

# Designing and Creating a CloudKit Database

Create a schema to store your app’s objects as records in iCloud using CloudKit.

## Overview

After you enable CloudKit in your app, you create a *schema* for your container that describes how to store your objects. A schema defines *record types* and the possible relationships between them. A record type is a template for the allowed keys and values of a record. This relationship is analogous to how a class (record type) defines the properties an instance (record) can have.

### Design your objects as records

CloudKit allows you to store your data as CKRecord objects, and relationships between those objects as CKRecord.Reference associations. Separate your data into record types by grouping objects of the same type together. If you’ve already separated your model data into classes, these classes might have the same record type in iCloud. Choose which objects and which of their properties and relationships you want to persist to iCloud.

Each object property that you persist maps to a key-value pair, known as a *field*, within a CKRecord. CKRecord supports value types for your fields, such as String, or more complex types, such as Data.

For example, a “to-do item” might have the following record type:

| **Key** | **Type** | **Example value** |
|----|----|----|
| title | String | “Get apples” |
| dueDate | Date | October 28, 2019 |
| isCompleted | Bool | false |

For information on additional supported value types, see CKRecord.

### Create records programmatically

Create a CKRecord object with a string representing the type of record you want to store, using initWithRecordType:. Every record type must have a unique string name.

```
let record = CKRecord(recordType: "ToDoItem")
```

Then set the record’s fields. Because CKRecord is key-value coding compliant, you can use setValuesForKeys(_:). The values you set could be from a details sheet that the user fills out.

```
record.setValuesForKeys([
    "title": "Get apples",
    "dueDate": DateComponents(
        calendar: Calendar.current,
        year: 2019,
        month: 10,
        day: 28).date!,
    "isCompleted": false // Stored as Int(64)
])
```

### Save initial records to iCloud

You can create a schema using CloudKit Dashboard, or you can create a *just-in-time schema* by writing records programmatically.

To save a record to your container, you must pick a database to save the record to. Each container has a single *public* database accessible to all app users, and *private* databases for each user of your app. Also, a user may have a *shared* database if that user is accessing another user’s shared private data. Note that every database within your app’s container shares the same schema.

Although an app can have multiple containers or can share a container, each app has one default container. You access the default container using default() on CKContainer. The following example uses the current user’s private database within the app’s default container and exists in an action handler for a Save button.

```
let container = CKContainer.default()
let database = container.privateCloudDatabase
```

Save the record to the user’s private database in the app’s container.

```
database.save(record) { record, error in
    if let error = error {
        // Handle error.
        return
    }
    // Record saved successfully.
}
```

When you run your app, it adds that record type to the schema and saves the record. If the record type already exists in the schema, iCloud uses the existing type. Saving a record works only if the user has signed into their iCloud account on their device.

If saving the record to iCloud succeeds, `error` is `nil`. (If `error` is non-`nil`, see CKError for possible values of `error.)`

Important

During development, you can change your schema as much as you want, but once it’s deployed to production, you can’t delete any part of it. You can only make additive changes, such as adding a new field to a record type, or adding new record types.

### Handle or prevent errors gracefully

When designing your app, consider how to handle or prevent error conditions. For example, an error occurs if your app attempts to save a record to a user’s private database and the user hasn’t yet signed in to iCloud. You might handle this scenario by checking whether the user has signed in before the app saves the record. If the user hasn’t signed in, present an alert. If they’re signed in, save the record.

The following example demonstrates preventing the error condition in this manner.

```
CKContainer.default().accountStatus { accountStatus, error in
    if accountStatus == .noAccount {
        DispatchQueue.main.async {
            let message = 
                """
                Sign in to your iCloud account to write records.
                On the Home screen, launch Settings, tap Sign in to your
                iPhone/iPad, and enter your Apple ID. Turn iCloud Drive on.
                """
            let alert = UIAlertController(
                title: "Sign in to iCloud",
                message: message,
                preferredStyle: .alert)
            alert.addAction(UIAlertAction(title: "OK", style: .cancel))
            self.present(alert, animated: true)
        }
    }
    else {
        // Save your record here.
    }
}
```

### Run your app

In Xcode, run your app to execute the code that saves records and creates the schema in the database. To verify success, see Inspecting and Editing an iCloud Container’s Schema.

## See Also

### Schemas

Managing iCloud Containers with CloudKit Database App

Inspect and modify the schema and data for your app’s iCloud container.

class CKRecordZone

A database partition that contains related records.

class CKRecord

A collection of key-value pairs that store your app’s data.

class Reference

A relationship between two records in a record zone.

class CKAsset

An external file that belongs to a record.

Integrating a Text-Based Schema into Your Workflow

Define and update your schema with the CloudKit Schema Language.

