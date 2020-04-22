# Device Temprs

The Device Temprs can have one or more of the following fields:

Field | Type | Required | Notes
----- | ---- | -------- | -----
id  | number | yes | Unique
device_id | number | yes | eg. 5
tempr_id | number | yes | eg. 2

[//]:#(*****************************************************************************)

## Create

```shell
curl --location --request POST 'http://oop.bluefrontier.local:9009/api/v1/device_temprs?tempr_id=1&device_id=3' \
--header 'Authorization: yourauthtoken' \
--header 'Content-Type: application/json' \
--data-raw ''
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

`POST http://oop.bluefrontier.local:9009/api/v1/device_temprs`

### Headers

Parameter | Description
--------- | -----------
Authorization | yourauthtoken

### Content Body

Json string containing:
`
	{
		"xxx" : { 
			"name" : "XYZ_ABC",
			"description" : "Test of XYZ Connector" 
		}
	}
`

<aside class="notice">Replace <code>yourauthtoken</code> with your actual authenication token</aside>



[//]:#(*****************************************************************************)

## List

```shell
curl --location --request GET 'http://oop.bluefrontier.local:9009/api/v1/device_temprs?filter[tempr_id]]=2' \
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
            "id": 6,
            "device_id": 6,
            "tempr_id": 2
        }
    ],
    "core_version": "1.1.4"
}
```

This command will return a list of device to temprs links

### HTTP Request

`GET http://oop.bluefrontier.local:9009/api/v1/device_temprs`

### URL Parameter

Parameter | Description
--------- | -----------
filter[tempr_id] | unique temprs id

### Headers

Parameter | Description
--------- | -----------
Authorization | yourauthtoken

<aside class="notice">Replace <code>yourauthtoken</code> with your actual authenication token</aside>



[//]:#(*****************************************************************************)

## Delete

```shell
curl --location --request DELETE 'http://oop.bluefrontier.local:9009/api/v1/device_temprs/10?device_id=9&tempr_id=4' \
--header 'Authorization: yourauthtoken'
```

Delete a single device temprs from the system.

### HTTP Request

`DELETE http://oop.bluefrontier.local:9009/api/v1/device_temprs/<id>?device_id=<did>&tempr_id=<tid>`

### URL Parameter

Parameter | Description
--------- | -----------
id | device_temprs ID to be deleted
did | device ID to be deleted
tid | temprs ID to be deleted

### Headers

Parameter | Description
--------- | -----------
Authorization | yourauthtoken

<aside class="notice">Replace <code>yourauthtoken</code> with your actual authenication token</aside>

