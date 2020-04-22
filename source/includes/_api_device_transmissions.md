# Device Transmissions


When gettinga List you can use these filters:

	filter[messageUuid] 
	filter[sort][field] 
	filter[sort][direction] 


[//]:#(*****************************************************************************)

## List

```shell
curl --location --request GET 'http://oop.bluefrontier.local:9009/api/v1/devices/9/transmissions?filter[messageUuid]=9dc5ab1c-8d05-4e5b-8c21-48a7b2f6f241&filter[sort][field]=created_at&filter[sort][direction]=desc' \
--header 'Authorization: yourauthtoken'
```

> On Success the command will return:

```json
```

This command will ...

### HTTP Request

`GET http://oop.bluefrontier.local:9009/api/v1/devices/<id>/transmissions?filter[messageUuid]=<uuid>&filter[sort][field]=created_at&filter[sort][direction]=desc`

### URL Parameter

Parameter | Description
--------- | -----------
id | device id
filter[messageUuid] | unique message id
filter[sort][field] | string field name
filter[sort][direction] | string either 'asc' or 'desc'

### Headers

Parameter | Description
--------- | -----------
Authorization | yourauthtoken

<aside class="notice">Replace <code>yourauthtoken</code> with your actual authenication token</aside>



[//]:#(*****************************************************************************)

## Show

```shell
curl --location --request GET 'http://oop.bluefrontier.local:9009/api/v1/devices/9/transmissions' \
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

This command will ...

### HTTP Request

`GET http://oop.bluefrontier.local:9009/api/v1/devices/<id>/transmissions/<id>`

### Headers

Parameter | Description
--------- | -----------
Authorization | yourauthtoken

<aside class="notice">Replace <code>yourauthtoken</code> with your actual authenication token</aside>
