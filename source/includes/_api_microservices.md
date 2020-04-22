# Microservices

The core token is predefined when the core is setup - see Jacks Documentation (LOL!)

[//]:#(*****************************************************************************)

## List Devices Auth

```shell
curl --location --request GET 'http://oop.bluefrontier.local:9009/services/v1/devices/auth' \
--header 'X-Core-Token: foobar'
```

> On success returns:

```
[
    {
        "id": 8,
        "authentication": {
            "hostname": "oop.bluefrontier.local",
            "headers.x-api-key": "some-api-key"
        },
        "tempr_url": "http://oop.bluefrontier.local:9009/services/v1/devices/8/temprs"
    },
    {
    	...
    }
]
```

### HTTP Request

`GET http://oop.bluefrontier.local:9009/services/v1/devices/auth`

### Headers

Parameter | Description
--------- | -----------
X-Core-Token | yourcoretoken

<aside class="notice">Replace <code>yourcoretoken</code> with your actual provided core token</aside>


[//]:#(*****************************************************************************)

## List Temprs for Device

```shell
curl --location --request GET 'http://oop.bluefrontier.local:9009/services/v1/devices/5/temprs' \
--header 'X-Core-Token: foobar' \
--header 'Content-Type: application/json'
```

> On success returns:

```
{
    "ttl": 300000,
    "data": [
        {
            "id": 1,
            "deviceId": 5,
            "scheduleId": null,
            "name": "ABC XYZ",
            "endpointType": null,
            "queueRequest": false,
            "queueResponse": false,
            "template": {},
            "createdAt": "2019-08-30T08:59:17.321Z",
            "updatedAt": "2019-09-09T12:49:56.297Z",
            "temprs": []
        },
        {...}
    ]
}
```

### HTTP Request

`GET http://oop.bluefrontier.local:9009/services/v1/devices/<id>/temprs`

### Headers

Parameter | Description
--------- | -----------
X-Core-Token | yourcoretoken

### URL Parameter

Parameter | Description
--------- | -----------
id | device ID


<aside class="notice">Replace <code>yourcoretoken</code> with your actual provided core token</aside>


[//]:#(*****************************************************************************)

## List Temprs for Schedule

```shell
curl --location --request GET 'http://oop.bluefrontier.local:9009/services/v1/schedules/1/temprs' \
--header 'X-Core-Token: foobar'
```

> On success returns:

```
```

### HTTP Request

`GET http://oop.bluefrontier.local:9009/services/v1/schedules/<id>/temprs`

### Headers

Parameter | Description
--------- | -----------
X-Core-Token | yourcoretoken

### URL Parameter

Parameter | Description
--------- | -----------
id | schedule ID


<aside class="notice">Replace <code>yourcoretoken</code> with your actual provided core token</aside>


[//]:#(*****************************************************************************)

## List Schedules

```shell
curl --location --request GET 'http://oop.bluefrontier.local:9009/services/v1/schedules' \
--header 'X-Core-Token: foobar'
```

> On success returns:

```
```

### HTTP Request

`GET http://oop.bluefrontier.local:9009/services/v1/schedules`

### Headers

Parameter | Description
--------- | -----------
X-Core-Token | yourcoretoken

<aside class="notice">Replace <code>yourcoretoken</code> with your actual provided core token</aside>

