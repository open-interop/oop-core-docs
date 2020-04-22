# Schedules

Timings are Cron style timing definitions
"/x" = runs every x minor time units, 
"x" = run on x minor time units after the major time until
eg. for minute "12/2" will run the task every 2 minutes after 12

Schedules have these fields:
Fieldname | Type | Info | Sortable
--------- | ---- | ---- | --------
id	| number | Unique ID | yes
name	| string | Readable name | yes
minute	| string | Timing string see above | no
hour	| string | Timing string see above | no
day_of_week	| string | Timing string see above | no
day_of_month	| string | Timing string see above | no
month_of_year	| string | Timing string see above | no
year	| string | Timing string see above | no
active	| bool | true or false | yes

Filters available:
Filter | Type
------ | ----
id | number
name | string
active | string 
sort[field] | string as above (where marked as sortable)
sort[direction] | string

[//]:#(*****************************************************************************)

## Create

```shell
curl --location --request POST 'http://oop.bluefrontier.local:9009/api/v1/schedules' \
--header 'Authorization: yourauthtoken' \
--header 'Content-Type: application/json' \
--header 'Content-Type: text/plain' \
--data-raw '{
	"schedule" : {
		"name" : "XYZ_Schedule",
		"day_of_week" : "1"
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
	"id": 88,
	"account_id": 1,
	"name": "XYZ_Schedule",
	"active": true,
	"minute": "*",
	"hour": "*",
	"day_of_week": "1",
	"day_of_month": "*",
	"month_of_year": "*",
	"year": "*",
	"created_at": "2020-04-22T15:12:08.260Z",
	"updated_at": "2020-04-22T15:12:08.260Z"
}
```

### HTTP Request

`POST http://oop.bluefrontier.local:9009/api/v1/schedules`

### Headers

Parameter | Description
--------- | -----------
Authorization | yourauthtoken

### Content Body

Json string containing:
`
	{
		"schedule" : { 
			"name" : "XYZ_Schedule",
			"day_of_week" : "1" 
		}
	}
`

<aside class="notice">Replace <code>yourauthtoken</code> with your actual authenication token</aside>



[//]:#(*****************************************************************************)

## List

```shell
curl --location --request GET 'http://oop.bluefrontier.local:9009/api/v1/schedules' \
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
	      "id": 1,
	      "name": "XYZ_Schedule",
	      "minute": "*/2",
	      "hour": "*",
	      "day_of_week": "*",
	      "day_of_month": "*",
	      "month_of_year": "*",
	      "year": "*",
	      "created_at": "2020-02-03T17:03:02.185Z",
	      "updated_at": "2020-02-05T18:21:41.830Z",
	      "active": true
	    }
    ],
    "core_version": "1.1.4"
}
```

This command will fetch a list of schedules based in the filters supplied, or all of them if no filters given.

### HTTP Request

`GET http://oop.bluefrontier.local:9009/api/v1/schedules?filter[xx]=yy`

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
curl --location --request PUT 'http://oop.bluefrontier.local:9009/api/v1/schedules/2' \
--header 'Content-Type: application/json' \
--header 'Authorization: yourauthtoken' \
--header 'Content-Type: text/plain' \
--data-raw '{ "schedule" : { "active" : false } }'
```

> On Success the command will return:

```json
{
    "account_id": 1,
    "id": 2,
    "active": false,
    "name": "XYZ_Schedule",
    "minute": "*",
    "hour": "*",
    "day_of_week": "1",
    "day_of_month": "*",
    "month_of_year": "*",
    "year": "*",
    "created_at": "2020-04-22T15:12:08.260Z",
    "updated_at": "2020-04-22T15:17:03.251Z"
}
```

This command will update the scedule for the supplied fields.

### HTTP Request

`PUT http://oop.bluefrontier.local:9009/api/v1/schedules/<id>`

### URL Parameter

Parameter | Description
--------- | -----------
id | schedule ID to be updated

### Content Body

Json string containing:
`
	{
		"schedule": {
			"active": false,
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
curl --location --request DELETE 'http://oop.bluefrontier.local:9009/api/v1/schedules/16' \
--header 'Content-Type: application/json' \
--header 'Authorization: yourauthtoken'
```

Delete a single schedule from the system.

### HTTP Request

`DELETE http://oop.bluefrontier.local:9009/api/v1/schedules/<id>`

### URL Parameter

Parameter | Description
--------- | -----------
id | schedule ID to be deleted

### Headers

Parameter | Description
--------- | -----------
Authorization | yourauthtoken

<aside class="notice">Replace <code>yourauthtoken</code> with your actual authenication token</aside>


[//]:#(*****************************************************************************)

## History

```shell
curl --location --request GET 'http://oop.bluefrontier.local:9009/api/v1/schedules/2/history' \
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
            "id": 410,
            "auditable_id": 2,
            "auditable_type": "Schedule",
            "associated_id": null,
            "associated_type": null,
            "user_id": 33,
            "user_type": "User",
            "username": null,
            "action": "create",
            "audited_changes": {
                "hour": "*",
                "name": "XYZ_Schedule",
                "year": "*",
                "active": true,
                "minute": "*",
                "account_id": 1,
                "day_of_week": "1",
                "day_of_month": "*",
                "month_of_year": "*"
            },
            "version": 1,
            "comment": null,
            "remote_address": "127.0.0.1",
            "request_uuid": "8f78e130-d7a3-4fbf-b6ac-b101b051bf37",
            "created_at": "2020-04-22T15:12:10.045Z"
        }
    ],
    "core_version": "1.1.4"
}
```

This command will ...

### HTTP Request

`GET http://oop.bluefrontier.local:9009/api/v1/schedules/<id>/history`

### URL Parameter

Parameter | Description
--------- | -----------
id | schedule ID to get history for

### Headers

Parameter | Description
--------- | -----------
Authorization | yourauthtoken

<aside class="notice">Replace <code>yourauthtoken</code> with your actual authenication token</aside>


[//]:#(*****************************************************************************)

## Assign Tempr to Schedule

```shell
curl --location --request POST 'http://oop.bluefrontier.local:9009/api/v1/schedules/10/assign_tempr?tempr_id=5' \
--header 'Authorization: yourauthtoken' \
--header 'Content-Type: application/json' \
--data-raw ''
```

> On Success the command will return:

```json
```

This command will ...

### HTTP Request

`GET http://oop.bluefrontier.local:9009/api/v1/schedules/<id>/assign_tempr?tempr_id=<tid>`

### URL Parameter

Parameter | Description
--------- | -----------
id | Schedule ID to assign to
tid | Tempr ID to assign

### Headers

Parameter | Description
--------- | -----------
Authorization | yourauthtoken

<aside class="notice">Replace <code>yourauthtoken</code> with your actual authenication token</aside>
