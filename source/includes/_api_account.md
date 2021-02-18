# Account

The account is used by core to know which records to fetch from the database, as they are all linked to an acount instance

Accounts have these fields:

Field | Type
----- | ----
id | number
name  | string
hostname  | string
active | boolean
owner_id | number
interface_scheme | string
interface_port | number
interface_path | string
created_at | date time
updated_at | date time


The account cannot be filtered, as the request GET will only ever return one record - the current account:

[//]:#(*****************************************************************************)

## Get Current Account

```shell
curl --location --request GET 'http://localhost/api/v1/account' \
--header 'Authorization: yourauthtoken'
```

> On Success the command will return:

```json
{
    "id": 3,
    "name": "ACC NAME",
    "hostname": "192.168.1.94",
    "active": true,
    "owner_id": null,
    "created_at": "2020-08-04T12:37:58.652Z",
    "updated_at": "2021-01-12T14:44:26.540Z",
    "interface_scheme": "http://",
    "interface_port": 80,
    "interface_path": "/"
}
```

This command will retrieve an object representing the current account used by core when the request was made.

### HTTP Request

`GET http://localhost/api/v1/account`

### URL Parameter

Parameter | Description
--------- | -----------
no params required...

### Headers

Parameter | Description
--------- | -----------
Authorization | yourauthtoken

<aside class="notice">Replace <code>yourauthtoken</code> with your actual authenication token</aside>



[//]:#(*****************************************************************************)

## Edit Account

```shell
curl --location --request PUT 'http://localhost/api/v1/account' \
--header 'Authorization: yourauthtoken' \
--header 'Content-Type: application/json' \
--header 'Content-Type: text/plain' \
--data-raw '{"account": { "name":"new name" } }'
```

> On Success the command will return:

```json
{
    "id": 3,
    "name": "new name",
    "hostname": "192.168.1.94",
    "interface_scheme": "http://",
    "interface_port": 80,
    "interface_path": "/",
    "active": true,
    "owner_id": null,
    "created_at": "2020-08-04T12:37:58.652Z",
    "updated_at": "2021-02-03T11:24:05.902Z"
}
```

This command will edit the current account, but only certain fields are editable.

### HTTP Request

`PUT http://localhost/api/v1/account`

### Headers

Parameter | Description
--------- | -----------
Authorization | yourauthtoken

<aside class="notice">Replace <code>yourauthtoken</code> with your actual authenication token</aside>

### Editable Fields

Field | Type
----- | ----
name  | string
interface_scheme | string
interface_port | number
interface_path | string


