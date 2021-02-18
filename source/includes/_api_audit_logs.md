# Audit Logs


Audit Logs have these fields:

Field | Type
----- | ----
id | number
archived | boolean
auditable_id | number
auditable_type | string
user_id | number
user_type | string
action | string
audited_changes | number
version | number
remote_address | string
request_uuid | string
created_at | date time


Filters available:

Filter | Type
------ | ----
id | number
archived | boolean
auditable_id | number
auditable_type | string
user_id | number
user_type | string
action | string
audited_changes | json
version | number
remote_address | string
request_uuid | string
created_at | date time
sort[field] | string as above
sort[direction] | string

[//]:#(*****************************************************************************)

## List Global Audit Logs

```shell
curl --location --request GET 'http://localhost/api/v1/audit_logs?filter[auditable_type]=device&filter[sort][field]=version&filter[sort][direction]=asc' \
--header 'Authorization: yourauthtoken'
```

> On Success the command will return:

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
            "id": 38,
            "auditable_id": 42,
            "auditable_type": "Device",
            "associated_id": null,
            "associated_type": null,
            "user_id": 23,
            "user_type": "User",
            "username": null,
            "action": "create",
            "audited_changes": {
                "name": "XyzAbc",
                "active": false,
                "site_id": 21,
                "latitude": null,
                "longitude": null,
                "time_zone": "",
                "account_id": 1,
                "device_group_id": 1,
                "authentication_path": "/gateway/xyzabc",
                "authentication_query": [],
                "authentication_headers": []
            },
            "version": 1,
            "comment": null,
            "remote_address": "127.0.0.1",
            "request_uuid": "005da287-ef80-62c0-9ac2-e7066c7b2250",
            "created_at": "2019-12-13T16:32:11.049Z"
        },
        {
            ...
        }
    ],
    "core_version": "1.1.4"
}
```


This command will retrieve a list of audit logs, based on the filters supplied, or all of them if no filters given.
In the example above, this will return all audit logs where the type is device, sorted (in ascending order) by the version.

### HTTP Request

`GET http://localhost/api/v1/audit_logs`

### URL Parameter

Parameter | Description
--------- | -----------
filter[auditable_type] | component type (device, tempr, schedule, etc...)
filter[..] | see table above for options
filter[sort][field] | string field name as above
filter[sort][direction] | string either 'asc' or 'desc'

### Headers

Parameter | Description
--------- | -----------
Authorization | yourauthtoken

<aside class="notice">Replace <code>yourauthtoken</code> with your actual authenication token</aside>



[//]:#(*****************************************************************************)

## Show Individual Audit Log

```shell
curl --location --request GET 'http://localhost/api/v1/audit_logs/501' \
--header 'Authorization: yourauthtoken'
```

> On Success the command will return:

```json
{
    "id": 501,
    "auditable_id": 42,
    "auditable_type": "Schedule",
    "associated_id": null,
    "associated_type": null,
    "user_id": 23,
    "user_type": "User",
    "username": null,
    "action": "create",
    "audited_changes": {
        "name": "XyzAbc",
        "active": false,
    },
    "version": 1,
    "comment": null,
    "remote_address": "127.0.0.1",
    "request_uuid": "005da287-ef80-62c0-9ac2-e7066c7b2250",
    "created_at": "2019-12-13T16:32:11.049Z"
},
```

This command will return a specific audit log with the id provided.

### HTTP Request

`GET http://localhost/api/v1/audit_logs/<id>`

### Headers

Parameter | Description
--------- | -----------
Authorization | yourauthtoken

<aside class="notice">Replace <code>yourauthtoken</code> with your actual authenication token</aside>