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
