## Device Management
* [Device Providers](#device-providers)
* [Foundational Trust Providers](#foundational-trust-providers)
* [Devices](#devices)
* [MDS](#mds)


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

### Response codes
200

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



# Devices

* [GET /devices/{devicetype}](#get-devicesdevicetype)
* [POST /device/l1/register](#post-devicel1register)
* [POST /device/l2/register](#post-devicel2register)
* [DELETE /device/l1/deregister](#delete-devicel1deregister)
* [DELETE /device/l2/deregister](#delete-devicel2deregister)
* [PUT /device/l1](#put-devicel1)
* [PUT /device/l2](#put-devicel2)

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
devicetype|yes|This is the device type. It can be L0 or L1. This field is case insensitive|-NA-|L1


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


### POST /device/l2/register

This service creates a L2 device in the platform. The history is persisted

### Resource URL
### `POST /device/l2/register`

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
  "id": "io.mosip.masterdata.device.l2.create",
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
	"id": "io.mosip.masterdata.device.l2.create",
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
	"id": "io.mosip.masterdata.device.l2.create",
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


### DELETE /device/l2/deregister

This service creates a L2 device in the platform. The history is persisted

### Resource URL
### `DELETE /device/l2/register`

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
  "id": "io.mosip.masterdata.device.l2.delete",
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
	"id": "io.mosip.masterdata.device.l2.delete",
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
	"id": "io.mosip.masterdata.device.l2.create",
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


### PUT /device/l2

This service updates a L2 device. The history is persisted

### Resource URL
### `PUT /device/l2`

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
  "id": "io.mosip.masterdata.device.l2.update",
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
	"id": "io.mosip.masterdata.device.l2.update",
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
	"id": "io.mosip.masterdata.device.l2.update",
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
