This section details about the service APIs in the Master data modules

* [Holiday Master API](#holiday-master-api) 

* [Blacklisted words Master API](#blacklisted-words-master-api)

* [Documents Category Master API](#documents-category-master-api)

* [Document formats Master API](#document-formats-master-api)

* [Machines Master API](#machines-master-api)

* [Devices Master API](#devices-master-api)

* [Languages Master API](#languages-master-api)

* [Gender Master API](#gender-master-api)

* [Titles Master API](#titles-master-api)

* [Biometric Types Master API](#biometric-types-master-api)

* [ID Types Master API](#id-types-master-api)

* [Application Types Master API](#application-types-master-api)

* [Registration Centers Master API](#registration-centers-master-api)

* [Biometrics Attributes Master API](#biometric-attributes-master-api)

* [Locations Master API](#locations-master-api)

* [Packet rejection reasons Master API](#packet-rejection-reasons-master-api)

* [Packet on hold reasons Master API](#packet-on-hold-reasons-master-api)

* [Documents Types Master API](#documents-types-api)

* [Machine Types Master API](#machine-types-master-api)

* [Machine Specifications Master API](#machine-specifications)

* [Registration Center User Machine Mapping API](#registration-center-user-machine-mapping-api)

* [Registration Center Machine API](#registration-center-machine-api)

* [Registration Center Device API](#registration-center-device-api)

* [Registration Center Machine Device API](#registration-center-machine-device-api)

* [Devices Master Type API](#device-types-master-api)

* [Device Specifications Master API](#device-specifications)

* [TemplateFileFormat Master API](#templateFileFormat-api)

* [Individual Types API](#individual-types-api)

* [Age group Types API](#age-group-types-api)

* [Template Types Master API](#template-types-api)

* [Applicant Valid documents API](#Applicant-valid-documents-api)

# Holiday Master API

* [GET /holidays](#get-holidays)
* [POST /holidays](#post-holidays)
* [PUT /holidays](#put-holidays)
* [DELETE /holidays](#delete-holidays)
* [GET /holidays/{holidayid}](#get-holidaysholidayid)
* [GET /holidays/{holidayid}/{langcode}](#get-holidaysholidayidlangcode)
* [GET /holidays/all](#get-holidaysall)


## GET /holidays

This service will get all the holidays. 

### Resource URL
### `GET /holidays`

### Resource details

Resource Details | Description
------------ | -------------
Response format | JSON
Requires Authentication | Yes

### Parameters
Name | Required | Description | Default Value | Example
-----|----------|-------------|---------------|--------
--NA-- 


### Example Response
```JSON
{
  "id": null,
  "version": null,
  "responsetime": "2019-11-15T09:41:14.274Z",
  "metadata": null,
  "response": {
    "holidays": [
      {
        "id": 2000001,
        "locationCode": "KTA",
        "holidayDate": "2019-01-01",
        "holidayDay": "2",
        "holidayMonth": "1",
        "holidayYear": "2019",
        "holidayName": "New Year's Day",
        "holidayDesc": "National Holiday",
        "langCode": "eng",
        "isActive": true
      }
	]
  },
  "errors": null
}
```
### Response codes

200

Description: Success

404

Description: Not Found

401

Description: Unauthorized

403

Description: Forbidden

-----

## POST /holidays
This service will create a new holiday. 

### Resource URL
### `POST /holidays`

### Resource details

Resource Details | Description
------------ | -------------
Response format | JSON
Requires Authentication | Yes

### Parameters
Name | Required | Description | Default Value | Example
-----|----------|-------------|---------------|--------
locationCode | Yes | location code ||
holidayDate | Yes| date ||
holidayMonth | Yes | month || 
holidayYear |Yes | year ||
holidayName |Yes | name ||
holidayDesc |Yes | description ||
langCode |Yes | language code ||
isActive |Yes | is active? ||

### Example Request
```JSON
{
  "id": "string",
  "metadata": {},
  "request": {
    "holidayDate": "string",
    "holidayDay": "string",
    "holidayDesc": "string",
    "holidayMonth": "string",
    "holidayName": "string",
    "holidayYear": "string",
    "id": 0,
    "isActive": true,
    "langCode": "string",
    "locationCode": "string"
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
    "holidayDate": "string",
    "holidayName": "string",
    "langCode": "string",
    "locationCode": "string"
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

204 

Description: Not Found


-----
## PUT /holidays

This service will update a holiday. 

### Resource URL
### `PUT /holidays`

### Resource details

Resource Details | Description
------------ | -------------
Response format | JSON
Requires Authentication | Yes

### Parameters
Name | Required | Description | Default Value | Example
-----|----------|-------------|---------------|--------
locationCode | Yes | location code ||
holidayDate | Yes| date ||
newHolidayDate | Yes | new date || 
newHolidayName | Yes | new name ||
holidayName | Yes | name ||
holidayDesc | Yes | description ||
langCode | Yes | language code ||
isActive | Yes | is active? ||
newHolidayDesc | Yes | new description ||

### Example Request
```JSON
{
  "id": "string",
  "metadata": {},
  "request": {
    "id": 0,
    "locationCode": "string",
    "holidayDate": "string",
    "holidayName": "string",
    "holidayDesc": "string",
    "langCode": "string",
    "isActive": true,
    "newHolidayName": "string",
    "newHolidayDate": "string",
    "newHolidayDesc": "string"
  },
  "requesttime": "2018-12-10T06:12:52.994Z",
  "version": "string"
}
```
### Example Response
```JSON
{
  "holidayDate": "string",
  "holidayName": "string",
  "langCode": "string",
  "locationCode": "string"
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

-----

## DELETE /holidays

This service will provides the service to delete a holiday. 


### Resource URL
### `DELETE /holidays`

### Resource details

Resource Details | Description
------------ | -------------
Response format | JSON
Requires Authentication | Yes

### Parameters
Name | Required | Description | Default Value | Example
-----|----------|-------------|---------------|--------
holidayDate | Yes | date to be deleted ||
holidayName | Yes | name of the holiday to be deleted ||
locationCode | Yes | location code ||

### Example Request
```JSON
{
  "id": "string",
  "metadata": {},
  "request": {
    "holidayDate": "string",
    "holidayName": "string",
    "locationCode": "string"
  },
  "requesttime": "2018-12-10T06:12:52.994Z",
  "version": "string"
}
```

### Example Response
```JSON
{
  "holidayDate": "string",
  "holidayName": "string",
  "locationCode": "string"
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

## GET /holidays/{holidayid}

This service will provides the service to get all holidays by Id. 


### Resource URL
### `GET /holidays/{holidayid}`

### Resource details

Resource Details | Description
------------ | -------------
Response format | JSON
Requires Authentication | Yes

### Parameters
Name | Required | Description | Default Value | Example
-----|----------|-------------|---------------|--------
holidayid | yes | holiday Id ||

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
    "holidays": [
      {
        "holidayDate": "string",
        "holidayDay": "string",
        "holidayDesc": "string",
        "holidayMonth": "string",
        "holidayName": "string",
        "holidayYear": "string",
        "id": 0,
        "isActive": true,
        "langCode": "string",
        "locationCode": "string"
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

Description: Not found

------

## GET /holidays/{holidayid}/{langcode}

This service will get all the holidays by holidayid and language code. 


### Resource URL
### `GET /holidays/{holidayid}/{langcode}`

### Resource details

Resource Details | Description
------------ | -------------
Response format | JSON
Requires Authentication | Yes

### Parameters
Name | Required | Description | Default Value | Example
-----|----------|-------------|---------------|--------
holidayid | yes | holiday Id ||||
langCode | Yes | language code ||


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
    "holidays": [
      {
        "holidayDate": "string",
        "holidayDay": "string",
        "holidayDesc": "string",
        "holidayMonth": "string",
        "holidayName": "string",
        "holidayYear": "string",
        "id": 0,
        "isActive": true,
        "langCode": "string",
        "locationCode": "string"
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

----

## GET /holidays/all

This service will retrieve all the holidays with additional metadata. 

### Resource URL
### `GET /holidays/all`

### Resource details

Resource Details | Description
------------ | -------------
Response format | JSON
Requires Authentication | Yes

### Parameters
Name | Required | Description | Default Value | Example
-----|----------|-------------|---------------|--------
orderBy | optional | response order	| desc	||
pageNumber |optional | page no for the requested data | 0 ||	
pageSize | optional	| page size for the requested data	| 10 ||
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
        "holidayDate": 0,
        "holidayDay": "string",
        "holidayDesc": "string",
        "holidayId": 0,
        "holidayMonth": "string",
        "holidayName": "string",
        "holidayYear": "string",
        "isActive": true,
        "isDeleted": true,
        "langCode": "string",
        "locationCode": "string",
        "name": "string",
        "updatedBy": "string"
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
### Response Codes

200

Description: Success

500

Description: Error occured while retrieving holidays

401

Description: Unauthorized

403

Description: Forbidden

404

Description: Not found

----

## Failure details
Error Code | Error Message | Error Description
------------|------------------------------|-------------
KER-MSD-019 | Error occured while fetching Holidays | Fetch Issue
KER-MSD-020 | Holiday not found | Data Not Found
KER-MSD-065 | Error occurred while inserting holiday | Insertion Issue
KER-MSD-099 | Error occurred while updating holiday | Update Issue
KER-MSD-100 | Error occurred while deleting holiday | Deletion Issue
KER-MSD-025 | Error occured while fetching Location Hierarchy | fetch issue
KER-MSD-026 | Location not found | Data Not Found
----
 

 

# Blacklisted words Master API

* [POST /blacklistedwords](#post-blacklistedwords)
* [PUT /blacklistedwords](#put-blacklistedwords)
* [GET /blacklistedwords/{langcode}](#get-blacklistedwordslangcode)
* [DELETE /blacklistedwords/{word}](#delete-blacklistedwordsword)
* [GET /blacklistedwords/all](#get-blacklistedwordsall)
* [PUT /blacklistedwords/details](#put-blacklistedwordsdetails)
* [POST /blacklistedwords/words](#post-blacklistedwordswords)


## POST /blacklistedwords

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

## PUT /blacklistedwords
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
## GET /blacklistedwords/{langcode}

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
## DELETE /blacklistedwords/{word}

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
## GET /blacklistedwords/all 

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

## PUT /blacklistedwords/details

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

## POST /blacklistedwords/words

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

## Failure details
Error Code | Error Message | Error Description
------------|------------------------------|-------------
KER-MSD-007 | Error occurred while fetching Blacklisted words | Fetch Issue
KER-MSD-008 | Blacklisted word not found | Data Not Found
KER-MSD-070 | Error occurred while inserting Blacklisted words | Insertion Issue
KER-MSD-105 | Error occurred while updating Blacklisted Word | Update Issue
KER-MSD-106 | Error occurred while deleting Blacklisted Word | Deletion Issue

----

# Documents Category Master API

* [POST /documentcategories](#post-documentcategories)
* [PUT /documentcategories](#put-documentcategories)
* [GET /documentcategories](#get-documentcategories)
* [GET /documentcategories/{code}/{langcode}](#get-documentcategories-code-langcode)
* [GET /documentcategories/{languagecode}](#get-documentcategories-languagecode)
* [DELETE /documentcategories/{code}](#delete-documentcategories-code)

# POST /documentcategories

This service will create the list of Documents Category which are used in the MOSIP platform. 

### Resource URL
### `POST /documentcategories`

### Resource details

Resource Details | Description
------------ | -------------
Response format | JSON
Requires Authentication | Yes

### Parameters
Name | Required | Description | Default Value | Example
-----|----------|-------------|---------------|--------
code|Yes|Document category code| |
description|optional|document description||
isActive|Yes|is active or not||
langCode|Yes|language code||
name|Yes|Document category name|| 

### Example Request
```JSON
{
  "id": "string",
  "version": "string",
  "metadata": {},
  "requesttime": "yyyy-MM-dd'T'HH:mm:ss.SSS'Z'",
  "request": {
              "code": "string",
              "description": "string",
              "isActive": true,
              "langCode": "string",
              "name": "string"
            }
}
```
### Example Response
```JSON
{
  "id": "string",
  "version": "string",
  "metadata": {},
  "responsetime": "yyyy-MM-dd'T'HH:mm:ss.SSS'Z'",
  "errors": [{
              "errorCode": "string",
              "message": "string"
             }],
  "response": {
               "code": "string",
               "langCode": "string"
              }
 }
```
### Response codes
201

Description: Created

400

Description: Bad request

401

Description: Unauthorized

403

Description: Forbidden
-----
This service will create the list of Documents Category which are used in the MOSIP platform. 

### Resource URL
### `PUT /documentcategories`

### Resource details

Resource Details | Description
------------ | -------------
Response format | JSON
Requires Authentication | Yes

### Parameters
Name | Required | Description | Default Value | Example
-----|----------|-------------|---------------|--------
code|Yes|Document category code| |
description|optional|document description||
isActive|Yes|is active or not||
langCode|Yes|language code||
name|Yes|Document category name|| 

### Example Request
```JSON
{
  "id": "string",
  "version": "string",
  "metadata": {},
  "requesttime": "yyyy-MM-dd'T'HH:mm:ss.SSS'Z'",
  "request": {
              "code": "string",
              "description": "string",
              "isActive": true,
              "langCode": "string",
              "name": "string"
            }
}
```
### Example Response
```JSON
{
  "id": "string",
  "version": "string",
  "metadata": {},
  "responsetime": "yyyy-MM-dd'T'HH:mm:ss.SSS'Z'",
  "errors": [{
              "errorCode": "string",
              "message": "string"
             }],
  "response": {
               "code": "string",
               "langCode": "string"
              }
 }
```
### Response codes
201

Description: Created

400

Description: Bad request

401

Description: Unauthorized

403

Description: Forbidden

404 

Description: Not Found


-----
# GET /documentcategories

This service will provides the service for the List of documents categories. 

### Resource URL
### `GET /documentcategories`

### Resource details

Resource Details | Description
------------ | -------------
Response format | JSON
Requires Authentication | Yes

### Parameters
Name | Required | Description | Default Value | Example
-----|----------|-------------|---------------|--------
-NA-

### Example Response
```JSON
{
  "id": "string",
  "version": "string",
  "metadata": {},
  "responsetime": "yyyy-MM-dd'T'HH:mm:ss.SSS'Z'",
  "errors": [{
             "errorCode": "string",
             "message": "string"
    }], 
  "response": {
             "documentcategories": [
                                      {
		                      "code": "string",
                                      "description": "string",
                                      "isActive": true,
                                      "langCode": "string",
                                      "name": "string"
                                      }
	                           ]
               }
}
```
200

Description: Success

400

Description: Bad request

401

Description: Unauthorized

404

Description: Not Found

# GET /documentcategories/{code}/{langcode}

This service will provides the service for the List of documents categories. 


### Resource URL
### `GET /documentcategories/{code}/{langcode}`

### Resource details

Resource Details | Description
------------ | -------------
Response format | JSON
Requires Authentication | Yes

### Parameters
Name | Required | Description | Default Value | Example
-----|----------|-------------|---------------|--------
-NA-

### Example Response
```JSON
{
  "id": "string",
  "version": "string",
  "metadata": {},
  "responsetime": "yyyy-MM-dd'T'HH:mm:ss.SSS'Z'",
  "errors": [{
      "errorCode": "string",
      "message": "string"
    }],
  "response": {
               "documentcategories": [
		                        { 
                                          "code": "string",
                                          "description": "string",
                                          "isActive": true,
                                          "langCode": "string",
                                          "name": "string"
		                         }
	                              ]
              }
}
```
200

Description: Success

400

Description: Bad request

401

Description: Unauthorized

404

Description: Not Found


# GET /documentcategories/{langcode} 

This service will provides the service for the List of documents categories based on the passed langcode. 


### Resource URL
### `GET /documentcategories/{langcode}`

### Resource details

Resource Details | Description
------------ | -------------
Response format | JSON
Requires Authentication | Yes

### Parameters
Name | Required | Description | Default Value | Example
-----|----------|-------------|---------------|--------
-NA-

### Example Response
```JSON
{
  "id": "string",
  "version": "string",
  "metadata": {},
  "responsetime": "yyyy-MM-dd'T'HH:mm:ss.SSS'Z'",
  "errors": [{
      "errorCode": "string",
      "message": "string"
    }],
  "response": {
	"documentcategories": [{
		                 "code": "string",
                                 "description": "string",
                                 "isActive": true,
                                 "langCode": "string",
                                 "name": "string"
	                      }]
            }
}
```
200

Description: Success

400

Description: Bad request

401

Description: Unauthorized

404
------
# DELETE /documentcategories/{code} 

This service will provides the service to delete documents categories based on the passed given code. 


### Resource URL
### `DELETE /documentcategories/{code}`

### Resource details

Resource Details | Description
------------ | -------------
Response format | JSON
Requires Authentication | Yes

### Parameters
Name | Required | Description | Default Value | Example
-----|----------|-------------|---------------|--------
-NA-

### Example Response
```JSON
{
  "id": "string",
  "version": "string",
  "metadata": {},
  "responsetime": "yyyy-MM-dd'T'HH:mm:ss.SSS'Z'",
  "errors": [{
      "errorCode": "string",
      "message": "string"
    }],
  "response": {
		 "code": "string"
              }
}
```
204

Description: No Content

401

Description: Unauthorized

404 

Description: Not Found

### Failure details
Error Code | Error Message | Error Description 
------------|------------------------------|-------------
KER-MSD-013 | Error occured while fetching Document Category details | Fetch Issue
KER-MSD-051 | Error occured while inserting Document Category details | Insertion Issue
KER-MSD-014 | Document Category not found | Data Not Found
KER-MSD-089 | Error occured while updating Document Category details | Update Issue
KER-MSD-090 | Error occured while deleting Document Category details | Deletion Issue
KER-MSD-123 | Cannot delete dependency found | Deletion Issue because of dependency

# Document formats Master API

* [POST /documentformats](#post-documentformats)
* [GET /documentformats](#get-documentformats)
* [GET /documentformats/{id}/{languagecode}](#get-documentformats-id-languagecode)

# POST /documentformats
Master data is required across the platform. 

This service will create the list of Documents Formats which are used in the MOSIP platform. 

### Resource URL
### `POST /documentformats`

### Resource details

Resource Details | Description
------------ | -------------
Response format | JSON
Requires Authentication | Yes

### Parameters
Name | Required | Description | Default Value | Example
-----|----------|-------------|---------------|--------
documentformats|Yes|List of document formats| | 

### Example Request
```JSON
{
  "id": "string",
  "version": "string",
  "metadata": {},
  "requesttime": "yyyy-MM-dd'T'HH:mm:ss.SSS'Z'",
  "request" : {
	  "documentformats": [
			          { "documentformat":"pdf", "languagecode":"string" },
			          { "documentformat":"png", "languagecode":"string" },
			          { "documentformat":"jpeg", "languagecode":"string"},
			          { "documentformat":"gif", "languagecode":"string" }
		           ]
	      }
}
```
### Example Response
```JSON
{
  "id": "string",
  "version": "string",
  "metadata": {},
  "responsetime": "yyyy-MM-dd'T'HH:mm:ss.SSS'Z'",
  "errors": [{
      "errorCode": "string",
      "message": "string"
    }],
 "response": {
  "successfully_created_documentformats": [
		                             {"documentformatid":id },
		                             {"documentformatid":id },
		                             {"documentformatid":id },
		                             {"documentformatid":id }  
                                           ]
             }
}
```
### Response codes
202

Description: Accepted

400

Description: Bad request

401

Description: Unauthorized

403

Description: Forbidden

# GET /documentformats
Master data is required across the platform. 

This service will provides the service for the List of documents formats. 



### Resource URL
### `GET /documentformats`

### Resource details

Resource Details | Description
------------ | -------------
Response format | JSON
Requires Authentication | Yes

### Parameters
Name | Required | Description | Default Value | Example
-----|----------|-------------|---------------|--------
-NA-


### Example Response
```JSON
{
  "id": "string",
  "version": "string",
  "metadata": {},
  "responsetime": "yyyy-MM-dd'T'HH:mm:ss.SSS'Z'",
  "errors": [{
      "errorCode": "string",
      "message": "string"
    }],
  "response": {
             "documentformats": [
			         {"id":"id", "format": "pdf" ,"languagecode":"string"},
			         {"id":"id", "format": "png" ,"languagecode":"string"},
			         {"id":"id", "format": "jpeg" ,"languagecode":"string"},
			         {"id":"id", "format": "gif" ,"languagecode":"string"}
	                        ]
               }
}
```
200

Description: Success

400

Description: Bad request

401

Description: Unauthorized

404

Description: Not Found

# GET /documentformats/{id}/{languagecode}

This service will provides the service for the List of documents formats. 

### Resource URL
### `GET /documentformats/{id}/{languagecode}`

### Resource details

Resource Details | Description
------------ | -------------
Response format | JSON
Requires Authentication | Yes

### Parameters
Name | Required | Description | Default Value | Example
-----|----------|-------------|---------------|--------
-NA-


### Example Response
```JSON
{
  "id": "string",
  "version": "string",
  "metadata": {},
  "responsetime": "yyyy-MM-dd'T'HH:mm:ss.SSS'Z'",
  "errors": [
    {
      "errorCode": "string",
      "message": "string"
    }
  ],
 "response": {
             "documentformats": [
			           {"id":"id", "format": "pdf" ,"languagecode":"string"},
			           {"id":"id", "format": "png" ,"languagecode":"string"},
			           {"id":"id", "format": "jpeg" ,"languagecode":"string"},
			           {"id":"id", "format": "gif" ,"languagecode":"string"}
		                ]
              }
}
```
200

Description: Success

400

Description: Bad request

401

Description: Unauthorized

404

Description: Not Found

# Machines Master API

* [POST /machines](#post-machines)
* [GET /machines](#get-machines)
* [GET /machines/{languagecode}](#get-machines-languagecode)
* [GET /machineshistory/{id}/{languagecode}/{eff_dtimes}](#get-machineshistory-id-languagecode-eff_dtimes)
* [DELETE /machines/{id}](#delete-machines-id)
* [PUT /machines](#put-machines)


# POST /machines

This service will create the list of Machines which are used in the MOSIP platform. 

### Resource URL
### `POST /machines`

### Resource details

Resource Details | Description
------------ | -------------
Response format | JSON
Requires Authentication | Yes

### Parameters
Name | Required | Description | Default Value | Example
-----|----------|-------------|---------------|--------
machinename|Yes|Name of the machine| | 
macid|Yes|Mac ID of the machine| | 
serialnumber|Yes|Serial number of the machine| | 
isactive|Yes|Is the machine active?| | 

### Example Request
```JSON
{
  "id": "string",
  "version": "string",
  "metadata": {},
  "requesttime": "yyyy-MM-dd'T'HH:mm:ss.SSS'Z'",
  "request": {
              "id": "string",
              "ipAddress": "string",
              "isActive": true,
              "langCode": "string",
              "macAddress": "string",
              "machineSpecId": "string",
              "name": "string",
              "serialNum": "string",
              "validityDateTime": "2018-12-24T05:52:46.758Z"
            }
}
```
### Example Response
```JSON
{
  "id": "string",
  "version": "string",
  "metadata": {},
  "responsetime": "yyyy-MM-dd'T'HH:mm:ss.SSS'Z'",
  "errors": [{
             "errorCode": "string",
             "message": "string"
            }],
 "response": {
               "id": "string"
             }
}
```
### Response codes
202

Description: Accepted

400

Description: Bad request

401

Description: Unauthorized

403

Description: Forbidden

# GET /machines

This service will provides the service to fetch the complete List of machines with the machine details. 

### Resource URL
### `GET /machines`

### Resource details

Resource Details | Description
------------ | -------------
Response format | JSON
Requires Authentication | Yes

### Parameters
Name | Required | Description | Default Value | Example
-----|----------|-------------|---------------|--------
-NA-


### Example Response
```JSON
{
  "id": "string",
  "version": "string",
  "metadata": {},
  "responsetime": "yyyy-MM-dd'T'HH:mm:ss.SSS'Z'",
  "errors": [{
            "errorCode": "string",
            "message": "string"
            }],
  "response": {
               "machines": [{
                            "id": "string",
                            "ipAddress": "string",
                            "isActive": true,
                            "langCode": "string",
                            "macAddress": "string",
                            "machineSpecId": "string",
                            "name": "string",
                            "serialNum": "string",
                            "validityDateTime": "2018-12-24T05:54:42.097Z"
                           }]
              }
}
```
200

Description: Success

400

Description: Bad request

401

Description: Unauthorized

404

Description: Not Found


# GET /machines/{languagecode}
Master data is required across the platform. 

This service will provides the service to fetch the List of machines with the machine details based on the language.

### Resource URL
### `GET /machines/{languagecode}`

### Resource details

Resource Details | Description
------------ | -------------
Response format | JSON
Requires Authentication | Yes

### Parameters
Name | Required | Description | Default Value | Example
-----|----------|-------------|---------------|--------
languagecode| Yes | Machine Languge Code|


### Example Response
```JSON
{
  "id": "string",
  "version": "string",
  "metadata": {},
  "responsetime": "yyyy-MM-dd'T'HH:mm:ss.SSS'Z'",
  "errors": [{
            "errorCode": "string",
            "message": "string"
            }],
  "response": {
              "machines": [{
                           "id": "string",
                           "ipAddress": "string",
                           "isActive": true,
                           "langCode": "string",
                           "macAddress": "string",
                           "machineSpecId": "string",
                           "name": "string",
                           "serialNum": "string",
                           "validityDateTime": "2018-12-24T05:58:03.286Z"
                          }]
                }
}
```
200

Description: Success

400

Description: Bad request

401

Description: Unauthorized

404

Description: Not Found


# GET /machineshistory/{id}/{languagecode}/{eff_dtimes}

This service will provides the service for the List of machines with their history. 


### Resource URL
### `GET /machineshistory/{id}/{languagecode}/{eff_dtimes}`

### Resource details

Resource Details | Description
------------ | -------------
Response format | JSON
Requires Authentication | Yes

### Parameters
Name | Required | Description | Default Value | Example
-----|----------|-------------|---------------|--------
ID|Yes|Machine History Id|
languagecode|Yes|Language code for the Machine|
eff_dtimes|Yes |Effective Date and Time of the Machine|

### Example Response
```JSON
{
  "id": "string",
  "version": "string",
  "metadata": {},
  "responsetime": "yyyy-MM-dd'T'HH:mm:ss.SSS'Z'",
  "errors": [{
      "errorCode": "string",
      "message": "string"
    }],
 "response": {
            "machineHistoryDetails": [
                                      {
                                      "effectDateTime": "2018-12-24T06:05:26.304Z",
                                      "id": "string",
                                      "ipAddress": "string",
                                      "isActive": true,
                                      "langCode": "string",
                                      "macAddress": "string",
                                      "machineSpecId": "string",
                                      "name": "string",
                                      "serialNum": "string",
                                      "validityDateTime": "2018-12-24T06:05:26.304Z"
                                   }
                                 ]
             }
}
```
200

Description: Success

400

Description: Bad request

401

Description: Unauthorized

404

Description: Not Found

# DELETE /machines/{id}

This service will delete the machines. 

### Resource URL
### `DELETE /machines/{id}`

### Resource details

Resource Details | Description
------------ | -------------
Response format | JSON
Requires Authentication | Yes

### Parameters
Name | Required | Description | Default Value | Example
-----|----------|-------------|---------------|--------
machineId|Yes|The machineId| | 

### Example Response
```JSON
{
  "id": "string",
  "version": "string",
  "metadata": {},
  "responsetime": "yyyy-MM-dd'T'HH:mm:ss.SSS'Z'",
  "errors": [{
      "errorCode": "string",
      "message": "string"
    }],
 "response": {
              "id": "string"
             }
}
```
200

Description: When Machine deleted successfully

204

Description: No Content

401

Description: Unauthorized

403
	
Description: Forbidden

404

Description: When machine not found

500

Description: Error occurred while deleting Machine

# PUT /machines

This service will update existing machines. 


### Resource URL
### `PUT /machines`

### Resource details

Resource Details | Description
------------ | -------------
Response format | JSON
Requires Authentication | Yes

### Parameters
Name | Required | Description | Default Value | Example
-----|----------|-------------|---------------|--------
-NA-


### Example Request
```JSON
{
  "id": "string",
  "version": "string",
  "metadata": {},
  "requesttime": "yyyy-MM-dd'T'HH:mm:ss.SSS'Z'",
  "request":  {
               "machineSpecId": "string",
               "id": "string",
               "ipAddress": "string",
               "isActive": true,
               "langCode": "string",
               "macAddress": "string",
               "name": "string",
               "serialNum": "string",
               "validityDateTime": "yyyy-MM-dd'T'HH:mm:ss.SSS'Z'"
            }
}
```
### Example Response
```JSON
{
  "id": "string",
  "version": "string",
  "metadata": {},
  "responsetime": "yyyy-MM-dd'T'HH:mm:ss.SSS'Z'",
  "errors": [{
      "errorCode": "string",
      "message": "string"
    }],
"response": {
               "id": "string"
            }
}
```
### Response codes
200

Description: When machine updated successfully

201

Description: Created

400

Description: When Request body passed is null or invalid

401

Description: Unauthorized

403

Description: Forbidden

404

Description: When Machine is not found

500

Description: While updating machine any error occurred

### Failure details

Error Code | Error Message | Error Description
------------|------------------------------|-------------
KER-MSD-029 | Error occured while fetching Machines | Fetch Issue
KER-MSD-063 | Error occurred while inserting Machine details | Insertion Issue
KER-MSD-030 | Machine not Found | Data Not Found
KER-MSD-087 | Error occurred while updating Machine details | Update Issue
KER-MSD-088 | Error occurred while deleting Machine details | Deletion Issue
KER-MSD-148 | Cannot delete as dependency found	Deletion | Issue because of dependency


# Devices Master API

* [POST /devices](#post-devices)
* [GET /devices]/{languagecode}](#get-devices)
* [GET /devices/{languagecode}/{deviceType}](#get-deviceType-languagecode)
* [PUT /devices](#put-devices)
* [DELETE /devices/{id}](#delete-devices-id)

# POST /devices

This service will create the list of Devices which are used in the MOSIP platform. 

### Resource URL
### `POST /devices`

### Resource details

Resource Details | Description
------------ | -------------
Response format | JSON
Requires Authentication | Yes

### Parameters
Name | Required | Description | Default Value | Example
-----|----------|-------------|---------------|--------
devicetype|Yes|Name of the device| | 
devicemodel|Yes|Mac ID of the device| | 

### Example Request
```JSON
{
  "id": "string",
  "version": "string",
  "metadata": {},
  "requesttime": "yyyy-MM-dd'T'HH:mm:ss.SSS'Z'",
  "request" : {
		"devices": {
				"deviceSpecId": "string",
                                "id": "string",
                                "ipAddress": "string",
                                "isActive": true,
                                "langCode": "string",
                                "macAddress": "string",
                                "name": "string",
                                "serialNum": "string",
                                "validityDateTime": "yyyy-MM-dd'T'HH:mm:ss.SSS'Z'"				
			   }
	      }
}
```
### Example Response
```JSON
{
  "id": "string",
  "version": "string",
  "metadata": {},
  "responsetime": "yyyy-MM-dd'T'HH:mm:ss.SSS'Z'",
  "errors": [{
      "errorCode": "string",
      "message": "string"
    }],
 "response": {
	     "successfully_created_devices": {
			                     "deviceid": "string"
		                             }	
}
```
### Response codes
202

Description: Accepted

400

Description: Bad request

401

Description: Unauthorized

403

Description: Forbidden

# GET /devices/{languagecode}

This service will provides the service for the List of devices. 


### Resource URL
### `GET /devices`

### Resource details

Resource Details | Description
------------ | -------------
Response format | JSON
Requires Authentication | Yes

### Parameters
Name | Required | Description | Default Value | Example
-----|----------|-------------|---------------|--------
-NA-


### Example Response
```JSON
{
  "id": "string",
  "version": "string",
  "metadata": {},
  "responsetime": "yyyy-MM-dd'T'HH:mm:ss.SSS'Z'",
  "errors": [{
      "errorCode": "string",
      "message": "string"
    } ],
  "response": {
	"devices": [{
			"deviceSpecId": "string",
                        "id": "string",
                        "ipAddress": "string",
                        "isActive": true,
                        "langCode": "string",
                        "macAddress": "string",
                        "name": "string",
                        "serialNum": "string",
                        "validityDateTime": "yyyy-MM-dd'T'HH:mm:ss.SSS'Z'"
	          }] 
             }
}
```
200

Description: Success

400

Description: Bad request

401

Description: Unauthorized

404

Description: Not Found


# GET /devices/{languagecode}/{deviceType}

This service will provides the service for the List of devices. 


### Resource URL
### `GET /devices/{languagecode}/{deviceType}`

### Resource details

Resource Details | Description
------------ | -------------
Response format | JSON
Requires Authentication | Yes

### Parameters
Name | Required | Description | Default Value | Example
-----|----------|-------------|---------------|--------
-NA-


### Example Response
```JSON
 {
  "id": "string",
  "version": "string",
  "metadata": {},
  "responsetime": "yyyy-MM-dd'T'HH:mm:ss.SSS'Z'",
  "errors": [{
      "errorCode": "string",
      "message": "string"
    }],
  "response": {
	"devices": [{
			 "deviceSpecId": "string",
                         "deviceTypeCode": "string",
                         "id": "string",
                         "ipAddress": "string",
                         "isActive": true,
                         "langCode": "string",
                         "macAddress": "string",
                         "name": "string",
                         "serialNum": "string",
                         "validityEndDateTime": "2019-04-05T09:30:13.608Z"
	         }]
    }
}
```
200

Description: Success

400

Description: Bad request

401

Description: Unauthorized

404

Description: Not Found

# PUT /devices

This service will update existing device. 


### Resource URL
### `PUT /devices`

### Resource details

Resource Details | Description
------------ | -------------
Response format | JSON
Requires Authentication | Yes

### Parameters
Name | Required | Description | Default Value | Example
-----|----------|-------------|---------------|--------
-NA-


### Example Request
```JSON
{
  "id": "string",
  "version": "string",
  "metadata": {},
  "requesttime": "yyyy-MM-dd'T'HH:mm:ss.SSS'Z'",
  "request": {
               "deviceSpecId": "string",
               "id": "string",
               "ipAddress": "string",
               "isActive": true,
               "langCode": "string",
               "macAddress": "string",
               "name": "string",
               "serialNum": "string",
               "validityDateTime": "yyyy-MM-dd'T'HH:mm:ss.SSS'Z'"
  }
}
```
### Example Response
```JSON
{
  "id": "string",
  "version": "string",
  "metadata": {},
  "responsetime": "yyyy-MM-dd'T'HH:mm:ss.SSS'Z'",
  "errors": [{
      "errorCode": "string",
      "message": "string"
    }],
  "response":{
                 "id": "string"
             }
}
```
### Response codes
200

Description: When Device updated successfully

201

Description: Created

400

Description: When Request body passed is null or invalid

401

Description: Unauthorized

403

Description: Forbidden

404

Description: When Device is not found

500

Description: While updating device any error occurred

# DELETE /devices/{id}

This service will delete the devices. 

### Resource URL
### `DELETE /devices/{id}`

### Resource details

Resource Details | Description
------------ | -------------
Response format | JSON
Requires Authentication | Yes

### Parameters
Name | Required | Description | Default Value | Example
-----|----------|-------------|---------------|--------
deviceId|Yes|The device Id| | 

### Example Response
```JSON
{
  "id": "string",
  "version": "string",
  "metadata": {},
  "responsetime": "yyyy-MM-dd'T'HH:mm:ss.SSS'Z'",
  "errors": [{
      "errorCode": "string",
      "message": "string"
    }],
  "response":{
               "id": "string"
            }
}
```
200

Description: When Device deleted successfully

204

Description: No Content

401

Description: Unauthorized

403
	
Description: Forbidden

404

Description: When Device not found

500

Description: Error occurred while deleting Device

#### Failure details
Error Code | Error Message | Error Description
------------|------------------------------|-------------
KER-MSD-009 | Error occured while fetching Devices | Fetch Issue
KER-MSD-069 | Error occurred while inserting Device details | Insertion Issue
KER-MSD-010 | Device not Found | Data Not Found
KER-MSD-083 | Error while updating | Update Issue
KER-MSD-084 | Error while deleting | Deletion Issue
KER-MSD-147 | Cannot delete as dependency found | Deletion Issue because of dependency


# Languages Master API

* [POST /languages](#post-languages)
* [GET /languages](#get-languages)
* [PUT /languages](#put-languages)
* [DELETE /languages/{code}](#delete-languages-code)

# POST /languages

This service will create a Language which is used in the MOSIP platform. 

### Resource URL
### `POST /languages`

### Resource details

Resource Details | Description
------------ | -------------
Response format | JSON
Requires Authentication | Yes

### Parameters
Name | Required | Description | Default Value | Example
-----|----------|-------------|---------------|--------
code|Yes|Code of the language| | 
name|Yes|Name of the language| | 

### Example Request
```JSON
{
  "id": "string",
  "version": "string",
  "metadata": {},
  "requesttime": "yyyy-MM-dd'T'HH:mm:ss.SSS'Z'",
  "request":  {
		"code": "string",
		"name": "string"
		"family": "string",
		"native_name": "string",
		"is_active": boolean
	      }
}
```
### Example Response
```JSON
{
  "id": "string",
  "version": "string",
  "metadata": {},
  "responsetime": "yyyy-MM-dd'T'HH:mm:ss.SSS'Z'",
  "errors": [{
      "errorCode": "string",
      "message": "string"
    }],
  "response": {
	"code": "string"
}
```
### Response codes
201

Description: Created

400

Description: Bad request

401

Description: Unauthorized

403

Description: Forbidden

# GET /languages

This service will provides the service for the List of languages. 

### Resource URL
### `GET /languages`

### Resource details

Resource Details | Description
------------ | -------------
Response format | JSON
Requires Authentication | Yes

### Parameters
Name | Required | Description | Default Value | Example
-----|----------|-------------|---------------|--------
code|Yes|Code of the language| | 
name|Yes|Name of the language| | 


### Example Request
-NA-

### Example Response
```JSON
{
  "id": "string",
  "version": "string",
  "metadata": {},
  "responsetime": "yyyy-MM-dd'T'HH:mm:ss.SSS'Z'",
  "errors": [{
      "errorCode": "string",
      "message": "string"
    }],
  "response": {
	"languages": [{
		      "code": "string",
		      "name": "string",
		      "family": "string",
		      "native_name": "string",
		      "is_active": "boolean"
	            }]
             }
}
```
200

Description: Success

400

Description: Bad request

401

Description: Unauthorized

404

Description: Not Found

# PUT /languages

This service will update a Language which is used in the MOSIP platform. 

### Resource URL
### `PUT /languages`

### Resource details

Resource Details | Description
------------ | -------------
Response format | JSON
Requires Authentication | Yes

### Parameters
Name | Required | Description | Default Value | Example
-----|----------|-------------|---------------|--------
code|Yes|Code of the language| | 
name|Yes|Name of the language| | 

### Example Request
```JSON
{
  "id": "string",
  "version": "string",
  "metadata": {},
  "requesttime": "yyyy-MM-dd'T'HH:mm:ss.SSS'Z'",
  "request":  {
		"code": "string",
		"name": "string"
		"family": "string",
		"native_name": "string",
		"is_active": boolean
	      }
}
```
### Example Response
```JSON
{
  "id": "string",
  "version": "string",
  "metadata": {},
  "responsetime": "yyyy-MM-dd'T'HH:mm:ss.SSS'Z'",
  "errors": [{
      "errorCode": "string",
      "message": "string"
    }],
  "response": {
	       "code": "string"
              }
}
```
### Response codes
200

Description: Ok

400

Description: Bad request

401

Description: Unauthorized

403

Description: Forbidden


# DELETE /languages/{code}

This service will delete a Language which is used in the MOSIP platform. 

### Resource URL
### `DELETE /languages/{code}`

### Resource details

Resource Details | Description
------------ | -------------
Response format | JSON
Requires Authentication | Yes

### Parameters
Name | Required | Description | Default Value | Example
-----|----------|-------------|---------------|--------
code|Yes|Code of the language| | 


### Example Request
-NA-
```
### Example Response
```JSON
{
  "id": "string",
  "version": "string",
  "metadata": {},
  "responsetime": "yyyy-MM-dd'T'HH:mm:ss.SSS'Z'",
  "errors": [{
               "errorCode": "string",
               "message": "string"
            }],
  "response": {
	      "code": "string"
              }
}
```
### Response codes
200

Description: Ok

400

Description: Bad request

401

Description: Unauthorized

403

Description: Forbidden

## Failure details
Error Code | Error Message | Error Description
------------|------------------------------|-------------
KER-MSD-24 | Language not found | Data Not Found
KER-MSD-23 | Error occured while fetching Languages | Fetch Issue
KER-MSD-049 | Error occurred while inserting Language details | Insertion Issue
KER-MSD-XXX | Error occured while updating Language | Update Issue
KER-MSD-XXX | Error occurred while deleting Language | Deletion Issue

# Gender Master API

* [POST /gendertypes](#post-gendertypes)
* [PUT/gendertypes](#put-gendertypes)
* [DELETE/gendertypes/{code}](#delete-gendertypes-code)
* [GET /gendertypes](#get-gendertypes)
* [GET /gendertypes/{languagecode}](#get-gendertypes-languagecode)
* [GET /gendertypes/{gendername}](#get-gendertypes-gendername)

# POST /gendertypes

This service will create the list of Gender which are used in the MOSIP platform. 

### Resource URL
### `POST /gendertypes`

### Resource details

Resource Details | Description
------------ | -------------
Response format | JSON
Requires Authentication | Yes

### Parameters
Name | Required | Description | Default Value | Example
-----|----------|-------------|---------------|--------
gendertype|Yes|Name of the gender| | 

### Example Request
```JSON
{
  "id": "string",
  "version": "string",
  "metadata": {},
  "requesttime": "yyyy-MM-dd'T'HH:mm:ss.SSS'Z'",
  "request": {
              "code": "GC002",
              "genderName": "Male",
              "isActive": true,
             "langCode": "ENG"
             }
}
```
### Example Response
```JSON
{
  "id": "string",
  "version": "string",
  "metadata": {},
  "responsetime": "yyyy-MM-dd'T'HH:mm:ss.SSS'Z'",
  "errors": [{
      "errorCode": "string",
      "message": "string"
    }],
  "response": {
               "code": "GC002",
               "langCode": "ENG"
              }
}
```
### Response codes
202

Description: Accepted

400

Description: Bad request

401

Description: Unauthorized

403

Description: Forbidden

# PUT/gendertypes

This service will update Gender which are used in the MOSIP platform. 

### Resource URL
### `PUT/gendertypes`

### Resource details

Resource Details | Description
------------ | -------------
Response format | JSON
Requires Authentication | Yes

### Parameters
Name | Required | Description | Default Value | Example
-----|----------|-------------|---------------|--------
code|Yes|Code of gender type| | 
genderName|Yes|Name of gender type| | 
isActive|Yes|is active or not| | 
code|Yes|language code of gender| | 

### Example Request
```JSON
{
  "id": "string",
  "version": "string",
  "metadata": {},
  "requesttime": "yyyy-MM-dd'T'HH:mm:ss.SSS'Z'",
  "request":  {
               "code": "GC001",
               "genderName": "Male",
               "isActive": true,
               "langCode": "ENG"
             }
}
```
### Example Response
```JSON
{
  "id": "string",
  "version": "string",
  "metadata": {},
  "responsetime": "yyyy-MM-dd'T'HH:mm:ss.SSS'Z'",
  "errors": [{
                "errorCode": "string",
                "message": "string"
           }],
  "response": {
                 "code": "GC001",
                 "langCode": "ENG"
              }
}
```
### Response codes
200

Description: OK

400

Description: Bad request

401

Description: Unauthorized

403

Description: Forbidden

# DELETE/gendertypes/{code}

This service will delete Gender which are used in the MOSIP platform. 

### Resource URL
### `DELETE/gendertypes/{code}`

### Resource details

Resource Details | Description
------------ | -------------
Response format | JSON
Requires Authentication | Yes

### Parameters
Name | Required | Description | Default Value | Example
-----|----------|-------------|---------------|--------
code|Yes|Code of gender type| |  

### Example Response
```JSON
{
  "id": "string",
  "version": "string",
  "metadata": {},
  "responsetime": "yyyy-MM-dd'T'HH:mm:ss.SSS'Z'",
  "errors": [{
               "errorCode": "string",
               "message": "string"
            }],
  "response": {
               "code": "GC001",
              }
}
```
### Response codes
200

Description: OK

400

Description: Bad request

401

Description: Unauthorized

403

Description: Forbidden

# GET /gendertypes
Master data is required across the platform. 

This service will provides the service for the List of Genders. 



### Resource URL
### `GET /gendertypes`

### Resource details

Resource Details | Description
------------ | -------------
Response format | JSON
Requires Authentication | Yes

### Parameters
Name | Required | Description | Default Value | Example
-----|----------|-------------|---------------|--------
genderid|Yes|Code of the language| | 
gendertype|Yes|Name of the language| | 


### Example Response
```JSON
{
  "id": "string",
  "version": "string",
  "metadata": {},
  "responsetime": "yyyy-MM-dd'T'HH:mm:ss.SSS'Z'",
  "errors": [{
              "errorCode": "string",
              "message": "string"
            }],
  "response": {  
               "genderType": [{
                               "code": "GC001",
                               "genderName": "Female",
                               "langCode": "eu",
                               "isActive": true
                               }]
}
```
200

Description: Success

400

Description: Bad request

401

Description: Unauthorized

404

Description: Not Found


# GET /gendertypes/{languagecode}

This service will provides the service for the List of Genders. 


### Resource URL
### `GET /gendertypes/{languagecode}`

### Resource details

Resource Details | Description
------------ | -------------
Response format | JSON
Requires Authentication | Yes

### Parameters
Name | Required | Description | Default Value | Example
-----|----------|-------------|---------------|--------
genderid|Yes|Code of the language| | 
gendertype|Yes|Name of the language| | 


### Example Response
```JSON
{
  "id": "string",
  "version": "string",
  "metadata": {},
  "responsetime": "yyyy-MM-dd'T'HH:mm:ss.SSS'Z'",
  "errors": [{
      "errorCode": "string",
      "message": "string"
    }],
  "response": {
             "genderType": [{
                           "code": "GC002",
                           "genderName": "Male",
                           "langCode": "ENG",
                           "isActive": true
                           }]
           }
}
```
200

Description: Success

400

Description: Bad request

401

Description: Unauthorized

404

Description: Not Found



# GET /gendertypes/{gendername}
Master data is required across the platform. 

This service will provides the gender based on the gender name. 



### Resource URL
### `GET /gendertypes/{gendername}`

### Resource details

Resource Details | Description
------------ | -------------
Response format | JSON
Requires Authentication | Yes

### Parameters
Name | Required | Description | Default Value | Example
-----|----------|-------------|---------------|--------
gendername|Yes|Name of the gender| | 


### Example Response
```JSON
{
  "id": "string",
  "version": "string",
  "metadata": {},
  "responsetime": "yyyy-MM-dd'T'HH:mm:ss.SSS'Z'",
  "errors": [{
      "errorCode": "string",
      "message": "string"
    }],
  "response": {
	       "code": "GC001",
	       "genderName": "Female",
	       "langCode": "eu",
	       "isActive": true
              }
}
```
200

Description: Success

## Failure details
Error Code | Error Message | Error Description
------------|------------------------------|-------------
KER-MSD-017 | Error occured while fetching gender types | Fetch Issue
KER-MSD-018 | Gender Type not found | Data Not Found
KER-MSD-068 | Could not insert Gender Data | Insertion Issue
KER-MSD-101 | Error occurred while updating Gender Type details | Update Issue
KER-MSD-102 | Error occurred while deleting Gender Type details | Deletion Issue


# Titles Master API

* [POST /title](#post-title)
* [GET /title](#get-title)
* [GET /title/{languagecode}](#get-title-languagecode)
* [PUT /title](#put-title)
* [DELETE /title/{code}](#delete-title-code)

# POST /title
Master data is required across the platform. 

This service will create the list of Title which are used in the MOSIP platform. 

### Resource URL
### `POST /title`

### Resource details

Resource Details | Description
------------ | -------------
Response format | JSON
Requires Authentication | Yes

### Parameters
Name | Required | Description | Default Value | Example
-----|----------|-------------|---------------|--------
titletype|Yes|Name of the title| | 

### Example Request
```JSON
{
  "id": "string",
  "version": "string",
  "metadata": {},
  "requesttime": "yyyy-MM-dd'T'HH:mm:ss.SSS'Z'",
  "request":  {
              "code": "cvf",
              "isActive": true,
              "langCode": "ghf",
              "titleDescription": "string",
              "titleName": "string"
             }
}
```
### Example Response
```JSON
{
  "id": "string",
  "version": "string",
  "metadata": {},
  "responsetime": "yyyy-MM-dd'T'HH:mm:ss.SSS'Z'",
  "errors": [ {
      "errorCode": "string",
      "message": "string"
    } ],
  "response": {
              "code": "cvf",
              "langCode": "ghf"
              }
}
```
### Response codes
201

Description: Created

400

Description: Bad request

401

Description: Unauthorized

403

Description: Forbidden

# GET /title
Master data is required across the platform. 

This service will provides the service for the List of Titles. 



### Resource URL
### `GET /title`

### Resource details

Resource Details | Description
------------ | -------------
Response format | JSON
Requires Authentication | Yes

### Parameters
Name | Required | Description | Default Value | Example
-----|----------|-------------|---------------|--------
titleid|Yes|Code of the language| | 
titletype|Yes|Name of the language| | 


### Example Response
```JSON
{
  "id": "string",
  "version": "string",
  "metadata": {},
  "responsetime": "yyyy-MM-dd'T'HH:mm:ss.SSS'Z'",
  "errors": [{
      "errorCode": "string",
      "message": "string"
    }],
  "response": {
          "titleList": [ {
                        "code": "43",
                        "titleName": "string",
                        "titleDescription": "string",
                        "isActive": true,
                        "langCode": "ENG"
                       } ]
             }
}
```
200

Description: Success

400

Description: Bad request

401

Description: Unauthorized

404

Description: Not Found


# GET /title/{languagecode}
Master data is required across the platform. 

This service will provides the service for the List of Titles. 



### Resource URL
### `GET /title/{languagecode}`

### Resource details

Resource Details | Description
------------ | -------------
Response format | JSON
Requires Authentication | Yes

### Parameters
Name | Required | Description | Default Value | Example
-----|----------|-------------|---------------|--------
titleid|Yes|Code of the language| | 
titletype|Yes|Name of the language| | 


### Example Response
```JSON
{
  "id": "string",
  "version": "string",
  "metadata": {},
  "responsetime": "yyyy-MM-dd'T'HH:mm:ss.SSS'Z'",
  "errors": [{
      "errorCode": "string",
      "message": "string"
    }],
  "response": {
              "titleList": [{
                            "code": "xcv",
                            "titleName": "string",
                            "titleDescription": "string",
                            "isActive": true,
                            "langCode": "qwe"
                            }]
              }
}
```
200

Description: Success

400

Description: Bad request

401

Description: Unauthorized

404

Description: Not Found

# PUT /title
Master data is required across the platform. 

This service will provides the service for updating a particular title. 



### Resource URL
### `PUT /title`

### Resource details

Resource Details | Description
------------ | -------------
Response format | JSON
Requires Authentication | Yes

### Parameters
Name | Required | Description | Default Value | Example
-----|----------|-------------|---------------|--------
code|Yes|Code of the title| | 
titleName|Yes|Name of the title| | 
isActive|Yes|Name of the title| |
langCode|Yes|Name of the title| |
titleDescription|Yes|Name of the title| |


### Example Response
```JSON
{
  "code": "xcv",
  "langCode": "qwe"
}
```
200

Description: Success

400

Description: Bad request

401

Description: Unauthorized

404

Description: Not Found

# DELETE /title/{code}
Master data is required across the platform. 

This service will provides the service for deleting a particular title. 



### Resource URL
### `DELETE /title/{code}`

### Resource details

Resource Details | Description
------------ | -------------
Response format | JSON
Requires Authentication | Yes

### Parameters
Name | Required | Description | Default Value | Example
-----|----------|-------------|---------------|--------
code|Yes|Code of the title| | 


### Example Response
```JSON
{
  "code": "xcv"
}
```
200

Description: Success

400

Description: Bad request

401

Description: Unauthorized

404

Description: Not Found

## Failure details
Error Code | Error Message | Error Description
------------|------------------------------|-------------
KER-MSD-047 | Error occured while fetching Titles | Fetch Issue
KER-MSD-048 | Title not found | Data Not Found
KER-MSD-XXX | Error occurred while inserting Title details | Insertion Issue
KER-MSD-103 | Error occurred while updating Title details | Update Issue
KER-MSD-104 | Error occurred while deleting Title details | Deletion Issue


# Biometric types Master API

* [POST /biometrictypes](#post-biometrictypes)
* [GET /biometrictypes](#get-biometrictypes)
* [GET /biometrictypes/{id}/{languagecode}](#get-biometrictypes-id-languagecode)

# POST /biometrictypes
Master data is required across the platform. 

This service will create the list of Biometric types which are used in the MOSIP platform. 

### Resource URL
### `POST /biometrictypes`

### Resource details

Resource Details | Description
------------ | -------------
Response format | JSON
Requires Authentication | Yes

### Parameters
Name | Required | Description | Default Value | Example
-----|----------|-------------|---------------|--------
biometrictype|Yes|Array of the biometric types| | 

### Example Request
```JSON

{
  "id": "string",
  "version": "string",
  "metadata": {},
  "requesttime": "yyyy-MM-dd'T'HH:mm:ss.SSS'Z'",
  "request": {
	  "biometrictypes": [
				{"biometrictype":"string"},
				{"biometrictype":"string"}
				{"languagecode":"string"}
	                   ]
	             }
}
```
### Example Response
```JSON
{
  "id": "string",
  "version": "string",
  "metadata": {},
  "responsetime": "yyyy-MM-dd'T'HH:mm:ss.SSS'Z'",
  "errors": [{
      "errorCode": "string",
      "message": "string"
    }],
  "response": {
	"biometrictypes": [
			     {"biometrictype":"string"},
			     {"biometrictype":"string"}
			     {"languagecode":"string"}
	                 ]
             }
}
```
### Response codes
202

Description: Accepted

400

Description: Bad request

401

Description: Unauthorized

403

Description: Forbidden

# GET /biometrictypes

This service will provides the service for the List of Biometrics. 



### Resource URL
### `GET /biometrictypes`

### Resource details

Resource Details | Description
------------ | -------------
Response format | JSON
Requires Authentication | Yes

### Parameters
Name | Required | Description | Default Value | Example
-----|----------|-------------|---------------|--------
biometrictypeid|Yes|Code of the language| | 
biometrictype|Yes|Name of the language| | 

### Example Response
```JSON
{
  "id": "string",
  "version": "string",
  "metadata": {},
  "responsetime": "yyyy-MM-dd'T'HH:mm:ss.SSS'Z'",
  "errors": [{
              "errorCode": "string",
              "message": "string"
           }],
   "response":{
                   "biometrictypes": [  { 
					"biometrictype": [
						         {"biometrictypeid":"string"},
						         {"biometrictype":"string"},
						         {"languagecode":"string"}						
					                ]
                                        }, 
				       { 
					"biometrictype": [
						{"biometrictypeid":"string"},
						{"biometrictype":"string"},
						{"languagecode":"string"}						
					]
				}
			]
}
```
200

Description: Success

400

Description: Bad request

401

Description: Unauthorized

404

Description: Not Found


# GET /biometrictypes/{id}/{languagecode}
Master data is required across the platform. 

This service will provides the service for the List of Biometrics. 



### Resource URL
### `GET /biometrictypes/{id}/{languagecode}`

### Resource details

Resource Details | Description
------------ | -------------
Response format | JSON
Requires Authentication | Yes

### Parameters
Name | Required | Description | Default Value | Example
-----|----------|-------------|---------------|--------
biometrictypeid|Yes|Code of the language| | 
biometrictype|Yes|Name of the language| | 

### Example Response
```JSON
{
  "biometrictypes": [
				{ 
					"biometrictype": [
						{"biometrictypeid":"string"},
						{"biometrictype":"string"},
						{"languagecode":"string"}						
					]
				}, 
				{ 
					"biometrictype": [
						{"biometrictypeid":"string"},
						{"biometrictype":"string"},
						{"languagecode":"string"}						
					]
				}
			]
}
```
200

Description: Success

400

Description: Bad request

401

Description: Unauthorized

404

Description: Not Found

## Failure details
Error Code | Error Message | Error Description
------------|------------------------------|-------------
KER-MSD-005 | Error occurred while fetching Biometric Types | Fetch Issue
KER-MSD-006 | Biometric Type not found | Data Not Found
KER-MSD-105 | Error occurred while inserting biometric type details | Insertion Issue


# ID Types Master API

* [POST /idtypes](#post-idtypes)
* [GET /idtypes/{langcode}](#get-idtypes-langcode)

# POST /idtypes
Master data is required across the platform. 

This service will create the list of Id types which are used in the MOSIP platform. 

### Resource URL
### `POST /idtypes`

### Resource details

Resource Details | Description
------------ | -------------
Response format | JSON
Requires Authentication | Yes

### Parameters
Name | Required | Description | Default Value | Example
-----|----------|-------------|---------------|--------
code|Yes|Name of the id type| | 
languagecode|Yes|Language of the id type| | 
isActive|Yes|is active?| |
name |Yes|is active?| |
descr | Yes | description ||

### Example Request
```JSON
{
  "id": "string",
  "version": "string",
  "metadata": {},
  "requesttime": "yyyy-MM-dd'T'HH:mm:ss.SSS'Z'",
  "request": {
               "code": "string",
               "descr": "string",
               "isActive": true,
               "langCode": "string",
               "name": "string"
              },
 }
```
### Example Response
```JSON
{
  "id": "string",
  "version": "string",
  "metadata": {},
  "responsetime": "yyyy-MM-dd'T'HH:mm:ss.SSS'Z'",
  "errors": [{
      "errorCode": "string",
      "message": "string"
    } ],
  "response": {
                "code": "string",
               "langCode": "string"
              }
}
```
### Response codes
202

Description: Accepted

400

Description: Bad request

401

Description: Unauthorized

403

Description: Forbidden


# GET /idtypes/{langcode}
Master data is required across the platform. 

This service will provides the service for the List of id types based on language. 



### Resource URL
### `GET /idtypes/{langcode}`

### Resource details

Resource Details | Description
------------ | -------------
Response format | JSON
Requires Authentication | Yes

### Parameters
Name | Required | Description | Default Value | Example
-----|----------|-------------|---------------|--------
langcode|Yes|Code of the language| | 


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
    "idtypes": [
      {
        "code": "string",
        "descr": "string",
        "isActive": true,
        "langCode": "string",
        "name": "string"
      }
    ]
  },
  "responsetime": "yyyy-MM-dd'T'HH:mm:ss.SSS'Z'",
  "version": "string"
}
```
200

Description: Success

400

Description: Bad request

401

Description: Unauthorized

404

Description: Not Found

## Failure details
Error Code | Error Message | Error Description
------------|------------------------------|-------------
KER-MSD-021 | Error occured while fetching ID Types | Fetch Issue
KER-MSD-022 | ID Type not found | Data Not Found
KER-MSD-059 | Error occurred while inserting ID Type details. | Insertion Issue

# Application Types Master API

* [POST /applicationtypes](#post-applicationtypes)
* [GET /applicationtypes](#get-applicationtypes)
* [GET /applicationtypes/{code}/{langcode}](#get-applicationtypes-code-languagecode)
* [GET /applicationtypes/{langcode}](#get-applicationtypes-languagecode)

# POST /applicationtypes
Master data is required across the platform. 

This service will create the list of ApplicationTypes which are used in the MOSIP platform. 

### Resource URL
### `POST /applicationtypes`

### Resource details

Resource Details | Description
------------ | -------------
Response format | JSON
Requires Authentication | Yes

### Parameters
Name | Required | Description | Default Value | Example
-----|----------|-------------|---------------|--------
applicationtypetype|Yes|Array of applicationtype| | 

### Example Request
```JSON
{
  "id": "string",
  "version": "string",
  "metadata": {},
  "requesttime": "yyyy-MM-dd'T'HH:mm:ss.SSS'Z'",
  "request":  {
	      "applicationtypes": [
		                       {"applicationtypetype":"string"},
		                       {"languagecode":"string"}
	                          ]
	      }
}
```
### Example Response
```JSON
{
  "id": "string",
  "version": "string",
  "metadata": {},
  "responsetime": "yyyy-MM-dd'T'HH:mm:ss.SSS'Z'",
  "errors": [{
      "errorCode": "string",
      "message": "string"
    }],
  "response": {
  "successfully_created_applicationtypes": [
	                	               {"applicationtypeid":"string"},
		                               {"languagecode":"string"}
                                           ]
             }
}
```
### Response codes
202

Description: Accepted

400

Description: Bad request

401

Description: Unauthorized

403

Description: Forbidden

# GET /applicationtypes
Master data is required across the platform. 

This service will provides the service for the List of ApplicationTypes. 



### Resource URL
### `GET /applicationtypes`

### Resource details

Resource Details | Description
------------ | -------------
Response format | JSON
Requires Authentication | Yes

### Parameters
Name | Required | Description | Default Value | Example
-----|----------|-------------|---------------|--------
applicationtypeid|Yes|Code of the language| | 
applicationtype|Yes|Name of the language| | 


### Example Response
```JSON
{
  "id": "string",
  "version": "string",
  "metadata": {},
  "responsetime": "yyyy-MM-dd'T'HH:mm:ss.SSS'Z'",
  "errors": [{
      "errorCode": "string",
      "message": "string"
    }],
  "response": {
  "applicationtypes": [
				{ 
					"applicationtype": [
						{"applicationtypeid":"string"},
						{"applicationtypetype":"string"},
						{"languagecode":"string"}
					]
				}, 
				{ 
					"applicationtype": [
						{"applicationtypeid":"string"},
						{"applicationtypetype":"string"}
						{"languagecode":"string"}
					]
				}
			] 
              }
}
```
200

Description: Success

400

Description: Bad request

401

Description: Unauthorized

404

Description: Not Found


# GET /applicationtypes/{code}/{langcode}
Master data is required across the platform. 

This service will provides the service for the List of ApplicationTypes. 



### Resource URL
### `GET /applicationtypes/{code}/{languagecode}`

### Resource details

Resource Details | Description
------------ | -------------
Response format | JSON
Requires Authentication | Yes

### Parameters
Name | Required | Description | Default Value | Example
-----|----------|-------------|---------------|--------
code |Yes|Code of the language| | 
langcode|Yes|Name of the language| | 


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
    "applicationtypes": [
      {
        "code": "string",
        "description": "string",
        "isActive": true,
        "langCode": "string",
        "name": "string"
      }
    ]
  },
  "responsetime": "yyyy-MM-dd'T'HH:mm:ss.SSS'Z'",
  "version": "string"
}
```
200

Description: Success

400

Description: Bad request

401

Description: Unauthorized

404

Description: Not Found

# GET /applicationtypes/{langcode}

This service is used to fetch all Application details by language code

### Resource URL
### `GET /applicationtypes/{languagecode}`

### Resource details

Resource Details | Description
------------ | -------------
Response format | JSON
Requires Authentication | Yes

### Parameters
Name | Required | Description | Default Value | Example
-----|----------|-------------|---------------|--------
langcode|Yes|Name of the language| | 

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
    "applicationtypes": [
      {
        "code": "string",
        "description": "string",
        "isActive": true,
        "langCode": "string",
        "name": "string"
      }
    ]
  },
  "responsetime": "yyyy-MM-dd'T'HH:mm:ss.SSS'Z'",
  "version": "string"
}
```
200

Description: Success

400

Description: Bad request

401

Description: Unauthorized

404

Description: Not Found

## Failure details
Error Code | Error Message | Error Description
------------|------------------------------|-------------
KER-MSD-001 | Error occurred while fetching Applications | Fetch Issue
KER-MSD-002 | Application not found | Data Not Found
KER-MSD-101 | Error occurred while inserting application details | Insertion Issue
KER-MSD-201 | Bad Request Found | Bad request

# Registration Centers Master API

* [POST /registrationcenters](#post-registrationcenters)
* [GET /registrationcenters](#get-registrationcenters)
* [GET /registrationcenters/{id}/{languagecode}](#get-registrationcenters-id-languagecode)
* [GET /getregistrationcenterholidays/{languagecode}/{registrationcenterid}/{year}](#get-getregistrationcenterholidays-languagecode-registrationcenterid-year)
* [GET /getlocspecificregistrationcenters/{langcode}/{locationcode}](#get-getlocspecificregistrationcenters-langcode-locationcode)
* [GET /getcoordinatespecificregistrationcenters/{languagecode}/{longitude}/{latitude}/{proximitydistance}](#get-getcoordinatespecificregistrationcenters-languagecode-longitude-latitude-proximitydistance)
* [GET /registrationcentershistory/{id}/{languagecode}/{eff_dtimes}](#get-registrationcentershistory-id-languagecode-eff_dtimes)
* [GET /getregistrationmachineusermappinghistory/{eff_dtimes}/{registrationcenterid}/{machineid}/{userid}](#get-getregistrationmachineusermappinghistory-eff_dtimes-registrationcenterid-machineid-userid)
* [GET /getlocspecificregistrationcenters/{hierarchylevel}/{textvalue}/{languagecode}](#get-getlocspecificregistrationcenters-hierarchylevel-textvalue-languagecode)

# POST /registrationcenters
Master data is required across the platform. 

This service will create the list of Registration Centers which are used in the MOSIP platform. 

### Resource URL
### `POST /registrationcenters`

### Resource details

Resource Details | Description
------------ | -------------
Response format | JSON
Requires Authentication | Yes

### Parameters
Name | Required | Description | Default Value | Example
-----|----------|-------------|---------------|--------
registrationcentername|Yes|Name of the registration center| | 
centertypecode|Yes|Code of the center type| | 
addressline1|No|Line 1 of the address| | 
addressline2|No|Line 2 of the address| | 
addressline3|No|Line 3 of the address| | 
longitude|Yes|Longitude of the registration center| | 
latitude|Yes|Latitude of the registration center| | 
contactphone|Yes|Contact phone number of the registration center| |  
workinghours|Yes|Working hours of the registration center| | 
perkioskprocesstime|Yes|Process time per kiosk in the registration center| | 
officestarttime|Yes|Office start time of the registration center| | 
officeendtime|Yes|Office end time of the registration center| | 
holidaylocationcode|Yes|Holiday location of the registration center| | 
isactive|Yes|Is the registration center active| | 
centertype|Yes|Type of the registration center| | 
address|Yes|Address of the registration center| | 
workinghours|Yes|Working hours of the registration center| | 
contactnumber|Yes|Contact number of the registration center| | 
pincode|Yes|Pincode of the registration center| | 
locationcode|Yes|Code of the location of the registration center| | 

### Example Request
```JSON
{
  "id": "string",
  "version": "string",
  "metadata": {},
  "requesttime": "yyyy-MM-dd'T'HH:mm:ss.SSS'Z'",
  "request": {
    "addressLine1": "string",
    "addressLine2": "string",
    "addressLine3": "string",
    "centerEndTime": "HH:mm:ss",
    "centerStartTime": "HH:mm:ss",
    "centerTypeCode": "string",
    "contactPerson": "string",
    "contactPhone": "string",
    "holidayLocationCode": "string",
    "id": "string",
    "isActive": true,
    "languageCode": "string",
    "latitude": "string",
    "locationCode": "string",
    "longitude": "string",
    "lunchEndTime": "HH:mm:ss",
    "lunchStartTime": "HH:mm:ss",
    "name": "string",
    "numberOfKiosks": 0,
    "perKioskProcessTime": "HH:mm:ss",
    "timeZone": "string",
    "workingHours": "string"
  }
}
```
### Example Response
```JSON
{
  "id": "string",
  "version": "string",
  "metadata": {},
  "responsetime": "yyyy-MM-dd'T'HH:mm:ss.SSS'Z'",
  "errors": [{
      "errorCode": "string",
      "message": "string"
    }],
  "response": {
	        "id":"string"
             }
}
```
### Response codes
200

Description: OK

201

Description: Created

202

Description: Accepted

400

Description: Bad request

401

Description: Unauthorized

403

Description: Forbidden

# GET /registrationcenters
Master data is required across the platform. 

This service will provides the service for the List of Registration Centers. 

### Resource URL
### `GET /registrationcenters`

### Resource details

Resource Details | Description
------------ | -------------
Response format | JSON
Requires Authentication | Yes

### Parameters
Name | Required | Description | Default Value | Example
-----|----------|-------------|---------------|--------
-NA-


### Example Response
```JSON
{
  "id": "string",
  "version": "string",
  "metadata": {},
  "responsetime": "yyyy-MM-dd'T'HH:mm:ss.SSS'Z'",
  "errors": [{
      "errorCode": "string",
      "message": "string"
    }],
  "response": {
  "registrationcenters": [
	{
			"registrationcentername":"",
			"centertypecode":"",
			"addressline1":"",
			"addressline2":"",
			"addressline3 ":"",
			"longitude ":"",
			"latitude":"",
			"contactphone":"",
			"numberofkiosks":"",
			"workinghours":"",
			"perkioskprocesstime":"",
			"officestarttime":"",
			"officeendtime":"",
			"holidaylocationcode":"",
			"isactive":"",
			"centertype":"",
			"address":"",
			"workinghours":"",
			"contactnumber":"",
			"pincode":"",
			"locationcode":""
	},
	{
			"registrationcentername":"",
			"centertypecode":"",
			"addressline1":"",
			"addressline2":"",
			"addressline3 ":"",
			"longitude ":"",
			"latitude":"",
			"contactphone":"",
			"numberofkiosks":"",
			"workinghours":"",
			"perkioskprocesstime":"",
			"officestarttime":"",
			"officeendtime":"",
			"holidaylocationcode":"",
			"isactive":"",
			"centertype":"",
			"address":"",
			"workinghours":"",
			"contactnumber":"",
			"pincode":"",
			"locationcode":""
	}
   ]
 }
}
```
200

Description: Success

400

Description: Bad request

401

Description: Unauthorized

404

Description: Not Found


# GET /registrationcenters/{id}/{languagecode}
Master data is required across the platform. 

This service will provides the service for the List of Registration Centers. 

### Resource URL
### `GET /registrationcenters/{id}/{languagecode}`

### Resource details

Resource Details | Description
------------ | -------------
Response format | JSON
Requires Authentication | Yes

### Parameters
Name | Required | Description | Default Value | Example
-----|----------|-------------|---------------|--------
-NA-


### Example Response
```JSON
{
  "id": "string",
  "version": "string",
  "metadata": {},
  "responsetime": "yyyy-MM-dd'T'HH:mm:ss.SSS'Z'",
  "errors": [{
      "errorCode": "string",
      "message": "string"
    }],
  "response": {
  "registrationcenters": [
	{
			"registrationcentername":"",
			"centertypecode":"",
			"addressline1":"",
			"addressline2":"",
			"addressline3 ":"",
			"longitude ":"",
			"latitude":"",
			"contactphone":"",
			"numberofkiosks":"",
			"workinghours":"",
			"perkioskprocesstime":"",
			"officestarttime":"",
			"officeendtime":"",
			"holidaylocationcode":"",
			"isactive":"",
			"centertype":"",
			"address":"",
			"workinghours":"",
			"contactnumber":"",
			"pincode":"",
			"locationcode":""
	},
	{
			"registrationcentername":"",
			"centertypecode":"",
			"addressline1":"",
			"addressline2":"",
			"addressline3 ":"",
			"longitude ":"",
			"latitude":"",
			"contactphone":"",
			"numberofkiosks":"",
			"workinghours":"",
			"perkioskprocesstime":"",
			"officestarttime":"",
			"officeendtime":"",
			"holidaylocationcode":"",
			"isactive":"",
			"centertype":"",
			"address":"",
			"workinghours":"",
			"contactnumber":"",
			"pincode":"",
			"locationcode":""
       	}
   ]
 }
}
```
200

Description: Success

400

Description: Bad request

401

Description: Unauthorized

404

Description: Not Found

# GET /getregistrationcenterholidays/{languagecode}/{registrationcenterid}/{year}
This service will list of holidays for a particular registration center for that particular year. 

### Resource URL
### `GET /getregistrationcenterholidays/{languagecode}/{registrationcenterid}/{year}`

### Resource details

Resource Details | Description
------------ | -------------
Response format | JSON
Requires Authentication | Yes

### Parameters
Name | Required | Description | Default Value | Example
-----|----------|-------------|---------------|--------
registrationcenterid|Yes|ID of the registration center| | 
year|Yes|The year for which the list of holidays is listed| | 


### Example Response
```JSON
{
  "id": "string",
  "version": "string",
  "metadata": {},
  "responsetime": "yyyy-MM-dd'T'HH:mm:ss.SSS'Z'",
  "errors": [{
      "errorCode": "string",
      "message": "string"
    }],
  "response": {
  "registrationcenter": [
	{
		"registrationcentername":"",
		"centertypecode":"",
		"addressline1":"",
		"addressline2":"",
		"addressline3 ":"",
		"longitude ":"",
		"latitude":"",
		"contactphone":"",
		"numberofkiosks":"",
		"workinghours":"",
		"perkioskprocesstime":"",
		"officestarttime":"",
		"officeendtime":"",
		"holidaylocationcode":"",
		"isactive":"",
		"centertype":"",
		"address":"",
		"workinghours":"",
		"contactnumber":"",
		"pincode":"",
		"locationcode":"",
		"holidays": [
			"holiday" : {
				"holidayID": "string",
				"holidayDate": "string",
				"holidayName": "string",
				"holidayDay": "string",	
				"holidayMonth": "string",
				"holidayYear": "string",
				"languagecode":"string"
			           }
		            ]		
	  }
     ]
   }
}
```
200

Description: Success

400

Description: Bad request

401

Description: Unauthorized

404

Description: Not Found


# GET /getlocspecificregistrationcenters/{langcode}/{locationcode}
This service will return a list of enrollment center details based on the location code 

### Resource URL
### `GET /getlocspecificregistrationcenters/{langcode}/{locationcode}`

### Resource details

Resource Details | Description
------------ | -------------
Response format | JSON
Requires Authentication | Yes

### Parameters
Name | Required | Description | Default Value | Example
-----|----------|-------------|---------------|--------
locationcode|Yes|The location code for which the list of enrollment centers are needed| | 


### Example Response
```JSON
{
  "id": "string",
  "version": "string",
  "metadata": {},
  "responsetime": "yyyy-MM-dd'T'HH:mm:ss.SSS'Z'",
  "errors": [{
      "errorCode": "string",
      "message": "string"
    }],
  "response": {
  "registrationCenters": [
    {
          "addressLine1": "string",
          "addressLine2": "string",
          "addressLine3": "string",
          "centerEndTime": "HH:mm:ss",
          "centerStartTime": "HH:mm:ss",
          "centerTypeCode": "string",
          "contactPerson": "string",
          "contactPhone": "string",
          "holidayLocationCode": "string",
          "id": "string",
          "isActive": true,
          "languageCode": "string",
          "latitude": "string",
          "locationCode": "string",
          "longitude": "string",
          "lunchEndTime": "HH:mm:ss",
          "lunchStartTime": "HH:mm:ss",
          "name": "string",
          "numberOfKiosks": 0,
          "perKioskProcessTime": "HH:mm:ss",
          "timeZone": "string",
          "workingHours": "string"
       }
   ]
 }
}
```
200

Description: OK

400

Description: Bad request

401

Description: Unauthorized

404

Description: Not Found

# GET /getcoordinatespecificregistrationcenters/{languagecode}/{longitude}/{latitude}/{proximitydistance}
This service will return a list of enrollment center details based on the coordinates

### Resource URL
### `GET /getcoordinatespecificregistrationcenters/{languagecode}/{longitude}/{latitude}/{proximitydistance}`

### Resource details

Resource Details | Description
------------ | -------------
Response format | JSON
Requires Authentication | Yes

### Parameters
Name | Required | Description | Default Value | Example
-----|----------|-------------|---------------|--------
languagecode|Yes|Language code in Language code in ISO 639-2 format| | 
longitude|Yes|The longitude for which the list of enrollment centers are needed| | 
latitude|Yes|The latitude code for which the list of enrollment centers are needed| | 
proximitydistance|Yes|The proximity diameter in meter| | 


### Example Response
```JSON
{
  "id": "string",
  "version": "string",
  "metadata": {},
  "responsetime": "yyyy-MM-dd'T'HH:mm:ss.SSS'Z'",
  "errors": [{
      "errorCode": "string",
      "message": "string"
    }],
  "response": {
  "registrationcenter": [
	{
			"registrationcentername":"",
			"centertypecode":"",
			"addressline1":"",
			"addressline2":"",
			"addressline3 ":"",
			"longitude ":"",
			"latitude":"",
			"contactphone":"",
			"numberofkiosks":"",
			"workinghours":"",
			"perkioskprocesstime":"",
			"officestarttime":"",
			"officeendtime":"",
			"holidaylocationcode":"",
			"isactive":"",
			"centertype":"",
			"address":"",
			"workinghours":"",
			"contactnumber":"",
			"pincode":"",
			"locationcode":""
	   }
     ]
  }
}
```
200

Description: Success

400

Description: Bad request

401

Description: Unauthorized

404

Description: Not Found

# GET /registrationcentershistory/{id}/{languagecode}/{eff_dtimes}

This service will provides the service for the List of Registration Centers History. 

### Resource URL
### `GET /registrationcentershistory/{id}/{languagecode}/{eff_dtimes}`

### Resource details

Resource Details | Description
------------ | -------------
Response format | JSON
Requires Authentication | Yes

### Parameters
Name | Required | Description | Default Value | Example
-----|----------|-------------|---------------|--------
-NA-


### Example Response
```JSON
{
  "id": "string",
  "version": "string",
  "metadata": {},
  "responsetime": "yyyy-MM-dd'T'HH:mm:ss.SSS'Z'",
  "errors": [{
      "errorCode": "string",
      "message": "string"
    }],
  "response":{
  "registrationcenters": [
	{
			"registrationcentername":"",
			"centertypecode":"",
			"addressline1":"",
			"addressline2":"",
			"addressline3 ":"",
			"longitude ":"",
			"latitude":"",
			"contactphone":"",
			"numberofkiosks":"",
			"workinghours":"",
			"perkioskprocesstime":"",
			"officestarttime":"",
			"officeendtime":"",
			"holidaylocationcode":"",
			"isactive":"",
			"centertype":"",
			"address":"",
			"workinghours":"",
			"contactnumber":"",
			"pincode":"",
			"locationcode":""
	},
	{
			"registrationcentername":"",
			"centertypecode":"",
			"addressline1":"",
			"addressline2":"",
			"addressline3 ":"",
			"longitude ":"",
			"latitude":"",
			"contactphone":"",
			"numberofkiosks":"",
			"workinghours":"",
			"perkioskprocesstime":"",
			"officestarttime":"",
			"officeendtime":"",
			"holidaylocationcode":"",
			"isactive":"",
			"centertype":"",
			"address":"",
			"workinghours":"",
			"contactnumber":"",
			"pincode":"",
			"locationcode":""
	}
    ]
  }
}
```
200

Description: Success

400

Description: Bad request

401

Description: Unauthorized

404

Description: Not Found

# GET /getregistrationmachineusermappinghistory/{eff_dtimes}/{registrationcenterid}/{machineid}/{userid}

This service will provides the history of mappings of mapping History of Registration, Machine and User based on Registration Center ID, Machine ID, User ID, Date and Language Code 

### Resource URL
### `GET /getregistrationmachineusermappinghistory/{eff_dtimes}/{registrationcenterid}/{machineid}/{userid}`

### Resource details

Resource Details | Description
------------ | -------------
Response format | JSON
Requires Authentication | Yes

### Parameters
Name | Required | Description | Default Value | Example
-----|----------|-------------|---------------|--------
languagecode|Yes|Language code in Language code in ISO 639-2 format| | 
eff_dtimes|Yes|From which date this change is with effective| | 2018-11-02T05:20:31.075
registrationcenterid|Yes|ID of the registration center| | 
machineid|Yes|ID of the machine| | 

### Example Response
```JSON
{
  "id": "string",
  "version": "string",
  "metadata": {},
  "responsetime": "yyyy-MM-dd'T'HH:mm:ss.SSS'Z'",
  "errors": [{
      "errorCode": "string",
      "message": "string"
    }],
  "response":{
  "registrationcenters": [
	{
		"registrationcenterid":"string",
		"machineid":"string",
		"userid":"string"
	},
	{
		"registrationcenterid":"string",
		"machineid":"string",
		"userid":"string"
	}
    ]
  }
}
```
200

Description: Success

400

Description: Bad request

401

Description: Unauthorized

404

Description: Not Found


# GET /getlocspecificregistrationcenters/{hierarchylevel}/{textvalue}/{languagecode}
This service will return a list of enrollment center details based on hierarchy level, text value and language code

### Resource URL
### `GET /getlocspecificregistrationcenters/{hierarchylevel}/{textvalue}/{languagecode}`

### Resource details

Resource Details | Description
------------ | -------------
Response format | JSON
Requires Authentication | Yes

### Parameters
Name | Required | Description | Default Value | Example
-----|----------|-------------|---------------|--------
hierarchylevel|Yes|The hierarchy level for which the list of enrollment centers are needed| | 
textvalue|Yes|This is a free text. The search will happen with the combination of heirarchy level, language code and this free text. The enrollment centers which satisfy these 3 criteria will be returned| | 
languagecode|Yes|The enrollment center description will be returned in this language code | | 


### Example Response
```JSON
{
  "id": "string",
  "version": "string",
  "metadata": {},
  "responsetime": "yyyy-MM-dd'T'HH:mm:ss.SSS'Z'",
  "errors": [{
      "errorCode": "string",
      "message": "string"
    }],
  "response":{
  "registrationcenter": [
	{
			"registrationcentername":"",
			"centertypecode":"",
			"addressline1":"",
			"addressline2":"",
			"addressline3 ":"",
			"longitude ":"",
			"latitude":"",
			"contactphone":"",
			"numberofkiosks":"",
			"workinghours":"",
			"perkioskprocesstime":"",
			"officestarttime":"",
			"officeendtime":"",
			"holidaylocationcode":"",
			"isactive":"",
			"centertype":"",
			"address":"",
			"workinghours":"",
			"contactnumber":"",
			"pincode":"",
			"locationcode":""
	 }
     ]
  }
}
```
200

Description: Success

400

Description: Bad request

401

Description: Unauthorized

404

Description: Not Found



# Biometric Attributes Master API

* [POST /biometricattributes](#post-biometricattributes)
* [GET /getbiometricattributesbyauthtype/{languagecode}/{biometrictypeid}](#get-getbiometricattributesbyauthtype-languagecode-biometrictypeid)

# POST /biometricattributes

This service will create the list of Biometric attributes which are used in the MOSIP platform. 

### Resource URL
### `POST /biometricattributes`

### Resource details

Resource Details | Description
------------ | -------------
Response format | JSON
Requires Authentication | Yes

### Parameters
Name | Required | Description | Default Value | Example
-----|----------|-------------|---------------|--------
biometricattribute|Yes|Array of the biometric attributes| | 

### Example Request
```JSON
{
  "id": "string",
  "version": "string",
  "metadata": {},
  "requesttime": "yyyy-MM-dd'T'HH:mm:ss.SSS'Z'",
  "request": {
	  "biometricattributes": [
				"biometricattribute",
				"languagecode":"string"
	                       ]
	    }
}
```
### Example Response
```JSON
{
  "id": "string",
  "version": "string",
  "metadata": {},
  "responsetime": "yyyy-MM-dd'T'HH:mm:ss.SSS'Z'",
  "errors": [{
      "errorCode": "string",
      "message": "string"
    }],
  "response":{
             "successfully_created_biometricattributes": [
		              {"biometricatributeid":"string"}
		              {"languagecode":"string"}
                          ]
             }
}
```
### Response codes
202

Description: Accepted

400

Description: Bad request

401

Description: Unauthorized

403

Description: Forbidden



# GET /getbiometricattributesbyauthtype/{languagecode}/{biometrictypeid}

This service will provides the service for the List of Biometrics based on the biometric authentication type. 


### Resource URL
### `GET /getbiometricattributesbyauthtype/{languagecode}/{biometrictypeid}`

### Resource details

Resource Details | Description
------------ | -------------
Response format | JSON
Requires Authentication | Yes

### Parameters
Name | Required | Description | Default Value | Example
-----|----------|-------------|---------------|--------
biometrictypeid|Yes|Id of the biometric auth type| | 

### Example Response
```JSON
{
  "id": "string",
  "version": "string",
  "metadata": {},
  "responsetime": "yyyy-MM-dd'T'HH:mm:ss.SSS'Z'",
  "errors": [{
      "errorCode": "string",
      "message": "string"
    }],
  "response":{
  "biometricattributes": [
                         {  
                           "code": "string",
	                   "name": "string",
	                   "description": "string",
                           "active": true
                         },
	                {
	                   "code": "string",
	                   "name": "string",
	                   "description": "string",
                           "active": true
                        }
                    ]
          }
}
```
200

Description: Success

400

Description: Bad request

401

Description: Unauthorized

404

Description: Not Found

## Failure details
Error Code | Error Message | Error Description
------------|------------------------------|-------------
KER-MSD-003 | Error occured while fetching BiometricAttributes | Fetch Issue
KER-MSD-004 | BiometricAttributes not found | Data Not Found
KER-APP-103 | Error occurred while inserting BiometricAttributes | Insertion Issue


# Locations Master API

* [POST /locations](#post-locations)
* [PUT /locations](#put-locations)
* [DELETE /locations/{locationcode}](#delete-locations-locationcode)
* [GET /locations/{langcode}](#get-locations-langcode)
* [GET /locations/{locationcode}/{langcode}](#get-locations-locationcode-langcode)
* [GET /locations/immediatechildren/{locationcode}/{langcode}](#get-locations-immediatechildren-locationcode-langcode)
* [GET /locations/locationhierarchy/{hierarchyname}](#get-locations-locationhierarchy-hierarchyname)
* [GET /locations/validate/{locationname}](#get-locations-validate-locationname)
* [GET /locations/all](#get-locations-all)

# `POST /locations`

### Resource URL
### `POST /locations`

### Resource details

Resource Details | Description
------------ | -------------
Response format | JSON
Requires Authentication | Yes

### Parameters
Name | Required | Description | Default Value | Example
-----|----------|-------------|---------------|--------
code|Yes|Code of the location| | 
name|Yes|Name of the location| | 
hierarchyLevel|Yes|Heirarchy level of the location| | 
hierarchyName|Yes|Hierarchy level name of the location| | 
parentLocCode|Yes|Parent location code of the location| | 
langCode|Yes|Language Code of the location| | 
isActive|Yes|Is this location active| | 


### Example Request
```JSON
{
  "id": "string",
  "version": "string",
  "metadata": {},
  "requesttime": "yyyy-MM-dd'T'HH:mm:ss.SSS'Z'",
  "request": {
                      "code": "string",
                      "hierarchyLevel": 0,
                      "hierarchyName": "string",
                      "isActive": true,
                      "langCode": "string",
                      "name": "string",
                      "parentLocCode": "string"
              }
}
```
### Example Response
```JSON
{
  "id": "string",
  "version": "string",
  "metadata": {},
  "responsetime": "yyyy-MM-dd'T'HH:mm:ss.SSS'Z'",
  "errors": [{
      "errorCode": "string",
      "message": "string"
    }],
  "response":{
             "code": "string",
             "isActive": true,
             "parentLocCode": "string"
             }
}
```
### Response codes
201

Description: Created

202

Description: Accepted

400

Description: Bad request

401

Description: Unauthorized

403

Description: Forbidden


# PUT /locations

### Resource URL
### `PUT /locations`

### Resource details

Resource Details | Description
------------ | -------------
Response format | JSON
Requires Authentication | Yes

### Parameters
Name | Required | Description | Default Value | Example
-----|----------|-------------|---------------|--------
code|Yes|Code of the location| | 
name|Yes|Name of the location| | 
hierarchyLevel|Yes|Heirarchy level of the location| | 
hierarchyName|Yes|Hierarchy level name of the location| | 
parentLocCode|Yes|Parent location code of the location| | 
langCode|Yes|Language Code of the location| | 
isActive|Yes|Is this location active| | 


### Example Request
```JSON
{
  "id": "string",
  "version": "string",
  "metadata": {},
  "requesttime": "yyyy-MM-dd'T'HH:mm:ss.SSS'Z'",
  "request": {
                      "code": "string",
                      "hierarchyLevel": 0,
                      "hierarchyName": "string",
                      "isActive": true,
                      "langCode": "string",
                      "name": "string",
                      "parentLocCode": "string"
            }
}
```
### Example Response
```JSON
{
  "id": "string",
  "version": "string",
  "metadata": {},
  "responsetime": "yyyy-MM-dd'T'HH:mm:ss.SSS'Z'",
  "errors": [{
      "errorCode": "string",
      "message": "string"
    }],
  "response":{
               "code": "string",
               "langCode:"string"

            }
}
```
### Response codes

202

Description: Accepted

400

Description: Bad request

401

Description: Unauthorized

403

Description: Forbidden



# DELETE /locations/{locationcode}

### Resource URL
### `DELETE /locations/{locationcode}`

### Resource details

Resource Details | Description
------------ | -------------
Response format | JSON
Requires Authentication | Yes


### Parameters
Name | Required | Description | Default Value | Example
-----|----------|-------------|---------------|--------
-NA-


### Example Response
```JSON
{
  "id": "string",
  "version": "string",
  "metadata": {},
  "responsetime": "yyyy-MM-dd'T'HH:mm:ss.SSS'Z'",
  "errors": [{
      "errorCode": "string",
      "message": "string"
    }],
  "response":  {
                "code": "string"
               }
}
```
### Response codes

202

Description: Accepted

400

Description: Bad request

401

Description: Unauthorized

403

Description: Forbidden



# GET /locations/{langcode}
Master data is required across the platform. 

This service will provides the service for the List of Locations. 



### Resource URL
### `GET /locations/{langcode}`

### Resource details

Resource Details | Description
------------ | -------------
Response format | JSON
Requires Authentication | Yes

### Parameters
Name | Required | Description | Default Value | Example
-----|----------|-------------|---------------|--------
-NA-

### Example Response
```JSON
{
  "id": "string",
  "version": "string",
  "metadata": {},
  "responsetime": "yyyy-MM-dd'T'HH:mm:ss.SSS'Z'",
  "errors": [{
      "errorCode": "string",
      "message": "string"
    }],
  "response":{
    "locations": [
        {
            "locationHierarchylevel": number,
            "locationHierarchyName": "string",
            "isActive":true
        },
        {
           "locationHierarchylevel": number,
           "locationHierarchyName": "string",
           "isActive":true
        }
    ]
  }
}
```
200

Description: Success

400

Description: Bad request

401

Description: Unauthorized

404

Description: Not Found

500

Description: Internal Server Error



# GET /locations/{locationcode}/{languagecode}
Master data is required across the platform. 

This service will provides the service for the List of Locations. 



### Resource URL
### `GET /locations/{locationcode}/{languagecode}`

### Resource details

Resource Details | Description
------------ | -------------
Response format | JSON
Requires Authentication | Yes

### Parameters
Name | Required | Description | Default Value | Example
-----|----------|-------------|---------------|--------
-NA-

### Example Response
```JSON
{
  "id": "string",
  "version": "string",
  "metadata": {},
  "responsetime": "yyyy-MM-dd'T'HH:mm:ss.SSS'Z'",
  "errors": [{
      "errorCode": "string",
      "message": "string"
    }],
  "response":{
       "locations": [
		    {
			"code":"string",
			"name":"string",
			"hierarchyLevel":"number",
			"hierarchyLevelName":"string",
			"parentLocCode":"",
			"langCode":"string",
			"isActive":"boolean",
			
		   },
		   {
			"code":"string",
			"name":"string",
			"hierarchyLevel":"number",
			"hierarchyLevelName":"string",
			"parentLocCode":"",
			"langCode":"string",
			"isActive":"boolean",
			
		   }
	     ] 
       }
}
```
200

Description: Success

400

Description: Bad request

401

Description: Unauthorized

404

Description: Not Found


# GET /locations/immediatechildren/{locationcode}/{languagecode}
Master data is required across the platform. 

This service will provides the service for the List of Locations. 



### Resource URL
### `GET /locations/immediatechildren/{locationcode}/{languagecode}`

### Resource details

Resource Details | Description
------------ | -------------
Response format | JSON
Requires Authentication | Yes

### Parameters
Name | Required | Description | Default Value | Example
-----|----------|-------------|---------------|--------
-NA-

### Example Response
```JSON
{
  "id": "string",
  "version": "string",
  "metadata": {},
  "responsetime": "yyyy-MM-dd'T'HH:mm:ss.SSS'Z'",
  "errors": [{
      "errorCode": "string",
      "message": "string"
    }],
  "response": {
          "locations": [ 
                       {
			"code":"string",
			"name":"string",
			"hierarchyLevel":"number",
			"hierarchyLevelName":"string",
			"parentLocCode":"",
			"langCode":"string",
			"isActive":"boolean"	
		      },
		      {
			"code":"string",
			"name":"string",
			"hierarchyLevel":"number",
			"hierarchyLevelName":"string",
			"parentLocCode":"",
			"langCode":"string",
			"isActive":"boolean"
		      }
	  ]
    }
}
```
200

Description: Success

400

Description: Bad request

401

Description: Unauthorized

404

Description: Not Found



# GET /locations/locationhierarchy/{hierarchyname}
Master data is required across the platform. 

This service will provides the service for the List of Locations based on the location hierarchy name. 



### Resource URL
### `GET /locations/locationhierarchy/{hierarchyname}`

### Resource details

Resource Details | Description
------------ | -------------
Response format | JSON
Requires Authentication | Yes

### Parameters
Name | Required | Description | Default Value | Example
-----|----------|-------------|---------------|--------
-NA-

### Example Response
```JSON
{
  "id": "string",
  "version": "string",
  "metadata": {},
  "responsetime": "yyyy-MM-dd'T'HH:mm:ss.SSS'Z'",
  "errors": [{
      "errorCode": "string",
      "message": "string"
    }],
  "response":{
           "locations": [
	         	{
			"code":"string",
			"name":"string",
			"hierarchyLevel":"number",
			"hierarchyLevelName":"string",
			"parentLocCode":"",
			"langCode":"string",
			"isActive":"boolean"	
		        },
		       {
			"code":"string",
			"name":"string",
			"hierarchyLevel":"number",
			"hierarchyLevelName":"string",
			"parentLocCode":"",
			"langCode":"string",
			"isActive":"boolean"
		       }
	        ]
        }
}
```
200

Description: Success

400

Description: Bad request

401

Description: Unauthorized

404

Description: Not Found




# GET /locations/validate/{locationname}

This service whether the given location name is valid or not. 


### Resource URL
### `GET /locations/validate/{locationname}`

### Resource details

Resource Details | Description
------------ | -------------
Response format | JSON
Requires Authentication | Yes

### Parameters
Name | Required | Description | Default Value | Example
-----|----------|-------------|---------------|--------
locationname|yes|This is the location name. | -NA- | 

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
    "status": "string"
  },
  "responsetime": "yyyy-MM-dd'T'HH:mm:ss.SSS'Z'",
  "version": "string"
}
```
200

Description: Success

403

Description: Forbidden

401

Description: Unauthorized

404

Description: Not Found

# GET /locations/all

This service will provide all locations

### Resource URL
### `GET /locations/all`

### Resource details

Resource Details | Description
------------ | -------------
Response format | JSON
Requires Authentication | Yes

### Parameters
Name | Required | Description | Default Value | Example
-----|----------|-------------|---------------|--------
pageNumber | optional | page no for the requested data | -NA- | 
pageSize | optional | page size for the requested data | -NA- | 
sortBy | optional | sort the requested data based on param value | -NA- | 
orderBy | optional | order the requested data based on param | -NA- | 

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
    "pageNo":"number",
	"totalPages":"number",
	"totalItems":"number",
	"data": [{
		"code":"string",
		"name":"string",
		"hierarchyLevel":"number",
		"hierarchyName":"string",
		"parentLocCode":"string",
		"langCode":"string"
	}]
  },
  "responsetime": "yyyy-MM-dd'T'HH:mm:ss.SSS'Z'",
  "version": "string"
}
```
200

Description: Success

403

Description: Forbidden

401

Description: Unauthorized

404

Description: Not Found

## Failure details
Error Code | Error Message | Error Description
------------|------------------------------|-------------
KER-MSD-025 | Error occured while fetching Location Hierarchy | Fetch Issue
KER-MSD-026 | Location not found | Data Not Found
KER-MSD-064 | Error occured while inserting location hierarchy details | Insertion Issue
KER-MSD-097 | Error occured wihile updating location hierarchy details | Update Issue
KER-MSD-098 | Error occured wihile deleting location hierarchy details | Deletion Issue
KER-MSD-028 | Location Hierarchy Level not found | Data Not Found
KER-MSD-027 | Error occured while fetching Location Hierarchy Levels | Fetch Issue
KER-MSD-389 | Parent location not found | Data Not Found
KER-MSD-385 | Location already exist under the hierarchy | insertion issue

# Packet Rejection Reasons Master API

* [POST /packetrejectionreasons/reasoncategory](#post-packetrejectionreasons-reasoncategory)
* [POST /packetrejectionreasons/reasonlist](#post-packetrejectionreasons-reasonlist)
* [GET /packetrejectionreasons](#get-packetrejectionreasons)
* [GET /packetrejectionreasons/{reasoncategorycode}/{languagecode}](#get-packetrejectionreasons-reasoncategorycode-languagecode)
* [GET /packetrejectionreasons/{id}/{languagecode}/{locationcode}](#get-packetrejectionreasons-id-languagecode-locationcode)

# POST /packetrejectionreasons/reasoncategory

This service will create the list of Packet Rejection Reasons which are used in the MOSIP platform. 

### Resource URL
### `POST /packetrejectionreasons/reasoncategory`

### Resource details

Resource Details | Description
------------ | -------------
Response format | JSON
Requires Authentication | Yes

### Parameters
Name | Required | Description | Default Value | Example
-----|----------|-------------|---------------|--------
code|Yes|Code of the reason category| | 
name|Yes|Name of the reason category| | 
description|Yes|description for the reason category| | 
isActive|Yes|whether the reason cateogry is in use| | 
langCode|Yes|language code of the reason category| | 


### Example Request
```JSON
{
  "id": "string",
  "version": "string",
  "metadata": {},
  "requesttime": "yyyy-MM-dd'T'HH:mm:ss.SSS'Z'",
  "request": {
		"code":"string",
		"name":"string",
		"description":"string",
		"lang_code":"string",
                "isActive":true
            }
}
```
### Example Response
```JSON
{
  "id": "string",
  "version": "string",
  "metadata": {},
  "responsetime": "yyyy-MM-dd'T'HH:mm:ss.SSS'Z'",
  "errors": [{
      "errorCode": "string",
      "message": "string"
    }],
  "response":{
	"code":"string",
	"lang_code":"string" 
           }
}
			
	
```
### Response codes

201

Description : Created

400

Description: Bad request

401

Description: Unauthorized

403

Description: Forbidden


# POST /packetrejectionreasons/reasonlist

This service will create the list of Packet Rejection Reasons which are used in the MOSIP platform. 

### Resource URL
### `POST /packetrejectionreasons/reasonlist`

### Resource details

Resource Details | Description
------------ | -------------
Response format | JSON
Requires Authentication | Yes

### Parameters
Name | Required | Description | Default Value | Example
-----|----------|-------------|---------------|--------
code|Yes|Code of the reason category| | 
name|Yes|Name of the reason category| | 
description|Yes|description for the reason category| |
rsnCatCode|Yes|foreign key reference from reason category code| | 
isActive|Yes|whether the reason cateogry is in use| | 
langCode|Yes|language code of the reason category| | 


### Example Request
```JSON
{
  "id": "string",
  "version": "string",
  "metadata": {},
  "requesttime": "yyyy-MM-dd'T'HH:mm:ss.SSS'Z'",
  "request": {
			{
				"code":"string",
				"name":"string",
				"description":"string",
                                "rsnCatCode":"string",
				"lang_code":"string",
                                "isActive":true
				
			}
			
             }
}
```
### Example Response
```JSON		
 {
  "id": "string",
  "version": "string",
  "metadata": {},
  "responsetime": "yyyy-MM-dd'T'HH:mm:ss.SSS'Z'",
  "errors": [{
      "errorCode": "string",
      "message": "string"
    }],
  "response":  {
                "code":"string",
                "lang_code":"string",
                "rsnCatCode":"string"
              }
}
			
	
```
### Response codes

201

Description : Created

400

Description: Bad request

401

Description: Unauthorized

403

Description: Forbidden


# GET /packetrejectionreasons
Master data is required across the platform. 

This service will provides the service for the List of Packet Rejection Reasons.



### Resource URL
### `GET /packetrejectionreasons`

### Resource details

Resource Details | Description
------------ | -------------
Response format | JSON
Requires Authentication | Yes

### Parameters
Name | Required | Description | Default Value | Example
-----|----------|-------------|---------------|--------
NA


### Example Response
```JSON
{
  "id": "string",
  "version": "string",
  "metadata": {},
  "responsetime": "yyyy-MM-dd'T'HH:mm:ss.SSS'Z'",
  "errors": [{
      "errorCode": "string",
      "message": "string"
    }],
  "response":{
	"reasonCategories" : [
		{
			"code":"string",
			"name":"string",
			"desc":"string",
			"lang_code":"string", 
                        "isActive":"string",
			"reasonLists" : [
				{
					"code":"string",
					"name":"string",
					"desc":"string",
                                        "rsnCatCode":"string",
                                        "isActive":true,
					"lang_code":"string"
				},
				{
					"code":"string",
					"name":"string",
					"desc":"string",
                                        "rsnCatCode":"string",
                                        "isActive":true,
					"lang_code":"string"
				}
			]
		}
	]	
   }
}
```
200

Description: Success

400

Description: Bad request

401

Description: Unauthorized

404

Description: Not Found


# GET /packetrejectionreasons/{reasoncategorycode}/{languagecode}

This service will provides the service for the List of Packet Rejection Reasons. 


### Resource URL
### `GET /packetrejectionreasons/{reasoncategorycode}/{languagecode}`

### Resource details

Resource Details | Description
------------ | -------------
Response format | JSON
Requires Authentication | Yes

### Parameters
Name | Required | Description | Default Value | Example
-----|----------|-------------|---------------|--------
NA


### Example Response
```JSON
{
  "id": "string",
  "version": "string",
  "metadata": {},
  "responsetime": "yyyy-MM-dd'T'HH:mm:ss.SSS'Z'",
  "errors": [{
      "errorCode": "string",
      "message": "string"
    }],
  "response":{
	"reasonCategories" : {
		"code":"string",
		"name":"string",
		"desc":"string",
		"lang_code":"string", 
                "isActive":true,
		"reason_lists" : [
			{
				"code":"string",
				"name":"string",
				"desc":"string",
                                "rsnCatCode":"string",
                                "isActive":true,
				"lang_code":"string"
			},
			{
				"code":"string",
				"name":"string",
				"desc":"string",
                                "rsnCatCode":"string",
                                "isActive":true,
				"lang_code":"string"
			}
		]
	}
  }
}
```
200

Description: Success

400

Description: Bad request

401

Description: Unauthorized

404

Description: Not Found


# GET /packetrejectionreasons/{id}/{languagecode}/{locationcode}

This service will provides the service for the List of Packet Rejection Reasons based on id, language and location code. 


### Resource URL
### `GET /packetrejectionreasons/{id}/{languagecode}/{locationcode}`

### Resource details

Resource Details | Description
------------ | -------------
Response format | JSON
Requires Authentication | Yes

### Parameters
Name | Required | Description | Default Value | Example
-----|----------|-------------|---------------|--------
packetrejectionreasonid|Yes|Code of the language| | 
packetrejectionreasondesc|Yes|Name of the language| | 


### Example Response
```JSON
{
  "id": "string",
  "version": "string",
  "metadata": {},
  "responsetime": "yyyy-MM-dd'T'HH:mm:ss.SSS'Z'",
  "errors": [{
      "errorCode": "string",
      "message": "string"
    }],
  "response":  {
  "packetrejectionreasons": [
				{ 
						"packetrejectionreasonid":"string",
						"packetrejectionreasondesc":"string",
						"languagecode":"string",
						"locationcode":"string"
				}, 
				{ 
						"packetrejectionreasonid":"string",
						"packetrejectionreasondesc":"string",
						"languagecode":"string"
						"locationcode":"string"
				}
			]
      }
}
```
200

Description: Success

400

Description: Bad request

401

Description: Unauthorized

404

Description: Not Found

## Failure details
Error Code | Error Message | Error Description
------------|------------------------------|-------------
KER-MSD-035 | Error occured while fetching Reasons | Fetch Issue
KER-MSD-036 | Reason not found | Data Not Found
KER-MSD-057 | Error occurred while inserting Reason details | Insertion Issue
KER-MSD-058 | Error occurred while inserting Reason details | Update Issue


# Packet On-hold Reasons Master API

* [POST /packetonholdreasons](#post-packetonholdreasons)
* [GET /packetonholdreasons](#get-packetonholdreasons)
* [GET /packetonholdreasons/{id}/{languagecode}](#get-packetonholdreasons-id-languagecode)

# POST /packetonholdreasons

This service will create the list of Packet On-hold Reasons which are used in the MOSIP platform. 

### Resource URL
### `POST /packetonholdreasons`

### Resource details

Resource Details | Description
------------ | -------------
Response format | JSON
Requires Authentication | Yes

### Parameters
Name | Required | Description | Default Value | Example
-----|----------|-------------|---------------|--------
packetonholdreasondesc|Yes|Name of the packet rejection reason| | 

### Example Request
```JSON
{
  "id": "string",
  "version": "string",
  "metadata": {},
  "requesttime": "yyyy-MM-dd'T'HH:mm:ss.SSS'Z'",
  "request": {
	  "packetonholdreasons": [
			{ 
				"packetonholdreasondesc":"string",
				"languagecode":"string"
			}, 
			{ 
				"packetonholdreasondesc":"string",
				"languagecode":"string"
			}
	  ]
	}
}
```
### Example Response
```JSON
{
  "id": "string",
  "version": "string",
  "metadata": {},
  "responsetime": "yyyy-MM-dd'T'HH:mm:ss.SSS'Z'",
  "errors": [{
      "errorCode": "string",
      "message": "string"
    }],
  "response": {
      "successfully_created_packetonholdreasons": [
			{ 
				"packetonholdreasonid":"string"
			}, 
			{ 
				"packetonholdreasonid":"string"
			}
                 ]
             }
  }
```
### Response codes
202

Description: Accepted

400

Description: Bad request

401

Description: Unauthorized

403

Description: Forbidden

# GET /packetonholdreasons
Master data is required across the platform. 

This service will provides the service for the List of Packet On-hold Reasons.



### Resource URL
### `GET /packetonholdreasons`

### Resource details

Resource Details | Description
------------ | -------------
Response format | JSON
Requires Authentication | Yes

### Parameters
Name | Required | Description | Default Value | Example
-----|----------|-------------|---------------|--------
packetonholdreasonid|Yes|Code of the language| | 
packetonholdreasondesc|Yes|Name of the language| | 


### Example Response
```JSON
{
  "id": "string",
  "version": "string",
  "metadata": {},
  "responsetime": "yyyy-MM-dd'T'HH:mm:ss.SSS'Z'",
  "errors": [{
      "errorCode": "string",
      "message": "string"
    }],
  "response":{
            "packetonholdreasons": [
				{ 
					"packetonholdreasonid":"string",
					"packetonholdreasondesc":"string",
					"languagecode":"string"
				}, 
				{ 
					"packetonholdreasonid":"string",
					"packetonholdreasondesc":"string",
					"languagecode":"string"
				}
			]
         }
}
```
200

Description: Success

400

Description: Bad request

401

Description: Unauthorized

404

Description: Not Found


# GET /packetonholdreasons/{id}/{languagecode}

This service will provides the service for the List of Packet On-hold Reasons. 


### Resource URL
### `GET /packetonholdreasons/{id}/{languagecode}`

### Resource details

Resource Details | Description
------------ | -------------
Response format | JSON
Requires Authentication | Yes

### Parameters
Name | Required | Description | Default Value | Example
-----|----------|-------------|---------------|--------
packetonholdreasonid|Yes|Code of the language| | 
packetonholdreasondesc|Yes|Name of the language| | 


### Example Response
```JSON
{
  "id": "string",
  "version": "string",
  "metadata": {},
  "responsetime": "yyyy-MM-dd'T'HH:mm:ss.SSS'Z'",
  "errors": [{
      "errorCode": "string",
      "message": "string"
    }],
  "response":    {
        "packetonholdreasons": [
				{ 
						"packetonholdreasonid":"string",
						"packetonholdreasondesc":"string",
						"languagecode":"string"
				}, 
				{ 
						"packetonholdreasonid":"string",
						"packetonholdreasondesc":"string",
						"languagecode":"string"
				}
			       ]
                  }
  }
```
200

Description: Success

400

Description: Bad request

401

Description: Unauthorized

404

Description: Not Found

# Documents Types API

* [POST /documenttype](#post-documenttype)
* [PUT /documenttype](#put-documenttype)
* [DELETE /documenttype](#delete-documenttype)
* [GET /documenttypes/{documentcategorycode}/{langcode}](#get-documenttypes-documentcategorycode-langcode)
* [GET /doccattypes/all](#get-doccattypes-all)
* [GET /documenttypes/{langcode}](#get-documenttypes-langcode)


# POST /documenttype

This service will create the list of Documents types which are used in the MOSIP platform. There is another service to map the document category and document type.

### Resource URL
### `POST /documenttype`

### Resource details

Resource Details | Description
------------ | -------------
Response format | JSON
Requires Authentication | Yes

### Parameters
Name | Required | Description | Default Value | Example
-----|----------|-------------|---------------|--------
code|Yes|Code of document type| | 
name|Yes|Name of the document type| | 
descr|Yes|Description of the document type| | 
lang_code|Yes|Language code of the document type| | 

### Example Request
```JSON
{
  "id": "string",
  "version": "string",
  "metadata": {},
  "requesttime": "yyyy-MM-dd'T'HH:mm:ss.SSS'Z'",
  "request": {
  "documenttypes": [
		{"code": "code", "name": "name", "descr":"descr", "lang_code":"lang_code", "is_active":"is_active"}
	     ]
          }
}
```
### Example Response
```JSON
{
  "id": "string",
  "version": "string",
  "metadata": {},
  "responsetime": "yyyy-MM-dd'T'HH:mm:ss.SSS'Z'",
  "errors": [{
      "errorCode": "string",
      "message": "string"
    }],
  "response": {
  "successfully_created_documenttypes": [
		{"code": "code", "name": "name", "descr":"descr", "lang_code":"lang_code", "is_active":"is_active"}
	]
       }
}
```

# PUT /documenttype

This service will update the list of Documents types which are used in the MOSIP platform. 

### Resource URL
### `PUT /documenttype`

### Resource details

Resource Details | Description
------------ | -------------
Response format | JSON
Requires Authentication | Yes

### Parameters
Name | Required | Description | Default Value | Example
-----|----------|-------------|---------------|--------
code|Yes|Code of document type| | 
name|Yes|Name of the document type| | 
descr|Yes|Description of the document type| | 
lang_code|Yes|Language code of the document type| | 

### Example Request
```JSON
{
  "id": "string",
  "version": "string",
  "metadata": {},
  "requesttime": "yyyy-MM-dd'T'HH:mm:ss.SSS'Z'",
  "request": {
  "documenttypes": [
		{"code": "code", "name": "name", "descr":"descr", "lang_code":"lang_code", "is_active":"is_active"},
         }
}
```
### Example Response
```JSON
{
  "id": "string",
  "version": "string",
  "metadata": {},
  "responsetime": "yyyy-MM-dd'T'HH:mm:ss.SSS'Z'",
  "errors": [{
      "errorCode": "string",
      "message": "string"
    }],
  "response": {
  "successfully_updated_documenttypes": [
		{"code": "code", "name": "name", "descr":"descr", "lang_code":"lang_code", "is_active":"is_active"}
	     ]
         }
}
```

# DELETE /documenttype

This service will delete document type. 

### Resource URL
### `DELETE /documenttype`

### Resource details

Resource Details | Description
------------ | -------------
Response format | JSON
Requires Authentication | Yes

### Parameters
Name | Required | Description | Default Value | Example
-----|----------|-------------|---------------|--------
code|Yes|Code of document type| | 

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
    "code": "string"
  },
  "responsetime": "yyyy-MM-dd'T'HH:mm:ss.SSS'Z'",
  "version": "string"
}
```

# GET /documenttypes/{documentcategorycode}/{langcode}

This service will provides the service for the valid doucment type avialbale for specific Document Category code


### Resource URL
### `GET /documenttypes/{documentcategorycode}/{langcode}`

### Resource details

Resource Details | Description
------------ | -------------
Response format | JSON
Requires Authentication | Yes

### Parameters
Name | Required | Description | Default Value | Example
-----|----------|-------------|---------------|--------

documentcategorycode |Yes| Code of document category | |
langcode | Yes | language code | |

### Example Response
```JSON
{
  "id": "string",
  "version": "string",
  "metadata": {},
  "responsetime": "yyyy-MM-dd'T'HH:mm:ss.SSS'Z'",
  "errors": [{
      "errorCode": "string",
      "message": "string"
    }],
  "response":   {
                "code": "string",
                "description": "string",
                "isActive": true,
                "langCode": "string",
                "name": "string"
                 }
  }
```
200

Description: Success

400

Description: Bad request

401

Description: Unauthorized

404

Description: Not Found


# GET /documenttypes/all

This service will provides the service for the List of documents types. 

### Resource URL
### `GET /documenttypes/all`

### Resource details

Resource Details | Description
------------ | -------------
Response format | JSON
Requires Authentication | Yes

### Parameters
Name | Required | Description | Default Value | Example
-----|----------|-------------|---------------|--------
pageNumber | optional | page no for the requested data | -NA- | 
pageSize | optional | page size for the requested data | -NA- | 
sortBy | optional | sort the requested data based on param value | -NA- | 
orderBy | optional | order the requested data based on param | -NA- | 

### Example Request
```JSON
-NA-
```
### Example Response
```JSON
{
  "id": "string",
  "version": "string",
  "metadata": {},
  "responsetime": "yyyy-MM-dd'T'HH:mm:ss.SSS'Z'",
  "errors": [{
      "errorCode": "string",
      "message": "string"
    }],
  "response":{
  "documenttypes": [
		{"code": "code", "name": "name", "descr":"descr", "lang_code":"lang_code", "is_active":"is_active"},
		{"code": "code", "name": "name", "descr":"descr", "lang_code":"lang_code", "is_active":"is_active"},
		{"code": "code", "name": "name", "descr":"descr", "lang_code":"lang_code", "is_active":"is_active"},
		{"code": "code", "name": "name", "descr":"descr", "lang_code":"lang_code", "is_active":"is_active"},
	          ]
             }
  }
```


# GET /documenttypes/{langcode}

This service will give back the document category and it's corresponding category types based on Individal type code, Age group type code and Gender type code. 

### Resource URL
### `GET /documenttypes/{langcode}`

### Resource details

Resource Details | Description
------------ | -------------
Response format | JSON
Requires Authentication | Yes

### Parameters
Name | Required | Description | Default Value | Example
-----|----------|-------------|---------------|--------
langcode |Yes| Code of langcode | |


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
    "documenttypes": [
      {
        "code": "string",
        "description": "string",
        "isActive": true,
        "langCode": "string",
        "name": "string"
      }
    ]
  },
  "responsetime": "yyyy-MM-dd'T'HH:mm:ss.SSS'Z'",
  "version": "string"
}
```

## Failure details
Error Code | Error Message | Error Description
------------|------------------------------|-------------
KER-MSD-015 | Error occured while fetching Document Types | Fetch Issue
KER-MSD-118 | Document Type not found | Data Not Found
KER-MSD-052 | Error occured while inserting Document Type details | Insertion Issue
KER-MSD-091 | Error occur while updating Document Type details | Update Issue
KER-MSD-124 | Cannot delete dependency found | Deletion Issue
KER-MSD-092 | Error occured while deleting Document Type details | Deletion Issue
KER-MSD-093 | Can not reactivate the document type | Activation/Deactivation issue
KER-MSD-094 | Can not deactivate the deactivated document type | Activation/Deactivation issue
KER-MSD-095 | Mendatory Parameter is missing in document type details | parameter missing


# Machine Types Master API

* [POST /machinetypes](#post-machinetypes)
* [GET /machinetypes](#get-machinetypes)
* [GET /machinetypes/{languagecode}](#get-machinetypes-languagecode)

# POST /machinetypes

This service will create the list of Machine types which are used in the MOSIP platform. 

### Resource URL
### `POST /machinetypes`

### Resource details

Resource Details | Description
------------ | -------------
Response format | JSON
Requires Authentication | Yes

### Parameters
Name | Required | Description | Default Value | Example
-----|----------|-------------|---------------|--------
machinetypecode|Yes|Code of the machine type| | 
machinename|Yes|Name of the machine type| | 
description|Yes|Description of the machine type| | 
languagecode|Yes|Language code of the machine type| | 
isactive|Yes|Is the machine type active?| | 

### Example Request
```JSON
{
  "id": "string",
  "version": "string",
  "metadata": {},
  "requesttime": "yyyy-MM-dd'T'HH:mm:ss.SSS'Z'",
  "request": {
       "code": "string",
       "description": "string",
      "isActive": true,
      "langCode": "string",
      "name": "string"
  }
}
```
### Example Response
```JSON
{
  "id": "string",
  "version": "string",
  "metadata": {},
  "responsetime": "yyyy-MM-dd'T'HH:mm:ss.SSS'Z'",
  "errors": [{
      "errorCode": "string",
      "message": "string"
    }],
  "response": {
            "code": "string",
            "langCode": "string"
             }
}
```
### Response codes
202

Description: Accepted

400

Description: Bad request

401

Description: Unauthorized

403

Description: Forbidden

# GET /machinetypes

This service will provides the service to fetch the complete List of machine types with the machine details. 

### Resource URL
### `GET /machinetypes`

### Resource details

Resource Details | Description
------------ | -------------
Response format | JSON
Requires Authentication | Yes

### Parameters
Name | Required | Description | Default Value | Example
-----|----------|-------------|---------------|--------
-NA-


### Example Response
```JSON
{
  "id": "string",
  "version": "string",
  "metadata": {},
  "responsetime": "yyyy-MM-dd'T'HH:mm:ss.SSS'Z'",
  "errors": [{
      "errorCode": "string",
      "message": "string"
    }],
  "response":{
  "machinetypes": [
				{ 
					"machinetypecode":"string",
					"machinename":"string",	
					"description":"string",
					"languagecode":"boolean",
					"isactive":"string" 
				}, 
				{ 
					"machinetypecode":"string",
					"machinename":"string",	
					"description":"string",
					"languagecode":"boolean",
					"isactive":"string" 
				}
			]
         }
}
```
200

Description: Success

400

Description: Bad request

401

Description: Unauthorized

404

Description: Not Found


# GET /machinetypes/{languagecode}

This service will provides the service to fetch the List of machines with the machine details based on the language code.

### Resource URL
### `GET /machinetypes/{languagecode}`

### Resource details

Resource Details | Description
------------ | -------------
Response format | JSON
Requires Authentication | Yes

### Parameters
Name | Required | Description | Default Value | Example
-----|----------|-------------|---------------|--------
-NA-


### Example Response
```JSON
{
  "id": "string",
  "version": "string",
  "metadata": {},
  "responsetime": "yyyy-MM-dd'T'HH:mm:ss.SSS'Z'",
  "errors": [{
      "errorCode": "string",
      "message": "string"
    }],
  "response":  {
           "machines": [
				{ 
					"machinetypecode":"string",
					"machinename":"string",	
					"description":"string",
					"languagecode":"boolean",
					"isactive":"string" 
				}, 
				{ 
					"machinetypecode":"string",
					"machinename":"string",	
					"description":"string",
					"languagecode":"boolean",
					"isactive":"string" 
				}
			]
           }
 }
```
200

Description: Success

400

Description: Bad request

401

Description: Unauthorized

404

Description: Not Found

## Failure details
Error Code | Error Message | Error Description
------------|------------------------------|-------------
KER-MSD-061 | Error occurred while inserting Machine Type details | Insertion Issue
KER-MSD-062 | Error occurred while fetching Machine Type details | Fetch Issue
KER-MSD-063 | Machine Type Not Found | Data Not Found

# Machine Specifications

* [POST /machinespecifications](#post-machinespecifications)
* [PUT /machinespecifications](#put-machinespecifications)
* [DELETE /machinespecifications/{id}](#delete-machinespecifications-id)
* [GET /machinespecifications/all](#get-machinespecifications-all)
* [GET /machinespecifications/{lang_code](#get-machinespecifications-lang_code)


# POST /machinespecifications

This service will create a Machine Specification which are used in the MOSIP platform. 

### Resource URL
### `POST /machinespecifications`

### Resource details

Resource Details | Description
------------ | -------------
Response format | JSON
Requires Authentication | Yes

### Parameters
Name | Required | Description | Default Value | Example
-----|----------|-------------|---------------|--------
id|Yes|ID of the Machine Specification| | 
name|Yes|Name of the machine Specification| | 
brand|Yes|Brand of the machine specification| | 
model|Yes|Model of the machine specification| | 
mtyp_code|Yes|Machine type code of the machine specification| | 
min_driver_ver|Yes|Minimum driver version required for the machine specification| | 
descr|Yes|Description of the machine specification| | 
lang_code|Yes|Language of the machine specification| | 
is_active|Yes|Is the Machine Specification active| | 

### Example Request
```JSON
{
  "id": "string",
  "version": "string",
  "metadata": {},
  "requesttime": "yyyy-MM-dd'T'HH:mm:ss.SSS'Z'",
  "request": {
    "brand": "string",
    "description": "string",
    "id": "string",
    "isActive": true,
    "langCode": "string",
    "machineTypeCode": "string",
    "minDriverversion": "string",
    "model": "string",
    "name": "string"
    }
}
```
### Example Response
```JSON
{
  "id": "string",
  "version": "string",
  "metadata": {},
  "responsetime": "yyyy-MM-dd'T'HH:mm:ss.SSS'Z'",
  "errors": [{
      "errorCode": "string",
      "message": "string"
    }],
  "response":  {
              "id": "string"
               }
}
```

# PUT /machinespecifications

This service will update a Machine Specification which are used in the MOSIP platform. 


### Resource URL
### `PUT /machinespecifications`

### Resource details

Resource Details | Description
------------ | -------------
Response format | JSON
Requires Authentication | Yes

### Parameters
Name | Required | Description | Default Value | Example
-----|----------|-------------|---------------|--------
id|Yes|ID of the Machine Specification| | 
lang_code|Yes|Language code of the Machine Specification| | 

### Example Request
```JSON
{
  "id": "string",
  "version": "string",
  "metadata": {},
  "requesttime": "yyyy-MM-dd'T'HH:mm:ss.SSS'Z'",
  "request":  {
    "brand": "string",
    "description": "string",
    "id": "string",
    "isActive": true,
    "langCode": "string",
    "machineTypeCode": "string",
    "minDriverversion": "string",
    "model": "string",
    "name": "string"
  }
}
```
### Example Response
```JSON
{
  "id": "string",
  "version": "string",
  "metadata": {},
  "responsetime": "yyyy-MM-dd'T'HH:mm:ss.SSS'Z'",
  "errors": [{
      "errorCode": "string",
      "message": "string"
    }],
  "response":  {
             "id": "string"
             }
}
```


# DELETE /machinespecifications/{id}

This service deletes a Machine Specification from the Machine Specifications master module. 

### Resource URL
### `DELETE /machinespecifications/{id}`

### Resource details

Resource Details | Description
------------ | -------------
Response format | JSON
Requires Authentication | Yes

### Parameters
Name | Required | Description | Default Value | Example
-----|----------|-------------|---------------|--------
id|Yes|ID of the Machine Specification| | 


### Example Response
```JSON
{
  "id": "string",
  "version": "string",
  "metadata": {},
  "responsetime": "yyyy-MM-dd'T'HH:mm:ss.SSS'Z'",
  "errors": [{
      "errorCode": "string",
      "message": "string"
    }],
  "response":  {
                "id": "string"
              }
 }
```

# GET /machinespecifications/all

This service will provides the list of all Machine Specifications in all languages. 


### Resource URL
### `GET /machinespecifications/all`

### Resource details

Resource Details | Description
------------ | -------------
Response format | JSON
Requires Authentication | Yes

### Parameters
Name | Required | Description | Default Value | Example
-----|----------|-------------|---------------|--------
orderBy | optional | order the requested data based on param ||
pageNumber | optional | page no for the requested data ||
pageSize | optional | page size for the requested data ||
sortBy | optional | sort the requested data based on param value ||

### Example Request
```JSON
-NA-
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
    "data": [
      {
        "brand": "string",
        "createdBy": "string",
        "description": "string",
        "id": "string",
        "isActive": true,
        "isDeleted": true,
        "langCode": "string",
        "machineTypeCode": "string",
        "machineTypeName": "string",
        "minDriverversion": "string",
        "model": "string",
        "name": "string",
        "updatedBy": "string"
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


# GET /machinespecifications/{lang_code}

This service will provides the list of all Machine Specifications in a specific language. 


### Resource URL
### `GET /machinespecifications/{lang_code}`

### Resource details

Resource Details | Description
------------ | -------------
Response format | JSON
Requires Authentication | Yes

### Parameters
Name | Required | Description | Default Value | Example
-----|----------|-------------|---------------|--------
-NA-

### Example Request
```JSON
-NA-
```

### Example Response
```JSON
{
  "id": "string",
  "version": "string",
  "metadata": {},
  "responsetime": "yyyy-MM-dd'T'HH:mm:ss.SSS'Z'",
  "errors": [{
      "errorCode": "string",
      "message": "string"
    }],
  "response":   {
	"id":"KJDS9",
	"name":"Laptop",
	"brand":"Hewlett Packard",
	"model":"L34-324",
	"mtyp_code":"GEW8",
	"min_driver_ver":"1.4",
	"descr":"This is a medium configuration",
	"lang_code":"eng",
	"is_active":true
   }
}
```

### Response codes
202

Description: Accepted

400

Description: Bad request

401

Description: Unauthorized

403

Description: Forbidden

## Failure details
Error Code | Error Message | Error Description
------------|------------------------------|-------------
KER-MSD-087 | Error occurred while fetching Machine Specification details | Fetch Issue
KER-MSD-117 | Machine Specification not found | Data Not Found
KER-MSD-062 | Error occurred while inserting Machine Specification details | Insertion Issue
KER-MSD-085 | Error occurred while updating Machine Specification details | Update Issue
KER-MSD-086 | Error occurred while deleteding Machine Specification details | Deletion Issue
KER-MSD-122 | Cannot delete dependency found | Dependency Issue
KER-MSD-349 | No Machine exist for Machine Type name | Data Not Found

# Registration Center User Machine Mapping API

* [POST /registrationmachineusermappings](#post-registrationmachineusermappings)
* [GET /getregistrationmachineusermappinghistory/{effdtimes}/{registrationcenterid}/{machineid}/{userid}(#get-getregistrationmachineusermappinghistory-effdtimes-registrationcenterid-machineid-userid)
* [PUT /registrationmachineusermappings](#put-registrationmachineusermappings)


## POST /registrationmachineusermappings

This service will create a Registration Center-User-Machine Mapping which are used in the MOSIP platform. 

### Resource URL
### `POST /registrationmachineusermappings`

### Resource details

Resource Details | Description
------------ | -------------
Response format | JSON
Requires Authentication | Yes

### Parameters
Name | Required | Description | Default Value | Example
-----|----------|-------------|---------------|--------
cntrId|Yes|Registration Center Id for request| | 
machineId|Yes|Machine Id for request| | 
usrId|Yes|User Id for request| | 
isActive|Yes|Mapping is active or not| | 

### Example Request
```JSON
{
  "id": "string",
  "version": "string",
  "metadata": {},
  "requesttime": "yyyy-MM-dd'T'HH:mm:ss.SSS'Z'",
  "request": {
    "cntrId": "RC001",
    "isActive": true,
    "machineId": "MC001",
    "usrId": "QC001"
  }
}
```
### Example Response
```JSON
{
  "id": "string",
  "version": "string",
  "metadata": {},
  "responsetime": "yyyy-MM-dd'T'HH:mm:ss.SSS'Z'",
  "errors": [{
      "errorCode": "string",
      "message": "string"
    }],
  "response": {
            "cntrId": "RC001",
            "machineId": "MC001",
            "usrId": "QC001"
            }
}
```
### Response codes
201

Description: Created

400

Description: Bad request

401

Description: Unauthorized

403

Description: Forbidden

## GET /getregistrationmachineusermappinghistory/{effdtimes}/{registrationcenterid}/{machineid}/{userid}

This service will provides the service for the Center-User-Machine with their history. 


### Resource URL
### `GET /getregistrationmachineusermappinghistory/{effdtimes}/{registrationcenterid}/{machineid}/{userid}`

### Resource details

Resource Details | Description
------------ | -------------
Response format | JSON
Requires Authentication | Yes

### Parameters
Name | Required | Description | Default Value | Example
-----|----------|-------------|---------------|--------
ID|Yes|Machine History Id|
effdtimes|Yes|Effective Date and Time of the Machine|
registrationcenterid|Yes|Registration Center Id|
machineid|Yes|Machine Id |
userid|Yes|User Id|

### Example Response
```JSON
{
  "id": "string",
  "version": "string",
  "metadata": {},
  "responsetime": "yyyy-MM-dd'T'HH:mm:ss.SSS'Z'",
  "errors": [{
      "errorCode": "string",
      "message": "string"
    }],
  "response":  {
      "registrationCenters": [
             {
              "cntrId": "string",
              "effectivetimes": "yyyy-MM-dd'T'HH:mm:ss.SSS'Z'",
              "isActive": true,
              "langCode": "string",
              "machineId": "string",
              "usrId": "string"
             }
        ]
    }
}
```
200

Description: Success

400

Description: Bad request

401

Description: Unauthorized

404

Description: Not Found

## PUT /registrationmachineusermappings

This service will create or update a Registration Center-User-Machine Mapping which are used in the MOSIP platform. 

### Resource URL
### `PUT /registrationmachineusermappings`

### Resource details

Resource Details | Description
------------ | -------------
Response format | JSON
Requires Authentication | Yes

### Parameters
Name | Required | Description | Default Value | Example
-----|----------|-------------|---------------|--------
cntrId|Yes|Registration Center Id for request| | 
machineId|Yes|Machine Id for request| | 
usrId|Yes|User Id for request| | 
isActive|Yes|Mapping is active or not| | 

### Example Request
```JSON
{
  "id": "string",
  "version": "string",
  "metadata": {},
  "requesttime": "yyyy-MM-dd'T'HH:mm:ss.SSS'Z'",
  "request": {
      "cntrId": "RC001",
      "isActive": true,
      "langCode": "string",
      "machineId": "MC001",
      "usrId": "QC001"
  }
}
```
### Example Response
```JSON
{
  "id": "string",
  "version": "string",
  "metadata": {},
  "responsetime": "yyyy-MM-dd'T'HH:mm:ss.SSS'Z'",
  "errors": [{
      "errorCode": "string",
      "message": "string"
    }],
  "response": {
    "mapped": [
      {
        "cntrId": "string",
        "machineId": "string",
        "usrId": "string"
      }
    ],
    "notmapped": [
       {
        "cntrId": "string",
        "machineId": "string",
        "usrId": "string"
      }
    ]
  }
}
```
### Response codes
201

Description: Created

400

Description: Bad request

401

Description: Unauthorized

403

Description: Forbidden


# Registration Center Machine API

* [POST /registrationcentermachine](#post-registrationcentermachine)
* [DELETE /registrationcentermachine/{regCenterId}/{machineId}](#delete-registrationcentermachine-regcenterid-machineid)
* [GET /registrationcentermachine/unmap/{regCenterId}/{machineId}](#get-registrationcentermachine-regcenterid-machineid)
* [GET /registrationcentermachine/map/{regCenterId}/{machineId}](#delete-registrationcentermachine-regcenterid-machineid)

## POST /registrationcentermachine
Master data is required across the platform. 

This service will create the mapping of registration canter and machine in the RegistrationCenterMachine Master module. 

### Resource URL
### `POST /registrationcentermachine`

### Resource details

Resource Details | Description
------------ | -------------
Response format | JSON
Requires Authentication | Yes

### Parameters
Name | Required | Description | Default Value | Example
-----|----------|-------------|---------------|--------
machineId|Yes|Available machine id| | 
regCenterId|Yes|Available registration center| | 

### Example Request
```JSON  
{
  "id": "string",
  "version": "string",
  "metadata": {},
  "requesttime": "yyyy-MM-dd'T'HH:mm:ss.SSS'Z'",
  "request": {
    "isActive": true,
    "langCode": "string",
    "machineId": "MC001",
    "regCenterId": "RC001"
  }
}


```
### Example Response
```JSON
 {
  "id": "string",
  "version": "string",
  "metadata": {},
  "responsetime": "yyyy-MM-dd'T'HH:mm:ss.SSS'Z'",
  "errors": [{
      "errorCode": "string",
      "message": "string"
    }],
  "response": {
      "machineId": "string",
      "regCenterId": "string"
  }
}
```
### Response codes
201

Description: Created

400

Description: Bad request

401

Description: Unauthorized

403

Description: Forbidden

500

Description: Internal Server Error 

## DELETE /registrationcentermachine/{regCenterId}/{machineId}

This service will provides the service for delete mapping of  Center-Machine. 


### Resource URL
### `DELETE /registrationcentermachine/{regCenterId}/{machineId}`

### Resource details

Resource Details | Description
------------ | -------------
Response format | JSON
Requires Authentication | Yes

### Parameters
Name | Required | Description | Default Value | Example
-----|----------|-------------|---------------|--------
regCenterId|Yes|Registration Center Id|
machineId|Yes|Machine Id |


### Example Response
```JSON
{
  "id": "string",
  "version": "string",
  "metadata": {},
  "responsetime": "yyyy-MM-dd'T'HH:mm:ss.SSS'Z'",
  "errors": [{
      "errorCode": "string",
      "message": "string"
    }],
  "response":  {
  "machineId": "MC001",
  "regCenterId": "RC001"
   }
}
```
200

Description: Success

400

Description: Bad request

401

Description: Unauthorized

404

Description: Not Found

## GET /registrationcentermachine/unmap/{regCenterId}/{machineId}

This service will provides the service for delete mapping of  Center-Machine. 


### Resource URL
### `GET /registrationcentermachine/unmap/{regCenterId}/{machineId}`

### Resource details

Resource Details | Description
------------ | -------------
Response format | JSON
Requires Authentication | Yes

### Parameters
Name | Required | Description | Default Value | Example
-----|----------|-------------|---------------|--------
regCenterId|Yes|Registration Center Id|
machineId|Yes|Machine Id |


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
    "message": "string",
    "status": "string"
  },
  "responsetime": "yyyy-MM-dd'T'HH:mm:ss.SSS'Z'",
  "version": "string"
}
```
200

Description: Success

400

Description: Bad request

401

Description: Unauthorized

404

Description: Not Found

## GET /registrationcentermachine/unmap/{regCenterId}/{machineId}

This service will unmap the mapping of  Center-Machine. 


### Resource URL
### `GET /registrationcentermachine/unmap/{regCenterId}/{machineId}`

### Resource details

Resource Details | Description
------------ | -------------
Response format | JSON
Requires Authentication | Yes

### Parameters
Name | Required | Description | Default Value | Example
-----|----------|-------------|---------------|--------
regCenterId|Yes|Registration Center Id|
machineId|Yes|Machine Id |


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
    "message": "string",
    "status": "string"
  },
  "responsetime": "yyyy-MM-dd'T'HH:mm:ss.SSS'Z'",
  "version": "string"
}
```
200

Description: Success

400

Description: Bad request

401

Description: Unauthorized

404

Description: Not Found

## GET /registrationcentermachine/map/{regCenterId}/{machineId}

This service will map the mapping of  Center-Machine. 


### Resource URL
### `GET /registrationcentermachine/map/{regCenterId}/{machineId}`

### Resource details

Resource Details | Description
------------ | -------------
Response format | JSON
Requires Authentication | Yes

### Parameters
Name | Required | Description | Default Value | Example
-----|----------|-------------|---------------|--------
regCenterId|Yes|Registration Center Id|
machineId|Yes|Machine Id |


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
    "message": "string",
    "status": "string"
  },
  "responsetime": "yyyy-MM-dd'T'HH:mm:ss.SSS'Z'",
  "version": "string"
}
```
200

Description: Success

400

Description: Bad request

401

Description: Unauthorized

404

Description: Not Found

## Failure details
Error Code | Error Message | Error Description
------------|------------------------------|-------------
KER-MSD-074 | Error occurred while inserting a mapping of Machine and Center | Insertion Issue
KER-MSD-114 | Mapping for Machine and Center not found | Data Not Found
KER-MSD-106 | Error occurred while deleting a mapping of Machine and Center | Deletion Issue
KER-MSD-xx | Error occurred while fetching Center Machine details | Fetch Issue
KER-MSD-411 | Admin not authorized to map/un-map this Registration Center or Machine | Authorization Issue
KER-MSD-XXX | Already is in inactive status | -NA-
KER-MSD-XXX | Registration center mapped to machine is decommisioned | -NA-
KER-MSD-XXX | Registration center already mapped to machine and is active | -NA-
KER-MSD-XXX | Registration center and machine is not in same hierarchy | -NA-
KER-MSD-030 | Machine not Found | Data Not found

# Registration Center Device API

* [POST /registrationcenterdevice](#post-registrationcenterdevice)
* [DELETE /registrationcenterdevice/{regCenterId}/{deviceId}](#delete-registrationcenterdevice-regcenterid-deviceid)

## POST /registrationcenterdevice
Master data is required across the platform. 

This service will create the mapping of registration canter and device in the RegistrationCenterDevice Master module. 

### Resource URL
### `POST /registrationcenterdevice`

### Resource details

Resource Details | Description
------------ | -------------
Response format | JSON
Requires Authentication | Yes

### Parameters
Name | Required | Description | Default Value | Example
-----|----------|-------------|---------------|--------
deviceId|Yes|Available device id| | 
regCenterId|Yes|Available registration center| | 

### Example Request
```JSON  
{
  "id": "string",
  "version": "string",
  "metadata": {},
  "requesttime": "yyyy-MM-dd'T'HH:mm:ss.SSS'Z'",
  "request": {
     "deviceId": "string",
    "isActive": true,
    "langCode": "string",
    "regCenterId": "string"
  }
}


```
### Example Response
```JSON
 {
  "id": "string",
  "version": "string",
  "metadata": {},
  "responsetime": "yyyy-MM-dd'T'HH:mm:ss.SSS'Z'",
  "errors": [{
      "errorCode": "string",
      "message": "string"
    }],
  "response":   {
        "deviceId": "string",
        "regCenterId": "string"
  }
}
```
### Response codes
201

Description: Created

400

Description: Bad request

401

Description: Unauthorized

403

Description: Forbidden

500

Description: Internal Server Error 

## DELETE/registrationcenterdevice/{regCenterId}/{deviceId}

This service will provides the service for delete mapping of  Device-Machine. 


### Resource URL
### `DELETE /registrationcenterdevice/{regCenterId}/{deviceId}`

### Resource details

Resource Details | Description
------------ | -------------
Response format | JSON
Requires Authentication | Yes

### Parameters
Name | Required | Description | Default Value | Example
-----|----------|-------------|---------------|--------
regCenterId|Yes|Registration Center Id|
deviceId|Yes|Device Id |


### Example Response
```JSON
{
  "id": "string",
  "version": "string",
  "metadata": {},
  "responsetime": "yyyy-MM-dd'T'HH:mm:ss.SSS'Z'",
  "errors": [{
      "errorCode": "string",
      "message": "string"
    }],
  "response":   {
           "deviceId": "DV001",
          "regCenterId": "RC001"
    }
}
```
200

Description: Success

400

Description: Bad request

401

Description: Unauthorized

404

Description: Not Found


# Registration Center Machine Device API

* [POST /registrationcentermachinedevice](#post-registrationcentermachinedevice)
* [DELETE /registrationcentermachinedevice/{regcenterid}/{machineid}/{deviceid}](#delete-registrationcentermachinedevice-regcenterid-machineid-deviceid)

## POST /registrationcentermachinedevice
Master data is required across the platform. 

This service will create the mapping of registration canter, machine and device in the RegistrationCenterMachineDevice Master module. 

### Resource URL
### `POST /registrationcentermachinedevice`

### Resource details

Resource Details | Description
------------ | -------------
Response format | JSON
Requires Authentication | Yes

### Parameters
Name | Required | Description | Default Value | Example
-----|----------|-------------|---------------|--------
machineId|Yes|Available machine id| | 
regCenterId|Yes|Available registration center| | 
deviceId|Yes|Available device id| | 

### Example Request
```JSON  
{
  "id": "string",
  "version": "string",
  "metadata": {},
  "requesttime": "yyyy-MM-dd'T'HH:mm:ss.SSS'Z'",
  "request": {
    "deviceId": "string",
    "isActive": true,
    "langCode": "string",
    "machineId": "string",
    "regCenterId": "string"
  }
}


```
### Example Response
```JSON
 {
  "id": "string",
  "version": "string",
  "metadata": {},
  "responsetime": "yyyy-MM-dd'T'HH:mm:ss.SSS'Z'",
  "errors": [{
      "errorCode": "string",
      "message": "string"
    }],
  "response":   {
   "deviceId": "string",
   "machineId": "string",
   "regCenterId": "string"
  }
}
```
### Response codes
201

Description: Created

400

Description: Bad request

401

Description: Unauthorized

403

Description: Forbidden

500

Description: Internal Server Error 


## DELETE /registrationcentermachinedevice/{regcenterid}/{machineid}/{deviceid}
Master data is required across the platform. 

This service will delete the mapping of registration canter, machine and device in the RegistrationCenter-Machine-Device Master module. 

### Resource URL
### `DELETE /registrationcentermachinedevice/{regcenterid}/{machineid}/{deviceid}`

### Resource details

Resource Details | Description
------------ | -------------
Response format | JSON
Requires Authentication | Yes

### Parameters
Name | Required | Description | Default Value | Example
-----|----------|-------------|---------------|--------
NA


### Example Response
```JSON
 {
  "id": "string",
  "version": "string",
  "metadata": {},
  "responsetime": "yyyy-MM-dd'T'HH:mm:ss.SSS'Z'",
  "errors": [{
      "errorCode": "string",
      "message": "string"
    }],
  "response":  {
   "deviceId": "string",
   "machineId": "string",
   "regCenterId": "string"
  }
}
```
### Response codes

400

Description: Bad request

401

Description: Unauthorized

403

Description: Forbidden

500

Description: Internal Server Error 



# Device Types Master API

* [POST /devicetypes](#post-devicetypes)
* [GET /devicetypes/all](#get-devicetypes-all)

## POST /devicetypes

This service will create the list of Device types which are used in the MOSIP platform. 

### Resource URL
### `POST /devicetypes`

### Resource details

Resource Details | Description
------------ | -------------
Response format | JSON
Requires Authentication | Yes

### Parameters
Name | Required | Description | Default Value | Example
-----|----------|-------------|---------------|--------
code|Yes|Code of the device type| | 
name|Yes|Name of the device type| | 
description|Yes|Description of the device type| | 
langCode|Yes|Language code of the device type| | 
isactive|Yes|Is the device type active?| | 
createdBy|Yes|created by?| |
isDeleted|Yes|Is the device type deleted?| |
updatedBy|Yes|updated by?| |
### Example Request
```JSON
{
  "id": "string",
  "metadata": {},
  "request": {
    "code": "string",
    "createdBy": "string",
    "description": "string",
    "isActive": true,
    "isDeleted": true,
    "langCode": "string",
    "name": "string",
    "updatedBy": "string"
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
    "code": "string",
    "langCode": "string"
  },
  "responsetime": "yyyy-MM-dd'T'HH:mm:ss.SSS'Z'",
  "version": "string"
}
```
### Response codes
201

Description: Created

400

Description: Bad request

401

Description: Unauthorized

403

Description: Forbidden

404

Description: Not found

500

Description: Internal Error

## GET /devicetypes/all

This service will get all the devicetypes. 

### Resource URL
### `GET /devicetypes/all`

### Resource details

Resource Details | Description
------------ | -------------
Response format | JSON
Requires Authentication | Yes

### Parameters
Name | Required | Description | Default Value | Example
-----|----------|-------------|---------------|--------
orderBy|optional|order the requested data based on param| | 
pageNumber|optional|page no for the requested data| | 
pageSize|optional|page size for the requested data| | 
sortBy|optional|sort the requested data based on param value| | 


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
        "code": "string",
        "createdBy": "string",
        "description": "string",
        "isActive": true,
        "isDeleted": true,
        "langCode": "string",
        "name": "string",
        "updatedBy": "string"
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

Description: Internal Error

## Failure details
Error Code | Error Message | Error Description
------------|------------------------------|-------------
KER-MSD-054 | Error occurred while fetching Device Type details | Fetch Issue
KER-MSD-003 | Required Device Type detail Not Found | Data Not Found
KER-MSD-053 | Error occurred while inserting Device Type details | Insertion Issue
KER-MSD-002 | Error occured while mapping Device Type details | Data Mapping Issue


# Device Specifications

* [POST /devicespecifications](#post-devicespecifications)
* [PUT /devicespecifications](#put-devicespecifications)
* [DELETE /devicespecifications/{id}](#delete-devicespecifications-id)
* [GET /devicespecifications/{langcode}/{devicetypecode}](#get-devicespecifications-langcode-devicetypecode)
* [GET /devicespecifications/{langcode}](#get-devicespecifications-langcode)

# POST /devicespecifications

This service will create a Device Specification which are used in the MOSIP platform. 

### Resource URL
### `POST /devicespecifications`

### Resource details

Resource Details | Description
------------ | -------------
Response format | JSON
Requires Authentication | Yes

### Parameters
Name | Required | Description | Default Value | Example
-----|----------|-------------|---------------|--------
id|Yes|ID of the Device Specification| | 
name|Yes|Name of the Device Specification| | 
brand|Yes|Brand of the Device specification| | 
model|Yes|Model of the Device specification| | 
dtyp_code|Yes|device type code of the Device specification| | 
min_driver_ver|Yes|Minimum driver version required for the Device specification| | 
descr|Yes|Description of the Device specification| | 
lang_code|Yes|Language of the Device specification| | 
is_active|Yes|Is the Device Specification active| | 

### Example Request
```JSON
{
  "id": "string",
  "version": "string",
  "metadata": {},
  "requesttime": "yyyy-MM-dd'T'HH:mm:ss.SSS'Z'",
  "request": {
    "brand": "string",
    "description": "string",
    "id": "string",
    "isActive": true,
    "langCode": "string",
    "DeviceTypeCode": "string",
    "minDriverversion": "string",
    "model": "string",
    "name": "string"
  }
}
```
### Example Response
```JSON
{
  "id": "string"
}
```

# PUT /devicespecifications

This service will update a Device Specification which are used in the MOSIP platform. 


### Resource URL
### `PUT /devicespecifications`

### Resource details

Resource Details | Description
------------ | -------------
Response format | JSON
Requires Authentication | Yes

### Parameters
Name | Required | Description | Default Value | Example
-----|----------|-------------|---------------|--------
id|Yes|ID of the Device Specification| | 
lang_code|Yes|Language code of the Device Specification| | 

### Example Request
```JSON
{
  "id": "string",
  "version": "string",
  "metadata": {},
  "requesttime": "yyyy-MM-dd'T'HH:mm:ss.SSS'Z'",
  "request": {
    "brand": "string",
    "description": "string",
    "id": "string",
    "isActive": true,
    "langCode": "string",
    "deviceTypeCode": "string",
    "minDriverversion": "string",
    "model": "string",
    "name": "string"
  }
}
```
### Example Response
```JSON
{
  "id": "string"
}
```

# DELETE /devicespecifications/{id}

This service deletes a Device Specification from the Device Specifications master module. 

### Resource URL
### `DELETE /devicespecifications/{id}`

### Resource details

Resource Details | Description
------------ | -------------
Response format | JSON
Requires Authentication | Yes

### Parameters
Name | Required | Description | Default Value | Example
-----|----------|-------------|---------------|--------
id|Yes|ID of the Device Specification| | 


### Example Response
```JSON
{
  "id": "string",
  "version": "string",
  "metadata": {},
  "responsetime": "yyyy-MM-dd'T'HH:mm:ss.SSS'Z'",
  "errors": [{
      "errorCode": "string",
      "message": "string"
    }],
  "response":  {
          "id": "string"
   }
}
```

# GET /devicespecifications/{langcode}/{devicetypecode}

This service will provides the list of all Device Specifications for specified language code and device type code . 


### Resource URL
### `GET /devicespecifications/{langcode}/{devicetypecode}`

### Resource details

Resource Details | Description
------------ | -------------
Response format | JSON
Requires Authentication | Yes

### Parameters
Name | Required | Description | Default Value | Example
-----|----------|-------------|---------------|--------
lang_code|Yes|Language code of the Device Specification| |
dtyp_code|Yes|device type code of the Device specification| | 

### Example Request
```JSON
-NA-
```

### Example Response
```JSON
{
  "id": "string",
  "version": "string",
  "metadata": {},
  "responsetime": "yyyy-MM-dd'T'HH:mm:ss.SSS'Z'",
  "errors": [{
      "errorCode": "string",
      "message": "string"
    }],
  "response":   {
  "devicespecifications": [
    {
      "brand": "string",
      "description": "string",
      "deviceTypeCode": "string",
      "id": "string",
      "isActive": true,
      "langCode": "string",
      "minDriverversion": "string",
      "model": "string",
      "name": "string"
    }
  ]
}
}

```


# GET /devicespecifications/{langcode}

This service will provides the list of all Device Specifications in a specific language. 


### Resource URL
### `GET /devicespecifications/{langcode}`

### Resource details

Resource Details | Description
------------ | -------------
Response format | JSON
Requires Authentication | Yes

### Parameters
Name | Required | Description | Default Value | Example
-----|----------|-------------|---------------|--------
langcode|Yes|Language code of the Device Specification| |

### Example Request
```JSON
-NA-
```

### Example Response
```JSON
{
  "id": "string",
  "version": "string",
  "metadata": {},
  "responsetime": "yyyy-MM-dd'T'HH:mm:ss.SSS'Z'",
  "errors": [{
      "errorCode": "string",
      "message": "string"
    }],
  "response" : {
  "devicespecifications": [
    {
      "brand": "string",
      "description": "string",
      "deviceTypeCode": "string",
      "id": "string",
      "isActive": true,
      "langCode": "string",
      "minDriverversion": "string",
      "model": "string",
      "name": "string"
    }
  ]
 }
}
```

### Response codes
202

Description: Accepted

400

Description: Bad request

401

Description: Unauthorized

403

Description: Forbidden

## GET /devicespecifications/all

This service will get all the devicespecifications. 

### Resource URL
### `GET /devicespecifications/all`

### Resource details

Resource Details | Description
------------ | -------------
Response format | JSON
Requires Authentication | Yes

### Parameters
Name | Required | Description | Default Value | Example
-----|----------|-------------|---------------|--------
orderBy|optional|order the requested data based on param| | 
pageNumber|optional|page no for the requested data| | 
pageSize|optional|page size for the requested data| | 
sortBy|optional|sort the requested data based on param value| | 


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
        "brand": "string",
        "createdBy": "string",
        "description": "string",
        "deviceTypeCode": "string",
        "deviceTypeName": "string",
        "id": "string",
        "isActive": true,
        "isDeleted": true,
        "langCode": "string",
        "minDriverversion": "string",
        "model": "string",
        "name": "string",
        "updatedBy": "string"
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

Description: Internal Error

## Failure details
Error Code | Error Message | Error Description
------------|------------------------------|-------------
KER-MSD-011 | Error occured while fetching Device Specifications | Fetch Issue
KER-MSD-012 | Device Specification not found | Data Not Found
KER-MSD-054 | Error occurred while inserting Device Specification details | Insertion Issue
KER-MSD-081 | Error occurred while updating Device Specification | Update Issue
KER-MSD-082 | Error occurred while deleting Device Specification | Deletion Issue
KER-MSD-121 | Cannot delete dependency found | Dependency issue
KER-MSD-347 | No Devices found for the received Device Type | Data Not Found

# TemplateFileFormat API

* [POST /templatefileformats](#post-templatefileformats)
* [PUT /templatefileformats](#put-templatefileformats)
* [DELETE /templatefileformats/{code}](#delete-templatefileformats-code)

# POST /templatefileformats

This service will create the list of templatefileformats  which are used in the MOSIP platform. 

### Resource URL
### `POST /templatefileformats`

### Resource details

Resource Details | Description
------------ | -------------
Response format | JSON
Requires Authentication | Yes

### Parameters
Name | Required | Description | Default Value | Example
-----|----------|-------------|---------------|--------
code|Yes|code of templatefileformat | | 
description|Yes|Description of the templatefileformat | | 
langcode|Yes|Language code of the temlate | | 
isActive |Yes|is active or not| |

### Example Request
```JSON
{
  "id": "string",
  "metadata": {},
  "request": {
    "code": "string",
    "description": "string",
    "isActive": true,
    "langCode": "string"
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
    "code": "string",
    "langCode": "string"
  },
  "responsetime": "yyyy-MM-dd'T'HH:mm:ss.SSS'Z'",
  "version": "string"
}
```
# PUT /templatefileformats

This service will update the list of templatefileformats  which are used in the MOSIP platform. 

### Resource URL
### `PUT /templatefileformats`

### Resource details

Resource Details | Description
------------ | -------------
Response format | JSON
Requires Authentication | Yes

### Parameters
Name | Required | Description | Default Value | Example
-----|----------|-------------|---------------|--------
code|Yes|code of templatefileformat | | 
description|Yes|Description of the templatefileformat | | 
langcode|Yes|Language code of the temlate | | 
isActive |Yes|is active or not| |

### Example Request
```JSON
{
  "id": "string",
  "metadata": {},
  "request": {
    "code": "string",
    "description": "string",
    "isActive": true,
    "langCode": "string"
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
    "code": "string",
    "langCode": "string"
  },
  "responsetime": "yyyy-MM-dd'T'HH:mm:ss.SSS'Z'",
  "version": "string"
}
```

# DELETE /templatefileformats/{code}
Master data is required across the platform. 

This service will deletes a list of templatefileformats from the Template master module. 

### Resource URL
### `DELETE /templates/{id}`

### Resource details

Resource Details | Description
------------ | -------------
Response format | JSON
Requires Authentication | Yes

### Parameters
Name | Required | Description | Default Value | Example
-----|----------|-------------|---------------|--------
code|Yes|id of the Template| 



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
## Failure details
Error Code | Error Message | Error Description
------------|------------------------------|-------------
KER-MSD-125 | Cannot delete dependency found. | Dependency Issue
KER-MSD-046 | Template not found | Data Not Found
KER-MSD-055 | Error occurred while inserting Template File Format details | Insertion Issue
KER-MSD-093 | Error occurred while updating Template | Update Issue
KER-MSD-094 | Error occurred while deleting Template | Deletion Issue

# Individual Types API

* [GET /individualtypes](#get-individualtypes)
* [GET /individualtypes/all](#get-individualtypes-all)

# GET /individualtypes

This service will provides the complete list of all individual types active in the MOSIP platform


### Resource URL
### `GET /individualtypes`

### Resource details

Resource Details | Description
------------ | -------------
Response format | JSON
Requires Authentication | Yes

### Parameters
Name | Required | Description | Default Value | Example
-----|----------|-------------|---------------|--------
-NA-

### Example Request
```JSON
-NA-
```

### Example Response
```JSON
{
  "id": "string",
  "version": "string",
  "metadata": {},
  "responsetime": "yyyy-MM-dd'T'HH:mm:ss.SSS'Z'",
  "errors": [{
      "errorCode": "string",
      "message": "string"
    }],
  "response":   {
  "individualtypes": [
    {
      "individualtypecode": "string",
      "name": "string",
      "description": "string",
      "langCode": "string",
      "isactive": boolean
    }
  ]
 }
}
```

### Response codes
200

Description: Success

## GET /individualtypes/all

This service will get all the individualtypes. 

### Resource URL
### `GET /individualtypes/all`

### Resource details

Resource Details | Description
------------ | -------------
Response format | JSON
Requires Authentication | Yes

### Parameters
Name | Required | Description | Default Value | Example
-----|----------|-------------|---------------|--------
orderBy|optional|order the requested data based on param| | 
pageNumber|optional|page no for the requested data| | 
pageSize|optional|page size for the requested data| | 
sortBy|optional|sort the requested data based on param value| | 


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
        "code": "string",
        "createdBy": "string",
        "isActive": true,
        "isDeleted": true,
        "langCode": "string",
        "name": "string",
        "updatedBy": "string"
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

Description: Internal Error

## Failure details
Error Code | Error Message | Error Description
------------|------------------------------|-------------
KER-MSD-152 | Error occured while fetching Individual Type | Fetch Issue
KER-MSD-151 | Individual Type not found | Data Not Found


# Age group Types API

* [GET /agegrouptype/{age}](#get-agegrouptype-age)

# GET /agegrouptype/{age}

This service will provides the age group based on the passed age. 


### Resource URL
### `GET /agegrouptype/{age}`

### Resource details

Resource Details | Description
------------ | -------------
Response format | JSON
Requires Authentication | Yes

### Parameters
Name | Required | Description | Default Value | Example
-----|----------|-------------|---------------|--------
-NA-

### Example Request
```JSON
-NA-
```

### Example Response
```JSON
{
  "id": "string",
  "version": "string",
  "metadata": {},
  "responsetime": "yyyy-MM-dd'T'HH:mm:ss.SSS'Z'",
  "errors": [{
      "errorCode": "string",
      "message": "string"
    }],
  "response":  {
	"agegrouptypecode": "string",
	"name": "string",
	"description": "string",
	"minimumage": "number",
	"maximumage": "number",
	"langCode": "string",
	"isactive": boolean
  }
}
```

### Response codes
200

Description: Success




# Template Types API

* [POST /templatetypes](#post-templatetypes)

# POST /templatetypes

This service creates template type based on provided. 


### Resource URL
### `POST /templatetypes`

### Resource details

Resource Details | Description
------------ | -------------
Response format | JSON
Requires Authentication | Yes

### Parameters
Name | Required | Description | Default Value | Example
-----|----------|-------------|---------------|--------
code|Yes|This is the template code field||
description|Yes| Description of the template type ||
isActive|Yes| is active? ||
langCode|Yes| language code ||

### Example Request
```JSON
{
  "id": "string",
  "metadata": {},
  "request": {
    "code": "string",
    "description": "string",
    "isActive": true,
    "langCode": "string"
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
    "code": "string",
    "langCode": "string"
  },
  "responsetime": "yyyy-MM-dd'T'HH:mm:ss.SSS'Z'",
  "version": "string"
}
```

### Response codes
201

Description: Successfully created

400	

Description: Request body passed is null or invalid

401	

Description: Unauthorized

403	

Description: Forbidden

404	

Description: Not Found

500	

Description:  any error occured while creating

## Failure details
Error Code | Error Message | Error Description
------------|------------------------------|-------------
KER-MSD-072 | Error occurred while inserting Template Type details into db | Insertion Issue


# Applicant Valid documents API

* [GET /applicanttype/{applicantId}/languages](#get-applicanttypeapplicantIdlanguages)

# GET /applicanttype/{applicantId}/languages

### Resource URL
### `GET /validdocuments/{languagecode}`

### Resource details

Resource Details | Description
------------ | -------------
Response format | JSON
Requires Authentication | Yes

### Parameters
Name | Required | Description | Default Value | Example
-----|----------|-------------|---------------|--------
applicantId|Yes|applicant id|-NA-|11105
languages|Yes| list of languages ||

### Example Request
```JSON
-NA-
```

### Example Success Response
```JSON
{{
  "errors": [
    {
      "errorCode": "string",
      "message": "string"
    }
  ],
  "id": "string",
  "metadata": {},
  "response": {
    "appTypeCode": "string",
    "documentCategories": [
      {
        "code": "string",
        "description": "string",
        "documentTypes": [
          {
            "code": "string",
            "description": "string",
            "isActive": true,
            "langCode": "string",
            "name": "string"
          }
        ],
        "isActive": true,
        "langCode": "string",
        "name": "string"
      }
    ],
    "isActive": true,
    "langCode": "string"
  },
  "responsetime": "yyyy-MM-dd'T'HH:mm:ss.SSS'Z'",
  "version": "string"
}
```


### Example Failure Response
```JSON
{
  "id": null,
  "version": null,
  "responsetime": "2019-11-21T06:37:34.237Z",
  "metadata": null,
  "response": null,
  "errors": [
    {
      "errorCode": "KER-ATH-401",
      "message": "Authentication Failed"
    }
  ]
}
```


### Response codes
200

Description: Success

## Failure details
Error Code | Error Message | Error Description
------------|------------------------------|-------------
KER-MSD-149 | Error occurred while fetching Applicant Type-Document Category-Document Type Mapping details | Fetch Issue
KER-MSD-150 | Document Category- Document Type mapping not found | Data Not Found
