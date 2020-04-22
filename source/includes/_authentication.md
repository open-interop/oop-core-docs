# Authentication

Before being able to use the system you will need to login with the username and password given to you (either by your manager or through signing up).

Use the authentication token retrieved with the Login call below.

## Login
```shell
curl --location --request POST 'http://localhost/api/v1/auth/login' \
--header 'Content-Type: application/json' \
--header 'Content-Type: text/plain' \
--data-raw '{
    "email": "your_email_address",
    "password": "your_password"
}'
```

### HTTP Request

`POST http://localhost/api/v1/auth/login`

### Content Body

Json string containing:
`
	{
		"email":"your_email_address",
		"password":"your_password"
	}
`
