# Transmissions


Transmissions have these fields:

Field | Type
----- | ----
id | number
device_id  | number
tempr_id  | number
schedule_id  | number
status | string
state | string
message_uuid | string
transmission_uuid | string
success | bool
transmitted_at | date time
created_at | date time
updated_at | date time


Filters available:

Filter | Type
------ | ----
id | number
status | number
tempr_id | number
schedule_id | number
message_uuid | string 
transmission_uuid | string 
success | boolean
state | string
transmitted_at | date time
created_at | date time
updated_at | date time
sort[field] | string as above
sort[direction] | string

[//]:#(*****************************************************************************)

## List Transmissions

```shell
curl --location --request GET 'http://localhost/api/v1/transmissions?filter[messageUuid]=9dc5ab1c-8d05-4e5b-8c21-48a7b2f6f241&filter[sort][field]=created_at&filter[sort][direction]=state' \
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
            "id": 25,
            "device_id": 9,
            "tempr_id": null,
            "schedule_id": null,
            "message_uuid": "35f1e645-be21-4eba-af61-cbbb0f9647f8",
            "transmission_uuid": null,
            "success": true,
            "status": 200,
            "transmitted_at": "2019-09-09T13:35:09.693Z",
            "response_body": "{\"messages\":[{\"test\":{\"core\":{},\"pii\":{\"custom\":{}},\"custom\":{\"raw\":{\"name\":\"patient1\",\"result\":\"negative\"}}},\"sample\":{\"core\":{},\"pii\":{\"custom\":{}},\"custom\":{}},\"patient\":{\"core\":{},\"pii\":{\"custom\":{}},\"custom\":{}},\"encounter\":{\"core\":{},\"pii\":{\"custom\":{}},\"custom\":{}}}]}",
            "request_body": null,
            "created_at": "2019-09-09T13:35:10.711Z",
            "updated_at": "2019-09-09T13:35:10.711Z"
        }
    ],
    "core_version": "1.1.4"
}
```

This command will retrieve a list of transmissions, based on the filters supplied, or all of them if no filters given.

### HTTP Request

`GET http://localhost/api/v1/transmissions?filter[messageUuid]=<uuid>&filter[sort][field]=created_at&filter[sort][direction]=state`

### URL Parameter

Parameter | Description
--------- | -----------
filter[messageUuid] | unique message id
filter[..] | see table above for options
filter[sort][field] | string field name as above
filter[sort][direction] | string either 'asc' or 'desc'

### Headers

Parameter | Description
--------- | -----------
Authorization | yourauthtoken

<aside class="notice">Replace <code>yourauthtoken</code> with your actual authenication token</aside>



[//]:#(*****************************************************************************)

## Show Transmission

```shell
curl --location --request GET 'http://localhost/api/v1/transmissions/42' \
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
            "id": 42,
            "device_id": 9,
            "tempr_id": null,
            "schedule_id": null,
            "message_uuid": "35f1e645-be21-4eba-af61-cbbb0f9647f8",
            "transmission_uuid": null,
            "success": true,
            "status": 200,
            "transmitted_at": "2019-09-09T13:35:09.693Z",
            "response_body": "{\"messages\":[{\"test\":{\"core\":{},\"pii\":{\"custom\":{}},\"custom\":{\"raw\":{\"name\":\"patient1\",\"result\":\"negative\"}}},\"sample\":{\"core\":{},\"pii\":{\"custom\":{}},\"custom\":{}},\"patient\":{\"core\":{},\"pii\":{\"custom\":{}},\"custom\":{}},\"encounter\":{\"core\":{},\"pii\":{\"custom\":{}},\"custom\":{}}}]}",
            "request_body": null,
            "created_at": "2019-09-09T13:35:10.711Z",
            "updated_at": "2019-09-09T13:35:10.711Z"
        }
    ],
    "core_version": "1.1.4"
}
```

This command will return a specific transmission with the id provided.

### HTTP Request

`GET http://localhost/api/v1/transmissions/<id>`

### Headers

Parameter | Description
--------- | -----------
Authorization | yourauthtoken

<aside class="notice">Replace <code>yourauthtoken</code> with your actual authenication token</aside>
