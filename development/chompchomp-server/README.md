# ChompChomp Server Documentation

-----

[Back to homepage](../..) • [software development guides](..)

-----

> This is currently a work-in-progress guide. Please feel free to contribute to it.

## Table of Contents

* [Database Schema](#database-schema)
  * [Schema Descriptions](#schema-descriptions)
  * [Sceham Example](#schema-example)

## Database Schema

Although there are different ways to store the data, i.e. a custom rolled database structure, document-like structure as with no-SQL databases, or tables as with SQL-like databases, it will be documented here as a document-like structure. This makes it easier to read.

Click [here](#schema-descriptions) to read about descriptions or [here](#schema-example) to see an example.

### Schema Descriptions

This is the schema of database objects stored on the server.

* `barcode`: A string of Trader Joe's internal barcode - according to the International Article Number spec, this should be made up of only integers
* `barcode_type`: `EAN8` or `EAN13`, if there are other types found, this will be updated
* `name`: String name of product - prefer the long name on tags rather than the short name on receipts due to searachability
* `price`: Most recent price observed
* `unit`: What unit the price is sold in, one of `EA` for each, `OZ` for ounces, `LB` for pounds
* `weight`: Floating point net weight of product in ounces
* `prices`: Observed prices of products - array of dictionaries
  * `store`: Integer Trader Joe's store number
  * `date`: String representation of date when this price was observed in `YYYY/MM/DD` format
  * `price`: Floating point price
* `images`: Array of dictionaries
  * `type`: One of `base64/png`, `base64/jpeg`, or `uri`
  * `data`: If `type` is `base64`, contains base 64 data of the image itself. If `type` is `uri`, contains a direct link to the image. Please try to pre-compress the image to save storage on the server

### Schema Example

This example follows the schema described above in [schema descriptions](#schema-descriptions).

```json
{
    "barcode": "00000000",
    "barcode_type": "EAN8",
    "name": "Cheese Wheel",
    "price": 1.99,
    "unit": "EA",
    "weight": 16,
    "prices": [
        {
            "store": 100,
            "date": "2021/01/01",
            "price": 1.99
        }
    ],
    "images": [
        {
            "type": "base64/png",
            "data": "data:image/png;base64,..."
        },
        {
            "type": "base64/jpeg",
            "data": "data:image/jpeg;base64,..."
        },
        {
            "type": "uri",
            "data": "https://i.imgur.com/2dn06CW.png"
        }
    ]
}
```
