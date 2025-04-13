

- App Store Connect API
- Analytics
-  Downloading Analytics Reports 

Article

# Downloading Analytics Reports

Learn how to request and review data about your apps, their usage, engagement, and performance.

## Overview

Use the Analytics Reports API to request and download reports for your apps. This API provides access to reports in these categories:

App Store Engagement  
Engagement information shows how people find, discover, and share your app on the App Store.

App Store Commerce  
Information about downloads, pre-orders, and purchases helps you analyze revenue and sales.

App Usage  
Usage information helps you understand how people interact with your apps, and includes details about app sessions, installations, and crashes

Framework Usage  
Framework usage details help you analyze how people interact with your app and how your app uses APIs.

Performance  
Performance metrics show how your app performs and how users interact with specific features.

Note

To learn more about the contents of each report, see Analytics Reports.

### Understand roles and reports

To download analytics reports, be sure your API key has one of the following roles, because each role has access to specific endpoints:

| Role | Manage requests | List and download reports |
|----|----|----|
| Admin | Request reports and Delete a report request | Read reports for a specific request |
| Sales and Reports |  | Read reports for a specific request |
| Finance |  | Read reports for a specific request |

Note

If you share an API key for your developer account with a third party for analyzing or processing your reports, select the `Sales and Reports` role when generating a new key. This role can access to the Download Sales and Trends Reports but can’t access Download Finance Reports endpoint.

### Request analytics reports

Start by using the Request reports API to request generation of reports for one of your apps. There are two types of `accessTypes` for report requests:

`ONGOING`  
Provides current data and is the most typical. It generates reports daily, weekly and monthly.

`ONE_TIME_SNAPSHOT`  
Provides up-to-the-moment data and goes back as far as is available. It doesn’t generate any new data after the day you request it.

Your first report request generates in 1–2 days. Subsequent `ONGOING` reports are available daily.

To see a list of your report requests, use Read report requests.

To read more information about a specific request, use Read report request information with the `ID` from Read report requests to see if the report is still active and generating new reports.

Note

If you don’t retrieve data for a long time, a report request changes to `stoppedDueToInactivity`. You need to make a new request to resume getting reports.

### Read the analytics reports

Use Read reports for a specific request to check whether your reports are available. This endpoint lists all the reports that the API generated to fulfill your request. For more about the information in each report see Analytics Reports.

Each report has a name and category attributes, like this:

```
      "attributes": {
        "name": "App Store Discovery and Engagement Detailed",
        "category": "APP_STORE_ENGAGEMENT"
      }
```

Some reports have two content levels, Standard or Detailed, which the report’s name reflects with a suffix. Standard reports include fields not easily related to uniquely identifiable user data. Detailed reports include all fields and also include additional privacy measures for the data, to help protect uniquely identifiable information for individuals.

To learn more about what data is in each report and report type, see Analytics Reports.

### Download specific analytic report data

Select a report of interest and use Read a list of instances of a report to see a list of report instances filtered by `granularity` and `processingDate`. *Instances* are discreet containers for a report data set. You can choose a `granularity` of daily, weekly, or monthly for the reports in an instance. The `processingDate` represents new data available that day. The data for a given report with a specific `processingDate` might contain data for that day, full data for past dates, or both.

Then, you use the Read the segments for a report endpoint to get a download URL for the report. *Segments* are the actual report files, and based on the amount of data for a specific instance, you might have multiple segments to download. You can also use `sizeInBytes` and `checksum` to verify a specific report segment downloaded successfully.

### Analyze your app data

After you download some reports, you can start analyzing the data and learning more about how people use your apps. To learn more about the fields and descriptions in these reports see Analytics Reports.

For `ONGOING` report requests you need to regularly use these APIs to get updated data for these reports.

