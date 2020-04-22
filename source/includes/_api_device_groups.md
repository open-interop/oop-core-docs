# Device Groups

The Device Group can have one or more of the following fields:

Field | Type | Required | Notes
----- | ---- | -------- | -----
id  | number | yes | Unique
xemail | string | yes | Unique
xtime_zone | string | no | Default en-gb
xpassword | string | yes | only accessed via API calls

[//]:#(*****************************************************************************)

## Create a New Device Group

```shell
curl --location --request POST 'http://localhost/api/v1/device_groups' \
--header 'Authorization: yourauthtoken' \
--header 'Content-Type: application/json' \
--header 'Content-Type: text/plain' \
--data-raw '{ "device_group" : { "name" : "XYZ_ABC", "description" : "Test of XYZ Connector" } }'
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

`POST http://localhost/api/v1/device_groups`

### Headers

Parameter | Description
--------- | -----------
Authorization | yourauthtoken

### Content Body

Json string containing:
`
	{
		"device_group" : { 
			"name" : "XYZ_ABC",
			"description" : "Test of XYZ Connector" 
		}
	}
`

<aside class="notice">Replace <code>yourauthtoken</code> with your actual authenication token</aside>


[//]:#(*****************************************************************************)

## List

```shell
curl --location --request GET 'http://localhost/api/v1/device_groups' \
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
            "id": 16,
            "name": "ABC-Capture devices",
            "created_at": "2019-10-25T14:24:50.649Z",
            "updated_at": "2019-10-25T14:24:50.649Z"
        },
        {
            "id": 1,
            "name": "XYZ Device Group",
            "created_at": "2019-08-30T08:58:48.022Z",
            "updated_at": "2019-08-30T08:58:48.022Z"
        }
    ],
    "core_version": "1.1.4"
}
```

This command will list existing device groups.

### HTTP Request

`GET http://localhost/api/v1/device_groups`

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
curl --location --request PUT 'http://localhost/api/v1/device_groups/4' \
--header 'Content-Type: application/json' \
--header 'Authorization: yourauthtoken' \
--header 'Content-Type: text/plain' \
--data-raw '{ "user" : { "time_zone" : "London" } }'
```

> On Success the command will return:

```json
```

This command will update specified fields within a device group.

### HTTP Request

`PUT http://localhost/api/v1/device_groups/<id>`

### URL Parameter

Parameter | Description
--------- | -----------
id | device group ID to be updated

### Content Body

Json string containing:
`
	{
		"xxx": {
			"name":"QWERTY",
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
```

Delete a single device group from the system.

### HTTP Request

`DELETE http://localhost/api/v1/device_groups/<id>`

### URL Parameter

Parameter | Description
--------- | -----------
id | device group ID to be deleted

### Headers

Parameter | Description
--------- | -----------
Authorization | yourauthtoken

<aside class="notice">Replace <code>yourauthtoken</code> with your actual authenication token</aside>


[//]:#(*****************************************************************************)

## History

```shell
curl --location --request GET 'http://localhost/api/v1/device_groups/1/history' \
--header 'Content-Type: application/json' \
--header 'Authorization: yourauthtoken'
```

> On Success the command will return:

```json
{
    "total_records": 0,
    "number_of_pages": 0,
    "page": {
        "number": 1,
        "size": 20
    },
    "data": [],
    "core_version": "1.1.4"
}
```

This command will get the audit history for the specified device group.

### HTTP Request

`GET http://localhost/api/v1/device_groups/<id>/history`

### URL Parameter

Parameter | Description
--------- | -----------
id | device group ID to get history for

### Headers

Parameter | Description
--------- | -----------
Authorization | yourauthtoken

<aside class="notice">Replace <code>yourauthtoken</code> with your actual authenication token</aside>
