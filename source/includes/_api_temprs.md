# Temprs

A `Tempr` is a template, mapping, recipe, or schema. It can have one or more of the following fields.

Field | Type | Required | Example
----- | ---- | -------- | -------
device_group_id |  number  | yes |
tempr_id        |  number  | yes |
name            |  string  | yes |
description     |  string  | no |
endpoint_type   |  string  | yes |
queue_request   |  boolean | ?? |
queue_response  |  boolean | ?? |
host            |  string  | yes | "your-endpoint.example.com"
port            |  number  | no | 443
path            |  string  | yes | "/api/devices/XYZ/messages?authentication_token=ABCDEX"
request_method  |  string  | yes | "POST"
protocol        |  string  | yes | "https"
language        |  string  | no | "js"
script          |  string  | no |

Filters available:

Filter | Type
------ | ----
id | number
device_group_id | number
name | string
description | string
sort[field] | string as above
sort[direction] | string

[//]:#(*****************************************************************************)

## Create

```shell
curl --location --request POST 'http://localhost/api/v1/temprs' \
--header 'Authorization: yourauthtoken' \
--header 'Content-Type: application/json' \
--header 'Content-Type: text/plain' \
--data-raw '{
    "tempr" : {
      "device_group_id": 2,
      "tempr_id" : 2,
      "name": "XYZ Bridge",
      "description": "The basic request sent from the original XYZ Bridge",
      "endpoint_type": null,
      "queue_request": false,
      "queue_response": false,
      "template": {
        "host": "endpoint.openinterop.local",
        "port": 443,
        "path": "/some/path/to/an/api",
        "request_method": "POST",
        "protocol": "https",
        "headers": {
          "Content-Type": "application/json"
        },
        "body": {
          "language": "js",
          "script": "module.exports = { \"event\" : message.message.body }"
        }
      }
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
  "id": 88
}
```

### HTTP Request

`POST http://localhost/api/v1/temprs`

### Headers

Parameter | Description
--------- | -----------
Authorization | yourauthtoken

### Content Body

Json string containing:
`
  {
    "tempr" : { 
      "name" : "XYZ_ABC",
      "description" : "Test of XYZ Connector" 
    }
  }
`

<aside class="notice">Replace <code>yourauthtoken</code> with your actual authenication token</aside>



[//]:#(*****************************************************************************)

## Preview (js)
```shell
curl --location --request POST 'http://localhost/api/v1/temprs/preview' \
--header 'Authorization: yourauthtoken' \
--header 'Content-Type: application/json' \
--header 'Content-Type: text/plain' \
--data-raw '{
    "tempr" : {
    "example_transmission" : "{  \"event\": {    \"COUNTRY_A\": \"UK\",    \"LABORATORY\": \"UTH\",    \"ORIGIN\": \"\",    \"PATIENT_ID\": \"PATTEST4\",    \"LAST_NAME\": \"\",    \"FIRST_NAME\": \"\" }}",
      "template" : {
      "host": "endpoint.openinterop.local",
      "port": 443,
      "path": "/some/path/to/an/api",
      "request_method": "POST",
      "protocol": "https",

      "headers": 
        {
          "Content-Type": "application/json"
        },
    "body" : {
      "language" : "js",
      "script" : "let payload = {   \"trackedEntityType\": \"tuhi0maUrlh\",   \"orgUnit\": message.message.body.event.FARM_NUM,   \"attributes\": [     {       \"attribute\": \"udQ5rLwup6d\",       \"value\": message.message.body.event.SPEC_NUM     },     {       \"attribute\": \"wAr0ZjIO0d8\",       \"value\": \"WNet_Animal\"     }   ],   \"enrollments\": [     {       \"orgUnit\": message.message.body.event.FARM_NUM,       \"program\": \"sWf6NXIupFI\",       \"programStage\": \"kGfHGNWI6iQ\",       \"enrollmentDate\": message.message.body.event.SPEC_DATE,       \"incidentDate\": message.message.body.event.SPEC_DATE,       \"events\": [         {           \"program\": \"sWf6NXIupFI\",           \"orgUnit\": message.message.body.event.FARM_NUM,           \"eventDate\": message.message.body.event.SPEC_DATE,           \"status\": \"COMPLETED\",           \"programStage\": \"kGfHGNWI6iQ\",           \"dataValues\": [               { \"dataElement\" : \"h74xyBYnXPB\", \"value\" : message.message.body.event.AMP_ND10 },               { \"dataElement\" : \"hMbQTNDTia2\", \"value\" : message.message.body.event.CPD_ND10 },               { \"dataElement\" : \"IYXfvQ9nS4O\", \"value\" : message.message.body.event.CIP_ND5 },               { \"dataElement\" : \"gnX3CxdocmO\", \"value\" : message.message.body.event.TCY_ND30 },               { \"dataElement\" : \"OxT8HFtgtCW\", \"value\" : message.message.body.event.GEN_ND10 },               { \"dataElement\" : \"zyXV5PZjiBm\", \"value\" : message.message.body.event.SXT_ND1_2 },               { \"dataElement\" : \"Wsk4NARIElI\", \"value\" : message.message.body.event.ORGANISM },               { \"dataElement\" : \"IvVVi4ft0v8\", \"value\" : message.message.body.event.SPEC_TYPE  }           ]         }       ]     }   ] };  module.exports = payload; "
    } }
  }
}'
```

> On Success the command returns JSON structured like this:

```json
{
    "rendered": {
        "host": "endpoint.openinterop.local",
        "port": "443",
        "path": "/some/path/to/an/api",
        "request_method": "POST",
        "protocol": "https",
        "headers": {
            "Content-Type": "application/json"
        },
        "body": "{\"trackedEntityType\":\"tuhi0maUrlh\",\"attributes\":[{\"attribute\":\"udQ5rLwup6d\"},{\"attribute\":\"wAr0ZjIO0d8\",\"value\":\"WNet_Animal\"}],\"enrollments\":[{\"program\":\"sWf6NXIupFI\",\"programStage\":\"kGfHGNWI6iQ\",\"events\":[{\"program\":\"sWf6NXIupFI\",\"status\":\"COMPLETED\",\"programStage\":\"kGfHGNWI6iQ\",\"dataValues\":[{\"dataElement\":\"h74xyBYnXPB\"},{\"dataElement\":\"hMbQTNDTia2\"},{\"dataElement\":\"IYXfvQ9nS4O\"},{\"dataElement\":\"gnX3CxdocmO\"},{\"dataElement\":\"OxT8HFtgtCW\"},{\"dataElement\":\"zyXV5PZjiBm\"},{\"dataElement\":\"Wsk4NARIElI\"},{\"dataElement\":\"IvVVi4ft0v8\"}]}]}]}"
    },
    "console": ""
}
```

### HTTP Request

`POST http://localhost/api/v1/temprs/preview`

### Headers

Parameter | Description
--------- | -----------
Authorization | yourauthtoken

### Content Body

Json string containing:
`
  {
    "tempr" : {
        "example_transmission" : "transmission data layout",
          "template" : {
            "host": "endpoint.openinterop.local",
            "port": 443,
            "path": "/some/path/to/an/api",
            "request_method": "POST",
            "protocol": "https",
          "headers": 
            {
                "Content-Type": "application/json"
            },
        "body" : {
          "language" : "moustache",
          "body" : "content of the template display"
        } 
      }
    }
  }
`

<aside class="notice">Replace <code>yourauthtoken</code> with your actual authenication token</aside>


[//]:#(*****************************************************************************)

## Preview (moustache)

```shell
curl --location --request POST 'http://localhost/api/v1/temprs/preview' \
--header 'Authorization: yourauthtoken' \
--header 'Content-Type: application/json' \
--header 'Content-Type: text/plain' \
--data-raw '{
    "tempr" : {
    "example_transmission" : "{  \"event\": {    \"COUNTRY_A\": \"UK\",    \"LABORATORY\": \"UTH\",    \"ORIGIN\": \"\",    \"PATIENT_ID\": \"PATTEST4\",    \"LAST_NAME\": \"\",    \"FIRST_NAME\": \"\" }}",
      "template" : {
      "host": "endpoint.openinterop.local",
      "port": 443,
      "path": "/some/path/to/an/api",
      "request_method": "POST",
      "protocol": "https",

      "headers": 
        {
          "Content-Type": "application/json"
        },
    "body" : {
      "language" : "moustache",
      "body" : "asd of this thing {{message.body.event.COUNTRY_A}} and also {{message.body.event.PATIENT_ID}}"
    } }
  }
}'
```
> On Success the command returns JSON structured like this:

```json
{
    "rendered": {
        "host": "endpoint.openinterop.local",
        "port": "443",
        "path": "/some/path/to/an/api",
        "request_method": "POST",
        "protocol": "https",
        "headers": {
            "Content-Type": "application/json"
        },
        "body": {
            "language": "moustache",
            "body": "asd of this thing UK and also PATTEST4"
        }
    },
    "console": ""
}
```

### HTTP Request

`POST http://localhost/api/v1/temprs/preview`

### Headers

Parameter | Description
--------- | -----------
Authorization | yourauthtoken

### Content Body

Json string containing:
`
  {
    "tempr" : {
        "example_transmission" : "transmission data layout",
          "template" : {
            "host": "endpoint.openinterop.local",
            "port": 443,
            "path": "/some/path/to/an/api",
            "request_method": "POST",
            "protocol": "https",
          "headers": 
            {
                "Content-Type": "application/json"
            },
        "body" : {
          "language" : "moustache",
          "body" : "content of the template display"
        } 
      }
    }
  }
`

<aside class="notice">Replace <code>yourauthtoken</code> with your actual authenication token</aside>



[//]:#(*****************************************************************************)

## List

```shell
curl --location --request GET 'http://localhost/api/v1/temprs' \
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
            "device_group_id": 1,
            "tempr_id": null,
            "name": "Dummy passthrough",
            "description": "",
            "endpoint_type": "http",
            "queue_request": true,
            "queue_response": true,
            "template": {
                "headers": {},
                "host": "localhost",
                "path": "/gateway/dummy-no-auth",
                "port": 9009,
                "protocol": "http",
                "request_method": "POST",
                "body": {
                    "language": "js",
                    "script": "module.exports = message.message.body"
                }
            },
            "example_transmission": null,
            "notes": "",
            "created_at": "2019-12-11T09:08:09.458Z",
            "updated_at": "2019-12-11T09:08:09.458Z"
        },
        {...}
    ],
    "core_version": "1.1.4"
}
```

This command will retrieve a list of Temprs on the system, matching supplied filters or all

### HTTP Request

`GET http://localhost/api/v1/temprs`

### URL Parameter

Parameter | Description
--------- | -----------
filter[xx] | yy

### Headers

Parameter | Description
--------- | -----------
Authorization | yourauthtoken

<aside class="notice">Replace <code>yourauthtoken</code> with your actual authenication token</aside>



[//]:#(*****************************************************************************)

## Update

```shell
curl --location --request PUT 'http://localhost/api/v1/temprs/68' \
--header 'Content-Type: application/json' \
--header 'Authorization: yourauthtoken' \
--header 'Content-Type: text/plain' \
--data-raw '{
  "tempr" : {
    "tempr_id" : 64
  }
}'
```

> On Success the command will return:

```json
```

This command will ...

### HTTP Request

`PUT http://localhost/api/v1/temprs/<id>`

### URL Parameter

Parameter | Description
--------- | -----------
id | tempr ID to be updated

### Content Body

Json string containing:
`
  {
    "tempr": {
      "tempr_id":"1234",
    }
  }
`

### Headers

Parameter | Description
--------- | -----------
Authorization | yourauthtoken

<aside class="notice">Replace <code>yourauthtoken</code> with your actual authenication token</aside>



[//]:#(*****************************************************************************)

## Delete

```shell
curl --location --request DELETE 'http://localhost/api/v1/temprs/65' \
--header 'Content-Type: application/json' \
--header 'Authorization: yourauthtoken' \
--header 'Content-Type: text/plain' \
--data-raw '{}'
```

Delete a single tempr from the system.

### HTTP Request

`DELETE http://localhost/api/v1/temprs/<id>`

### URL Parameter

Parameter | Description
--------- | -----------
id | tempr ID to be deleted

### Headers

Parameter | Description
--------- | -----------
Authorization | yourauthtoken

<aside class="notice">Replace <code>yourauthtoken</code> with your actual authenication token</aside>


[//]:#(*****************************************************************************)

## History

```shell
curl --location --request GET 'http://localhost/api/v1/temprs/56/history' \
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
            "id": 289,
            "auditable_id": 56,
            "auditable_type": "Tempr",
            "associated_id": null,
            "associated_type": null,
            "user_id": 1,
            "user_type": "User",
            "username": null,
            "action": "create",
            "audited_changes": {
                "body": {},
                "name": "Dummy passthrough",
                "notes": "",
                "template": {
                    "body": {
                        "script": "module.exports = message.message.body",
                        "language": "js"
                    },
                    "host": "openinterop.local",
                    "path": "/gateway/dummy-no-auth",
                    "port": 9009,
                    "headers": {},
                    "protocol": "http",
                    "request_method": "POST"
                },
                "tempr_id": null,
                "account_id": 1,
                "description": "",
                "endpoint_type": "http",
                "queue_request": true,
                "queue_response": true,
                "device_group_id": 1,
                "example_transmission": null
            },
            "version": 1,
            "comment": null,
            "remote_address": "127.0.0.1",
            "request_uuid": "93740d5d-5935-44a8-b8ba-a2eae9e07d79",
            "created_at": "2019-12-11T09:08:09.469Z"
        }
    ],
    "core_version": "1.1.4"
}
```

This command will ...

### HTTP Request

`GET http://localhost/api/v1/temprs/<id>/history`

### URL Parameter

Parameter | Description
--------- | -----------
id | tempr ID to get history for

### Headers

Parameter | Description
--------- | -----------
Authorization | yourauthtoken

<aside class="notice">Replace <code>yourauthtoken</code> with your actual authenication token</aside>
