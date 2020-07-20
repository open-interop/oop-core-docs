# Layers

A 'Layer' is a piece of code that you can include in Temprs.

Field | Type | Required | Example
----- | ---- | -------- | -------
id |  number  | yes |
name | string | ?? |
reference | string | ?? |
script | string | ?? |

Filters available:

Filter | Type
------ | ----
id | number
name | string
reference | string
-script | string
sort[field] | string as above
sort[direction] | string

[//]:#(*****************************************************************************)

## Create a New Layers

```shell
curl --location --request POST 'http://localhost/api/v1/layers' \
--header 'Authorization: yourauthtoken' \
--header 'Content-Type: application/json' \
--header 'Content-Type: text/plain' \
--data-raw '{
  "layer": {
    "name": "My Layer",
    "reference": "test",
    "script": "module.exports = \"asd\""
  }
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
    "id": 3,
    "account_id": 123,
    "name": "My Layer",
    "reference": "test",
    "script": "module.exports = \"asd\"",
    "archived": false,
    "created_at": "2020-06-22T10:10:10.100Z",
    "updated_at": "2020-06-29T11:10:06.204Z"
}
```

### HTTP Request

`POST http://localhost/api/v1/layers`

### Headers

Parameter | Description
--------- | -----------
Authorization | yourauthtoken

### Content Body

Json string containing:
`
  {
    "layer" : { 
      "name" : "My Layer",
      "reference": "test",
      "script": "module.exports = \"asd\""
    }
  }
`

<aside class="notice">Replace <code>yourauthtoken</code> with your actual authenication token</aside>



[//]:#(*****************************************************************************)

## List Layers

```shell
curl --location --request GET 'http://localhost/api/v1/layers' \
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
            "name": "Test Layer",
            "reference": "test-layer",
            "script": "module.exports = {\n\"SomethingHere\": {\n \"type\": \"object\",\n \"properties\": {\n\"message\": {\n \"body\": \"string\"\n}\n}\n }\n}",
            "created_at": "2019-12-11T09:08:09.458Z",
            "updated_at": "2019-12-11T09:08:09.458Z"
        },
        {...}
    ],
    "core_version": "1.1.4"
}
```

This command will retrieve a list of Layers on the system, based on the filters supplied, or all of them if no filters given.

### HTTP Request

`GET http://localhost/api/v1/layers`

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

## Update a Layer

```shell
curl --location --request PUT 'http://localhost/api/v1/layers/68' \
--header 'Content-Type: application/json' \
--header 'Authorization: yourauthtoken' \
--header 'Content-Type: text/plain' \
--data-raw '{
  "layer": {
    "name": "Other Name"
  }
}'
```

> On Success the command will return:

```json
{
    "account_id": 123,
    "id": 68,
    "name": "Other Name",
    "reference": "test-layer",
    "script": "module.exports = {\n \"SomethingHere\": {\n \"type\": \"object\",\n \"properties\": {\n \"message\": {\n \"body\": \"string\"\n }\n }\n }\n}",
    "archived": false,
    "created_at": "2020-06-26T15:13:17.048Z",
    "updated_at": "2020-06-29T11:04:12.722Z"
}
```

This command will update specific details for a Layer on the system.

### HTTP Request

`PUT http://localhost/api/v1/layers/<id>`

### URL Parameter

Parameter | Description
--------- | -----------
id | Layer ID to be updated

### Content Body

Json string containing:
`
  {
    "layer": {
      "field":"value",
      "other field":"value"
    }
  }
`

### Headers

Parameter | Description
--------- | -----------
Authorization | yourauthtoken

<aside class="notice">Replace <code>yourauthtoken</code> with your actual authenication token</aside>



[//]:#(*****************************************************************************)

## Delete a Layer

```shell
curl --location --request DELETE 'http://localhost/api/v1/layers/65' \
--header 'Content-Type: application/json' \
--header 'Authorization: yourauthtoken' \
```

Delete a single Layer from the system.

### HTTP Request

`DELETE http://localhost/api/v1/layers/<id>`

### URL Parameter

Parameter | Description
--------- | -----------
id | Layer ID to be deleted

### Headers

Parameter | Description
--------- | -----------
Authorization | yourauthtoken

<aside class="notice">Replace <code>yourauthtoken</code> with your actual authenication token</aside>


[//]:#(*****************************************************************************)

## Assign Tempr to Layer

```shell
curl --location --request POST 'http://localhost/api/v1/layers/2/assign_tempr?tempr_id=39' \
--header 'Content-Type: application/json' \
--header 'Authorization: yourauthtoken'
```

> On Success the command will return:

```json
{
  "id": 8,
  "tempr_id": 39,
  "layer_id": 2,
  "created_at": "2020-06-26T16:27:50.936Z",
  "updated_at": "2020-06-26T16:27:50.936Z"
}
```

This command will assign a Tempr to the specified Layer.

### HTTP Request

`GET http://localhost/api/v1/layers/<id>/assign_tempr?tempr_id=<tid>`

### URL Parameter

Parameter | Description
--------- | -----------
id | Layer ID to assign Tempr to
tid | Tempr ID to assign to Layer

### Headers

Parameter | Description
--------- | -----------
Authorization | yourauthtoken

<aside class="notice">Replace <code>yourauthtoken</code> with your actual authenication token</aside>


[//]:#(*****************************************************************************)

## Layer History

```shell
curl --location --request GET 'http://localhost/api/v1/layers/1/history' \
--header 'Content-Type: application/json' \
--header 'Authorization: yourauthtoken'
```

> On Success the command will return:

```json
{
    "total_records": 1,
    "number_of_pages": 1,
    "page": {
        "number": 1,
        "size": 20
    },
    "data": [
        {
          "id": 431,
          "auditable_id": 2,
          "auditable_type": "Layer",
          "associated_id": null,
          "associated_type": null,
          "user_id": 1,
          "user_type": "User",
          "username": null,
          "action": "create",
          "audited_changes": {
              "name": "Test Layer",
              "script": "module.exports = {\n \"SomethingHere\": {\n \"type\": \"object\",\n  \"properties\": {,\n \"message\": {\n \"body\": \"string\"\n }\n }\n }",
              "archived": false,
              "reference": "test-layer",
              "account_id": 123
          },
          "version": 1,
          "comment": null,
          "remote_address": "127.0.0.1",
          "request_uuid": "d22cf719-6d8e-4196-ab7c-d529a097ecd8",
          "created_at": "2020-06-26T15:13:17.063Z"
        },
        {...}
    ],
    "core_version": "1.1.5"
}
```

The History command will get some details about the history of the Layer.

### HTTP Request

`GET http://localhost/api/v1/layers/<id>/history`

### URL Parameter

Parameter | Description
--------- | -----------
id | Layer ID to get history for

### Headers

Parameter | Description
--------- | -----------
Authorization | yourauthtoken

<aside class="notice">Replace <code>yourauthtoken</code> with your actual authenication token</aside>
