# Password

[//]:#(*****************************************************************************)

## Request Password Reset

```shell
curl --location --request POST 'http://oop.bluefrontier.local:9009/api/v1/passwords' \
--header 'Content-Type: application/json' \
--header 'Content-Type: text/plain' \
--data-raw '{
  "email": "your_email_address"
}'
```

If you have forgotten your password then you can request a token to allow it to be reset.

### HTTP Request

`POST http://oop.bluefrontier.local:9009/api/v1/passwords`

### Content Body

Json string containing:
`
	{
		"email":"your_email_address"
	}
`


[//]:#(*****************************************************************************)

## Reset password

```shell
curl --location --request POST 'http://oop.bluefrontier.local:9009/api/v1/passwords/reset' \
--header 'Content-Type: application/json' \
--header 'Content-Type: text/plain' \
--data-raw '{
  "token": "your_password_reset_token",
  "password" : "newpassword",
  "password_confirmation" : "newpassword"
}'
```

Once you have the reset password token (from above), then you can send though an updated password along with a confirmation copy of it.

### HTTP Request

`POST http://oop.bluefrontier.local:9009/api/v1/passwords/reset`

### Headers

Parameter | Description
--------- | -----------
token | your_password_reset_token
password | your_new_password_string
password_confirmation | your_new_password_string

<aside class="notice">Replace <code>your_password_reset_token</code> with the actual password reset token you will have received from the password reset request above!</aside>
