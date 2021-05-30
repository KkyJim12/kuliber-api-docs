# Kuliber API Specs
Kuliber internal api specs.
# Stacks: 
* `Golang`
* `Postgresql`
* `Google Cloud Platform`
* `Redis`
* `Docker`

# Table of contents
* [Base URL](#base-url)
* [Error Codes](#error-codes)
* [All API Endpoints](#all-api-endpoints)
* [API Specs](#api-specs)

# Base URL
https://api.kuliber.com

# Error Codes

# All API Endpoints
* [Register](#register)

# API Specs

## Register
#### Description: Registering a new user.
#### Method: `POST`
#### Path: 
``` 
/api/v1/users
```

#### Middleware: 
* None

#### Query:
| Name | Type | Validate |
| --- | --- | --- |
| firstname | *string* | `required` `max:255`|
| lastname | *string* | `required` `max:255`|
| email | *string* | `required` `max:255` `email`|
| countryName | *string* | `required` `len:2`|
| countryCode | *string* | `required` `len:3`|
| phone | *string* | `required` `len:10`|
| password | *string* | `required` `min:6` `max:255` |
| confirmPassword | *string* | `required` `same:password`|
| policyAgree | *boolean* | `required` |

#### Response:
```javascript
{
  "error": 0,
  "result": [
    {
      "token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJLdWxpYmVyIiwiaWF0IjoxNjIyMzY4ODA5LCJleHAiOjE2NTM5MDQ4MDksImF1ZCI6Ind3dy5hcGkua3VsaWJlci5jb20iLCJzdWIiOiJrdWxpYmVyIn0.0yaJvgRqtjL5EQjqGCnMO7aqvduJGM4yQHxGQkfKL9U"
    }
  ]
}
```

