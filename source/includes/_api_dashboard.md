# Dashboard

The Dashboard is where summary information would be gathered from


[//]:#(*****************************************************************************)

## Transmissions Status

### HTTP Request

`GET http://localhost/api/v1/dashboards/transmissions?group=status`


### URL Parameters

Parameter | Description
--------- | -----------
group | status, state or success


### Headers

Parameter | Description
--------- | -----------
Authorization | yourauthtoken

<aside class="notice">Replace <code>yourauthtoken</code> with your actual authenication token</aside>

```shell
curl "http://localhost/api/v1/dashboards/transmissions?group=status"
  -H "Authorization: yourauthtoken"
```

## Messages By Date

### HTTP Request

`GET http://localhost/api/v1/dashboards/messages?group=created_at`


### URL Parameters

Parameter | Description
--------- | -----------
group | created_at

### Headers

Parameter | Description
--------- | -----------
Authorization | yourauthtoken

<aside class="notice">Replace <code>yourauthtoken</code> with your actual authenication token</aside>

```shell
curl "http://localhost/api/v1/dashboards/messages?group=created_at"
  -H "Authorization: yourauthtoken"
```