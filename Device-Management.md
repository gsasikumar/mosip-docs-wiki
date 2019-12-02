## Device Management
* [Device Providers](#device-providers)
* [Foundational Trust Providers](#foundational-trust-providers)
* [Devices](#devices)
* [MDS API](#mds-api)

# Device Providers

* [GET /deviceprovider](#get-deviceprovider)
* [GET /deviceprovider/{deviceProviderId}](#get-deviceproviderdeviceProviderId)
* [POST /deviceprovider](#post-deviceprovider)
* [PUT /deviceprovider](#put-deviceprovider)


### GET /deviceprovider

This service returns all the device providers in the system.

### Resource URL
### `GET /deviceprovider`

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
-NA-

### Example success response
```JSON
{
	"id": "io.mosip.masterdata.deviceprovider.get",
	"version": "1.0",
	"metadata": {},
	"responsetime": "yyyy-MM-dd'T'HH:mm:ss.SSS'Z'",
	"errors": null,
	"response" : {
		"id": "string",
		"vendor_name": "string",
		"address": "string",
		"email": "string",
		"contact_number": "string",
		"is_active": "string",
		"created_by": "string",
		"created_dttimes": "string",
		"updated_by": "string",
		"updated_dttimes": "string"
	}
}
```

### Response codes
200

### Example failure response
```JSON
{
	"id": "io.mosip.masterdata.deviceprovider.get",
	"version": "1.0",
	"metadata": {},
	"responsetime": "yyyy-MM-dd'T'HH:mm:ss.SSS'Z'",
	"errors": [{
		"errorCode": "string",
		"message": "string"
	}],
	"response" : null
}
```

### Response codes
200


### GET /deviceprovider/{deviceProviderId}

This service returns the device provider based on the requested input. 

### Resource URL
### `GET /deviceprovider/{deviceProviderId}`

### Resource details

Resource Details | Description
------------ | -------------
Response format | JSON
Requires Authentication | Yes

### Parameters
Name | Required | Description | Default Value | Example
-----|----------|-------------|---------------|--------
deviceProviderId|yes|This is the id of the device provider|-NA|-NA-


### Example Request
-NA-

### Example success response
```JSON
{
	"id": "io.mosip.masterdata.deviceprovider.get",
	"version": "1.0",
	"metadata": {},
	"responsetime": "yyyy-MM-dd'T'HH:mm:ss.SSS'Z'",
	"errors": null,
	"response" : {
		"id": "string",
		"vendor_name": "string",
		"address": "string",
		"email": "string",
		"contact_number": "string",
		"is_active": "string",
		"created_by": "string",
		"created_dttimes": "string",
		"updated_by": "string",
		"updated_dttimes": "string"
	}
}
```

### Response codes
200

### Example failure response
```JSON
{
	"id": "io.mosip.masterdata.deviceprovider.get",
	"version": "1.0",
	"metadata": {},
	"responsetime": "yyyy-MM-dd'T'HH:mm:ss.SSS'Z'",
	"errors": [{
		"errorCode": "string",
		"message": "string"
	}],
	"response" : null
}
```
#### Failure details
Error Code  | Error Message | Error Description
-----|----------|-------------
KER-ATH-401 |Authentication Failed|If no role/invalid token is detected


### POST /deviceprovider

This service creates a service provider. The history is persisted

### Resource URL
### `POST /deviceprovider`

### Resource details

Resource Details | Description
------------ | -------------
Response format | JSON
Requires Authentication | Yes

### Parameters
Name | Required | Description | Default Value | Example
-----|----------|-------------|---------------|--------
vendor_name|yes|This is the name of the vendor|-NA|-NA-
address|yes|This is the address of the vendor|-NA|-NA-
email|yes|This is the email of the vendor|-NA|-NA-
contact_number|yes|This is the contact number of the vendor|-NA|-NA-
is_active|yes|This field represents whether this entity is active or not|-NA|-NA-

### Example Request
```JSON
{
  "id": "io.mosip.masterdata.deviceprovider.create",
  "version": "V1.0",
  "metadata": {},
  "requesttime": "yyyy-MM-dd'T'HH:mm:ss.SSS'Z'",
  "request": {
				"vendor_name": "string",
				"address": "string",
				"email": "string",
				"contact_number": "string",
				"is_active": "boolean"
            }
 }
```

### Example success response
```JSON
{
	"id": "io.mosip.masterdata.deviceprovider.create",
	"version": "1.0",
	"metadata": {},
	"responsetime": "yyyy-MM-dd'T'HH:mm:ss.SSS'Z'",
	"errors": null,
	"response" : {
		"id": "string"
	}
}
```

### Response codes
200

### Example failure response
```JSON
{
	"id": "io.mosip.masterdata.deviceprovider.create",
	"version": "1.0",
	"metadata": {},
	"responsetime": "yyyy-MM-dd'T'HH:mm:ss.SSS'Z'",
	"errors": [{
		"errorCode": "string",
		"message": "string"
	}],
	"response" : null
}
```

### Response codes
200

#### Failure details
Error Code  | Error Message | Error Description
-----|----------|-------------
KER-ATH-401 |Authentication Failed|If no role/invalid token is detected
ADM-DPM-010 |Mandatory input parameter is missing|If any mandatory input parameter is missing
ADM-DPM-011 |Device Provider already exist|If the Device provider details already exist
ADM-DPM-012 |Error occurred while registering a Device Provider|If there an error from DB while storing details of Device Provider

### PUT /deviceprovider

This service updates a service provider. The history is persisted

### Resource URL
### `PUT /deviceprovider`

### Resource details

Resource Details | Description
------------ | -------------
Response format | JSON
Requires Authentication | Yes

### Parameters
Name | Required | Description | Default Value | Example
-----|----------|-------------|---------------|--------
vendor_name|yes|This is the name of the vendor|-NA|-NA-
address|yes|This is the address of the vendor|-NA|-NA-
email|yes|This is the email of the vendor|-NA|-NA-
contact_number|yes|This is the contact number of the vendor|-NA|-NA-
is_active|yes|This field represents whether this entity is active or not|-NA|-NA-

### Example Request
```JSON
{
  "id": "io.mosip.masterdata.deviceprovider.update",
  "version": "V1.0",
  "metadata": {},
  "requesttime": "yyyy-MM-dd'T'HH:mm:ss.SSS'Z'",
  "request": {
				"vendor_name": "string",
				"address": "string",
				"email": "string",
				"contact_number": "string",
				"is_active": "boolean"
            }
 }
```

### Example success response
```JSON
{
	"id": "io.mosip.masterdata.deviceprovider.update",
	"version": "1.0",
	"metadata": {},
	"responsetime": "yyyy-MM-dd'T'HH:mm:ss.SSS'Z'",
	"errors": null,
	"response" : {
		"id": "string"
	}
}
```

### Response codes
200

### Example failure response
```JSON
{
	"id": "io.mosip.masterdata.deviceprovider.update",
	"version": "1.0",
	"metadata": {},
	"responsetime": "yyyy-MM-dd'T'HH:mm:ss.SSS'Z'",
	"errors": [{
		"errorCode": "string",
		"message": "string"
	}],
	"response" : null
}
```

### Response codes
200

#### Failure details
Error Code  | Error Message | Error Description
-----|----------|-------------
KER-ATH-401 |Authentication Failed|If no role/invalid token is detected
ADM-DPM-013|Mandatory input parameter is missing|If any mandatory input parameter is missing
ADM-DPM-014 |Error occurred while registering a Device Provider|If there an error from DB while storing details of Device Provider

# Foundational Trust Providers

* [GET /foundationaltrustprovider](#get-foundationaltrustprovider)
* [GET /foundationaltrustprovider/{foundationalTrustProviderID}](#get-foundationaltrustproviderfoundationalTrustProviderID)
* [POST /foundationaltrustprovider](#post-foundationaltrustprovider)
* [PUT /foundationaltrustprovider](#put-foundationaltrustprovider)


### GET /foundationaltrustprovider

This service returns all the Foundational Trust Providers in the system. 

### Resource URL
### `GET /foundationaltrustprovider`

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
-NA-

### Example success response
```JSON
{
	"id": "io.mosip.masterdata.foundationaltrustprovider.get",
	"version": "1.0",
	"metadata": {},
	"responsetime": "yyyy-MM-dd'T'HH:mm:ss.SSS'Z'",
	"errors": null,
	"response" : {
		"id": "string",
		"name": "string",
		"address": "string",
		"email": "string",
		"contact_number": "string",
		"is_active": "string",
		"created_by": "string",
		"created_dttimes": "string",
		"updated_by": "string",
		"updated_dttimes": "string"
	}
}
```

### Response codes
200

### Example failure response
```JSON
{
	"id": "io.mosip.masterdata.foundationaltrustprovider.get",
	"version": "1.0",
	"metadata": {},
	"responsetime": "yyyy-MM-dd'T'HH:mm:ss.SSS'Z'",
	"errors": [{
		"errorCode": "string",
		"message": "string"
	}],
	"response" : null
}
```

### Response codes
200

### GET /foundationaltrustprovider/{foundationalTrustProviderId}

This service returns all the Foundational Trust Providers in the system. 

### Resource URL
### `GET /foundationaltrustprovider/{foundationalTrustProviderId}`

### Resource details

Resource Details | Description
------------ | -------------
Response format | JSON
Requires Authentication | Yes

### Parameters
Name | Required | Description | Default Value | Example
-----|----------|-------------|---------------|--------
foundationalTrustProviderId|yes|This is the id of the foundational trust provider|-NA|-NA-


### Example Request
-NA-

### Example success response
```JSON
{
	"id": "io.mosip.masterdata.foundationaltrustprovider.get",
	"version": "1.0",
	"metadata": {},
	"responsetime": "yyyy-MM-dd'T'HH:mm:ss.SSS'Z'",
	"errors": null,
	"response" : {
		"id": "string",
		"name": "string",
		"address": "string",
		"email": "string",
		"contact_number": "string",
		"is_active": "string",
		"created_by": "string",
		"created_dttimes": "string",
		"updated_by": "string",
		"updated_dttimes": "string"
	}
}
```

### Response codes
200

### Example failure response
```JSON
{
	"id": "io.mosip.masterdata.foundationaltrustprovider.get",
	"version": "1.0",
	"metadata": {},
	"responsetime": "yyyy-MM-dd'T'HH:mm:ss.SSS'Z'",
	"errors": [{
		"errorCode": "string",
		"message": "string"
	}],
	"response" : null
}
```

### Response codes
200


### POST /foundationaltrustprovider

This service creates a service provider. 

### Resource URL
### `POST /foundationaltrustprovider`

### Resource details

Resource Details | Description
------------ | -------------
Response format | JSON
Requires Authentication | Yes

### Parameters
Name | Required | Description | Default Value | Example
-----|----------|-------------|---------------|--------
vendor_name|yes|This is the name of the vendor|-NA|-NA-
address|yes|This is the address of the vendor|-NA|-NA-
email|yes|This is the email of the vendor|-NA|-NA-
contact_number|yes|This is the contact number of the vendor|-NA|-NA-
is_active|yes|This field represents whether this entity is active or not|-NA|-NA-

### Example Request
```JSON
{
  "id": "io.mosip.masterdata.foundationaltrustprovider.create",
  "version": "V1.0",
  "metadata": {},
  "requesttime": "yyyy-MM-dd'T'HH:mm:ss.SSS'Z'",
  "request": {
				"name": "string",
				"address": "string",
				"email": "string",
				"contact_number": "string",
				"is_active": "boolean"
            }
 }
```

### Example success response
```JSON
{
	"id": "io.mosip.masterdata.foundationaltrustprovider.create",
	"version": "1.0",
	"metadata": {},
	"responsetime": "yyyy-MM-dd'T'HH:mm:ss.SSS'Z'",
	"errors": null,
	"response" : {
		"id": "string"
	}
}
```

### Response codes
200

### Example failure response
```JSON
{
	"id": "io.mosip.masterdata.foundationaltrustprovider.create",
	"version": "1.0",
	"metadata": {},
	"responsetime": "yyyy-MM-dd'T'HH:mm:ss.SSS'Z'",
	"errors": [{
		"errorCode": "string",
		"message": "string"
	}],
	"response" : null
}
```

### Response codes
200

#### Failure details
Error Code  | Error Message | Error Description
-----|----------|-------------
KER-ATH-401|Authentication Failed|If no role/invalid token is detected
ADM-DPM-015|Mandatory input parameter is missing|If any mandatory input parameter is missing
ADM-DPM-016|Foundational Trust Provider already exist|If the Foundational Trust provider details already exist
ADM-DPM-017|Error occurred while registering a Foundational Trust Provider|If there an error from DB while storing details of Foundational Trust Provider


### PUT /foundationaltrustprovider

This service updates a service provider. 

### Resource URL
### `PUT /foundationaltrustprovider`

### Resource details

Resource Details | Description
------------ | -------------
Response format | JSON
Requires Authentication | Yes

### Parameters
Name | Required | Description | Default Value | Example
-----|----------|-------------|---------------|--------
vendor_name|yes|This is the name of the vendor|-NA|-NA-
address|yes|This is the address of the vendor|-NA|-NA-
email|yes|This is the email of the vendor|-NA|-NA-
contact_number|yes|This is the contact number of the vendor|-NA|-NA-
is_active|yes|This field represents whether this entity is active or not|-NA|-NA-

### Example Request
```JSON
{
  "id": "io.mosip.masterdata.foundationaltrustprovider.update",
  "version": "V1.0",
  "metadata": {},
  "requesttime": "yyyy-MM-dd'T'HH:mm:ss.SSS'Z'",
  "request": {
				"name": "string",
				"address": "string",
				"email": "string",
				"contact_number": "string",
				"is_active": "boolean"
            }
 }
```

### Example success response
```JSON
{
	"id": "io.mosip.masterdata.foundationaltrustprovider.update",
	"version": "1.0",
	"metadata": {},
	"responsetime": "yyyy-MM-dd'T'HH:mm:ss.SSS'Z'",
	"errors": null,
	"response" : {
		"id": "string"
	}
}
```

### Response codes
200

### Example failure response
```JSON
{
	"id": "io.mosip.masterdata.foundationaltrustprovider.update",
	"version": "1.0",
	"metadata": {},
	"responsetime": "yyyy-MM-dd'T'HH:mm:ss.SSS'Z'",
	"errors": [{
		"errorCode": "string",
		"message": "string"
	}],
	"response" : null
}
```

### Response codes
200

#### Failure details
Error Code  | Error Message | Error Description
-----|----------|-------------
KER-ATH-401|Authentication Failed|If no role/invalid token is detected
ADM-DPM-018|Mandatory input parameter is missing|If any mandatory input parameter is missing
ADM-DPM-019|Error occurred while registering a Foundational Trust Provider|If there an error from DB while storing details of Foundational Trust Provider



# Devices

* [GET /devices/{devicetype}](#get-devicesdevicetype)
* [POST /device/l0/register](#post-devicel0register)
* [POST /device/l1/register](#post-devicel1register)
* [DELETE /device/l0/deregister](#delete-devicel0deregister)
* [DELETE /device/l1/deregister](#delete-devicel1deregister)
* [PUT /device/l0](#put-devicel0)
* [PUT /device/l1](#put-devicel1)
* [POST/deviceprovidermanagement/validate](#post-deviceprovidermanagementvalidate)
* [POST/deviceprovidermanagement/validate/history](#post-deviceprovidermanagementvalidatehistory)

### GET /device/{devicetype}

This service returns all the device in the system based on the device type.

### Resource URL
### `GET /device/{devicetype}`

### Resource details

Resource Details | Description
------------ | -------------
Response format | JSON
Requires Authentication | Yes

### Parameters
Name | Required | Description | Default Value | Example
-----|----------|-------------|---------------|--------
devicetype|yes|This is the device type. It can be L0 or L1. This field is case insensitive|-NA-|L0


### Example Request
-NA-

### Example success response
```JSON
{
	"id": "io.mosip.masterdata.device.get",
	"version": "1.0",
	"metadata": {},
	"responsetime": "yyyy-MM-dd'T'HH:mm:ss.SSS'Z'",
	"errors": null,
	"response" : {
		"deviceId": "string",
		"deviceTypeCode": "string",
		"deviceSubTypecode": "string",
		"statusCode": "string",
		"deviceId": "string",
		"deviceSubId": "string",
		"serialNumber": "string",
		"providerId": "string",
		"providerName": "string",
		"purpose": "string"
		"firmware": "string",
		"make": "string",
		"model": "string",
		"expiryDate": "date",
		"certificationLevel": "string",
		"foundationalTrustProviderId": "string",
		"foundationalTrustSignature": "string",
		"foundationalTrustCertificate": "string",
		"dproviderSignature": "string",
		"isActive": "string",
		"createdBy": "string",
		"createdDateTime": "date",
		"updatedBy": "string",
		"updatedDateTime": "date",
		"isDeleted": "boolean"
	}
}
```

### Response codes
200

### Example failure response
```JSON
{
	"id": "io.mosip.masterdata.device.get",
	"version": "1.0",
	"metadata": {},
	"responsetime": "yyyy-MM-dd'T'HH:mm:ss.SSS'Z'",
	"errors": [{
		"errorCode": "string",
		"message": "string"
	}],
	"response" : null
}
```

### Response codes
200


### POST /device/l0/register

This service creates a L0 device in the platform. The history is persisted

### Resource URL
### `POST /device/l0/register`

### Resource details

Resource Details | Description
------------ | -------------
Response format | JSON
Requires Authentication | Yes

### Parameters
Name | Required | Description | Default Value | Example
-----|----------|-------------|---------------|--------
deviceCode|yes|This is the code of the device|-NA|-NA-
deviceId|yes|This is the id of the device|-NA|-NA-
deviceInfo|yes|This is the information about the device|-NA|-NA-
certification|yes|This is the certification of the device|-NA|-NA-
deviceExpiry|yes|This is the expiry date of the device|-NA|-NA-
deviceMake|yes|This is the make of the device|-NA|-NA-
deviceModel|yes|This is the model of the device|-NA|-NA-
deviceSubId|yes|This is the sub type id of the device|-NA|-NA-
firmware|yes|This is the firmware of the device|-NA|-NA-
timestamp|yes|This is the timestamp of the record|-NA|-NA-
deviceProviderId|yes|This is the id of the provide|-NA|-NA-
deviceProviderName|yes|This is the name of the device|-NA|-NA-
foundationTrustCertificate|no|This is the foundational trust provider's certificate|-NA|-NA-
foundationalTrustProviderID|no|This is the id of the foundational trust provider|-NA|-NA-
foundationalTrustSignature|no|This is the signature of the foundational trust provider|-NA|-NA-
status|yes|This is the status of the device|-NA|-NA-
subType|yes|This is the sub type of the device|-NA|-NA-
type|yes|This is the type of the device|-NA|-NA-
dpSignature|no|This is the signature of the image|-NA|-NA-

### Example Request
```JSON
{
  "id": "io.mosip.masterdata.device.l0.create",
  "version": "V1.0",
  "metadata": {},
  "requesttime": "yyyy-MM-dd'T'HH:mm:ss.SSS'Z'",
  "request": {
			"deviceData": {
				"deviceCode": "string",
				"deviceId": "string",
				"deviceInfo": {
					"certification": "string",
					"deviceExpiry": "date",
					"deviceMake": "string",
					"deviceModel": "string",
					"deviceSubId": "string",
					"firmware": "string",
					"timestamp": "date"
				},
				"deviceProviderId": "string",
				"deviceProviderName": "string",
				"foundationTrustCertificate": "string",
				"foundationalTrustProviderID": "string",
				"foundationalTrustSignature": "string",
				"status": "string",
				"subType": "string",
				"type": "string"
			},
			"dpSignature": "string"
        }
 }
```

### Example success response
```JSON
{
	"id": "io.mosip.masterdata.device.l0.create",
	"version": "1.0",
	"metadata": {},
	"responsetime": "yyyy-MM-dd'T'HH:mm:ss.SSS'Z'",
	"errors": null,
	"response" : {
		"deviceId": "string"
	}
}
```

### Response codes
200

### Example failure response
```JSON
{
	"id": "io.mosip.masterdata.device.l0.create",
	"version": "1.0",
	"metadata": {},
	"responsetime": "yyyy-MM-dd'T'HH:mm:ss.SSS'Z'",
	"errors": [{
		"errorCode": "string",
		"message": "string"
	}],
	"response" : null
}
```

### Response codes
200

#### Failure details
Error Code  | Error Message | Error Description
-----|----------|-------------
KER-ATH-401|Authentication Failed|If no role/invalid token is detected
ADM-DPM-025|Mandatory input parameter is missing|If any mandatory input parameter is missing
ADM-DPM-026|Device Type does not exist|If Device Type received does not exist
ADM-DPM-027|Device Sub-Type does not exist|If Device Sub-Type received does not exist
ADM-DPM-028|Invalid Status received|If in Status, standard values are not received
ADM-DPM-029|For Device ID, Json value expected for a L0 Device|If in Device, a singed Json is not received if certification level is L0
ADM-DPM-030|Make/Model inside the Json does not match with the input|If Make/Model inside the digital ID does not match with details received in input
ADM-DPM-031|Device Provider details inside the Json does not match with the input|If Device Provider ID/Device Provider name inside the digital ID does not match with details received in input
ADM-DPM-032|Device Provider ID/Name does not exist in the list of Registered Device Providers|If Device Provider ID/Name does not exist against the Device Provider Details
ADM-DPM-034|Invalid Purpose received|If in purpose, standard values are not received
ADM-DPM-036|Error occurred while storing MDS Details|If there an error from DB while registering the Device


### POST /device/l0/register

This service creates a L0 device in the platform. The history is persisted

### Resource URL
### `POST /device/l0/register`

### Resource details

Resource Details | Description
------------ | -------------
Response format | JSON
Requires Authentication | Yes

### Parameters
Name | Required | Description | Default Value | Example
-----|----------|-------------|---------------|--------
deviceCode|yes|This is the code of the device|-NA|-NA-
deviceId|yes|This is the id of the device|-NA|-NA-
deviceInfo|yes|This is the information about the device|-NA|-NA-
certification|yes|This is the certification of the device|-NA|-NA-
deviceExpiry|yes|This is the expiry date of the device|-NA|-NA-
deviceMake|yes|This is the make of the device|-NA|-NA-
deviceModel|yes|This is the model of the device|-NA|-NA-
deviceSubId|yes|This is the sub type id of the device|-NA|-NA-
firmware|yes|This is the firmware of the device|-NA|-NA-
timestamp|yes|This is the timestamp of the record|-NA|-NA-
deviceProviderId|yes|This is the id of the provide|-NA|-NA-
deviceProviderName|yes|This is the name of the device|-NA|-NA-
foundationTrustCertificate|yes|This is the foundational trust provider's certificate|-NA|-NA-
foundationalTrustProviderID|yes|This is the id of the foundational trust provider|-NA|-NA-
foundationalTrustSignature|yes|This is the signature of the foundational trust provider|-NA|-NA-
status|yes|This is the status of the device|-NA|-NA-
subType|yes|This is the sub type of the device|-NA|-NA-
type|yes|This is the type of the device|-NA|-NA-
dpSignature|yes|This is the signature of the image|-NA|-NA-

### Example Request
```JSON
{
  "id": "io.mosip.masterdata.device.l0.create",
  "version": "V1.0",
  "metadata": {},
  "requesttime": "yyyy-MM-dd'T'HH:mm:ss.SSS'Z'",
  "request": {
			"deviceData": {
				"deviceCode": "string",
				"deviceId": "string",
				"deviceInfo": {
					"certification": "string",
					"deviceExpiry": "date",
					"deviceMake": "string",
					"deviceModel": "string",
					"deviceSubId": "string",
					"firmware": "string",
					"timestamp": "date"
				},
				"deviceProviderId": "string",
				"deviceProviderName": "string",
				"foundationTrustCertificate": "string",
				"foundationalTrustProviderID": "string",
				"foundationalTrustSignature": "string",
				"status": "string",
				"subType": "string",
				"type": "string"
			},
			"dpSignature": "string"
        }
 }
```

### Example success response
```JSON
{
	"id": "io.mosip.masterdata.device.l0.create",
	"version": "1.0",
	"metadata": {},
	"responsetime": "yyyy-MM-dd'T'HH:mm:ss.SSS'Z'",
	"errors": null,
	"response" : {
		"deviceId": "string"
	}
}
```

### Response codes
200

### Example failure response
```JSON
{
	"id": "io.mosip.masterdata.device.l0.create",
	"version": "1.0",
	"metadata": {},
	"responsetime": "yyyy-MM-dd'T'HH:mm:ss.SSS'Z'",
	"errors": [{
		"errorCode": "string",
		"message": "string"
	}],
	"response" : null
}
```

### Response codes
200


### POST /device/l1/register

This service creates a L1 device in the platform. The history is persisted

### Resource URL
### `POST /device/l1/register`

### Resource details

Resource Details | Description
------------ | -------------
Response format | JSON
Requires Authentication | Yes

### Parameters
Name | Required | Description | Default Value | Example
-----|----------|-------------|---------------|--------
deviceCode|yes|This is the code of the device|-NA|-NA-
deviceId|yes|This is the id of the device|-NA|-NA-
deviceInfo|yes|This is the information about the device|-NA|-NA-
certification|yes|This is the certification of the device|-NA|-NA-
deviceExpiry|yes|This is the expiry date of the device|-NA|-NA-
deviceMake|yes|This is the make of the device|-NA|-NA-
deviceModel|yes|This is the model of the device|-NA|-NA-
deviceSubId|yes|This is the sub type id of the device|-NA|-NA-
firmware|yes|This is the firmware of the device|-NA|-NA-
timestamp|yes|This is the timestamp of the record|-NA|-NA-
deviceProviderId|yes|This is the id of the provide|-NA|-NA-
deviceProviderName|yes|This is the name of the device|-NA|-NA-
foundationTrustCertificate|yes|This is the foundational trust provider's certificate|-NA|-NA-
foundationalTrustProviderID|yes|This is the id of the foundational trust provider|-NA|-NA-
foundationalTrustSignature|yes|This is the signature of the foundational trust provider|-NA|-NA-
status|yes|This is the status of the device|-NA|-NA-
subType|yes|This is the sub type of the device|-NA|-NA-
type|yes|This is the type of the device|-NA|-NA-
dpSignature|yes|This is the signature of the image|-NA|-NA-

### Example Request
```JSON
{
  "id": "io.mosip.masterdata.device.l1.create",
  "version": "V1.0",
  "metadata": {},
  "requesttime": "yyyy-MM-dd'T'HH:mm:ss.SSS'Z'",
  "request": {
			"deviceData": {
				"deviceCode": "string",
				"deviceId": "string",
				"deviceInfo": {
					"certification": "string",
					"deviceExpiry": "date",
					"deviceMake": "string",
					"deviceModel": "string",
					"deviceSubId": "string",
					"firmware": "string",
					"timestamp": "date"
				},
				"deviceProviderId": "string",
				"deviceProviderName": "string",
				"foundationTrustCertificate": "string",
				"foundationalTrustProviderID": "string",
				"foundationalTrustSignature": "string",
				"status": "string",
				"subType": "string",
				"type": "string"
			},
			"dpSignature": "string"
        }
 }
```

### Example success response
```JSON
{
	"id": "io.mosip.masterdata.device.l1.create",
	"version": "1.0",
	"metadata": {},
	"responsetime": "yyyy-MM-dd'T'HH:mm:ss.SSS'Z'",
	"errors": null,
	"response" : {
		"deviceId": "string"
	}
}
```

### Response codes
200

### Example failure response
```JSON
{
	"id": "io.mosip.masterdata.device.l1.create",
	"version": "1.0",
	"metadata": {},
	"responsetime": "yyyy-MM-dd'T'HH:mm:ss.SSS'Z'",
	"errors": [{
		"errorCode": "string",
		"message": "string"
	}],
	"response" : null
}
```

### Response codes
200



### DELETE /device/l0/deregister

This service creates a L0 device in the platform. The history is persisted

### Resource URL
### `DELETE /device/l0/register`

### Resource details

Resource Details | Description
------------ | -------------
Response format | JSON
Requires Authentication | Yes

### Parameters
Name | Required | Description | Default Value | Example
-----|----------|-------------|---------------|--------
deviceCode|yes|This is the code of the device|-NA|-NA-
timestamp|yes|This is the timestamp of the record|-NA|-NA-
dpSignature|yes|This is the digital signature|-NA|-NA-

### Example Request
```JSON
{
  "id": "io.mosip.masterdata.device.l0.delete",
  "version": "V1.0",
  "metadata": {},
  "requesttime": "yyyy-MM-dd'T'HH:mm:ss.SSS'Z'",
  "request": {
			"device": {
				"deviceCode": "string",
				"timestamp": "date"
			},
			"signature": "string"
        }
 }
```

### Example success response
```JSON
{
	"id": "io.mosip.masterdata.device.l0.delete",
	"version": "1.0",
	"metadata": {},
	"responsetime": "yyyy-MM-dd'T'HH:mm:ss.SSS'Z'",
	"errors": null,
	"response" : {
		"deviceId": "string"
	}
}
```

### Response codes
200

### Example failure response
```JSON
{
	"id": "io.mosip.masterdata.device.l0.create",
	"version": "1.0",
	"metadata": {},
	"responsetime": "yyyy-MM-dd'T'HH:mm:ss.SSS'Z'",
	"errors": [{
		"errorCode": "string",
		"message": "string"
	}],
	"response" : null
}
```

### Response codes
200


### DELETE /device/l1/deregister

This service creates a L1 device in the platform. The history is persisted

### Resource URL
### `DELETE /device/l1/register`

### Resource details

Resource Details | Description
------------ | -------------
Response format | JSON
Requires Authentication | Yes

### Parameters
Name | Required | Description | Default Value | Example
-----|----------|-------------|---------------|--------
deviceCode|yes|This is the code of the device|-NA|-NA-
timestamp|yes|This is the timestamp of the record|-NA|-NA-
dpSignature|yes|This is the digital signature|-NA|-NA-

### Example Request
```JSON
{
  "id": "io.mosip.masterdata.device.l1.delete",
  "version": "V1.0",
  "metadata": {},
  "requesttime": "yyyy-MM-dd'T'HH:mm:ss.SSS'Z'",
  "request": {
			"device": {
				"deviceCode": "string",
				"timestamp": "date"
			},
			"signature": "string"
        }
 }
```

### Example success response
```JSON
{
	"id": "io.mosip.masterdata.device.l1.delete",
	"version": "1.0",
	"metadata": {},
	"responsetime": "yyyy-MM-dd'T'HH:mm:ss.SSS'Z'",
	"errors": null,
	"response" : {
		"deviceId": "string"
	}
}
```

### Response codes
200

### Example failure response
```JSON
{
	"id": "io.mosip.masterdata.device.l1.create",
	"version": "1.0",
	"metadata": {},
	"responsetime": "yyyy-MM-dd'T'HH:mm:ss.SSS'Z'",
	"errors": [{
		"errorCode": "string",
		"message": "string"
	}],
	"response" : null
}
```

### Response codes
200


### PUT /device/l0

This service updates a L0 device. The history is persisted

### Resource URL
### `PUT /device/l0`

### Resource details

Resource Details | Description
------------ | -------------
Response format | JSON
Requires Authentication | Yes

### Parameters
Name | Required | Description | Default Value | Example
-----|----------|-------------|---------------|--------
deviceCode|yes|This is the code of the device|-NA|-NA-
deviceId|yes|This is the id of the device|-NA|-NA-
deviceInfo|yes|This is the information about the device|-NA|-NA-
certification|yes|This is the certification of the device|-NA|-NA-
deviceExpiry|yes|This is the expiry date of the device|-NA|-NA-
deviceMake|yes|This is the make of the device|-NA|-NA-
deviceModel|yes|This is the model of the device|-NA|-NA-
deviceSubId|yes|This is the sub type id of the device|-NA|-NA-
firmware|yes|This is the firmware of the device|-NA|-NA-
timestamp|yes|This is the timestamp of the record|-NA|-NA-
deviceProviderId|yes|This is the id of the provide|-NA|-NA-
deviceProviderName|yes|This is the name of the device|-NA|-NA-
foundationTrustCertificate|no|This is the foundational trust provider's certificate|-NA|-NA-
foundationalTrustProviderID|no|This is the id of the foundational trust provider|-NA|-NA-
foundationalTrustSignature|no|This is the signature of the foundational trust provider|-NA|-NA-
status|yes|This is the status of the device|-NA|-NA-
subType|yes|This is the sub type of the device|-NA|-NA-
type|yes|This is the type of the device|-NA|-NA-
dpSignature|no|This is the signature of the image|-NA|-NA-

### Example Request
```JSON
{
  "id": "io.mosip.masterdata.device.l0.update",
  "version": "V1.0",
  "metadata": {},
  "requesttime": "yyyy-MM-dd'T'HH:mm:ss.SSS'Z'",
  "request": {
			"deviceData": {
				"deviceCode": "string",
				"deviceId": "string",
				"deviceInfo": {
					"certification": "string",
					"deviceExpiry": "date",
					"deviceMake": "string",
					"deviceModel": "string",
					"deviceSubId": "string",
					"firmware": "string",
					"timestamp": "date"
				},
				"deviceProviderId": "string",
				"deviceProviderName": "string",
				"foundationTrustCertificate": "string",
				"foundationalTrustProviderID": "string",
				"foundationalTrustSignature": "string",
				"status": "string",
				"subType": "string",
				"type": "string"
			},
			"dpSignature": "string"
        }
 }
```

### Example success response
```JSON
{
	"id": "io.mosip.masterdata.device.l0.update",
	"version": "1.0",
	"metadata": {},
	"responsetime": "yyyy-MM-dd'T'HH:mm:ss.SSS'Z'",
	"errors": null,
	"response" : {
		"deviceId": "string"
	}
}
```

### Response codes
200

### Example failure response
```JSON
{
	"id": "io.mosip.masterdata.device.l0.update",
	"version": "1.0",
	"metadata": {},
	"responsetime": "yyyy-MM-dd'T'HH:mm:ss.SSS'Z'",
	"errors": [{
		"errorCode": "string",
		"message": "string"
	}],
	"response" : null
}
```

### Response codes
200

#### Failure details
Error Code  | Error Message | Error Description
-----|----------|-------------
KER-ATH-401|Authentication Failed|If no role/invalid token is detected
ADM-DPM-036|Mandatory input parameter is missing|If any mandatory input parameter is missing
ADM-DPM-037|Invalid Status received|If in Status, standard values are not received
ADM-DPM-038|Error occurred while updating Device Status|If there an error from DB while updating Device Status


### PUT /device/l1

This service updates a L1 device. The history is persisted

### Resource URL
### `PUT /device/l1`

### Resource details

Resource Details | Description
------------ | -------------
Response format | JSON
Requires Authentication | Yes

### Parameters
Name | Required | Description | Default Value | Example
-----|----------|-------------|---------------|--------
deviceCode|yes|This is the code of the device|-NA|-NA-
deviceId|yes|This is the id of the device|-NA|-NA-
deviceInfo|yes|This is the information about the device|-NA|-NA-
certification|yes|This is the certification of the device|-NA|-NA-
deviceExpiry|yes|This is the expiry date of the device|-NA|-NA-
deviceMake|yes|This is the make of the device|-NA|-NA-
deviceModel|yes|This is the model of the device|-NA|-NA-
deviceSubId|yes|This is the sub type id of the device|-NA|-NA-
firmware|yes|This is the firmware of the device|-NA|-NA-
timestamp|yes|This is the timestamp of the record|-NA|-NA-
deviceProviderId|yes|This is the id of the provide|-NA|-NA-
deviceProviderName|yes|This is the name of the device|-NA|-NA-
foundationTrustCertificate|yes|This is the foundational trust provider's certificate|-NA|-NA-
foundationalTrustProviderID|yes|This is the id of the foundational trust provider|-NA|-NA-
foundationalTrustSignature|yes|This is the signature of the foundational trust provider|-NA|-NA-
status|yes|This is the status of the device|-NA|-NA-
subType|yes|This is the sub type of the device|-NA|-NA-
type|yes|This is the type of the device|-NA|-NA-
dpSignature|yes|This is the signature of the image|-NA|-NA-

### Example Request
```JSON
{
  "id": "io.mosip.masterdata.device.l1.update",
  "version": "V1.0",
  "metadata": {},
  "requesttime": "yyyy-MM-dd'T'HH:mm:ss.SSS'Z'",
  "request": {
			"deviceData": {
				"deviceCode": "string",
				"deviceId": "string",
				"deviceInfo": {
					"certification": "string",
					"deviceExpiry": "date",
					"deviceMake": "string",
					"deviceModel": "string",
					"deviceSubId": "string",
					"firmware": "string",
					"timestamp": "date"
				},
				"deviceProviderId": "string",
				"deviceProviderName": "string",
				"foundationTrustCertificate": "string",
				"foundationalTrustProviderID": "string",
				"foundationalTrustSignature": "string",
				"status": "string",
				"subType": "string",
				"type": "string"
			},
			"dpSignature": "string"
        }
 }
```

### Example success response
```JSON
{
	"id": "io.mosip.masterdata.device.l1.update",
	"version": "1.0",
	"metadata": {},
	"responsetime": "yyyy-MM-dd'T'HH:mm:ss.SSS'Z'",
	"errors": null,
	"response" : {
		"deviceId": "string"
	}
}
```

### Response codes
200

### Example failure response
```JSON
{
	"id": "io.mosip.masterdata.device.l1.update",
	"version": "1.0",
	"metadata": {},
	"responsetime": "yyyy-MM-dd'T'HH:mm:ss.SSS'Z'",
	"errors": [{
		"errorCode": "string",
		"message": "string"
	}],
	"response" : null
}
```

### Response codes
200

#### Failure details
Error Code  | Error Message | Error Description
-----|----------|-------------
KER-ATH-401|Authentication Failed|If no role/invalid token is detected
ADM-DPM-036|Mandatory input parameter is missing|If any mandatory input parameter is missing
ADM-DPM-037|Invalid Status received|If in Status, standard values are not received
ADM-DPM-038|Error occurred while updating Device Status|If there an error from DB while updating Device Status

### POST /deviceprovidermanagement/validate

This service will validate the device details from the list of registered devices.

### Resource URL
### `POST /deviceprovidermanagement/validate`

### Resource details

Resource Details | Description
------------ | -------------
Response format | JSON
Requires Authentication | Yes

### Request Parameters
Name | Required | Description | Default Value | Example
-----|----------|-------------|---------------|--------
deviceCode|Yes|code of the device| | 
digitalId|Yes|JSON object consists of device details| | 
deviceServiceVersion|Yes|DeviceServiceVersion of the mds| | 

### Example Request
```
https://mosip.io/masterdata/deviceprovidermanagement/validate

{
   "id":"string",
   "metadata":null,
   "request":{
        "deviceCode":"string",
     	"deviceServiceVersion":"string",
     	"digitalId":{
     		"serialNo": "string",
                "make": "string",
                "model" : "string",
                "type": "string",
                "dp": "string",
                "dpId": "string",
                "dateTime": "string"

}
},
   "version":"1.0",
   "requesttime":"2019-08-21T16:34:22.890Z"
}
```

### Example Response

200 Ok

```JSON
{
  "id": "string",
  "version": "string",
  "metadata": {},
  "responsetime": "2018-12-10T06:12:52.994Z",
  "errors": null,
  "response":  [
    {
      "message": "Device details validated successfully"
    }
  ],
}

```

##### Error Response:

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
 "response": null
}

```

#### Failure details
Error Code  | Error Message | Error Description
-----|----------|-------------
KER-MSD-500 |Internal Server Error|If system error occurs
KER-ATH-403 |Forbidden|If unauthorized role detected
KER-ATH-401 |Authentication Failed|If no role/invalid token is detected
ADM-DPM-001 |Device does not exist|If the Device does not exist 
ADM-DPM-002 |Device is Revoked/Retired|If the Device exist and is in Revoked/Retired
ADM-DPM-003 |Device Provider does not exist|If the Device Provider does not exist
ADM-DPM-004 |Device Provider is marked Inactive|If the Device Provider exist and is in Inactive State
ADM-DPM-005 |MDS does not exist|If the MDS does not exist
ADM-DPM-006 |MDS is marked Inactive|If the MDS exist and is in Inactive State
ADM-DPM-007 |Software version does not match against the Service ID|If the Software version does not match the Service ID received
ADM-DPM-008 |Device Provider ID does not match against the Service ID|If the Device provider ID does not match the Service ID received
ADM-DPM-009 |Error occurred while checking a Device Details| If there an error from DB while checking device details

### POST/deviceprovidermanagement/validate/history

This service will validate the device history details from the list of registered devices.

### Resource URL
### `POST/deviceprovidermanagement/validate/history`

### Resource details

Resource Details | Description
------------ | -------------
Response format | JSON
Requires Authentication | Yes

### Request Parameters
Name | Required | Description | Default Value | Example
-----|----------|-------------|---------------|--------
deviceCode|Yes|code of the device| | 
digitalId|Yes|JSON object of the device details| | 
deviceServiceVersion|Yes|DeviceServiceVersion of the mds| |
timeStamp|Yes|Timestamp in LocalDataTimeformat of history table| | 

### Example Request
```
https://mosip.io/masterdata/deviceprovidermanagement/validate/history

{
   "id":"string",
   "metadata":null,
   "request":{
        "deviceCode":"10001",
     	"deviceServiceVersion":"0.1v",
        "timestamp":"2019-09-09T09:09:09.000Z"
     	"digitalId":{
     		"serialNo": "string",
                "make": "string",
                "model" : "string",
                "type": "string",
                "dp": "string",
                "dpId": "string",
                "dateTime": "string"
                }

},
   "version":"1.0",
   "requesttime":"2019-08-21T16:34:22.890Z"
}
```

### Example Response

200 Ok

```JSON
{
  "id": "string",
  "version": "string",
  "metadata": {},
  "responsetime": "2018-12-10T06:12:52.994Z",
  "errors": null,
  "response":  [
    {
      "status": "valid"
      "message": "Device details history validated successfully"
    }
  ],
}

```

##### Error Response:

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
 "response": null
}

```

#### Failure details
Error Code  | Error Message | Error Description
-----|----------|-------------
KER-MSD-500 |Internal Server Error|If system error occurs
KER-ATH-403 |Forbidden|If unauthorized role detected
KER-ATH-401 |Authentication Failed|If no role/invalid token is detected
ADM-DPM-001 |Device does not exist|If the Device does not exist 
ADM-DPM-002 |Device is Revoked/Retired|If the Device exist and is in Revoked/Retired
ADM-DPM-003 |Device Provider does not exist|If the Device Provider does not exist
ADM-DPM-004 |Device Provider is marked Inactive|If the Device Provider exist and is in Inactive State
ADM-DPM-005 |MDS does not exist|If the MDS does not exist
ADM-DPM-006 |MDS is marked Inactive|If the MDS exist and is in Inactive State
ADM-DPM-007 |Software version does not match against the Service ID|If the Software version does not match the Service ID received
ADM-DPM-008 |Device Provider ID does not match against the Service ID|If the Device provider ID does not match the Service ID received
ADM-DPM-009 |Error occurred while checking a Device Details| If there an error from DB while checking device details

# MDS API

* [POST /mds](#post-mds)
* [GET /mds/{id}](#get-mds)
* [PUT /mds](#put-devicetypes)
* [DELETE /mds/{id}](#delete-mds)

# POST /mds
Master data is required across the platform. 

This service will create the MDS which are used in the MOSIP platform. 

### Resource URL
### `POST /mds`

### Resource details

Resource Details | Description
------------ | -------------
Response format | JSON
Requires Authentication | Yes

### Parameters
Name | Required | Description | Default Value | Example
-----|----------|-------------|---------------|--------
id|Yes|id of the mds| | 
deviceProviderId|Yes|Deviceproviderid of the mds| | 
deviceTypeCode|Yes|Devicetypecode of the mds| | 
deviceSubTypeCode|Yes|Devicesubtypecode of the mds| | 
swversion|Yes|sofware version of the mds| | 
swbinaryhash|Yes|sofware version of the mds| | 
make|Yes|make of the mds| | 
model|Yes|model of the mds| | 

### Example Request
```JSON
{
  "id": "string",
  "metadata": {},
  "request":  {
    "id": "mdsid",
    "deviceProviderId": "deviceProviderId",
    "deviceTypeCode": "Finger",
    "deviceSubTypeCode": "Slab",
    "swversion": "v1",
    "swbinaryhash": "10B4ABB32EDF42C2862D857C0FD26B8FD810CE973B5FF34CEF4D4128C3F5C510",
    "make": "make",
    "model": "model"
  },
  "requesttime": "2018-12-10T06:12:52.994Z",
  "version": "string"
}
```
### Example Response

200 Ok

```JSON
{
  "id": "string",
  "version": "string",
  "metadata": {},
  "responsetime": "2018-12-10T06:12:52.994Z",
  "errors": null,
  "response":  [
    {
      "id": "mdsid"
    }
  ],
}

```

##### Error Response:

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
 "response": null
}

```

#### Failure details
Error Code  | Error Message | Error Description
-----|----------|-------------
KER-ATH-401|Authentication Failed|If no role/invalid token is detected
ADM-DPM-020|Mandatory input parameter is missing|If any mandatory input parameter is missing
ADM-DPM-021|MDS Details already exist|If the MDS Details already exist
ADM-DPM-039|Device Provider ID not found in the list of Device Providers|Device Provider ID received does not exist in the Device Provider Table
ADM-DPM-040|Device Type Code not found in the list of Device Types|Device Type Code received does not exist in the Device Type Table
ADM-DPM-041|Device Sub Type Code not found in the list of Device Sub Types|Device Sub Type Code received does not exist in the Device Sub Type Table

# GET /mds/{id}
Master data is required across the platform. 

This service will provides the service to get the mds. 

### Resource URL
### `GET /mds/{id}`

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
		"id": "mdsid",
    "deviceProviderId": "deviceProviderId",
    "deviceTypeCode": "Finger",
    "deviceSubTypeCode": "Slab",
    "swversion": "v1",
    "swbinaryhash": "10B4ABB32EDF42C2862D857C0FD26B8FD810CE973B5FF34CEF4D4128C3F5C510",
    "make": "make",
    "model": "model",
    "isActive": true,
    "swCreatedBy": "superadmin",
    "swCreatedDateTime": "2019-07-26T12:18:40.718Z",
    "createdBy": "superadmin",
    "createdDateTime": "2019-07-26T12:18:40.718Z",
    "updatedBy": null,
    "updatedDateTime": null,
    "isDeleted": null,
    "deletedDateTime": null
  }
}
```
##### Error Response:

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
 "response": null
}

```

#### Failure details
Error Code  | Error Message | Error Description
-----|----------|-------------
KER-MSD-500 |Internal Server Error|If system error occurs
KER-ATH-403 |Forbidden|If unauthorized role detected
KER-ATH-401 |Authentication Failed|If no role/invalid token is detected

# PUT /mds
Master data is required across the platform. 

This service will update the MDS which are used in the MOSIP platform. 

### Resource URL
### `PUT /mds`

### Resource details

Resource Details | Description
------------ | -------------
Response format | JSON
Requires Authentication | Yes

### Parameters
Name | Required | Description | Default Value | Example
-----|----------|-------------|---------------|--------
id|Yes|id of the mds| | 
deviceProviderId|Yes|Deviceproviderid of the mds| | 
deviceTypeCode|Yes|Devicetypecode of the mds| | 
deviceSubTypeCode|Yes|Devicesubtypecode of the mds| | 
swversion|Yes|sofware version of the mds| | 
swbinaryhash|Yes|sofware version of the mds| | 
make|Yes|make of the mds| | 
model|Yes|model of the mds| | 

### Example Request
```JSON
{
  "id": "string",
  "metadata": {},
  "request":  {
    "id": "mdsid",
    "deviceProviderId": "deviceProviderId",
    "deviceTypeCode": "Finger",
    "deviceSubTypeCode": "Slab",
    "swversion": "v1",
    "swbinaryhash": "10B4ABB32EDF42C2862D857C0FD26B8FD810CE973B5FF34CEF4D4128C3F5C510",
    "make": "make",
    "model": "model"
  },
  "requesttime": "2018-12-10T06:12:52.994Z",
  "version": "string"
}
```
### Example Response

200 Ok

```JSON
{
  "id": "string",
  "version": "string",
  "metadata": {},
  "responsetime": "2018-12-10T06:12:52.994Z",
  "errors": null,
  "response":  [
    {
      "id": "mdsid"
    }
  ],
}

```

##### Error Response:

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
 "response": null
}

```

#### Failure details
Error Code  | Error Message | Error Description
-----|----------|-------------
KER-ATH-401|Authentication Failed|If no role/invalid token is detected
ADM-DPM-020|Mandatory input parameter is missing|If any mandatory input parameter is missing
ADM-DPM-021|MDS Details already exist|If the MDS Details already exist
ADM-DPM-039|Device Provider ID not found in the list of Device Providers|Device Provider ID received does not exist in the Device Provider Table
ADM-DPM-040|Device Type Code not found in the list of Device Types|Device Type Code received does not exist in the Device Type Table
ADM-DPM-041|Device Sub Type Code not found in the list of Device Sub Types|Device Sub Type Code received does not exist in the Device Sub Type Table

# DELETE /mds/{id}
Master data is required across the platform. 

This service will provides the service to delete the mds. 

### Resource URL
### `DELETE /mds/{id}`

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

200 Ok

```JSON
{
  "id": "string",
  "version": "string",
  "metadata": {},
  "responsetime": "yyyy-MM-dd'T'HH:mm:ss.SSS'Z'",
  "errors": null,
  "response": {
		 "id": "mdsid"
  }
}
```
##### Error Response:

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
 "response": null
}

```

#### Failure details
Error Code  | Error Message | Error Description
-----|----------|-------------
KER-MSD-500 |Internal Server Error|If system error occurs
KER-ATH-403 |Forbidden|If unauthorized role detected
KER-ATH-401 |Authentication Failed|If no role/invalid token is detected
