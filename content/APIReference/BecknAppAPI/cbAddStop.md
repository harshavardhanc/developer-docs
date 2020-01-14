---
title: "Add Stop - Callback"
---

Callback response to Trip/Stop/Add.

#### API Endpoint

    Journey/cb_init

#### Request Structure :

The request structure of a search request consists of a **Header** and **Body**.

The request Header is an object of the [Header](/Resources/Header) class. The *Action* field of the Header object will be equal to *"Trip/Stop/cb_add"*

The request Body is a [Trip](/Resources/Trip) object with the inserted [Stop](#) object in the stops array.

##### Example Request:

**Header :**

```json
{
  "Action": "Trip/Stop/cb_add",
  "Token": "string",
  "transaction_id" : "string",
  "Timestamp": "2019-09-13T14:31:54"
}
```
**Body :**

```json
{
  "id": "< Unique Trip ID >",
  "state": "CONFIRM",
  "MobilityService": {
    "id": "h3nM51o2POfNqXeZJXu6",
    "name": "Port Authority Bus Service",
    "provision_type": "FIXED",
    "reservability": {
      "is_reservable": true
    },
    "capacity_type": {
      "carrier_reservable": false,
      "seat_reservable": false
    },
    "mobility_form": {
      "carrier": {
        "category": "BUS"
      },
      "medium": "ROADWAYS"
    }
  },
  "route": {
    "flexibilty": "FIXED CORRIDOR",
    "medium": "ROADWAYS",
    "stops": [
      {
        "location": {
          "value": "(12.878742,77.999654)",
          "format": "geocode"
        },
        "arrival_time": "2019-09-13T14:31:54+05:30",
        "buffer_time": "60 s",
        "departure_time": "2019-09-13T14:31:54+05:30"
      },
      {
        "location": {
          "value": "(12.878742,77.999654)",
          "format": "geocode"
        },
        "buffer_time": "60 s",
        "departure_time": "2019-09-13T14:31:54+05:30"
      },
      {
        "location": {
          "value": "(12.878742,77.999654)",
          "format": "geocode"
        },
        "arrival_time": "2019-09-13T14:31:54+05:30"
      }
    ],
    "edges": [
      {
        "travel_time": "2 min",
        "path": "polyline:(12.878742,77.999654),(12.878742,77.999654),(12.878742,77.999654)"
      }
    ]
  }
}
```

#### Response Structure

The response structure will consist of a **Header** and an optional **Body**

As the API is non-blocking, the Response to the above Request will be a **ACK** or a **NACK** response. The response Header is an object of the [Header](/Resources/Header) class. The ACK and NACK response Headers will have the action field equal to *"ACK"* and *"NACK"* respectively. The ACK response Body will be an **empty** JSON object.

The NACK response body may optionally contain an [Error](/Resources/Error) object.

##### Example ACK Response

**Header :**

```json
{
  "action": "ACK",
  "message": "Success Message string"
}
```

**Body :**
``` json
{}
```
##### Example NACK Response :

**Header :**
```json
{
  "action": "NACK",
  "message": "Error message string"
}
```
**Body :**
```json
{}
```