

- App Store Connect API
-  List variants information 

Web Service Endpoint

# List variants information

List variants for specific alternative distribution package version.

App Store Connect API 3.3+

## URL

``` source
GET https://api.appstoreconnect.apple.com/v1/alternativeDistributionPackageVersions/{id}/variants
```

## Path Parameters

`id`

`string`

 (Required) 

## Query Parameters

`fields[alternativeDistributionPackageVariants]`

`[string]`

Possible Values: `url, urlExpirationDate, alternativeDistributionKeyBlob, fileChecksum`

`limit`

`integer`

Maximum: `200`

## Response Codes

` 200 ``OK`

AlternativeDistributionPackageVariantsResponse

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

## Discussion

### Example Request and Response

- Request
- Response

```
https://api.appstoreconnect.apple.com/v1/alternativeDistributionPackageVersions/d1663e24-4360-4f7f-a661-8e616e3b3c3b/variants
```

```
{
  "data": [
    {
      "type": "alternativeDistributionPackageVariants",
      "id": "4c541b7a-15c3-43f9-955a-b6a108efbeb2",
      "attributes": {
        "url": "https://iosapps.itunes.apple.com/itunes-assets/SWDistributionArtifacts123/v4/2b/59/89/2b59891d-a15d-2dd5-6045-ca7678a30ffa/pre-thinned11331259484252926706.thinned.signed.dpkg.ipa?accessKey=1711772701_39674671210770318_4DTOwpunkZVQMLKpZ%2BjAwNgowYmcTc4wuMOmTOFvZGoatM6NH9nxnXAT4LPlxj4TjTJFgpup7mqKY4e2MCsK%2BPx%2F0YPImr7IGgKpHO%2Fpv%2BTsM2Xnar8bfWFBqNiAbNj0sXyOWGadl2yWlQGjj2d6l%2BAsWVscbovMko%2F3hqq8uZpfAVwZxcxsMBlKT35DmHQdt7Dou4vRj2A5%2FwaINXl5c7v42Bdei62Kl8o24dDmKzoFra1TiqcfmQC6Iv5DsIAl",
        "urlExpirationDate": "2024-03-29T21:25:01-07:00",
        "alternativeDistributionKeyBlob": "Z1HWrJd3AAAABAAAAAFUYH7ql3cAAAAEAAAAAfaWTj6EhQAAAAi2qUZInWMx01vEfIGEhQAAAAgAAAAAZbrpdWGqs9GEhQAAAAgAAAACgAlM7EDAqpNQ2wAAABAzDh0ZVuF6s3hEc8DgLYgHjmtHAlDbAAAA0OQldaDzMsijkMiQ+9cc7FcfIgY7Hccf9vPByDdNfeRb6IDCbTi/a7KsW/RVI15GeemXR3GOepUi8Fq0J2qr+g8XYbvMDgrdBaPwQcnjuzGEh9lSyZuk6h0BjwKyiQzM7Mt0fwsays6PVT2CaNJyMK6usqT4w+d9vztyLMEN2GAiEPn/q9IMmGcic5/T/+FLwCDRu/Rhj3FOIr4aCQZ+bnmbzyDv7r7a/B+siE0X0MTXsxoU4gGVvu2ThAoe+q6i9t6MtEu2N9B9FRcr1mAFxZoxOKXMUNsAAAAQhERpq5CkvNJrNdG2N6aILnZf7XBQ2wAAABDGwg2p+OJe8Z8PHtIA+2piJJC4HVDbAAAAEId4O7Ee3AyXNH6AYuOMw5po1KUAUNsAAABQdEQLV7XE5oAm3zpWhf74Rixf4tyhsBbgsKI8qeoJgONvIcz0byYB2EPSuQthWwTQJQDENNOvJiZkX52vVaFwCYpxoaRuMTo7A38Jtao6BLAHUZI1UNsAAAAgLT/ZgOBfpYaQUYzSeiZSjHrBqEbWFYtaqR/FwtOYSIwAAAAAUNsAAAAOAAAAAAAAAAAAAAAAAAA="
      },
      "links": {
        "self": "https://api.appstoreconnect.apple.com/v1/alternativeDistributionPackageVariants/4c541b7a-15c3-43f9-955a-b6a108efbeb2"
      }
    },
    {
      "type": "alternativeDistributionPackageVariants",
      "id": "b4ab437b-5c13-42c7-b5ea-a8ec9889e402",
      "attributes": {
        "url": "https://iosapps.itunes.apple.com/itunes-assets/SWDistributionArtifacts123/v4/36/46/ba/3646ba66-ad35-b5a1-b5a9-9a9dc490a003/pre-thinned11331259484252926706.thinned.signed.dpkg.ipa?accessKey=1711772702_1427237359064611442_j%2FXB8MGW%2FGVR9o3N6rCI63PgujyZoZVxN7xMmIwZIAZfFwCOr5WUQiwEQvXaguUGwtpKraEKQNbzsIq5vlSWVLr0G1Hz7OkjAQPlskdJqdFTLmzDOe8YuWMrtFXCUZ%2BUPm6KZQu2sZyfNdVoqoXCOVSV9KgpwVKUKvuZ5Oj9bg6k9L4afH4HLC7%2FZ0S0E%2BlG1HerKnKyOjewWCJqV0t7Yi6%2FjCY6EKE4yoPp9clquAJd6aR%2BxuGb%2FqwY%2FstsDRBl",
        "urlExpirationDate": "2024-03-29T21:25:02-07:00",
        "alternativeDistributionKeyBlob": "Z1HWrJd3AAAABAAAAAFUYH7ql3cAAAAEAAAAAfaWTj6EhQAAAAi4/6JJzTF4Y1vEfIGEhQAAAAgAAAAAZbrpdWGqs9GEhQAAAAgAAAACgAlM7EDAqpNQ2wAAABAUX/CANenwTqE+zCa0Go5RjmtHAlDbAAAA0O8d9OmuQVVLLHJ5NqHuy5RiIg1gFCSU596JSVqt30JomAeZmyeg7A033eOrl5UGaFPAFUtWBNYAG5Oy3LXEXurHcGP7R0bduTrcyRhUraRWwRZkFvlYSUpCqL4Ye6W+A1vBMODKDxXDk8ROjANbhCmnUTrE3wZ6N1RJqtbFiMAAL5V8ZHMgR/mppgj0/Qnv9R7Wkw7Fr00Mrn1xZcFZ4OtMG035PassXBun2/uV+Er5MItxy5QhBmmD9GDvKQfvJ/llljGGGQcUHVtH6hhr1QgxOKXMUNsAAAAQC7LlwBMbbKKOEA6MUONYa3Zf7XBQ2wAAABAMXIBQHUgb2uppLsFRWsjAJJC4HVDbAAAAEGkHfBWOZZ1ZzdI6an6H19Ro1KUAUNsAAABQkxQNnSw0CYr8aqmmO5mWa2erqyF96ZJP4vnno4RaWGYOBCJ+UtourTQRLEbLVMn9aAxqGNquuLQpYhxvsPS3VJkAwC5spOFlLS6RaYUnDTUHUZI1UNsAAAAg4ny+K6+r3sdb4bFZbmzsyAzIFORr5P0GcuNXEaYCHSMAAAAAUNsAAAAOAAAAAAAAAAAAAAAAAAA="
      },
      "links": {
        "self": "https://api.appstoreconnect.apple.com/v1/alternativeDistributionPackageVariants/b4ab437b-5c13-42c7-b5ea-a8ec9889e402"
      }
    }
  ],
  "links": {
    "self": "https://api.appstoreconnect.apple.com/v1/alternativeDistributionPackageVersions/d1663e24-4360-4f7f-a661-8e616e3b3c3b/variants"
  },
  "meta": {
    "paging": {
      "total": 2,
      "limit": 50
    }
  }
}
```

## See Also

### Getting version information

Read information for an alternative distribution package version

Get detail information about a specific alternative distribution package version.

Read version information for an alternative distribution package

Get version detail information about a specific alternative distribution package.

List deltas information

List deltas for a specific alternative distribution package version.

