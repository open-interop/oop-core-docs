# Schedule Temprs

The Schedule Temprs can have one or more of the following fields:

Field | Type | Required | Notes
----- | ---- | -------- | -----
id  | number | yes | Unique
xemail | string | yes | Unique
xtime_zone | string | no | Default en-gb
xpassword | string | yes | only accessed via API calls

[//]:#(*****************************************************************************)

## Create

```shell
curl --location --request POST 'http://localhost/api/v1/schedule_temprs?tempr_id=1&schedule_id=1' \
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

`POST http://localhost/api/v1/schedule_temprs?tempr_id=<tid>&schedule_id=<sid>`

### Headers

Parameter | Description
--------- | -----------
Authorization | yourauthtoken

### URL Parameter

Parameter | Description
--------- | -----------
tid | tempr ID
sid | schedule ID

### Content Body

Json string containing:
`
	{
	}
`

<aside class="notice">Replace <code>yourauthtoken</code> with your actual authenication token</aside>



[//]:#(*****************************************************************************)

## List

```shell
curl --location --request GET 'http://localhost/api/v1/schedule_temprs?filter[schedule_id]=1' \
--header 'Authorization: yourauthtoken' \
--header 'Content-Type: application/json'
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
            "schedule_id": 1,
            "tempr_id": 59
        }
    ],
    "core_version": "1.1.4"
}
```

This command will ...

### HTTP Request

`GET http://localhost/api/v1/schedule_temprs?filter[schedule_id]=<sid>`

### URL Parameter

Parameter | Description
--------- | -----------
sid | schedule ID
filter[xx] | yy

### Headers

Parameter | Description
--------- | -----------
Authorization | yourauthtoken

<aside class="notice">Replace <code>yourauthtoken</code> with your actual authenication token</aside>




[//]:#(*****************************************************************************)

## Delete

```shell
curl --location --request DELETE 'http://localhost/api/v1/schedule_temprs/1?device_id=4&tempr_id=8' \
--header 'Content-Type: application/json' \
--header 'Authorization: yourauthtoken' \
--header 'Content-Type: text/plain'
```

Delete a single xxx from the system.

### HTTP Request

`DELETE http://localhost/api/v1/schedule_temprs/<id>?device_id=<did>&tempr_id=<tid>`

### URL Parameter

Parameter | Description
--------- | -----------
id | schedule temprs ID to be deleted
did | device ID
tid | tempr ID

### Headers

Parameter | Description
--------- | -----------
Authorization | yourauthtoken

<aside class="notice">Replace <code>yourauthtoken</code> with your actual authenication token</aside>

