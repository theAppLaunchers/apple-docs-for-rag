

- Advanced Commerce API
-  Choosing tax codes for your SKUs 

Article

# Choosing tax codes for your SKUs

Select a tax code for each SKU that represents a product your app offers as an in-app purchase.

## Overview

Each SKU, which represents a unique product that your app offers as an in-app purchase, needs a tax code. You provide the tax code value each time you use the Advanced Commerce API to transact.

Use the following table to look up tax codes for your products.

Note

Other tax codes are available, similar to those listed in Set a tax category. If you don’t see an appropriate tax code for your product in the table below, send a request using the Advanced Commerce API Access form on the Advanced Commerce API page.

### Look up tax codes for in-app purchases

Select the tax code for your subscription or one-time purchase based on the following tax categories, subcategories, and attributes. You can use the App Store Software category as a default.

| Tax category / Tax subcategory | Selected attributes | Tax code for subscriptions | Tax code for one-time purchases |
|----|----|----|----|
| App Store Software (Default) | No selectable attributes | C003-00-1 | C003-00-2 |
| Audiobooks / Has ISBN, ISSN, or ECN | Available for offline listening | S007-01-1 | S007-01-2 |
| Audiobooks / Has ISBN, ISSN, or ECN | Available for offline listening  The standard (list) price is displayed  Contains stories with distributed speaker roles, noises, and music | S007-010409-1 | S007-010409-2 |
| Audiobooks / Does not have ISBN, ISSN, or ECN | Available for offline listening | S008-02-1 | S008-02-2 |
| Books / Has ISBN, ISSN, or ECN | Available for offline viewing  The standard (list) price is displayed  Contains interactive features (excluding dictionary, notation, and commenting features)  Contains profane or swear words | S001-03050614-1 | S001-03050614-2 |
| Boosting | No selectable attributes | N/A | C025-00-2 |
| Video / Pay-Per-View | No attribute selected | N/A | S022-00-2 |
| Video / Pay-Per-View | Exclusively features live TV broadcasting and/or linear programming | N/A | S022-01-2 |
| Video / Purchase for permanent access | Content is available for offline viewing | N/A | S020-01-2 |
| Video / Rental | Content is primarily accessed through streaming | N/A | S019-01-2 |
| Video / Subscription | No attribute selected | S021-08-1 | S021-08-2 |
| Video / Subscription | Live TV broadcasting and/or linear programming make up more than 10% of total content | S021-0308-1 | S021-0308-2 |

For more information about tax categories, see Set a tax category.

## See Also

### Tax codes and pricing

Specifying prices for Advanced Commerce SKUs

Provide prices for SKUs with the supported number of decimal places, in milliunits of currency.

Handling subscription price changes

Provide necessary customer communications to notify and gather applicable consent before you initiate a price change.

