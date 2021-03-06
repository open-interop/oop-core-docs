# Devices

A device is a representation of the physical device used to collect data.  It can be based at a site location, or at a specified latitude/longitude, within a time-zone.

The Device can have one or more of the following fields:

Field | Type | Required | Notes
----- | ---- | -------- | -----
id  | number | yes | Unique
name | string | no | Readable name
device_group_id | number | no | eg. 1
site_id | number | no | eg. 21
latitude | number | no | eg. null
longitude | number | no | eg. null
time_zone | string | no | eg. "en-GB"
active | boolean | no | true or false

Filters available:

Filter | Type
------ | ----
id | number
name | string
device_group_id | number
site_id | number
latitude | number
longitude | number
time_zone | string
active | boolean
sort[field] | string as above (except latitude and longitude)
sort[direction] | string

[//]:#(*****************************************************************************)

## Create a New Device

```shell
curl --location --request POST 'http://localhost/api/v1/devices' \
--header 'Authorization: yourauthtoken' \
--header 'Content-Type: application/json' \
--header 'Content-Type: text/plain' \
--data-raw '{
	"device" : {
		"name" : "XYZ_ABC",
		"device_group_id" : 1,
		"site_id" : 1,
		"authentication_path" : "/gateway/xyz-abc"
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
    "id": 2,
    "name": "XYZ ABC",
    "device_group_id": 1,
    "site_id": 1,
    "latitude": null,
    "longitude": null,
    "time_zone": "",
    "created_at": "2019-12-13T16:32:11.002Z",
    "updated_at": "2019-12-13T16:32:15.603Z",
    "active": true
}
```

### HTTP Request

`POST http://localhost/api/v1/devices`

### Headers

Parameter | Description
--------- | -----------
Authorization | yourauthtoken

### Content Body

Json string containing:
`
	{
		"device" : { 
			"name" : "XYZ_ABC",
			"description" : "Test of XYZ Connector" 
		}
	}
`

<aside class="notice">Replace <code>yourauthtoken</code> with your actual authenication token</aside>



[//]:#(*****************************************************************************)

## List Devices

```shell
curl --location --request GET 'http://localhost/api/v1/devices' \
--header 'Authorization: yourauthtoken'
```

> On Success the command will return:

```json
{
    "total_records": 6,
    "number_of_pages": 1,
    "page": {
        "number": 1,
        "size": 20
    },
    "data": [
        {
            "id": 42,
            "name": "XyzAbc",
            "device_group_id": 1,
            "site_id": 11,
            "latitude": null,
            "longitude": null,
            "time_zone": "",
            "created_at": "2019-12-13T16:32:11.002Z",
            "updated_at": "2019-12-13T16:32:15.603Z",
            "active": true
        },
        {...}
    ]
}
```

This command will retrieve a list of devices, based on the filters supplied, or all of them if no filters given.

### HTTP Request

`GET http://localhost/api/v1/devices`

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

## Update a Device

```shell
curl --location --request PUT 'http://localhost/api/v1/devices/3' \
--header 'Content-Type: application/json' \
--header 'Authorization: yourauthtoken' \
--header 'Content-Type: text/plain' \
--data-raw '{ "device" : { "authentication_headers" : [] } }'
```

> On Success the command will return:

```json
{
    "account_id": 7,
    "id": 3,
    "authentication_headers": [],
    "authentication_query": [],
    "name": "XYZ_ABC",
    "authentication_path": "/gateway/xyz-abc",
    "site_id": 1,
    "device_group_id": 1,
    "latitude": null,
    "longitude": null,
    "time_zone": null,
    "created_at": "2020-07-15T15:47:51.569Z",
    "updated_at": "2020-07-15T15:47:51.569Z",
    "active": true
}
```

This command will update a specific device's fields.

### HTTP Request

`PUT http://localhost/api/v1/devices/<id>`

### URL Parameter

Parameter | Description
--------- | -----------
id | xxx ID to be updated

### Content Body

Json string containing:
`
	{
		"device": {
			"authentication_headers":"???",
		}
	}
`

### Headers

Parameter | Description
--------- | -----------
Authorization | yourauthtoken

<aside class="notice">Replace <code>yourauthtoken</code> with your actual authenication token</aside>



[//]:#(*****************************************************************************)

## Delete a Device

```shell
curl --location --request DELETE 'http://localhost/api/v1/devices/16' \
--header 'Content-Type: application/json' \
--header 'Authorization: yourauthtoken' \
--header 'Content-Type: text/plain'
```

Delete a single device from the system.

### HTTP Request

`DELETE http://localhost/api/v1/devices/<id>`

### URL Parameter

Parameter | Description
--------- | -----------
id | device ID to be deleted

### Headers

Parameter | Description
--------- | -----------
Authorization | yourauthtoken

<aside class="notice">Replace <code>yourauthtoken</code> with your actual authenication token</aside>


[//]:#(*****************************************************************************)

## Device History

```shell
curl --location --request GET 'http://localhost/api/v1/devices/59/audit_logs' \
--header 'Content-Type: application/json' \
--header 'Authorization: yourauthtoken'
```

> On Success the command will return:

```json
{
    "total_records": 2,
    "number_of_pages": 1,
    "page": {
        "number": 1,
        "size": 20
    },
    "data": [
        {
            "id": 38,
            "auditable_id": 42,
            "auditable_type": "Device",
            "associated_id": null,
            "associated_type": null,
            "user_id": 23,
            "user_type": "User",
            "username": null,
            "action": "create",
            "audited_changes": {
                "name": "XyzAbc",
                "active": false,
                "site_id": 21,
                "latitude": null,
                "longitude": null,
                "time_zone": "",
                "account_id": 1,
                "device_group_id": 1,
                "authentication_path": "/gateway/xyzabc",
                "authentication_query": [],
                "authentication_headers": []
            },
            "version": 1,
            "comment": null,
            "remote_address": "127.0.0.1",
            "request_uuid": "005da287-ef80-62c0-9ac2-e7066c7b2250",
            "created_at": "2019-12-13T16:32:11.049Z"
        },
        {
            ...
        }
    ],
    "core_version": "1.1.4"
}
```

This command will provide details of the audit history for the device.

### HTTP Request

`GET http://localhost/api/v1/devices/<id>/audit_logs`

### URL Parameter

Parameter | Description
--------- | -----------
id | device ID to get history for

### Headers

Parameter | Description
--------- | -----------
Authorization | yourauthtoken

<aside class="notice">Replace <code>yourauthtoken</code> with your actual authenication token</aside>



[//]:#(*****************************************************************************)

## Assign Tempr to Device

```shell
curl --location --request POST 'http://localhost/api/v1/devices/10/assign_tempr?tempr_id=5' \
--header 'Content-Type: application/json' \
--header 'Authorization: yourauthtoken' \
--header 'Content-Type: text/plain' \
--data-raw '{
  "device_tempr": {
    "endpoint_type": "http",
    "queue_response": true,
    "options": {
      "host": "202.31.132.92",
      "port": 80,
      "path": "/qwe/api/trackedEntityInstances",
      "requestMethod": "POST",
      "protocol": "http",
      "headers":
        {
          "Content-Type": "application/json",
          "Authorization" : "Basic arFjaz0nIVzhNTV6b3Kk"
        }
     
    }
  }
}'
```

Assign a Tempr to a single device on the system.

### HTTP Request

`POST http://localhost/api/v1/devices/<id>/assign_tempr?tempr_id=<tid>`

### URL Parameter

Parameter | Description
--------- | -----------
id | device ID to be assigned to
tid | tempr id to assign


### Headers

Parameter | Description
--------- | -----------
Authorization | yourauthtoken

<aside class="notice">Replace <code>yourauthtoken</code> with your actual authenication token</aside>
