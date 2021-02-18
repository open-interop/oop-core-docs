# Users

Users are made up of the following fields... (and other words)

The User can have one or more of the following fields:

Field | Type | Required | Notes
----- | ---- | -------- | -----
id  | number | yes | Unique
email | string | yes | Unique
time_zone | string | no | Default en-gb
password | string | yes | only accessed via API calls
first_name | string | no | only letters, spaces or hyphens
last_name | string | no | only letters, spaces or hypens
job_title | string | no | 
description | text | no | 
date_of_birth | date time | no | date time in the past

Filters available:

Filter | Type
------ | ----
id | number
email | string
time_zone | string
sort[field] | string as above (excluding password)
sort[direction] | string

[//]:#(*****************************************************************************)

## Create a New User

```shell
curl --location --request POST 'http://localhost/api/v1/users' \
--header 'Authorization: yourauthtoken' \
--header 'Content-Type: application/json' \
--header 'Content-Type: text/plain' \
--data-raw '{
"user" : {
  "email": "new_email_address",
  "password": "new_password",
  "password_confirmation": "new_password",
  "first_name": "test",
  "last_name": "user name",
  "date_of_birth": "12/12/1999"
}}'
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
  "id": 2
}
```

### HTTP Request

`POST http://localhost/api/v1/users`

### Headers

Parameter | Description
--------- | -----------
Authorization | yourauthtoken

### Content Body

Json string containing:
`
	{
		"email":"new_email_address",
		"password":"new_password",
		"password_confirmation":"new_password",
    "first_name": "test",
    "last_name": "user name",
    "date_of_birth": "12/12/1999"
	}
`

<aside class="notice">Replace <code>yourauthtoken</code> with your actual authenication token</aside>



[//]:#(*****************************************************************************)

## Get User

```shell
curl --location --request GET 'http://localhost/api/v1/users/666' \
--header 'Authorization: yourauthtoken' \
--header 'Content-Type: application/json'
```

> On Success:

```json
  {
    "id": 9,
    "email": "test@example.com",
    "created_at": "2020-08-04T13:34:04.298Z",
    "updated_at": "2021-01-07T09:29:03.472Z",
    "time_zone": "Hawaii",
    "first_name": "NEW NAME",
    "last_name": "LAST",
    "description": null,
    "job_title": null,
    "date_of_birth": "2021-01-25"
  },
```

Get details for a single user on the system.

### HTTP Request

`GET http://localhost/api/v1/users/<id>`

### URL Parameter

Parameter | Description
--------- | -----------
id | User ID

### Headers

Parameter | Description
--------- | -----------
Authorization | yourauthtoken



[//]:#(*****************************************************************************)

## List Users

```shell
curl --location --request GET 'http://localhost/api/v1/users' \
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
            "id": 9,
            "email": "test@example.com",
            "created_at": "2020-08-04T13:34:04.298Z",
            "updated_at": "2021-01-07T09:29:03.472Z",
            "time_zone": "Hawaii",
            "first_name": "NEW NAME",
            "last_name": "OH",
            "description": null,
            "job_title": null,
            "date_of_birth": "2021-01-25"
        },
        {...}
    ],
    "core_version": "1.1.4"
}
```

Gets a list of the users on the system, based on the filters supplied, or all of them if no filters given.

### HTTP Request

`GET http://localhost/api/v1/users`

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

## Delete a User

```shell
curl --location --request DELETE 'http://localhost/api/v1/users/666' \
--header 'Authorization: yourauthtoken' \
--header 'Content-Type: application/json'
```

Delete a single user from the system.

### HTTP Request

`DELETE http://localhost/api/v1/users/<id>`

### URL Parameter

Parameter | Description
--------- | -----------
id | User ID to be deleted

### Headers

Parameter | Description
--------- | -----------
Authorization | yourauthtoken

<aside class="notice">Replace <code>yourauthtoken</code> with your actual authenication token</aside>


[//]:#(*****************************************************************************)

## Update a User

```shell
curl --location --request PUT 'http://localhost/api/v1/users/666' \
--header 'Authorization: yourauthtoken' \
--header 'Content-Type: application/json'  \
--data-raw '{ "user" : { "time_zone" : "Bern" } }'
```

Update details for a single user on the system.

### HTTP Request

`PUT http://localhost/api/v1/users/<id>`

### URL Parameter

Parameter | Description
--------- | -----------
id | User ID to be updated

### Headers

Parameter | Description
--------- | -----------
Authorization | yourauthtoken

### Content Body

Json string containing:
`
	{
		"user": {
			"time_zone":"Bern",
		}
	}
`

<aside class="notice">Replace <code>yourauthtoken</code> with your actual authenication token</aside>
