# Authentication

Before being able to use the system you will need to login with the username and password given to you (either by your manager or through signing up).

Use the authentication token retrieved with the Login call below.

[//]:#(*****************************************************************************)

## Login
```shell
curl --location --request POST 'http://oop.bluefrontier.local:9009/api/v1/auth/login' \
--header 'Content-Type: application/json' \
--header 'Content-Type: text/plain' \
--data-raw '{
    "email": "your_email_address",
    "password": "your_password"
}'
```

> On Success it will return:

```json
{
    "token": "eyJhbGciOiJIUzI1NiJ9.byJ1c2VyX2lkIjozMywiZXhwIsoxNTg3NTz1MDc3fQ.z44g3zSXGZkZDwa1iW4NgC7Bd_GSxiz3qCpNu5jYDiQ",
    "exp": "04-20-2020 09:44",
    "email": "bob.testing@testing.co.uk"
}
```

### HTTP Request

`POST http://oop.bluefrontier.local:9009/api/v1/auth/login`

### Content Body

Json string containing:
`
	{
		"email":"your_email_address",
		"password":"your_password"
	}
`
