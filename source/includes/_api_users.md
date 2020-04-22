# Users

Users are made up of the following fields... (and other words)

The Site can have one or more of the following fields:

Field | Type | Required | Notes
----- | ---- | -------- | -----
id  | number | yes | Unique
email | string | yes | Unique
time_zone | string | no | Default en-gb
password | string | yes | only accessed via API calls

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
  "password_confirmation": "new_password"
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
        "id": 666,
        "email": "testperson1@testplace.com",
        "created_at": "2019-12-13T16:30:56.104Z",
        "updated_at": "2020-04-14T09:43:33.425Z",
        "time_zone": "Mexico City"
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
            "id": 666,
            "email": "testperson1@testplace.com",
            "created_at": "2019-12-13T16:30:56.104Z",
            "updated_at": "2020-04-14T09:43:33.425Z"
        },
        {...}
    ],
    "core_version": "1.1.4"
}
```

Gets a list of the users on the system.

### HTTP Request

`GET http://localhost/api/v1/users`

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
