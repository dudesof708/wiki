# ChompChomp Server Documentation

-----

[Back to homepage](../..) • [software development guides](..)

-----

> This is currently a work-in-progress guide. Please feel free to contribute to it.

## Table of Contents

* [Development](#development)
* [Getting Started](#getting-started)
* [Routes](#routes)
  * [Get Item](#get-item)
  * [New Item](#new-item)
  * [Edit Item](#edit-item)
  * [Observe Item](#observe-item)
  * [Add Image](#add-image)
  * [Get Images](#get-images)
* [Database Schema](#database-schema)
  * [Schema Descriptions](#schema-descriptions)
  * [Schema Example](#schema-example)
* [Contributing](#contributing)
  * [Project Structure](#project-structure)

## Development

The server runs on localhost, port 5050 when run in development mode. This means you can navigate to [http://localhost:5050](http://localhost:5050) to see your server in action.

## Getting Started

To install, you'll need Python 3.7 or newer. If you can't figure out how to install Python, maybe it's time to reevalulate if you know what you're doing. (Just kidding, Google it or message the Discord channel.)

For the purposes of this guide, Python will be referred to as `python`. You may have your bindings set to `python3` or `python3.7` if you're using macOS or Linux, or `py -3` or `py -3.7` if you're using Windows.

1. Clone the [`ChompChomp-server`](https://github.com/dudesof708/ChompChomp-server) with git. If you don't know how, see [this guide](../../software/git).
2. Create a virtual environment:

   ```bash
   python -m venv venv
   ```

3. Activate the virtual environment. On Windows, run:

   ```ps
   .\venv\Scripts\activate
   ```

   or on Linux or macOS, run:

   ```bash
   source venv/bin/activate
   ```

4. Install required dependencies with `pip`. You may need to use `pip3` depending on how you have Python installed.

   ```bash
   pip install -r requirements.txt
   ```

## Routes

You can test your routes however you want, including by opening a custom build of the app pointing at your computer, but I reccommend [Postman](https://www.postman.com/). It's easy to use and easy to set up.

There are four routes

* `GET` [Get Item](#get-item)
* `POST` [New Item](#new-item)
* `POST` [Edit Item](#edit-item)
* `POST` [Observe Item](#observe-item)
* `POST` [Add Image](#add-image)
* `GET` [Get Images](#get-images)

### Get Item

**`GET`** `/items/get`: Gets an item from the database

*Requirements:*

* Must provide a parameter `barcode`

Provide a barcode to the database and it will respond with the corresponding object.

*Returns:*

On success, it returns status code `200 OK` with the corresponding item, except the images is replaced with the number of images:

```json
{
    "barcode": "00000000",
    ...
    "images": 3
```

On error, it returns status code `400 BAD REQUEST` if no barcode was provided or `404 NOT FOUND` if the barcode does not exist.

```json
{
    "error": true
}
```

### New Item

**`POST`** `/items/new`: Takes a new item as a JSON object.

*Requirements:*

* POST data must be of raw or text body type but contain a JSON-deserializable input.
* The `Content-Header` header with data `application/json` is required.

The input schema is:

* `date`: ISO 8601-compatiable timestamp
* `store`: String containing store number, city, and state code
* `name`: String containing name of product
* `price`: String containing float value of price
* `weight`: String containing float value of weight in oz.
* `barcode`: String value containing EAN-8 or EAN-13 barcode value

As an example, the input looks something like this:

```json
{
    "date": "2021-04-12T02:48:56.813Z",
    "store": "7 West Los Angeles, CA",
    "name": "Cheese Wheel",
    "price": "1.99",
    "weight": "16",
    "barcode": "00000000"
}
```

*Returns:*

On success, it returns status code `200 OK` with a success message:

```json
{
    "success": true
}
```

On error, it returns `400 BAD REQUEST` or `500 INTERNAL SERVER ERROR` depending on the error, with a corresponding error message:

```json
{
    "error": "Something happened!"
}
```

### Edit Item

**`POST`** `/item/edit`: Edits an item

*Requirements:*

* POST data must be of raw or text body type but contain a JSON-deserializable input.
* The `Content-Header` header with data `application/json` is required.
* The barcode must already exist in the database.

The input schema is:

* `barcode`: String value containing EAN-8 or EAN-13 barcode value to update
* `name`: (optional) Name to update
* `unit`: (optional) Update units
* `weight`: (optional) New weight to update to

As an example, here is something you can provide:

```json
{
    "barcode": "00000000",
    "weight": "16"
}
```

*Returns:*

The server returns status code `200 OK` with the new item (sans images) if successful, like so:

```json
{
    "barcode": "00000000",
    ...
    "images": 3
}
```

If the input was invalid, the server returns `400 BAD REQUEST` with the corresponding error message or `500 SERVER ERROR` if the input was unexpected. If the barcode does not exist, the server returns `404 NOT FOUND` instead.

Example:

```json
{
    "error": "Something happened!"
}
```

### Observe Item

**`POST`** `/item/observe`: Adds a price observation to an item

This endpoint hasn't been implemented yet.

### Add Image

**`POST`** `/item/images/add`: Add an image to the database

This endpoint hasn't been implemented yet.

### Get Images

**`GET`** `/item/images/get`: Get images from the database

*Requirements:*

* Must provide a barcode as a parameter as `barcode`

Provide the barcode to the database and it will return an array of images according to the spec as they are stored in the database.

*Returns:*

On success, it returns status code `200 OK` with images. Example:

```json
[
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
```

It may return `404 NOT FOUND` if the barcode doesn't exist and `400 BAD REQUEST` if no barcode was provided. If there are no images, it returns an empty array.

## Database Schema

Although there are different ways to store the data, i.e. a custom rolled database structure, document-like structure as with no-SQL databases, or tables as with SQL-like databases, it will be documented here as a document-like structure. This makes it easier to read.

Click [here](#schema-descriptions) to read about descriptions or [here](#schema-example) to see an example.

### Schema Descriptions

This is the schema of database objects stored on the server.

Some notes:

* In SQL format, subkeys, such as the prices array, is stored as a large JSON serializable object.
* Items without barcodes are not currently stored in the cache. This handling may be added later.

Schema:

* `barcode`: A string of Trader Joe's internal barcode - according to the International Article Number spec, this should be made up of only integers
* `barcode_type`: `EAN8`, `EAN13` or `Unknown`, if there are other types found, this will be updated
* `name`: String name of product - prefer the long name on tags rather than the short name on receipts due to searachability
* `price`: Most recent price observed
* `unit`: What unit the price is sold in, one of `EA` for each, `OZ` for ounces, `LB` for pounds
* `weight`: Floating point net weight of product in ounces
* `prices`: Observed prices of products - array of dictionaries
  * `store`: Integer Trader Joe's store number, or -1 if unknown or not assigned
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

## Contributing

So you want to contribute code, that's great! Here's a brief overview of the project...

### Project Structure

> This section is WIP.
