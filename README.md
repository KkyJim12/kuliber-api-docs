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
* [Login](#login)
* [Create Company](#create-company)

# API Specs

## Register
#### Description: Registering a new user.
#### Method: `POST`
#### Path: 
``` 
/api/v1/register
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
| phone | *string* | `required` `phone`|
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

## Login
#### Description: Logging in to the system.
#### Method: `POST`
#### Path: 
``` 
/api/v1/login
```

#### Middleware: 
* None

#### Query:
| Name | Type | Validate |
| --- | --- | --- |
| email | *string* | `required` `max:255` `email`|
| password | *string* | `required` `min:6` `max:255` |

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

## Create Company
#### Description: Creating company profile after login.
#### Method: `POST`
#### Path: 
``` 
/api/v1/company
```

#### Middleware: 
* Auth

#### Query:
| Name | Type | Validate |
| --- | --- | --- |
| companyName | *string* | `required` `max:255` |
| companyCategory | *string* | `required` |
| phoneNumber | *string* | `required` `phone` |
| address | *string* | `required` `max:255` |
| subDistrict | *string* | `required` `max:255` |
| province | *string* | `required` `max:255` |
| postalCode | *string* | `required` `postalcode` |
| imageID | *uuid* | `required` `max:255` |

#### Response:
```javascript
{
  "error": 0,
}
```

## Image Upload
#### Description: Uploading an image.
#### Method: `POST`
#### Path: 
``` 
/api/v1/image-upload
```

#### Middleware: 
* Auth

#### Query:
| Name | Type | Validate |
| --- | --- | --- |
| image | *file* | `required` `size:2mb`|

#### Response:
```javascript
{
  "error": 0,
}
```

