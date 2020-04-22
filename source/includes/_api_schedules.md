# Schedules

Timings are Cron style timing definitions
"/x" = runs every x minor time units, 
"x" = run on x minor time units after the major time until
eg. for minute "12/2" will run the task every 2 minutes after 12

Schedules have these fields:
Fieldname | Type | Info
id	| number | Unique ID
name	| string | Readable name
minute	| string | Timing string see above
hour	| string | Timing string see above
day_of_week	| string | Timing string see above
day_of_month	| string | Timing string see above
month_of_year	| string | Timing string see above
year	| string | Timing string see above
active	| bool | true or false
    }

[//]:#(*****************************************************************************)

## Create

```shell
curl --location --request POST 'http://localhost/api/v1/schedules' \
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
  "id": 88
}
```

### HTTP Request

`POST http://localhost/api/v1/schedules`

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
curl --location --request GET 'http://localhost/api/v1/schedules' \
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

This command will ...

### HTTP Request

`GET http://localhost/api/v1/schedules`

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
curl --location --request PUT 'http://localhost/api/v1/schedules/1' \
--header 'Content-Type: application/json' \
--header 'Authorization: yourauthtoken' \
--header 'Content-Type: text/plain' \
--data-raw '{ "schedule" : { "active" : false } }'
```

> On Success the command will return:

```json
```

This command will ...

### HTTP Request

`PUT http://localhost/api/v1/schedules/<id>`

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
curl --location --request DELETE 'http://localhost/api/v1/schedules/16' \
--header 'Content-Type: application/json' \
--header 'Authorization: yourauthtoken'
```

Delete a single schedule from the system.

### HTTP Request

`DELETE http://localhost/api/v1/schedules/<id>`

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
curl --location --request GET 'http://localhost/api/v1/schedules/59/history' \
--header 'Content-Type: application/json' \
--header 'Authorization: yourauthtoken'
```

> On Success the command will return:

```json
```

This command will ...

### HTTP Request

`GET http://localhost/api/v1/schedules/<id>/history`

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
curl --location --request POST 'http://localhost/api/v1/schedules/10/assign_tempr?tempr_id=5' \
--header 'Authorization: yourauthtoken' \
--header 'Content-Type: application/json' \
--data-raw ''
```

> On Success the command will return:

```json
```

This command will ...

### HTTP Request

`GET http://localhost/api/v1/schedules/<id>/assign_tempr?tempr_id=<tid>`

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
