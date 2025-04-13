

- CloudKit
- Managing iCloud Containers with CloudKit Database App
-  Handling an iCloud Container’s Data 

Article

# Handling an iCloud Container’s Data

Inspect and manage your app’s iCloud container data using the CloudKit Database app.

## Overview

You can use the CloudKit Database app to inspect data within a public iCloud container. If you develop using the same iCloud account to store private data, you can also use the CloudKit Database app to inspect and edit private data.

Don’t use the CloudKit Database app as a general data editor. Although you can create, modify, and delete records using the CloudKit Dashboard app, the intent of this functionality is to help you debug your schema during the design phase.

### Find and inspect records

Use the CloudKit Database app to search for records of a particular record type within a zone of the chosen database. To search for records in this way, you must first add a queryable index for that record type’s `recordName`. For more information, see the Enable querying for your record type section of Inspecting and Editing an iCloud Container’s Schema.

To search for records of a record type:

1.  From the CloudKit Database app, select your app’s container.

2.  Select Records from the Data section on the left.

3.  In the pane on the right, select the database, zone, and record type to view records for.

4.  Optionally, select fields to reduce the amount of data that returns in the results.

5.  Use the query input bar to add further filters to the request.

6.  Click the Query Records button, and view the results.

7.  Expand a record’s disclosure triangle to view its details.

Note

If you get the error, `“Field recordName is not marked queryable,”` see the Enable querying for your record type section of Inspecting and Editing an iCloud Container’s Schema.

### Create a record

You can create records in public databases in either the development or production environment. If your developer account is also an iCloud account, you can do the same for your private database.

To create a new record:

1.  From the CloudKit Database app, select your app’s container.

2.  Select Records from the Data section on the left.

3.  Click the Add button (+) at the top of the page, and choose Create New Record. The New Record dialog appears on the right. The new record has a random UUID that CloudKit assigns as the record name.

4.  Select the database, type, and zone you’re creating a record for.

5.  Enter values in the Fields area, and click Save.

### Modify or delete a record

In the development and production environment, you can modify and delete records in public databases. If your developer account is also an iCloud account, you can do the same for your private or shared databases.

To modify or delete an existing record:

1.  From the CloudKit Database app, select your app’s container.

2.  Select Records from the Data section on the left.

3.  In the pane on the right, select the database, zone, and record type to view records for.

4.  Optionally, select fields to reduce the amount of data that returns in the results.

5.  Use the query input bar to add further filters to the request.

6.  Click the Query Records button to search for records that match your criteria.

7.  In the results list, select the record you want to edit or delete. Its fields appear in the Custom Fields area in the Record Details dialog at the right.

8.  To edit a record, enter new values in the text fields and click Save.

9.  To delete a record, click the Delete button. Then, in the dialog that appears, click Delete to confirm the deletion.

## See Also

### Container Management

Inspecting and Editing an iCloud Container’s Schema

Review and edit the schema for your app’s container using the CloudKit Database app.

Deploying an iCloud Container’s Schema

Reset your container’s state during development and deploy your container’s schema to production.

Obtaining an API Token for an iCloud Container

Generate an API token to access CloudKit web services or use CloudKit JS.

