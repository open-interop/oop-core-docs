# Sites

Sites are made up of the folloqinf fields... (and other words)

The Site can have one or more of the following fields:

Field | Type | Required
----- | ---- | --------
account_id  | number | yes
site_id  | number | no
name  | string | no
description  | string | no
address  | string | no
city  | string | no
state  | string | no
zip_code  | string | no
country  | string | no
region  | string | no
latitude  | number | no
longitude  | number | no
time_zone  | string | no
external_uuids  | object | no
full_name  | string | no


[//]:#(*****************************************************************************)

## Create a New Site

```shell
curl --location --request POST 'http://oop.bluefrontier.local:9009/api/v1/sites' \
--header 'Authorization: yourauthtoken' \
--header 'Content-Type: application/json' \
--header 'Content-Type: text/plain' \
--data-raw '{ "site" : { "name" : "XYZABC", "account_id" : 22 } }'
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
  "account_id": 22,
  "site_id": null,
  "name": "XYZABC",
  "description": null,
  "address": null,
  "city": null,
  "state": null,
  "zip_code": null,
  "country": null,
  "region": null,
  "latitude": null,
  "longitude": null,
  "time_zone": null,
  "external_uuids": {},
  "created_at": "2020-04-14T16:28:08.984Z",
  "updated_at": "2020-04-14T16:28:09.025Z",
  "full_name": "XYZABC"
}
```

### HTTP Request

`POST http://oop.bluefrontier.local:9009/api/v1/sites`

### Headers

Parameter | Description
--------- | -----------
Authorization | yourauthtoken

### Content Body

Json string containing:
`
	{
		"site" : { 
			"name" : "XYZABC",
			"account_id" : 22 
		}
	}
`

<aside class="notice">Replace <code>yourauthtoken</code> with your actual authenication token</aside>




[//]:#(*****************************************************************************)

## List Sites

```shell
curl --location --request GET 'http://oop.bluefrontier.local:9009/api/v1/sites' \
--header 'Authorization: yourauthtoken' \
--header 'Content-Type: application/json'
```

> On Success the command returns JSON structured like this:

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
            "id": 88,
            "account_id": 22,
            "site_id": null,
            "name": "XYZABC",
            "full_name": "XYZABC",
            "description": null,
            "address": null,
            "city": null,
            "state": null,
            "zip_code": null,
            "country": null,
            "region": null,
            "latitude": null,
            "longitude": null,
            "time_zone": null,
            "external_uuids": {},
            "created_at": "2020-04-14T16:28:08.984Z",
            "updated_at": "2020-04-14T16:28:09.025Z"
        },
        {...}
    ],
    "core_version": "1.1.4"
}
```

Gets a list of the sites on the system.

### HTTP Request

`GET http://oop.bluefrontier.local:9009/api/v1/sites`

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

## Delete a Site

```shell
curl --location --request DELETE 'http://oop.bluefrontier.local:9009/api/v1/sites/666' \
--header 'Authorization: yourauthtoken' \
--header 'Content-Type: application/json'
```

Delete a single site from the system.

### HTTP Request

`DELETE http://oop.bluefrontier.local:9009/api/v1/sites/<id>`

### URL Parameter

Parameter | Description
--------- | -----------
id | Site ID to be deleted

### Headers

Parameter | Description
--------- | -----------
Authorization | yourauthtoken

<aside class="notice">Replace <code>yourauthtoken</code> with your actual authenication token</aside>




[//]:#(*****************************************************************************)

## Update a Site

```shell
curl --location --request PUT 'http://oop.bluefrontier.local:9009/api/v1/sites/666' \
--header 'Authorization: yourauthtoken' \
--header 'Content-Type: application/json'  \
--data-raw '{ "site" : { "name" : "QWERTY" } }'
```

Update details for a single site on the system.

### HTTP Request

`PUT http://oop.bluefrontier.local:9009/api/v1/sites/<id>`

### URL Parameter

Parameter | Description
--------- | -----------
id | Site ID to be updated

### Headers

Parameter | Description
--------- | -----------
Authorization | yourauthtoken

### Content Body

Json string containing:
`
	{
		"site": {
			"name":"QWERTY",
		}
	}
`

<aside class="notice">Replace <code>yourauthtoken</code> with your actual authenication token</aside>



[//]:#(*****************************************************************************)

## History

```shell
curl --location --request GET 'http://oop.bluefrontier.local:9009/api/v1/sites/666/history' \
--header 'Authorization: yourauthtoken' \
--header 'Content-Type: application/json'
```

Get the History Audit information for a single Site on the system.

### HTTP Request

`PUT http://oop.bluefrontier.local:9009/api/v1/sites/<id>/history`

### URL Parameter

Parameter | Description
--------- | -----------
id | Site ID to be updated

### Headers

Parameter | Description
--------- | -----------
Authorization | yourauthtoken

<aside class="notice">Replace <code>yourauthtoken</code> with your actual authenication token</aside>



[//]:#(*****************************************************************************)

## Sidebar

```shell
curl --location --request GET 'http://oop.bluefrontier.local:9009/api/v1/sites/sidebar?site_id=666' \
--header 'Authorization: yourauthtoken' \
--header 'Content-Type: application/json'
```

> On Success it Returns:

```json
{
    "sites": [
        {
            "id": 666,
            "name": "Test Account Site",
            "device_groups": [
                {
                    "id": 56,
                    "name": "Test Account Device Group",
                    "devices": [
                        {
                            "id": 42,
                            "name": "Test Account Device"
                        },
                        {
                            "id": 23,
                            "name": "AnotherTestDevice"
                        }
                    ]
                },
                {
                    "id": 78,
                    "name": "XYZ-Capture devices",
                    "devices": []
                }
            ]
        },
        {
		...
		}
	]
}
```

Get the Sidebar structure for a single Site on the system.

### HTTP Request

To get ALL sites:

`PUT http://oop.bluefrontier.local:9009/api/v1/sites/sidebar`

For a specific site:

`PUT http://oop.bluefrontier.local:9009/api/v1/sites/sidebar?site_id=5`


### URL Parameter

Parameter | Description
--------- | -----------
site_id | (optional) Site ID to get sidebar for

### Headers

Parameter | Description
--------- | -----------
Authorization | yourauthtoken


<aside class="notice">Replace <code>yourauthtoken</code> with your actual authenication token</aside>
