# Sputnik

-----

[Back to homepage](../..) • [software development](..)

-----

## Table of Contents

* [Database Schema](#database-schema)

## Database Schema

The database stores multiple types of items:

* [Grocery Item](#grocery-item)
* [Store](#store)
* [Store Location](#store-location)

### Grocery Item

An item in the grocery store.

Notes:

* Only interday prices are tracked, no need for intraday
* Pretty much everything is optional (if the value is 0, don't include it)
* `unit` is `EA` (each), `PK` (pack), `OZ` (ounces), `LB` (pounds), `KG` (kilos). If `unit` is `PK`, then `unit_size` default is likely not 1
* All nutrition facts in grams. May need to convert oz to grams to figure out number of servings
* IDs are for internal database tracking

Example:

```json
{
  "id": 0,
  "store": 0,
  "barcode": "0076394622502",
  "barcode_type": "UPC",
  "name": "Alfaro's Astesano White Bakery Bread",
  "price": 3.49,
  "unit": "EA",
  "unit_size": 1,
  "weight": 20,
  "prices": [
    {
      "store": 1,
      "date": "2021/01/01",
      "price": 3.49
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
  ],
  "nutrition": {
    "serving_size": 38,
    "servings": 15,
    "calories": 110,
    "fat": {
      "total": 1.5,
      "saturated": 0,
      "trans": 0,
      "poly": 0.5, // Polyunsaturated Fat
      "mono": 0 // Monounsaturated Fat
    },
    "cholesterol": 0,
    "sodium": 0.19,
    "carbs": {
      "total": 20,
      "fiber": 1,
      "sugar": 2
    },
    "protein": 3,
    "vitamin": {
      "a": 0,
      "b": 0,
      "c": 0,
      "d": 0,
      "k": 0
    },
    "other": {
      "calcium": 0.05,
      "iron": 0.0011,
      "potassium": 0
    }
  }
}
```

### Store

A unique store chain, that uses the same internal database of grocery items.

Example:

```json
{
  "id": 0,
  "name": "Trader Joe's",
  "locations": [0]
}
```

### Store Location

A unique store location, representing a physical location of a store.

Example:

```json
{
  "id": 0,
  "store": 0,
  "address": {
    "street": "451 E Avendia De Los Arboles", // Optional
    "city": "Thousand Oaks",
    "state": "CA",
    "zip": "91360", // Optional
    "longitude": 34.218881, // Optional
    "latitude": -118.869229 // Optional
  },
  "meta": {
    "internal_id": "196" // Optional
  }
}
```
