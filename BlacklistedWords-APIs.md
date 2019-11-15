This section details about the service APIs for the BlacklistedWords 


* [BlacklistedWords Master API](#BlacklistedWords-master-api)


# BlacklistedWords Master API

* [POST /blacklistedwords](#post-blacklistedwords)
* [PUT /blacklistedwords](#put-blacklistedwords)
* [GET /blacklistedwords/{langcode}](#get-blacklistedwordslangcode)
* [DELETE /blacklistedwords/{word}](#delete-blacklistedwordsword)
* [GET /blacklistedwords/all](#get-blacklistedwordsall)
* [PUT /blacklistedwords/details](#put-blacklistedwordsdetails)
* [POST /blacklistedwords/words](#post-blacklistedwordswords)
* [POST /blacklistedwords/filtervalues](#post-blacklistedwordsfiltervalues)
* [POST /blacklistedwords/search](#post-blacklistedwordssearch)


# POST /blacklistedwords

This service will create a blacklistedword which will be used in the MOSIP platform. 

### Resource URL
### `POST /blacklistedwords`

### Resource details

Resource Details | Description
------------ | -------------
Response format | JSON
Requires Authentication | Yes

### Parameters
Name | Required | Description | Default Value | Example
-----|----------|-------------|---------------|--------
description | optional | blacklisted word description ||
isActive | Yes | is active or not ||
langCode | Yes | language code ||
word | Yes | blacklisted word name || 

### Example Request
```JSON
{
  "id": "string",
  "metadata": {},
  "request": {
    "description": "string",
    "isActive": true,
    "langCode": "string",
    "word": "string"
  },
  "requesttime": "2018-12-10T06:12:52.994Z",
  "version": "string"
}
```
### Example Response
```JSON
{
  "errors": [
    {
      "errorCode": "string",
      "message": "string"
    }
  ],
  "id": "string",
  "metadata": {},
  "response": {
    "langCode": "string",
    "word": "string"
  },
  "responsetime": "yyyy-MM-dd'T'HH:mm:ss.SSS'Z'",
  "version": "string"
}
```
### Response codes

201

Description: Created

404

Description: Not Found

401

Description: Unauthorized

403

Description: Forbidden

-----

# PUT /blacklistedwords
This service will update the blacklisted word which is used in the MOSIP platform. 

### Resource URL
### `PUT /blacklistedwords`

### Resource details

Resource Details | Description
------------ | -------------
Response format | JSON
Requires Authentication | Yes

### Parameters
Name | Required | Description | Default Value | Example
-----|----------|-------------|---------------|--------
description | optional | blacklisted word description ||
isActive | Yes| is active or not ||
langCode | Yes | language code ||
oldWord | Yes | old blacklisted word || 
word |Yes |blacklisted word ||

### Example Request
```JSON
{
  "id": "string",
  "metadata": {},
  "request": {
    "description": "string",
    "isActive": true,
    "langCode": "string",
    "oldWord": "string",
    "word": "string"
  },
  "requesttime": "2018-12-10T06:12:52.994Z",
  "version": "string"
}
```
### Example Response
```JSON
{
  "errors": [
    {
      "errorCode": "string",
      "message": "string"
    }
  ],
  "id": "string",
  "metadata": {},
  "response": {
    "langCode": "string",
    "word": "string"
  },
  "responsetime": "yyyy-MM-dd'T'HH:mm:ss.SSS'Z'",
  "version": "string"
}
```
### Response codes

201

Description: Created

401

Description: Unauthorized

403

Description: Forbidden

404 

Description: Not Found


-----
# GET /blacklistedwords/{langcode}

This service will provides the service for the List of blacklisted words based on the passed language code. 

### Resource URL
### `GET /blacklistedwords/{langcode}`

### Resource details

Resource Details | Description
------------ | -------------
Response format | JSON
Requires Authentication | Yes

### Parameters
Name | Required | Description | Default Value | Example
-----|----------|-------------|---------------|--------
langcode|Yes| language code ||

### Example Response
```JSON
{
  "errors": [
    {
      "errorCode": "string",
      "message": "string"
    }
  ],
  "id": "string",
  "metadata": {},
  "response": {
    "blacklistedwords": [
      {
        "description": "string",
        "isActive": true,
        "langCode": "string",
        "word": "string"
      }
    ]
  },
  "responsetime": "yyyy-MM-dd'T'HH:mm:ss.SSS'Z'",
  "version": "string"
}
```
### Response codes

200

Description: Success

401

Description: Unauthorized

403

Description: Forbidden

404

Description: Not Found

-----
# DELETE /blacklistedwords/{word}

This service will provides the service to delete the blacklisted word. 


### Resource URL
### `DELETE /blacklistedwords/{word}`

### Resource details

Resource Details | Description
------------ | -------------
Response format | JSON
Requires Authentication | Yes

### Parameters
Name | Required | Description | Default Value | Example
-----|----------|-------------|---------------|--------
word | Yes | blacklisted word to be deleted ||

### Example Response
```JSON
{
  "errors": [
    {
      "errorCode": "string",
      "message": "string"
    }
  ],
  "id": "string",
  "metadata": {},
  "response": {
    "code": "string"
  },
  "responsetime": "yyyy-MM-dd'T'HH:mm:ss.SSS'Z'",
  "version": "string"
}
```
### Response codes

200

Description: Success

204

Description: No Content

401

Description: Unauthorized

403

Description: Forbidden

----
# GET /blacklistedwords/all 

This service will provides the service for the List of blacklistedwords. 


### Resource URL
### `GET /blacklistedwords/all`

### Resource details

Resource Details | Description
------------ | -------------
Response format | JSON
Requires Authentication | Yes

### Parameters
Name | Required | Description | Default Value | Example
-----|----------|-------------|---------------|--------
orderBy | optional | response order | desc ||
pageNumber | optional | page no for the requested data | 0 ||
pageSize | optional | page size for the requested data | 10 ||
sortBy | optional | sort the requested data based on param value | createdDateTime || 

### Example Response
```JSON
{
  "errors": [
    {
      "errorCode": "string",
      "message": "string"
    }
  ],
  "id": "string",
  "metadata": {},
  "response": {
    "data": [
      {
        "createdBy": "string",
        "description": "string",
        "isActive": true,
        "isDeleted": true,
        "langCode": "string",
        "updatedBy": "string",
        "word": "string"
      }
    ],
    "pageNo": 0,
    "totalItems": 0,
    "totalPages": 0
  },
  "responsetime": "yyyy-MM-dd'T'HH:mm:ss.SSS'Z'",
  "version": "string"
}
```
### Response codes

200

Description: Success

401

Description: Unauthorized

403

Description: Forbidden

404

Description: Not found

500

Description: Error occured while retrieving blacklisted words
------
#PUT /blacklistedwords/details

This service will update the blacklisted word details except the word itself. 


### Resource URL
### `PUT /blacklistedwords/details`

### Resource details

Resource Details | Description
------------ | -------------
Response format | JSON
Requires Authentication | Yes

### Parameters
Name | Required | Description | Default Value | Example
-----|----------|-------------|---------------|--------
description | optional | blacklisted word description ||
isActive | Yes | is active or not ||
langCode | Yes | language code ||
word | Yes | blacklisted word name || 

### Example Request
```JSON
{
  "id": "string",
  "metadata": {},
  "request": {
    "description": "string",
    "isActive": true,
    "langCode": "string",
    "word": "string"
  },
  "requesttime": "2018-12-10T06:12:52.994Z",
  "version": "string"
}
```
### Example Response
```JSON
{
  "errors": [
    {
      "errorCode": "string",
      "message": "string"
    }
  ],
  "id": "string",
  "metadata": {},
  "response": {
    "langCode": "string",
    "word": "string"
  },
  "responsetime": "yyyy-MM-dd'T'HH:mm:ss.SSS'Z'",
  "version": "string"
}
```
### Response codes

200

Description: Success

201

Description: Created

401

Description: Unauthorized

403

Description: Forbidden

404 

Description: Not Found

----

# POST /blacklistedwords/words

This service will validate list of words if they are blacklisted or not. 

### Resource URL
### `POST /blacklistedwords/words`

### Resource details

Resource Details | Description
------------ | -------------
Response format | JSON
Requires Authentication | Yes

### Parameters
Name | Required | Description | Default Value | Example
-----|----------|-------------|---------------|--------
blacklisted words | Yes | blacklisted words to be validated  ||

### Example Request
```JSON
{
  "id": "string",
  "metadata": {},
  "request": {
    "blacklistedwords": [
      "string"
    ]
  },
  "requesttime": "2018-12-10T06:12:52.994Z",
  "version": "string"
}
```

### Example Response
```JSON
{
  "id": "string",
  "version": "string",
  "responsetime": "2019-11-15T08:04:42.310Z",
  "metadata": null,
  "response": {
    "code": "Valid"
  },
  "errors": null
}
```
### Response Codes

200

Description: Success

201

Description: Created

401

Description: Unauthorized

403

Description: Forbidden

404

Description: Not found
----
#### Failure details
Error Code | Error Message | Error Description
------------|------------------------------|-------------
KER-MSD-007 | Error occurred while fetching Blacklisted words | Fetch Issue
KER-MSD-008 | Blacklisted word not found | Data Not Found
KER-MSD-070 | Error occurred while inserting Blacklisted words | Insertion Issue
KER-MSD-105 | Error occurred while updating Blacklisted Word | Update Issue
KER-MSD-106 | Error occurred while deleting Blacklisted Word | Deletion Issue


