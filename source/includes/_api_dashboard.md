# Dashboard

The Dashboard is where summary information would be gathered from


[//]:#(*****************************************************************************)

## Transmissions Status

### HTTP Request

`GET http://oop.bluefrontier.local/api/v1/dashboards/transmissions?group=status`


### URL Parameters

Parameter | Description
--------- | -----------
group | status


### Headers

Parameter | Description
--------- | -----------
Authorization | yourauthtoken

<aside class="notice">Replace <code>yourauthtoken</code> with your actual authenication token</aside>

```shell
curl "http://oop.bluefrontier.local/api/v1/dashboards/transmissions?group=status"
  -H "Authorization: yourauthtoken"
```
