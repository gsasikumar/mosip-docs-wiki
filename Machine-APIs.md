This section details about the service APIs in the Document modules


* [Machines API](#machines-master-api)

* [Machine Types Master API](#machine-types-master-api)

* [Machine Specifications API](#machine-specifications)

* [Machine - Search API](#post-machinessearch)

* [Machine - Filter values](#post-machinesfiltervalues)


# Machines Master API

* [POST /machines](#post-machines)
* [GET /machines](#get-machines)
* [GET /machines/{languagecode}](#get-machineslanguagecode)
* [GET /machineshistory/{id}/{languagecode}/{eff_dtimes}](#get-machineshistoryidlanguagecodeeff_dtimes)
* [DELETE /machines/{id}](#delete-machinesid)
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
  "errors": null,
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
  "errors": null,
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
  "errors": null,
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
  "errors": null,
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
  "errors": null,
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
  "errors": null,
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


### Failure Response
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
"response": null
}
```

#### Failure details
Error Code | Error Message | Error Description
------------|------------------------------|-------------
KER-MSD-029 | Error occured while fetching Machines | Fetch Issue
KER-MSD-063 | Error occurred while inserting Machine details | Insertion Issue
KER-MSD-030 | Machine not Found | Data Not Found
KER-MSD-087 | Error occurred while updating Machine details | Update Issue
KER-MSD-088 | Error occurred while deleting Machine details | Deletion Issue
KER-MSD-148 | Cannot delete as dependency found | Deletion Issue because of dependency


# Machine Types Master API







* [POST /machinetypes](#post-machinetypes)
* [GET /machinetypes](#get-machinetypes)
* [GET /machinetypes/{languagecode}](#get-machinetypeslanguagecodee)
* [POST /machinetypes/search](#post-machinetypessearch)
* [POST /machinetypes/filtervalues](#post-machinetypesfiltervalues)

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
  "errors": null,
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
  "errors": null,
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
  "errors": null,
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

### Failure Response
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
  "response":  null
 }
```

#### Failure details
Error Code | Error Message | Error Description
------------|------------------------------|-------------
KER-MSD-061 | Error occurred while inserting Machine Type details | Insertion Issue
KER-MSD-062 | Error occurred while fetching Machine Type details | Fetch Issue
KER-MSD-063 | Machine Type Not Found | Data Not Found

# Machine Type search APIs

* [POST /machinetypes/search](#post-machinetypessearch)

# POST /machinetypes/search

This service is for the machine type search functionality. All the filter parameters are passed and the machines types are searched and the matching results are returned. 

### Resource URL
### `POST /machinetypes/search`

### Resource details

Resource Details | Description
------------ | -------------
Response format | JSON
Requires Authentication | Yes

### Parameters
Name | Required | Description | Default Value | Example
-----|----------|-------------|---------------|--------
filters|No|Array of the filter applied. In case of "list" screen, this array will be empty| -NA- |
columnName|No|The column name in the JSON response| -NA- |
type|No|The value have to be in ["contains","equals",”startsWith”,"between"]| -NA- |
value|No|Value or id selected in the filter by the end user| -NA- |
fromValue|No|If the type is "between", this field is the value of the start range| -NA- |
toValue|No|If the type is "between", this field is the value of the end range| -NA- |
languagecode|Yes|Language code in Language code in ISO 639-2 format| | 
sort|No|This is an array of the sort field and type| | 
sortfield| The field on which the sort is applied | | modifiedDate
sorttype| This should be either of ['ASC','DESC']| | ASC
pagination|The pagination parameter object| |
pageStart|This is the start index | 0 | 10
pageFetch| This is the amount of records to be fetched | 10 | 10


### Example Request
```JSON
{
	"id": "string",
	"metadata": {},
	"requesttime": "2018-12-10T06:12:52.994Z",
	"version": "string",
	"request": {
		"filters" : [
			{
				"columnName": "",
				"type": "in",
				"value": "",  
				"fromValue": "",    
				"toValue": ""
			}
		],
		"sort":[
			{
				"sortfield":"string",
				"sorttype":"ASC"
			}
		],
		"pagination":{
			"pageStart":"number",
			"pageFetch":"number"
		},
		"languageCode":""
		
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
  "errors": null,
  "response": {
     "machineTypes": [
      {
     "code": "string",
    "description": "string",
    "isActive": true,
    "langCode": "string",
    "name": "string"  
 }
    ],
	"fromRecord" : "number",
	"toRecord":"number",
	"totalRecord":"number"
 }
}
```
# Machine Types filter values

* [POST /machinetypes/filtervalues](#post-machinetypesfiltervalues)

# POST /machinetypes/filtervalues

This service returns the filter values which are required in the dropdown entries of the filter screen.  

### Resource URL
### `POST /machinetypes/filtervalues`

### Resource details

Resource Details | Description
------------ | -------------
Response format | JSON
Requires Authentication | Yes

### Parameters
Name | Required | Description | Default Value | Example
-----|----------|-------------|---------------|--------
filters|No|Array of the filter applied. In case of "list" screen, this array will be empty| -NA- |
columnName|No|The column name in the JSON response| -NA- |
type|No|The value have to be in ["unique","all"]| unique | unique
languagecode|Yes|Language code in Language code in ISO 639-2 format| | 


### Example Request
```JSON
{
	"id": "string",
	"metadata": {},
	"requesttime": "2018-12-10T06:12:52.994Z",
	"version": "string"
	"request": {
		"filters" : [
			{
				"columnName": ""
				"type": "unique"
			}
		],
		"languageCode": "string",
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
  "errors": null,
  "response": {
  "filters": [
	{
		"fieldID": "string",
		"fieldValue": "string"
	}
   ]
 }
}
```

# Machine Specifications

* [POST /machinespecifications](#post-machinespecifications)
* [PUT /machinespecifications](#put-machinespecifications)
* [DELETE /machinespecifications/{id}](#delete-machinespecificationsid)
* [GET /machinespecifications](#get-machinespecifications)
* [GET /machinespecifications/{lang_code}](#get-machinespecificationslang_code)
* [POST /machinespecifications/search](#post-machinespecificationssearch)
* [POST /machinespecifications/filtervalues](#post-machinespecificationsfiltervalues)


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
  "errors": null,
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
  "errors": null,
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
  "errors": null,
  "response":  {
                "id": "string"
              }
 }
```

# GET /machinespecifications

This service will provides the list of all Machine Specifications in all languages. 


### Resource URL
### `GET /machinespecifications`

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
  "errors": null,
  "response":  {
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
  "errors": null,
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

### Failure Response:
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
  "response":   null
}
```

#### Failure details
Error Code | Error Message | Error Description
------------|------------------------------|-------------
KER-MSD-029 | Error occurred while fetching Machines | Fetch Issue
KER-MSD-062 | Error occurred while inserting Machine Specification details | Insertion Issue
KER-MSD-117 | Machine Specification not Found | Data Not Found
KER-MSD-085 | Error occurred while updating Machine Specification details | Update Issue
KER-MSD-086 | Error occurred while deleting Machine Specification details | Deletion Issue
KER-MSD-122 | Cannot delete dependency found | Deletion Issue because of dependency


# Machine Specifications Search APIs

* [POST /machinespecifications/search](#post-machinespecificationssearch)

# POST /machinespecifications/search

This service is for the machine specifications search functionality. All the filter parameters are passed and the machines specifications are searched and the matching results are returned. 

### Resource URL
### `POST /machinespecifications/search`

### Resource details

Resource Details | Description
------------ | -------------
Response format | JSON
Requires Authentication | Yes

### Parameters
Name | Required | Description | Default Value | Example
-----|----------|-------------|---------------|--------
filters|No|Array of the filter applied. In case of "list" screen, this array will be empty| -NA- |
columnName|No|The column name in the JSON response| -NA- |
type|No|The value have to be in ["contains","equals",”startsWith”,"between"]| -NA- |
value|No|Value or id selected in the filter by the end user| -NA- |
fromValue|No|If the type is "between", this field is the value of the start range| -NA- |
toValue|No|If the type is "between", this field is the value of the end range| -NA- |
languagecode|Yes|Language code in Language code in ISO 639-2 format| | 
sort|No|This is an array of the sort field and type| | 
sortfield| The field on which the sort is applied | | modifiedDate
sorttype| This should be either of ['ASC','DESC']| | ASC
pagination|The pagination parameter object| |
pageStart|This is the start index | 0 | 10
pageFetch| This is the amount of records to be fetched | 10 | 10

### Filter Values
Filter Name| Search Values
-----|----------
name|["contains","equals","startsWith"]
brand|["contains","equals","startsWith"]
model|["contains","equals","startsWith"]
device type name|["contains","equals","startsWith"]
status|["equals"]
model|["contains","equals","startsWith"]

### Example Request
```JSON
{
	"id": "string",
	"metadata": {},
	"requesttime": "2018-12-10T06:12:52.994Z",
	"version": "string",
	"request": {
		"filters" : [
			{
				"columnName": "",
				"type": "in",
				"value": "",  
				"fromValue": "",  
				"toValue": ""
			}
		],
		"sort":[
			{
				"sortfield":"string",
				"sorttype":"ASC"
			}
		],
		"pagination":{
			"pageStart":"number",
			"pageFetch":"number"
		},
		"languageCode":""
		
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
  "errors": null,
  "response": {
     "machineSpecifications": [
      {
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
    ],
	"fromRecord" : "number",
	"toRecord":"number",
	"totalRecord":"number"
 }
}
```
# Machine Specifications filter values

* [POST /machinespecifications/filtervalues](#post-machinespecificationsfiltervalues)

# POST /machinespecifications/filtervalues

This service returns the filter values which are required in the dropdown entries of the filter screen.  

### Resource URL
### `POST /machinespecifications/filtervalues`

### Resource details

Resource Details | Description
------------ | -------------
Response format | JSON
Requires Authentication | Yes

### Parameters
Name | Required | Description | Default Value | Example
-----|----------|-------------|---------------|--------
filters|No|Array of the filter applied. In case of "list" screen, this array will be empty| -NA- |
columnName|No|The column name in the JSON response| -NA- |
type|No|The value have to be in ["unique","all"]| unique | unique
languagecode|Yes|Language code in Language code in ISO 639-2 format| | 


### Example Request
```JSON
{
	"id": "string",
	"metadata": {},
	"requesttime": "2018-12-10T06:12:52.994Z",
	"version": "string"
	"request": {
		"filters" : [
			{
				"columnName": ""
				"type": "unique"
			}
		],
		"languageCode": "string",
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
  "errors": null,
  "response": {
  "filters": [
	{
		"fieldID": "string",
		"fieldValue": "string"
	}
   ]
 }
}
```


# Machine search APIs

* [POST /machines/search](#post-machinessearch)

# POST /machines/search

This service is for the machine search functionality. All the filter parameters are passed and the machines are searched and the matching results are returned. 

### Resource URL
### `POST /machines/search`

### Resource details

Resource Details | Description
------------ | -------------
Response format | JSON
Requires Authentication | Yes

### Parameters
Name | Required | Description | Default Value | Example
-----|----------|-------------|---------------|--------
filters|No|Array of the filter applied. In case of "list" screen, this array will be empty| -NA- |
columnName|No|The column name in the JSON response| -NA- |
type|No|The value have to be in ["contains","equals",”startsWith”,"between"]| -NA- |
value|No|Value or id selected in the filter by the end user| -NA- |
fromValue|No|If the type is "between", this field is the value of the start range| -NA- |
toValue|No|If the type is "between", this field is the value of the end range| -NA- |
languagecode|Yes|Language code in Language code in ISO 639-2 format| | 
sort|No|This is an array of the sort field and type| | 
sortfield| The field on which the sort is applied | | modifiedDate
sorttype| This should be either of ['ASC','DESC']| | ASC
pagination|The pagination parameter object| |
pageStart|This is the start index | 0 | 10
pageFetch| This is the amount of records to be fetched | 10 | 10

### Filter Values
Filter Name| Search Values
-----|----------
Machine Name|["contains","equals","startsWith"]
Status|["equals"]
MAC Address|["contains","equals","startsWith"]
Serial Number|["contains","equals","startsWith"]
Map Status|["contains","equals","startsWith"]
Machine Type|["contains","equals","startsWith"]
Machine Specification ID|["contains","equals","startsWith"]

### Example Request
```JSON
{
	"id": "string",
	"metadata": {},
	"requesttime": "2018-12-10T06:12:52.994Z",
	"version": "string",
	"request": {
		"filters" : [
			{
				"columnName": "",
				"type": "in",
				"value": "", 
				"fromValue": "",  
				"toValue": ""
			}
		],
		"sort":[
			{
				"sortfield":"string",
				"sorttype":"ASC"
			}
		],
		"pagination":{
			"pageStart":"number",
			"pageFetch":"number"
		},
		"languageCode":""
		
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
  "errors": null,
  "response": {
     "data": [
      {
        "id": "string",
        "ipAddress": "string",
        "isActive": true,
        "langCode": "string",
        "macAddress": "string",
        "machineSpecId": "string",
        "name": "string",
        "serialNum": "string",
        "validityDateTime": "yyyy-MM-dd'T'HH:mm:ss.SSS'Z'"
      }
    ],
	"fromRecord" : "number",
	"toRecord":"number",
	"totalRecord":"number"
 }
}
```
# Machine filter values

* [POST /machines/filtervalues](#post-machinesfiltervalues)

# POST /machines/filtervalues

This service returns the filter values which are required in the dropdown entries of the filter screen.  

### Resource URL
### `POST /machines/filtervalues`

### Resource details

Resource Details | Description
------------ | -------------
Response format | JSON
Requires Authentication | Yes

### Parameters
Name | Required | Description | Default Value | Example
-----|----------|-------------|---------------|--------
filters|No|Array of the filter applied. In case of "list" screen, this array will be empty| -NA- |
columnName|No|The column name in the JSON response| -NA- |
type|No|The value have to be in ["unique","all"]| unique | unique
languagecode|Yes|Language code in Language code in ISO 639-2 format| | 


### Example Request
```JSON
{
	"id": "string",
	"metadata": {},
	"requesttime": "2018-12-10T06:12:52.994Z",
	"version": "string"
	"request": {
		"filters" : [
			{
				"columnName": ""
				"type": "unique"
			}
		],
		"languageCode": "string",
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
  "errors": null,
  "response": {
  "filters": [
	{
		"fieldID": "string",
		"fieldValue": "string"
	}
   ]
 }
}
```