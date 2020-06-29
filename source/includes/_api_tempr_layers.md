# Tempr Layer

A Tempr Layer is an association between Temprs and Layers.

Field | Type | Required | Example
----- | ---- | -------- | -------
tempr_id |  number  | yes |
layer_id |  number  | yes |

Filters available:

Filter | Type
------ | ----
layer_id | number
tempr_id | number
sort[field] | string as above
sort[direction] | string


[//]:#(*****************************************************************************)

## Create

```shell
curl --location --request POST 'http://localhost/api/v1/tempr_layers?tempr_id=39&layer_id=2' \
--header 'Authorization: yourauthtoken' \
--header 'Content-Type: application/json' \
}'
```

> If there is a problem then the command returns JSON structured like this (with multiple errors the fields will each have an entry):

```json
{
  "<fieldname>": [
    "<error message details>"
  ]
}
```

> On Success the command returns JSON structured like this:

```json
{
  "id": 88,
  "tempr_id": 39,
  "layer_id": 2
}
```

### HTTP Request

`POST http://localhost/api/v1/tempr_layers`

### URL Parameter

Parameter | Description
--------- | -----------
tempr_id | Tempr ID
layer_id | Layer ID

### Headers

Parameter | Description
--------- | -----------
Authorization | yourauthtoken

### Content Body

<aside class="notice">Replace <code>yourauthtoken</code> with your actual authenication token</aside>




[//]:#(*****************************************************************************)

## List

```shell
curl --location --request GET 'http://localhost/api/v1/tempr_layers?filter[layer_id]=2' \
--header 'Authorization: yourauthtoken' \
--header 'Content-Type: application/json'
```

> On Success the command will return:

```json
{
    "total_records": 5,
    "number_of_pages": 1,
    "page": {
        "number": 1,
        "size": 20
    },
    "data": [
        {
            "id": 56,
            "tempr_id": 213,
            "layer_id": 2
        },
        {...}
    ],
    "core_version": "1.1.5"
}
```

This command will retrieve a list of Tempr-Layer associations on the system for a given filter.

### HTTP Request

`GET http://localhost/api/v1/tempr_layers`

### URL Parameter

Parameter | Description
--------- | -----------
filter[..] | see table above for options

### Headers

Parameter | Description
--------- | -----------
Authorization | yourauthtoken

<aside class="notice">Replace <code>yourauthtoken</code> with your actual authenication token</aside>



[//]:#(*****************************************************************************)

## Delete

```shell
curl --location --request DELETE 'http://localhost/api/v1/tempr_layers/1?tempr_id=n&layer_id=n' \
--header 'Content-Type: application/json' \
--header 'Authorization: yourauthtoken' \
```

Delete a single Tempr-Layer association from the system - requires both Tempr id and Layer id.

### HTTP Request

`DELETE http://localhost/api/v1/tempr_layers/<id>`

### URL Parameter

Parameter | Description
--------- | -----------
tempr_id | Tempr ID +
layer_id | Layer ID +

### Headers

Parameter | Description
--------- | -----------
Authorization | yourauthtoken

<aside class="notice">Replace <code>yourauthtoken</code> with your actual authenication token</aside>

