# Messages


Messages have these fields:

Field | Type
----- | ----
id | number
device_id  | number
schedule_id  | number
origin_id | number
origin_type | string
ip_address | string
uuid | string
body | text
transmission_count | number
created_at | date time
updated_at | date time


Filters available:

Filter | Type
------ | ----
id | number
device_id  | number
schedule_id  | number
origin_id | number
origin_type | string
ip_address | string
uuid | string
body | text
transmission_count | number
created_at | date time
updated_at | date time
sort[field] | string as above
sort[direction] | string

[//]:#(*****************************************************************************)

## List Messages

```shell
curl --location --request GET 'http://localhost/api/v1/messages?filter[device_id]=22&filter[sort][field]=created_at&filter[sort][direction]=desc' \
--header 'Authorization: yourauthtoken'
```

> On Success the command will return:

```json
{
    "total_records": 14,
    "number_of_pages": 1,
    "page": {
        "number": 1,
        "size": 20
    },
    "data": [
        {
            "id": 501,
            "device_id": 22,
            "schedule_id": null,
            "origin_id": 22,
            "origin_type": "Device",
            "ip_address": "::ffff:172.19.0.1",
            "uuid": "8951a701-9330-4a64-8f1a-c934422fa753",
            "body": {
                "path": "/devices",
                "query": {},
                "method": "POST",
                "ip": "::ffff:172.19.0.1",
                "body": {},
                "headers": {
                    "x-core-token": "foobar",
                    "authorization": "Basic dGVzdEBleGFtcGxlLmNvbTp0ZXN0dGVzdA==",
                    "user-agent": "PostmanRuntime/7.26.5",
                    "accept": "*/*",
                    "postman-token": "043a7a01-faa9-40b1-84f5-35d38c5b889c",
                    "host": "192.168.1.201:3000",
                    "accept-encoding": "gzip, deflate, br",
                    "connection": "keep-alive",
                    "content-length": "0"
                },
                "hostname": "192.168.1.201",
                "protocol": "http"
            },
            "transmission_count": 1,
            "created_at": "2020-10-28T16:48:17.159Z",
            "updated_at": "2020-10-28T16:48:17.159Z"
        },
        {
            "id": 500,
            "device_id": 22,
            "schedule_id": null,
            "origin_id": 22,
            "origin_type": "Device",
            "ip_address": "test",
            "uuid": "edad31d5-0044-4b4b-9396-8de274c5029c",
            "body": {
                "path": "/devices",
                "query": {},
                "method": "POST",
                "ip": "::ffff:172.19.0.1",
                "body": {},
                "headers": {
                    "x-core-token": "foobar",
                    "authorization": "Basic dGVzdEBleGFtcGxlLmNvbTp0ZXN0dGVzdA==",
                    "user-agent": "PostmanRuntime/7.26.5",
                    "accept": "*/*",
                    "postman-token": "c069ab23-1b0d-4fb6-865c-c69d77a5c6cd",
                    "host": "192.168.1.201:3000",
                    "accept-encoding": "gzip, deflate, br",
                    "connection": "keep-alive",
                    "content-length": "0"
                },
                "hostname": "192.168.1.201",
                "protocol": "http"
            },
            "transmission_count": 1,
            "created_at": "2020-10-28T16:47:44.525Z",
            "updated_at": "2020-10-28T16:47:44.525Z"
        },
        ...
    ],
    "core_version": "1.1.7"
}
```

This command will retrieve a list of transmissions, based on the filters supplied, or all of them if no filters given.

### HTTP Request

`GET http://localhost/api/v1/messages?filter[device_id]=22&filter[sort][field]=created_at&filter[sort][direction]=desc`

### URL Parameter

Parameter | Description
--------- | -----------
filter[device_id] | unique device id
filter[..] | see table above for options
filter[sort][field] | string field name as above
filter[sort][direction] | string either 'asc' or 'desc'

### Headers

Parameter | Description
--------- | -----------
Authorization | yourauthtoken

<aside class="notice">Replace <code>yourauthtoken</code> with your actual authenication token</aside>



[//]:#(*****************************************************************************)

## Show Message

```shell
curl --location --request GET 'http://localhost/api/v1/messages/501' \
--header 'Authorization: yourauthtoken'
```

> On Success the command will return:

```json
{
    "id": 501,
    "account_id": 3,
    "device_id": 22,
    "schedule_id": null,
    "uuid": "8951a701-9330-4a64-8f1a-c934422fa753",
    "body": {
        "path": "/devices",
        "query": {},
        "method": "POST",
        "ip": "::ffff:172.19.0.1",
        "body": {},
        "headers": {
            "x-core-token": "foobar",
            "authorization": "Basic dGVzdEBleGFtcGxlLmNvbTp0ZXN0dGVzdA==",
            "user-agent": "PostmanRuntime/7.26.5",
            "accept": "*/*",
            "postman-token": "043a7a01-faa9-40b1-84f5-35d38c5b889c",
            "host": "192.168.1.201:3000",
            "accept-encoding": "gzip, deflate, br",
            "connection": "keep-alive",
            "content-length": "0"
        },
        "hostname": "192.168.1.201",
        "protocol": "http"
    },
    "created_at": "2020-10-28T16:48:17.159Z",
    "updated_at": "2020-10-28T16:48:17.159Z",
    "origin_id": 22,
    "origin_type": "Device",
    "transmission_count": 1,
    "ip_address": "::ffff:172.19.0.1"
}
```

This command will return a specific transmission with the id provided.

### HTTP Request

`GET http://localhost/api/v1/messages/<id>`

### Headers

Parameter | Description
--------- | -----------
Authorization | yourauthtoken

<aside class="notice">Replace <code>yourauthtoken</code> with your actual authenication token</aside>
