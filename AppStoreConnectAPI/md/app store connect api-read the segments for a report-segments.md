

- App Store Connect API
-  Read the segments for a report 

Web Service Endpoint

# Read the segments for a report

Get details for a specific analytics report segment.

App Store Connect API 3.4+

## URL

``` source
GET https://api.appstoreconnect.apple.com/v1/analyticsReportInstances/{id}/segments
```

## Path Parameters

`id`

`string`

 (Required) 

The opaque resource ID that uniquely identifies the Apps resource. Obtain the app resource ID from the Read report instance information response.

## Query Parameters

`fields[analyticsReportSegments]`

`[string]`

Possible Values: `checksum, sizeInBytes, url`

`limit`

`integer`

Maximum: `200`

## Response Codes

` 200 ``OK`

AnalyticsReportSegmentsResponse

`OK`

Content-Type: application/json

` 400 ``Bad Request`

ErrorResponse

`Bad Request`

Content-Type: application/json

` 401 ``Unauthorized`

ErrorResponse

`Unauthorized`

Content-Type: application/json

` 403 ``Forbidden`

ErrorResponse

`Forbidden`

Content-Type: application/json

` 404 ``Not Found`

ErrorResponse

`Not Found`

Content-Type: application/json

## Mentioned in 

Downloading Analytics Reports

## Discussion

Tip

The download URLs are valid for 5 minutes after generating. You need to download the reports immediately after calling this endpoint.

### Examples Request and Response

- Request
- Response

```
https://api.appstoreconnect.apple.com/v1/analyticsReportInstances/d4a141c8-7647-4bdf-b9ae-04cab705d641/segments
```

```
{
  "data": [
    {
      "type": "analyticsReportSegments",
      "id": "503110d4-0fa2-41c0-9d41-ab7c7dac683f",
      "attributes": {
        "checksum": "3817152bb13cb70f615d9bb3899aaba6",
        "sizeInBytes": 156,
        "url": "https://asp-qa-us-west-2.s3.us-west-2.amazonaws.com/reports/389801252/APP_CRASHES_PRIMARY/DAILY/ONGOING/20240125/1707515196512/0.csv.gz?X-Amz-Security-Token=IQoJb3JpZ2luX2VjEGgaCXVzLXdlc3QtMiJIMEYCIQDeFnB%2B7UL2CsdboFmIXHoikVs3VyOVaTOJr0sfMkM2sAIhAM2jsmRPkxi1ZfY4F1rX%2Bzh5AQIODkr1AZbTsl5BCMHhKqICCFEQARoMNjEwNDgzMzUxMzUwIgzfxJlERt4K4Em4Hp8q%2FwHPjAxuT28WVnqXiR%2Fekc1WqV%2B6FgUJiWefx5%2FilyLIF%2FSeQ%2F%2Boav%2F9xdgPymjnX9nHs6T%2FKNxESQaEclt9JLvoSNwRKPIFxEXGDpiSTNzRNKdPtp6KngfX2N6Eu8O7IxVl%2BsZ8Vt8jRYJEbpi2dzP2xqqBtvhQUSdP4HI4HIeVETU67tIDb61oATqKzk6kS1%2B3HkVVHsOYTG9wLzYegwBKOel0QkgslVx9AzuzyFsYt9z8ZPmsjssElrbFswUODqEHRK4FmOxlmkXSyLuKNLT0YgFGIS85%2BHxZrocrAJp1dgK5vlzmioVPx7t1O4qwQI5JyALx1Y9K1G1hxkUzlqcwrqLargY6nAHeG%2BXoJLrLG6RWyvnWDbU9sWUEWCX6WCNxU%2Bd%2BHdyngLd6%2FkFpB8fDBMQpQMvIuDO%2FTXGs%2F39Day4vZyNyIZCsxdP7coYejv7HJed48tGoEqbLWs6WdArcx6xnCGyXyYbWU1mkP%2BG5gkSxx0sQqxeQYoQfbFwpARuNZqpXoFoZUAj1GIEx1DxOOYKcj5LzImG5HFHpvXPqrTEtG0E%3D&X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Date=20240222T001200Z&X-Amz-SignedHeaders=host&X-Amz-Expires=300&X-Amz-Credential=ASIAY4I5EV43MJZFZNQ4%2F20240222%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Signature=59e731e051cf6484291fbd9d77077c8e4128945d1bf274149f098c11dfdc60b6"
      },
      "links": {
        "self": "https://api.appstoreconnect.apple.com/v1/analyticsReportSegments/503110d4-0fa2-41c0-9d41-ab7c7dac683f"
      }
    }
  ],
  "links": {
    "self": "https://api.appstoreconnect.apple.com/v1/analyticsReportInstances/d4a141c8-7647-4bdf-b9ae-04cab705d641/segments"
  },
  "meta": {
    "paging": {
      "total": 1,
      "limit": 50
    }
  }
}

```

## See Also

### Reading Reports, Instances, and Segments

Read report information

Get details for a specific analytics report.

Read a list of instances of a report

Read list of all the granularity options for a specific type of analytics report.

Read report instance information

Get details for a specific instance of an analytics report.

Read the details for a report segment

Get details and download information for a specific analytics report segment.

