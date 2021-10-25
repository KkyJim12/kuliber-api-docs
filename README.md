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
* [Forget Password](#forget-password)
* [Create Company](#create-company)
* [Image Upload](#image-upload)
* [Analysis Summary](#analysis-summary)
* [Analysis Detail](#analysis-detail)
* [Sales History](#sales-history)

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

## Forget Password
#### Description: Sending change password method to a specific email.
#### Method:`POST`
``` 
/api/v1/forget-password
```

#### Middleware: 
* None

#### Query:
| Name | Type | Validate |
| --- | --- | --- |
| email | *string* | `required` `email` |

#### Response:
```javascript
{
  "error": 0
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
  "error": 0
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
| image | *file* | `required` `image` `size:2mb`|

#### Response:
```javascript
{
  "error": 0,
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
  "error": 0
}
```

## Analysis Summary
#### Description: Get sales, profit, debtor by period.
#### Method: `GET`
#### Path: 
``` 
/api/v1/analysis-summary
```

#### Middleware: 
* Auth

#### Query:
| Name | Type | Validate |
| --- | --- | --- |
| period | *string* | `none` |

#### Response:
```javascript
{
  "error": 0,
  "result": [
    {
      "sales": 1000000,
      "profit": 240000,
      "debtor": 400000
    }
  ]
}
```

## Analysis Detail
#### Description: Get sales, profit, debtor detail by period.
#### Method: `GET`
#### Path: 
``` 
/api/v1/analysis-detail
```

#### Middleware: 
* Auth

#### Query:
| Name | Type | Validate |
| --- | --- | --- |
| type | *string* | `none` |
| period | *string* | `none` |

#### Response:
```javascript
{
  "error": 0,
  "result": [
    { 
      "type": "sales"
      "period": "week",
      "details": {
        "monday": 10000,
        "tuesday": 20000,
        "wednesday": 30000,
        "thursday": 40000,
        "friday": 50000,
        "saturday": 60000,
        "sunday": 70000
     }
    }
  ]
}
```

## Sales History
#### Description: Get sales history in dashboard page.
#### Method: `GET`
#### Path: 
``` 
/api/v1/sales-history
```

#### Middleware: 
* Auth

#### Query:
| Name | Type | Validate |
| --- | --- | --- |
| amount | *integer* | `none` |

#### Response:
```javascript
{
  "error": 0,
  "result": [
    { 
      "amount": 10,
      "details": [
        {
          "id": "688610c7-44d8-4039-8ca6-241ce08bac60",
          "customer_name": "Piyakarn Nimmakulvirut",
          "price": 25000,
          "date": "2021-06-05T21:46:03+00:00",
          "status": "pending",
        },
        {
          "id": "a8406634-5ed5-4969-bb68-e204543a672f",
          "customer_name": "Vachiraporn Nimmakulvirut",
          "price": 57000,
          "date": "2021-06-05T21:46:03+00:00",
          "status": "complete",
        }
      ]
    }
  ]
}
```
