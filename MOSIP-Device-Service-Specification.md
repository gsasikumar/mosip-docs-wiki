#### Aug 2019 | Version: 0.9.5 
#### Status: Draft 
#### Last updated date: 24th April 2020

## Table of Contents 

1. [Introduction & Background](#1-introduction--background)
1. [Glossary of Terms](#2-glossary-of-terms)
1. [Device Specification](#3-device-specification)
1. [Device Trust](#4-device-trust)
1. [Device Service - Communication Interfaces](#5-device-service---communication-interfaces)

    5.1. [Device Discovery](#51-device-discovery) 

    5.2. [Device Info](#52-device-info) 
 
    5.3 [Capture](#53-capture) 

    5.4 [Device Stream](#54-device-stream) 
 
    5.5 [Device Registration Capture](#55-device-registration-capture) 
 
1. [Device Server](#6-device-server)

    6.1 [Registration](#61-registration)

    6.2. [De-Register](#62-de-register)
1. [Management Server](#7-management-server)
1. [Compliance](#8-compliance)
---
## 1. Introduction & Background 

### Objective

The objective of this specification document is to establish the technical and compliance standards/ protocols that are necessary for a biometric device to be used in MOSIP solutions.

### Target Audience

This is a biometric device specification document and aims to help the biometric device manufactures, their developers, and their designers in building MOSIP compliant devices.
This document assumes that the readers are familiar with MOSIP registration and authentication services.

### MOSIP Devices

All devices that collect biometric data for MOSIP should operate within the specification of this document.

---
## 2. Glossary of Terms
* Device Provider - An entity that manufactures or imports the devices in their name. This entity should have legal rights to obtain an organization level digital certificate from the respective authority in the country.
* Foundational Trust Provider - An entity that manufactures the foundational trust module.
* Device - A hardware capable of capturing biometric information.
* L1 Certified Device / L1 Device - A device certified as capable of performing encryption in line with this spec in its trusted zone.
* L0 Certified Device / L0 Device - A device certified as one where the encryption is done on the host machine device driver or the MOSIP device service.
* Foundational Trust Provider Certificate - A digital certificate issued to the “Foundational Trust Provider”. This certificate proves that the provider has successfully gone through the required Foundational Trust Provider evaluation. The entity is expected to keep this certificate in secure possession in an HSM. All the individual trust certificates are issued using this certificate as the root. This certificate would be issued  by the countries in conjunction with MOSIP.
* Device Provider Certificate - A digital certificate issued to the “Device Provider”. This certificate proves that the provider has been certified for L0/L1 respective compliance. The entity is expected to keep this certificate in secure possession in an HSM. All the individual trust certificates are issued using this certificate as the root. This certificate is issued by the countries in conjunction with MOSIP.
* Registration - The process of applying for a Foundational Id.
* KYC - Know Your Customer. The process of providing consent to perform profile verification and update.
* Auth - The process of verifying one’s identity.
* FPS - Frames Per Second
* Management Server - A server run by the device provider to manage the life cycle of the biometric devices.
* Device Registration - The process of registering the device with MOSIP servers.
* Signature - All signature should be as per RFC 7515.
* header in signature - Header in signature means the attribute with "type" set to "MDSSign" "alg" set to RS256 and x5c set to base64encoded certificate.
* payload is the byte array of the actual data, always represented as base64urlencoded.
* signature - base64urlencoded signature bytes
* ISO Format Time - ISO 8601 with format yyyy-mm-dd HH:MM:ssZ
---
## 3. Device Specification

The MOSIP device specification provides compliance guidelines to devices for them to work with MOSIP. The compliance is based on device capability, trust and communication protocols. A MOSIP compliant device would follow the standards established in this document. It is expected that the devices are compliant to this specification and tested and validated. The details of each of these are outlined in the subsequent sections.

**Device Capability:**
The MOSIP compliant device is expected to perform the following:
*   Should have the ability to collect one or more biometric
*   Should have the ability to sign the captured biometric image or template.
*   Should have the ability to protect secret keys
*   Should have no mechanism to inject the biometric

**Base Specifications for Devices:**
1. Fingerprint Capture

Refer ISO 19794-4:2011

<table>
  <tr>
   <td><strong>Factor</strong>
   </td>
   <td><strong>Registration Devices</strong>
   </td>
   <td><strong>Authentication Devices</strong>
   </td>
  </tr>
  <tr>
   <td>Minimum Resolution
   </td>
   <td>> 500 native dpi. Bare minimum recommended. Higher densities are preferred
   </td>
   <td>> 500 native dpi. Bare minimum recommended. Higher densities are preferred
   </td>
  </tr>
  <tr>
   <td>FRR **
   </td>
   <td>< 2% FRR in respective country
   </td>
   <td>< 2% FRR in respective country
   </td>
  </tr>
  <tr>
   <td>FAR **
   </td>
   <td>0.01%
   </td>
   <td>0.01%
   </td>
  </tr>
  <tr>
   <td>DPI
   </td>
   <td>500 *
   </td>
   <td>500
   </td>
  </tr>
  <tr>
   <td>Image Specification
   </td>
   <td>ISO 19794-4 B.1 AFIS Normative
   </td>
   <td>ISO 19794-4 B.2 Personal Verification
   </td>
  </tr>
  <tr>
   <td>ESD
   </td>
   <td>>= 8kv
   </td>
   <td>>= 8kv
   </td>
  </tr>
  <tr>
   <td>EMC compliance
   </td>
   <td>FCC class A or equivalent
   </td>
   <td>FCC class A or equivalent
   </td>
  </tr>
  <tr>
   <td>Operating Temperature**
   </td>
   <td>0 - 50 C
   </td>
   <td>-30 -to 50 C
   </td>
  </tr>
  <tr>
   <td>Liveness detection***
   </td>
   <td>As per IEEE 2790
   </td>
   <td>As per IEEE 2790
   </td>
  </tr>
  <tr>
   <td>Preview
   </td>
   <td>> 3 FPS Jpeg lossless frames with NFIQ 2 score superimposed
   </td>
   <td> None
   </td>
  </tr>
  <tr>
   <td>Image Format
   </td>
   <td>JPEG 2000 lossless
   </td>
   <td>JPEG2000 lossless
   </td>
  </tr>
  <tr>
   <td>Quality Score
   </td>
   <td>NFIQ 2
   </td>
   <td>NFIQ 1
   </td>
  </tr>
  <tr>
   <td>FTM
   </td>
   <td>L0 - Use host based security, L1 - FTM supported security 
   </td>
   <td>L1 - FTM supported security, L2 - with tamper protection.
   </td>
  </tr>
</table>

```
* Sufficiency to be validated for registration
** MOSIP adapters can change this if needed 
*** MOSIP adapters to decide on the availability of this feature
```

2. IRIS Capture

Refer ISO 19796-6:2011 Part 6 Specifications.
<table>
  <tr>
   <td><strong>Factor</strong>
   </td>
   <td><strong>Registration Devices</strong>
   </td>
   <td><strong>Authentication Devices</strong>
   </td>
  </tr>
  <tr>
   <td>Rotation angle
   </td>
   <td>Before compression, the Iris image will have to be pre-processed to calculate rotation angle. Refer section 6.3.1 of ISO 19794-6 for rotation angle calculation for rectilinear images.
   </td>
   <td>
   </td>
  </tr>
  <tr>
   <td>Rotation Uncertainty
   </td>
   <td>Refer ISO 19794-6
   </td>
   <td>
   </td>
  </tr>
  <tr>
   <td>Minimum Diameter
   </td>
   <td>As per ISO 19794-6:2011 medium and higher quality images are only acceptable,. Hence for this Standard, minimum acceptable Iris diameter will be 150 pixels
   </td>
   <td>Same
   </td>
  </tr>
  <tr>
   <td>Margin
   </td>
   <td>Same as ISO
   </td>
   <td>
   </td>
  </tr>
  <tr>
   <td>Color
   </td>
   <td>The iris images shall be captured and stored in grey scale with pixel depth of 8 bits/pixel.
   </td>
   <td>
   </td>
  </tr>
  <tr>
   <td>Illumination
   </td>
   <td>The eye should be illuminated using infrared or any other source that could produce high quality grayscale image.
   </td>
   <td>
   </td>
  </tr>
  <tr>
   <td>Image Format
   </td>
   <td>JPEG 2000 lossless
   </td>
   <td>JPEG 2000 lossless
   </td>
  </tr>
  <tr>
   <td>Aspect Ratio
   </td>
   <td>1:1
   </td>
   <td>
   </td>
  </tr>
  <tr>
   <td>Image Quality
   </td>
   <td>   ISO/IEC    29794-­‐6
   </td>
   <td>
       ISO/IEC    29794-­‐6
   </td>
  </tr>
  <tr>
   <td>Operation Temperature*
   </td>
   <td>-30 C to +50 C
   </td>
   <td>-30 C to +50 C
   </td>
  </tr>
  <tr>
   <td>EMC compliance
   </td>
   <td>FCC Class A or equivalent
   </td>
   <td>FCC Class A or equivalent
   </td>
  </tr>
  <tr>
   <td>Preview
   </td>
   <td>> 3 FPS Jpeg lossless frames with quality score superimposed
   </td>
   <td>Not Applicable
   </td>
  </tr>
  <tr>
   <td>Image Specification
   </td>
   <td>ISO 19794-6
   </td>
   <td>ISO 19794-6
   </td>
  </tr>
  <tr>
   <td>ISO Format
   </td>
   <td>K3
   </td>
   <td>K7
   </td>
  </tr>
  <tr>
   <td>FTM
   </td>
   <td>L0 - Use host based security, L1 - FTM supported security 
   </td>
   <td>L1 - FTM supported security, L2 - with tamper protection.
   </td>
  </tr>
</table>

```
* MOSIP adopters to decide and finalize
```

3. Face Capture

Refer ISO 19794-5:2011

<table>
  <tr>
   <td><strong>Factor</strong>
   </td>
   <td><strong>Registration Devices</strong>
   </td>
   <td><strong>Authentication Devices</strong>
   </td>
  </tr>
  <tr>
   <td>Minimum Resolution
   </td>
   <td>1080 Pixels at 2.8 mm with 110 degree view
   </td>
   <td>1080 Pixels at 2.8 mm
   </td>
  </tr>
  <tr>
   <td>Skin Tone
   </td>
   <td>All
   </td>
   <td>All
   </td>
  </tr>
  <tr>
   <td>Operation Temperature*
   </td>
   <td>-30 C to +50 C
   </td>
   <td>-30 C to +50 C
   </td>
  </tr>
  <tr>
   <td>EMC compliance
   </td>
   <td>FCC Class A or equivalent
   </td>
   <td>FCC Class A or equivalent
   </td>
  </tr>
  <tr>
   <td>Image Specification
   </td>
   <td>ISO/IEC 19794 - 5
   </td>
   <td>ISO/IEC 19794 - 5
   </td>
  </tr>
  <tr>
   <td>Exception Image Specification
   </td>
   <td>Full Frontal with FACE features, two palms next to the face, waist up photo. 6X4 mm
   </td>
   <td>N/A
   </td>
  </tr>
  <tr>
   <td>Image quality
   </td>
   <td>ICAO - Full frontal image, +/- 5 degrees rotation, 24 bit RGB, white background, 35 mm width, 45 mm height
   </td>
   <td>
   </td>
  </tr>
  <tr>
   <td>Image format
   </td>
   <td>JPEG 2000 lossless
   </td>
   <td>JPEG 2000 lossless
   </td>
  </tr>
  <tr>
   <td>FTM
   </td>
   <td>L0 - Use host based security, L1 - FTM supported security 
   </td>
   <td>L1 - FTM supported security, L2 - with tamper protection.
   </td>
  </tr>
</table>


We recommend that countries look at ergonomics, accessibility, ease of usage, and common availability of devices while choosing devices for use in registration and authentication scenarios.

---

## 4. Device Trust

MOSIP compliant devices provide a trust environment for the devices to be used in registration, KYC and auth scenarios. The trust level is established based on the device support for trusted execution.

  L1 - The trust is provided by a secure chip with secure execution environment.

  L2 - The trust is provided by a secure chip with secure execution environment and complete tamper protection and responsive across the entire device.

  L0 - The trust is provided at the software level. No hardware related trust exist. This type of compliance is used in controlled environments.

  

### Foundational Trust Module (FTM):

The foundational trust module would be created using a secure microprocessor capable of performing all required biometric processing and secure storage of keys. The foundational device trust would satisfy the below requirements.

1. The module has the ability to securely generate, store and process cryptographic keys.
2. Generation of asymmetric keys and symmetric keys with TRNG.
3. The module has the ability to protect keys from extraction.
4. The module has to protect the keys from physical tampering, temperature, frequency and voltage related attacks.
5. The module could withstand against Hardware cloning.
6. The module could withstand probing attacks
7. The module provides memory segregation for cryptographic operations and protection against buffer over flow attacks
8. The module provides ability to withstand cryptographic side channel attacks like Differential Power analysis attacks, Timing attacks.
9. CAVP validated implementation of the cryptographic algorithm.
10. The module has the ability to perform a cryptographically validatable secure boot.
11. The module has the ability to run trusted applications.

The foundational device trust derived from this module is used to enable trust-based computing for biometric capture.
The foundational device trust module provides for a trusted execution environment based on the following.
1. Secure Boot
    1. Ability to cryptographically verify code before execution.
    2. Ability to check for integrity violation of the module/device
    3. Halt upon failure.
    4. Ability to securely upgrade and perform forward only upgrades, to thwart downgrade attacks. 
    5. SHA256 hash equivalent or above should be used for all hashing requirements
    6. All root of trust is provisioned upon first boot or before
    7. All upgrades would be considered success only after the successful boot with proper hash and signature verification. 
    8. The boot should fail upon hash/signature failures and would never operate in a intermediatory state. 
    9. Maximum of 10  failed attempts should lock the upgrade process and brick the device. However chip manufactures can decide to be less than 10.

1. Secure application
    1. Ability to run applications that are trusted.
    2. Protect against downgrading of applications.
    3. Isolated memory to support cryptographic operations. 
    4. All trust are anchored during the first boot and not modifiable.

**Certification:**
The FTM should have a at least one of the following certifications in each category to meet the given requirement.

Category: Cryptographic Algorithm Implementation

    * CAVP (RSA, AES, SHA256, TRNG (DRBGVS), ECC)

Note: The supported algorithm and curves are listed [here](#cryptography)

Category:  FTM Chip
    
    * FIPS 140-2 L3 or above
    * PCI PTS 5 or above (Pre certified)
    * Common Criteria (EAL4 and above)
      * TODO:FILL IN

Category Tamper:
  
  * For L1 level compliance the FTM should support tamper evidence.
  * For L2 level compliance the FTM should support all of L1 and capabilities to adopt tamper responsiveness.

**Threats to Protect**
The FTM should protect against the following threats.

	1. Hardware cloning attacks - Ability to protect against attacks that could result in a duplicate with keys.
	2. Hardware Tamper attacks
      a. Physical tamper - No way to physically tamper and obtain it secrets. 
      b. Voltage & frequency related attacks - Should shield against voltage leaks and should prevent against low voltage. The FTM should always be in either of the state operational normally or inoperable. The FTM should never be operable when its input voltages are not met.
      c. Temperature attacks on crypto block - Low or High the FTM is expected to operate or reach inoperable state. No state in between.
	3. Differential Power Analysis attack 
	4. Probing attacks - FTM should protect its surface area against any probe related attacks.
	5. Segregation of memory for execution of cryptographic operation (crypto block should be protected from buffer overflow type attacks)
	6. Vulnerability of the cryptographic algorithm implementation
	7. Attacks against secure boot & secure upgrade
	8. TEE/Secure processor OS attack


**Foundational Trust Module Identity:**

Upon an FTM provider approved by the MOSIP adopters, the FTM provider would submit a self signed public certificate to the adopter. Let us call this as the FTM root.

The adopter would use this certificate to seed their device trust database.The FTM root and their key pairs should be generated and stored in FIPS 140-2 Level 3 or more compliant devices with no possible mechanism to extract the keys.

The foundational module upon its first boot is expected to generate a random asymmetric key pair and provide the public part of the key to obtain a valid certificate. 

The FTM provider would validate to ensure that the chip is unique and would issue a certificate with the issuer set to FTM root. 

The entire certificate issuance would be in a secured provisioning facility. Auditable upon notice by the adopters or its approved auditors.

The certificate issued to the module will have a defined validity period as per the MOSIP certificate policy document defined by the MOSIP adopters.

This certificate and private key within the FTM chip is expected to be in it permanent memory.

***_Note:_*** The validity for the chip certificate can not exceed 20 years from the date of manufacturing.

---
### Device: 

Mosip devices are most often used to collect biometrics. The devices are expected to follow the specification for all level of compliance and its usage. The mosip devices fall under the category of Trust Level 3 (TL3) as defined in MOSIP architecture. At TL3 device is expected to be whitelisted with a fully capable PKI and secure storage of keys at the hardware. 

L0 - A device can obtain L0 certification when it uses software level cryptographic library with no secure boot or FTM.  These devices will follow different device identity and the same would be mentioned as part of exception flows.

L1 - A device can obtain L1 certification when its built in secure facility with one of the certified FTM.

L2 - A device can obtain L2 certification when its build in secure facility with one of the certified FTM with tamper responsiveness. Also the device should be capable of demonstrating tamper responsiveness during its entire life time.

**Device Identity:**

It is imperative that all devices that connect to MOSIP are identifiable. MOSIP believes in cryptographic Identity as its basis for trust.

**Physical Id:** An identification mark that shows MOSIP compliance and a readable unique device serial number (minimum of 12 digits), make and model. The same information has to be available over a 2D QR Code or Barcode. This is to help field support and validation. 

**Digital Id:** A digital device Id in MOSIP would be a signed JSON (RFC 7515) as follows:
```
{
    “serialNo”: "Serial number",

    “make”: "Make of the device",

    “model” : "Model of the device",

    “type”: [“Fingerprint”, “Iris”, “Face"], //More types will be added.

    “deviceSubType”: "subtypes of the biometric device",

    “deviceProvider”: "Device provider name",

    “deviceProviderId”: "Device provider Id",

    “dateTime”: "Datetime in ISO format with timezone.  Identity request time"

}
```
Signed with the JSON Web Signature (RFC 7515) using the “Foundational Trust Module” Identity key, this data is the fundamental identity of the device.  Every MOSIP compliant device will need the foundational trust module. 

The only exception to this rule is for the L0 compliant devices that have the purpose (explained below during device registration)  as "Registration". L0 devices would sign the Digital Id with the device key.

Signed Digital Id would look as follows.
```
"digitalId": "base64urlencoded(header).base64urlencoded(payload).base64urlencoded(signature)"

```
The header in the digital id would have 
```
"alg": "RS256",
"type": "JWT",
"x5c": "<Certificate of the FTM chip, If in case the chain of certificates are sent then the same will be ignored">
```

MOSIP assumes that the first certificate in the x5c is the FTM's chip public certificate issued by the FTM root certificate.

Unsigned digital Id would look as follows.
```
"digitalId": "base64urlencoded(payload)"
```
payload is the Digital ID json object.

**Accepted Values:**:
```
    serialNo - Serial number of the device. This value should be same as printed on the device (Refer Physical ID)

    make - Brand name. This value should be same as printed on the device (Refer Physical ID)

    model - Model of the device. This value should be same as printed on the device (Refer Physical ID)

    type - [“Fingerprint”, “Iris”, “Face’’], //More types will be added.
    
    deviceSubType - subtype is based on the type. 
    
              Finger app- “Slap”, “Single”, “Touchless”
              Iris - “Single”, “Double”,
              Face - "Full face"

    deviceProvider - Device provider name, This would be a legal entity in the country,

    deviceProviderId: Device provider Id issued by MOSIP adopters
    
    dateTime:  ISO format with timezone.  The time during the issuance of this identity
```

**Keys**
List of keys used in the device and their explanation.

***Device Key***

Each biometric device would contain an authorized private key after the device registration. This key is rotated frequently based on the requirement from the respective adopter of MOSIP. By default MOSIP recommends 30 days key rotation policy for the device key. The device keys are created by the device providers inside the FTM during a successful registration.

The device keys are used for signing the biometric. More details of the signing and its usage will be [here](#devicecommunication)

This key is issued by the device provider and the certificate of the device key is issued by the device provider key which in turn is issued by the MOSIP adopter after approval of the device providers specific model.

***FTM Key***

The FTM key is the root of the identity. This key is created by the FTM provider during the manufacturing/provisioning stage. This is a permanent key and would never be rotated. This key is used to sign the Digital ID.

***MOSIP Key***

The MOSIP key is the public key provided by the MOSIP adopter. This key is used to encrypt the biometric biometric. Details of the encryption is listed below.

We recommend to rotate this key every 1 year. 

---

## <a name="devicecommunication"></a>5. Device Service - Communication Interfaces

The section explains the necessary details of the biometric device connectivity, accessibility, discoverability and protocols used to build and communicate with the device.

The device should implement only the following set of APIs.  All the API’s are independent of the physical layer and the operating system, with the invocation being different across operating systems. While the operating system names are defined in this spec a similar technology can be used for unspecified operating systems.

It is expected that the device service ensures that the device is connected  locally to the host.

### 5.1 Device Discovery:
#### Specifications for Windows and Linux

Device discovery would be used to identify MOSIP compliant devices in a system by the applications. The protocol is designed as simple plug and play with all the necessary abstraction to the specifics.
Discovery Request:

**Request:**
```
{

“type”: "type of the device"

}
```
**Accepted Values:**
```
type: “Biometric Device”, “Fingerprint”, “Face”, “Iris”

Note: “Biometric Device” - is a special type and used in case if you are looking for any biometric device.
```
**Response:**
```
[
    {    
    “deviceId”: "internal Id",
    “deviceStatus”: "device status",
    “certification”: "certification level",
    “serviceVersion”: "device service version",
    “deviceSubId”: "device sub Id’s",
    “callbackId”: "baseurl to reach to the device“,
    "digitalId": "digital id of the device",
    "deviceCode": "A unique code given by MOSIP after successful registration",
    "specVersion": ["Array of supported MDS specification version"],
    "purpose": "Auth  or Registration or empty if not registered",
    "error": {
        "errorcode": "101",
        "errorinfo": "Invalid JSON Value Type For Discovery.. 
        }
    },
    ...
]
```
**Accepted Values:**
```

deviceStatus - "Ready", "Busy", "Not Ready", "Not Registered”

certification - “L0”, “L1”, "L2" - Level of certification

serviceVersion - Version of the MDS specification that is supported.

deviceId - Internal Id to identify the actual biometric device within the device service.

deviceSubId - is the internal Id of the device. For example in case of iris capture, the device can have two modules in a single device, it is possible to address each device with a sub Id so we can identify or command each of it in isolation. Sub Id is a simple index which always starts with 1 and increases sequentially for each sub device present.

callbackId - this differs as per the OS. In case of Linux and windows operating systems it is a http URL. In the case of android, it is the intent name. In IOS it is the URL scheme. The call back url takes precedence over future request as a base URL.

digitalId - Digital id as per the Digital Id definition.  

deviceCode - A unique code given by MOSIP after successful registration,

specVersion - Array of supported MDS specification version",

purpose - Purpose of the device in the MOSIP ecosystem.

errorCode - standardized error code.
errorInfo - description of the error that can be displayed to end user. Multi lingual support. 

```
***_Note:_*** The response is an array that we could have a single device enumerating with multiple biometric options.

***_Note:_*** The service should ensure to respond only if the type parameter matches the type of device or the type parameter is a “Biometric Device”.

***_Note:_*** This response is a direct json as show in the response.


#### Windows/Linux:

All the device API will be based on the HTTP specification. The device always binds to 127.0.0.1 with any of the available ports ranging from 4501 - 4600.  The IP address used for binding has to be 127.0.0.1 and not localhost.
The applications that require access to MOSIP devices could discover them by sending the http request to the supported port range. We will call this port as the device_service_port in the rest of the document.

**_HTTP Request:_**

```
MOSIPDISC http://127.0.0.1:<device_service_port>/device
HOST: 127.0.0.1: <device_service_port>
EXT: <app name>
```

**_HTTP Response:_**

```
HTTP/1.1 200 ok
CACHE-CONTROL:no-store
LOCATION:http://127.0.0.1:<device_service_port>
Content-Length: length in bytes of the body
Content-Type: application/json
Connection: Closed
```

***_Note:_*** the pay loads are json in both the cases and are part of the body.

*callbackId would be set to the [http://127.0.0.1:<device_service_port>](http://127.0.0.1:<device_service_port>). So, the caller will use the respective http verb/method and the url to call the service.


#### Android:
All devices on an android device should listen to the following intent io.mosip.device
Upon invocation of this intent the devices are expected to respond back with the json response filtered by the respective type.

*callbackId would be set to the appId. So, the caller will create the intent appId.Info or appId.Capture

#### IOS:
All device on an IOS device would respond to the url schema as follows.
MOSIPDISC://<call-back-app-url>?ext=<caller app name>&type=<type as defined in mosip device request>
If a MOSIP compliant device service app exist then the url would launch the service. The service in return should respond back to the caller using the call-back-app-url with the base64 encoded json as the url parameter for the key data.

***_Note:_*** In IOS there are restrictions to have multiple apps registering to the same URL schema.

*callbackId would be set to the device service appname. So, the caller has to call appnameInfo or appnameCapture as the url scheme.

### 5.2 Device Info:
The device information API would be used to identify the MOSIP compliant devices and their status by the applications.


**Request:**

NONE

**Accepted Values:**

**Response:**
```
[
    {
        deviceInfo: { 
        “deviceStatus”: "current status",
        “deviceId”: "internal Id",
        “firmware”: "firmware version",
        “certification”: "certification level",
        “serviceVersion”: "device service version",
        “deviceSubId”: "device sub Id’s",
        “callbackId”: "baseurl to reach to the device“,
        "digitalId": "signed digital id as described in the digital id section of this document",
        "deviceCode": "A unique code given by MOSIP after successful registration",
        "env": "target environment",
        "purpose": "Auth  or Registration",
        "specVersion": ["Array of supported MDS specification version"],
         },
        "error": {
            "errorcode": "101",
            "errorinfo": "Invalid JSON Value "
        }
    }
    ...
]
```

The final JSON is Signed with the JSON Web Signature using the “Foundational Trust Module” Identity key, this data is the fundamental identity of the device.  Every MOSIP compliant device will need the foundational trust module.

So the API would respond in the following format.
```
[
 {
  "deviceInfo": "base64urlencode(header).base64urlencode(payload).base64urlencode(signature)"
  "error": {
     "errorcode": "100",
      "errorinfo": "Device not registered. In this case the device info will be only base64urlencode(payload)"
   }
 }
]
```

**Allowed values:**

```

deviceInfo.deviceStatus - [“Ready”, “Busy”, “Not Ready”, "Not Registered"]. This is the status of the device.
deviceInfo.deviceId - Internal Id to identify the actual biometric device within the device service.
deviceInfo.firmware - Exact version of the firmware, In case of L0 this is same as serviceVersion.
deviceInfo.certification - “L0”, “L1” - Level of certification.
deviceInfo.serviceVersion - Version of the current service.
deviceInfo.deviceSubId - is the internal id of the device. In case of iris when we have two iris capture modules in a single device, it is possible to address each device with a sub Id so we can identify or command each of it in isolation. This in an index that always starts with 1 and increments sequentially.
deviceInfo.callbackId - base URL to communicate.
deviceInfo.digitalId - as defined under the digital id section.
deviceInfo.env - "None" if not registered. If registered, then send the registered env "Staging", "Developer", "Pre-Production", "Production"
deviceInfo.purpose - "Auth" or "Registration" or empty in case the status is "Not Registered".
deviceInfo.specVersion - "Array of MDS specification version".
error - relevant errors as defined under the "Error section" of this document.

```
**_Note_**: The response is an array that we could have a single device enumerating with multiple biometric options.

**_Note_**: The service should ensure to respond only if the type parameter matches the type of device or the type parameter is a “Biometric Device”.

#### Windows/Linux:
The applications that require more details of the MOSIP devices could get them by sending the http request to the supported port range.

**_HTTP Request:_**
```
MOSIPDINFO http://127.0.0.1:<device_service_port>/info
HOST: 127.0.0.1:<device_service_port>
EXT: <app name>
```

**_HTTP Response:_**
```
HTTP/1.1 200 ok
CACHE-CONTROL:no-store
LOCATION:http://127.0.0.1:<device_service_port>
Content-Length: length in bytes of the body
Content-Type: application/json
Connection: Closed
```

Note: the pay loads are json in both the cases and are part of the body.

#### Android:
On an android device should listen to the following intent appId.Info
Upon invocation of this intent the devices are expected to respond back with the json response filtered by the respective type.

#### IOS:
On an IOS device would respond to the url schema as follows.
APPIDINFO://<call-back-app-url>?ext=<caller app name>&type=<type as defined in mosip device request>
If a MOSIP compliant device service app exist then the url would launch the service. The service in return should respond back to the called using the call-back-app-url with the base64 encoded json as the url parameter for the key data.

Note: In IOS there are restrictions to have multiple app registering to the same URL schema.

### 5.3 Capture:
The capture request would be used to capture a biometric from MOSIP compliant devices by the applications.  The capture call will respond with success to only one call at a time. So in case of a parallel call the device info details are sent with status as “Busy”

Capture Request:

**Request:**

```
{
    “env”:  "target environment",
    "purpose": "Auth  or Registration",
    "specVersion": "expected version of the MDS spec",
    "timeout" : <timeout for capture>,
    “captureTime”: <time of capture request in ISO format including timezone>,
    "domainUri": <uri of the auth server>,
    “transactionId”: <transaction Id for the current capture>,

    “bio”: [
        {
            “type”: <type of the biometric data>,
            “count”:  <fingerprint/Iris count, in case of face max is set to 1>,
            "bioSubType": ["Array of subtypes"],
            “requestedScore”: <expected quality score that should match to complete a successful capture>,
            “deviceId”: <internal Id>,
            “deviceSubId”: <specific device Id>,
            “previousHash”: <hash of the previous block>
        }
    ],
    customOpts:
    {
        //max of 50 key value pair. This is so that vendor specific parameters can be sent if necessary. The values cannot be hard coded and have to be configured by the apps server and should be modifiable upon need by the applications. Vendors are free to include additional parameters and fine-tuning parameters. None of these values should go undocumented by the vendor. No sensitive data should be available in the customOpts.
    }

}
```

**Allowed Values:**

```

env - Allowed values are Staging| Developer| Pre-Production | Production

purpose - Allowed values are Auth| Registration

specVersion - version of the biometric block as specified in the authentication or customer registration specification.

timeout - Max time the app will wait for the capture. Its expected that the api will respond back before timeout with the best frame. All timeouts are in milliseconds

captureTime - time of capture in ISO format with timezone. The time is as per the requesting application.

domainUri - unique uri per auth providers. This can be used to federate across multiple providers or countries or unions.

transactionId - unique Id of the transaction. This is an internal Id to the application thats providing the service. Use different id for every successful auth. So even if the transaction fails after auth we expect this number to be unique.

bio.type -  “FIR” , “IIR”, “Face”

bio.count - number of biometric data that is collected for a given type. The device should validate and ensure that this number is in line with the type of biometric that's captured.

bio.bioSubType - “LF_INDEX”, “LF_MIDDLE”, “LF_RING”, “LF_LITTLE”,  “LF_THUMB” “RF_INDEX”, “RF_MIDDLE”, “RF_RING”, “RF_LITTLE”,  “RF_THUMB”, “L_IRIS”, “R_IRIS”, "UNKNOWN"

bio.requestedScore - what is the expected quality? Upon reaching the necessary quality the biometric device is expected to auto capture the image.

bio.deviceId - a unique Id per device service. In case a single device handles both face and iris the device Id will identify iris and camera uniquely. In case the Id is sent as 0 then the device is expected to capture biometric from both the devices.

bio.deviceSubId  - a specific device sub Id.  Should be set to 0 if we don't know any specific device sub Id.

bio.previousHash - For the first capture the previousHash is hash of empty utf8 string. From the second capture the previous captures hash (as hex encoded) is used as input. This is used to chain all the captures across modalities so all captures have happened for the same transaction and during the same time period. 

customOpts - If in case the device vendor has additional parameters that they can take and act accordingly then those values can be sent by the application developers to the device service.
```

**Response:**

```
[

        {
          "specVersion" : "MDS spec version",
          "data": {	

            "digitalId" : "digital Id as described in this document",

            "deviceCode": "A unique code given by MOSIP after successful registration",

            "deviceServiceVersion": "Service version",

            "bioType": "FIR",

            "bioSubType": "UNKNOWN",
            
            "purpose": "Auth  or Registration",

            "env":  "target environment",

            "domainUri": "uri of the auth server",

            "bioValue": "encrypted with session key and base64urlencoded biometric data",

            "transactionId": "unique transaction id",

            "timestamp": "ISO format datetime with time zone",

            "requestedScore": "floating point number to represent the minimum required score for the capture",

            "qualityScore": "floating point number representing the score for the current capture"

          },

          "hash": "sha256(sha256 hash in hex format of the previous data block + sha256 hash in hex format of the current data block before encryption)",

          "sessionKey": "encrypted with MOSIP public key (dynamically selected based on the uri) and encoded session key biometric",

          "error": {

        "errorcode": "101",

        "errorinfo": "Invalid JSON Value"

    }

    },

        {
          "specVersion" : "MDS spec version",
          "data": {

            "digitalId": "digital Id as described in this document",
 
            "deviceCode": "A unique code given by MOSIP after successful registration",

            "deviceServiceVersion": "Service version",

            "bioType": "FIR",

            "bioSubType": "LEFT",

            "purpose": "Auth  or Registration",
            
            "env":  "target environment", 
            
            "domainUri": "uri of the auth server",          

            "bioValue": "encrypted with session key and base64urlencoded biometric data",

            "transactionId": "unique transaction id",

            "timestamp": "ISO Format date time with timezone"

          },

          "hash": "sha256(sha256 hash in hex format of the previous data block + sha256 hash in hex format of the current data block before encryption)",

          "sessionKey": "encrypted with MOSIP public key and encoded session key biometric",

          "thumbprint": "SHA256 thumbprint of the certificate that was used for encryption of session key",

          "error": {

             "errorcode": "101",

              "errorinfo": "Invalid JSON Value"

         }

    }

]
```

**Accepted Values:**
```
data.bioValue - Encrypted and Encoded to base64urlencode biometric value. AES GCM encryption with a random key. The IV for the encryption is set to last 16 digits of the timestamp. ISO formatted bioValue. Look at the Authentication document to understand more about the encryption.  

data.timestamp - Time as per the biometric device. Note: The biometric device is expected to sync its time from the management server at regular intervals so accurate time could be maintained on the device.

hash - the value of the previousHash attribute in the request object or the value of hash attribute of the previous data block (used to chain every single data block) concatenated with the hex encode sha256 hash of the current data block before encryption.  

sessionKey - Random AES key used for the encryption of the bioValue. The encryption key is encrypted using the public key with recommended algorithm. Sent as base64urlencoded

```

data - The entire data object is stored as follows. 

```
"data" : "base64urlencode(header).base64urlencode(payload).base64urlencode(signature)

payload - is defined as the entire byte array of data block. 

```

#### Windows/Linux:

The applications that requires to capture biometric data from a MOSIP devices could do so by sending the http request to the supported port range.

**_HTTP Request:_**

CAPTURE [http://127.0.0.1:<device_service_port>/capture](http://127.0.0.1/capture)

HOST: 127.0.0.1: <apps port>

EXT: <app name>

**_HTTP Response:_**

```
HTTP/1.1 200 ok

CACHE-CONTROL:no-store

LOCATION:[http://127.0.0.1](http://127.0.0.1):<device_service_port>

Content-Length: length in bytes of the body

Content-Type: application/json

Connection: Closed
```

Note: the pay loads are json in both the cases and are part of the body.

#### Android:

All device on an android device should listen to the following intent appid.capture

Upon this intend the devices are expected to respond back with the json response filtered by the respective type.

#### IOS:

All device on an IOS device would respond to the url schema as follows.

APPIDCAPTURE://<call-back-app-url>?ext=<caller app name>&type=<type as defined in mosip device request>

If a MOSIP compliant device service app exist then the url would launch the service. The service in return should respond back to the called using the call-back-app-url with the base64 encoded json as the url parameter for the key data.

### 5.4 Device Stream
The device would open a stream channel to send the live video streams. This would help when there is an assisted operation to collect biometric.  Please note the stream API’s are available only for registration environment.

**Device Stream Request:**

Used only for the registration module compatible devices. This api is visible only for the devices that are registered for the purpose as "Registration".

**Request:**

```
{
    “deviceId”: "internal Id",
    “deviceSubId”: "device sub Id’s",
}
```

**Accepted Values:**

```
deviceId - Internal Id
deviceSubId - The sub id of the device thats responsoible to stream the data.
```

**Response:**

Live Video stream with quality of 3 frames per second or more using M-JPEG2000 https://en.wikipedia.org/wiki/Motion_JPEG

**_Note:_** Preview should have the quality markings and segment marking. The preview would also be used to display any error message to the user screen. All error messages should be localized.


#### Windows/Linux:

The applications that require more details of the MOSIP devices could get them by sending the http request to the supported port range.

**_HTTP Request:_**

STREAM   http://127.0.0.1:<device_service_port>/stream

HOST: 127.0.0.1: <apps port>

EXT: <app name>

**_HTTP Response:_**

HTTP Chunk of frames to be displayed. Minimum frames 3 per second

#### Android:

No support for streaming

#### IOS:

No support for streaming

### 5.5 Device Registration Capture:

The registration client application will discover the device. Once the device is discovered the status of the device is obtained with the device info API. During the registration the registration client sends the RCAPTURE API and the response will provide the actual biometric data in a digitally signed non encrypted form.   When the Device Registration Capture API is called the frames should not be added to the stream. The device is expected to send the images in ISO format.

The requestedScore is in the scale of 1-100. So, in cases where you have four fingers the average of all will be considered for capture threshold. The device would always send the best frame during the capture time even if the requested score is not met.

**Device Registration Capture Request:**

The API is used by the devices that are compatible for the registration module. This API should not be supported by the devices that are compatible for authentication.

**Request:**

```
{

“env”:  "target environment",

"specVersion": "expected MDS spec version",

"timeout": "timeout for registration capture",

“captureTime”: "time of capture request in ISO format including timezone",

“registrationId”: "registration Id for the current capture",

“bio”: [
  	{

     	“type”: "type of the biometric data",
			“count”:  "fingerprint/Iris count, in case of face max is set to 1",
			“exception”: ["finger or iris to be excluded"],
			“requestedScore”: "expected quality score that should match to complete a successful capture.",
			“deviceId”: "internal Id",
			“deviceSubId”: "specific device Id",
			“previousHash”: "hash of the previous block"
  	}
],

customOpts:

{

    //max of 50 key value pair. This is so that vendor specific parameters can be sent if necessary. The values cannot be hard coded and have to be configured by the apps server and should be modifiable upon need by the applications. Vendors are free to include additional parameters and fine-tuning parameters. None of these values should go undocumented by the vendor. No sensitive data should be available in the customOpts.

 }

}
```

**Accepted Values:**

```
env - Allowed values are Staging| Developer| Pre-Production | Production

specVersion - version of the biometric block as specified in the registration specification.

timeout - Max time the app will wait for the capture.

captureTime - time of capture in ISO format with timezone, This is time as per the request application.

bio.type - “FIR” , “IIR”, “Face”

bio.count - number of biometric data that is collected for a given type. The device should validate and ensure this number is in line with the type of biometric that's captured.

bio.exception: “LF_INDEX”, “LF_MIDDLE”, “LF_RING”, “LF_LITTLE”,  “LF_THUMB” “RF_INDEX”, “RF_MIDDLE”, “RF_RING”, “RF_LITTLE”,  “RF_THUMB”, “L_IRIS”, “R_IRIS”. This is an array and all the exceptions are marked. In case of an empty element assume there is no exception. In case exceptions are sent for face then follow the exception photo specification above.

bio.requestedScore - what is the expected quality? Upon reaching the necessary quality the biometric device is expected to auto capture the image.

bio.deviceId - a unique Id per device service. In case a single device handles both face and iris the device Id will identify iris and camera uniquely. In case the Id is sent as 0 then the device is expected to capture biometric from both the devices.

bio.deviceSubId  - a specific device sub Id.  Should be set to nothing if we don't know any specific device sub Id. In case of Fingerprint/IRIS its 1 for left and 2 for right fingerprint/iris. 3 for thumb/two iris. The device id could be used to enable a specific feature in the scanner appropriate for that biometric feature. For eg: if we need to get only a left Iris in a binocular scanner then we can use the sub id.

bio.previousHash - For the first capture the previousHash is hash of empty utf8 string. From the second capture the previous captures hash (as hex encoded) is used as input. This is used to chain all the captures across modalities so all captures have happened for the same transaction and during the same time period.
```

**Response:**

```
{"biometrics": [

        {
          "specVersion" : "MDS Spec version",
          
          "data": {	

            "digitalId": "digital id of the device as per the Digital Id definition..",

            "bioType": "Biometric type",

            "deviceCode": "A unique code given by MOSIP after successful registration",

            "deviceServiceVersion": "",

            "bioSubType": “LF_INDEX”,

            "purpose": "Auth  or Registration",
            "env":  "target environment",

            "bioValue": "<base64urlencoded extracted biometric (ISO format)>",

            "registrationId": "1234567890",

            "timestamp": "2019-02-15T10:01:57.086+05:30",

            "requestedScore": "<floating point number to represent the minimum required score for the capture. This ranges from 0-100>",

            "qualityScore": "<floating point number representing the score for the current capture. This ranges from 0-100>"

          },

          "hash": "sha256(sha256 hash in hex format of the previous data block + sha256 hash in hex format of the current data block)",         

         "error": {

        "errorcode": "101",

        "errorinfo": "Invalid JSON Value Type For Discovery.. ex: {type: 'Biometric Device' or 'Fingerprint' or 'Face' or 'Iris' } "

    }

        },

        {
          "specVersion" : "MDS Spec version",
          "data": {

            "deviceCode": "",

            "bioType" : "Iris",

            "digitalId": "digital id of the device as per the Digital Id definition.", 

            "deviceServiceVersion": "",

            "bioSubType": "L_IRIS",

            "purpose": "Auth  or Registration",
            "env":  "<target environment>",             

            "bioValue": "<base64urlencoded extracted biometric (ISO format)>",

            "registrationId": "1234567890",

            "timestamp": "2019-02-15T10:01:57.086+05:30"

          },

          "hash": "sha256(sha256 hash in hex format of the previous data block + sha256 hash in hex format of the current data block before encryption)",

    "error": {

            "errorcode": "101",

            "errorinfo": "Invalid JSON Value Type For Discovery.. ex: {type: 'Biometric Device' or 'Fingerprint' or 'Face' or 'Iris' } "

        }

        }

      ]
}
```

**Accepted Values:**
```
data - base64urlencode(header).base64urlencode(payload).base64urlencode(signature)

data.bioType - “FIR” , “IIR”, “Face”

data.bioSubType - “LF_INDEX”, “LF_MIDDLE”, “LF_RING”, “LF_LITTLE”,  “LF_THUMB” “RF_INDEX”, “RF_MIDDLE”, “RF_RING”, “RF_LITTLE”,  “RF_THUMB”, “L_IRIS”, “R_IRIS”

data.timestamp - Time as per the biometric device. Note: The biometric device is expected to sync its time from the management server at regular intervals so accurate time could be maintained on the device.

```
#### Windows/Linux: 

The applications that require more details of the MOSIP devices could get them by sending the http request to the supported port range.

**_HTTP Request:_**

RCAPTURE  http://127.0.0.1:<device_service_port>/capture

HOST: 127.0.0.1: <apps port>

EXT: <app name>

**_HTTP Response:_**

HTTP response.

#### Android:

No support for Registration Capture

#### IOS:

No support for Registration Capture

---

## 6. Device Server

The device server exposes two external device APIs to manage devices. These will be consumed from Management Server created by the device provider. Refer to the subsequent section in this document.

### 6.1 Registration:
The MOSIP server would provide the following device registration API which is whitelisted to the management servers of the device provider or their partners.

***_Note:_*** This API is exposed by the MOSIP server to the device providers.

**Version:** v1

http://device.mosip.io/device/register

HTTP Request

Type: POST

```
{

  "id": "io.mosip.deviceregister",

  "request": {

    "deviceData": "JWT of the below device data"

  },

  "requesttime": "current timestamp in ISO format from management server",

  "version": "registration server api version as defined above"

}
```

**Device Data:**

```


“deviceData”: { 

“deviceId”: "unique Id to identify a biometric capture device",

"purpose": "Auth  or Registration. Can not be empty",

“deviceInfo”: {
    “deviceSubId”: "an array of sub Ids that are available",
    
    “certification”:  "certification level",

    "digitalId": "signed digital id of the device",

    “firmware”: "firmware version",

    “deviceExpiry”: "device expiry date",

    “timestamp”:  "ISO format datetime with timezone from device"
    },
    “foundationalTrustProviderId” : "foundation trust provider Id, in case of L0 this is empty"
  }
```
**Accepted Values:**

```
deviceId - Unique device id that the device provider uses to identify the device. (This can also be serial no if the device provider is sure of maintaining the uniqueness across all their devices)

digitalId - Digital id is signed by the FTM chip key in L1. In case of L0 the digital id is signed by the device key. 

***__Note:__ During the registration of L0 devices please sign using the key thats generated inside the device and send the public key in x509 encoded spec form. After successful registration the management server should issue a certificate against the same public key as a response to the registration call.

```
device data is sent in the following format.

"deviceData" : base64urlencode(header).base64urlencode(payload).base64urlencode(signature)

payload is the object in deviceData.

The request is signed with the device provider key at the management server.

**Response:**

```
{
    "id": "io.mosip.deviceregister",

    "version": "registration server api version as defined above",

    "responsetime": "iso time format",

    "response": "JWT of the below device data",

    “error”: [{ //Filled in case of error. remaining keys above are dropped in case of errors.

   	 "code": "error code if registration fails",

   	 "message": "description of the error code",

    } ]

}

```
**Definition of response:**

```

"response": {

    “status”:  "registration status",

    "digitalId": "digital id of the device a sent by the request", 

    "deviceCode": "UUID RFC4122 Version 4 for the device issued by the mosip server",

    "timestamp": "timestamp in ISO format",

    "env": "prod/development/stage"

 }


```
The response is of the following format
```
"response" : base64urlencode(header).base64urlencode(payload).base64urlencode(signature)
```
The response should be sent to the device. The device is expected to store the deviceCode within its storage in a safe manner. This device code is used during the capture stage.

***_Note:_*** The device once registered for a specific purpose can not be changed after successful registration. The device can only be used for that specific mosip process.

### 6.2 De-Register:
http://device.mosip.io/device/deregister

**Version:** v1

HTTP Request

Type: POST

**Request:**

```
{
  "id": "io.mosip.devicederegister",
  "version": "de-registration server api version as defined above",
  "request": { 
      "device": {
      “deviceCode”: "<device code>",
      “env”: "<environment>"
    }
  }
  "requesttime": "current timestamp in ISO format",
   “error”: [{ //Filled in case of error. remaining keys above are dropped in case of errors.

   	 "code": "error code if registration fails",

   	 "message": "description of the error code",

    } ]
}
```
The entire request is sent as a JWT format. So the final request will look like

```
"request": {
  "device" : "base64urlencode(header).base64urlencode(payload).base64urlencode(signature)"
}
```


**Response:**
```
   {
     "id": "io.mosip.devicederegister",
     "version": "de-registration server api version as defined above",
     "responsetime": "iso time format",
     "response" {
       "status": "Success",
       "deviceCode": "<device code>",
       "env": "<environment>",
       "timestamp": "timestamp in ISO format",
       "error": {
         "code" : "<error code if de-registration fails>",
         "message" : "<human readable description of the error code>"
         }
       }
       
   }

```
The entire response is sent as a JWT format. So the final response will look like

```
  "response" : "base64urlencode(header).base64urlencode(payload).base64urlencode(signature)"
```
---


### 6.2 Certificates:
http://device.mosip.io/device/encryptioncertficates

**Version:** v1

HTTP Request

Type: GET

**Request:**

```
{
  "id": "io.mosip.auth.country.certificate",
  "version": "de-registration server api version as defined above",
  request: {
    "country" : "if empty return the current certificate, if a country is defined then send out the countries keys"
  },
  "requesttime": "current timestamp in ISO format"
}
```
The request is sent as a JWT format. So the final request will look as below.

```
  request : {
    "country": "base64urlencode(header).base64urlencode(payload).base64urlencode(signature)"
    }
```


**Response:**
```
   {
     "id": "io.mosip.auth.country.certificate",
     "version": "de-registration server api version as defined above",
     "responsetime": "iso time format",
     "response" [{
       "certificate": "base64encoded certificate as x509 V3 format"
       }]
   }

```
The entire response is sent as a JWT format. So the final response will look like

```
  "response" : "base64urlencode(header).base64urlencode(payload).base64urlencode(signature)"
```
---

## 7. Management Server Functionalities and Interactions

The management server has the following objectives.
1. Validate the devices to ensure its a genuine device from the respective device provider. This can be achieved using the device info and the certificates for the Foundational Trust Module.
1. Register the genuine device with the MOSIP device server.
1. Manage/Sync time between the end device the server. The time to be synced should be the only trusted time accepted by the device.
1. Ability to issue commands to the end device for
    1. De-registration of the device (Device Keys)
    1. Collect device information to maintain, manage, support and upgrade a device remotely.
1. A central repository of all the approved devices from the device provider.
1. Safe storage of keys using HSM FIPS 140-2 Level 3. These keys are used to issue the device certificate upon registration.
The Management Server is created and hosted by the device provider outside of MOSIP software. The communication protocols between the MDS and the Management Server can be decided by the respective device provider. Such communication should be restricted to the above specified interactions only. No transactional information should be sent to this server.
1. Should have the ability to push updates from the server to the client devices.


### Management Client
Management client is the interface that connects the device with the respective management server. Its important that the communication between the management server and its clients are designed with scalability, robustness, performance and security. The management server may add many more capabilities than what is described here, But the basic security objectives should be met at all times irrespective of the offerings. 

1. For better and efficient handling of device at large volume, we expect the devices to auto register to the Management server.
1. All communication to the server and from the server should follow that below properties.
  a) All communication are digitally signed with the approved algorithms 
  b) All communication to the server are encrypted using one of the approved public key cryptography.
  c) All request has timestamps attached in ISO format to the milliseconds inside the signature.
  d) All communication back and fourth should have the signed digital id as one of the attribute.
1. Its expected that the auto registration has an absolute way to identify and validate the devices.
1. The management client should be able to detect the devices in a plug and play model.
1. All key rotation should be triggered from the server.
1. Should have the ability to detect if its speaking to the right management server.
1. All upgrades should be verifiable and the client should have ability to verify software upgrades. 
1. Should not allow any downgrade of software.
1. Should not expose any API to capture biometric. The management server should have no ability to trigger a capture request.
1. No logging of biometric data is allowed. (Both in the encrypted and unencrypted format)

---

## 8. Compliance

L2 Certified Device / L2 Device - A device certified as capable of performing encryption on the device inside its trusted zone with tamper responsive features

L1 Certified Device / L1 Device - A device certified as capable of performing encryption on the device inside its trusted zone.

L0 Certified Device / L0 Device - A device certified as one where the encryption is done on the host inside its device driver or the MOSIP device service.

### Secure Provisioning

Secure provisioning is applicable to both the FTM and the Device providers. 

1. The devices and FTM should have a mechanism to protect against fraudulent attempts to create or replicate.
1. The device and FTM trust should be programmed in a secure facility which is certified by the respective MOSIP adopters. 
1. Organization should have mechanism to segregate the FTM's and Devices built for MOSIP using cryptographically valid and repeatable process.
1. All debug options within the FTM or device should be disabled permanently
1. All key creations need for provisioning should happen automatically using FIPS 140-2 Level 3 or higher devices. No individual or a group or organization should have mechanism to influence this behavior.
1. Before the devices/FTM leaving the secure provisioning facility all the necessary trust should be established and should not be re-programable. 



### Compliance Level

<table>
  <tr>
   <td>API
   </td>
   <td>Compatible
   </td>
  </tr>
  <tr>
   <td>Device Discovery
   </td>
   <td>L0/L1/L2
   </td>
  </tr>
  <tr>
   <td>Device Info
   </td>
   <td>L0/L1/L2
   </td>
  </tr>
  <tr>
   <td>Capture
   </td>
   <td>L1/L2
   </td>
  </tr>
  <tr>
   <td>Registration Capture
   </td>
   <td>L0/L1/L2
   </td>
  </tr>
</table>

---

## <a name="cryptography"></a> 9. Cryptography
Supported algorithm

<table>
<tr> <th> Usage </th> <th>Algorithm</th> <th> Key Size </th> <th> Storage </th> </tr>
<tr> <td> Encryption of biometrics - Session Key </td> <td>AES</td> <td> >=256 </td> <td> No storage, Key is created with TRNG/DRBG inside FTM </td> </tr>
<tr> <td> Encryption session key data outside of FTM </td> <td>RSA OAEP</td> <td> >=2048 </td> <td> FTM trusted memory </td> </tr>
<tr> <td> Encryption session key data outside of FTM </td> <td>ECC curve 25519</td> <td> >=256 </td> <td> FTM trusted memory </td> </tr>

<tr> <td> Biometric Signature </td> <td>RSA </td> <td> >=2048 </td> <td> Key never leaves FTM created and destroyed </td> </tr>
<tr> <td> Biometric Signature </td> <td>ECC curve 25519</td> <td> >=256 </td> <td> Key never leaves FTM created and destroyed </td> </tr>

<tr> <td> Secure Boot </td> <td>RSA </td> <td> >=256 </td> <td> FTM trusted memory </td> </tr>
<tr> <td> Secure Boot </td> <td>ECC curve 25519</td> <td> >=256 </td> <td> FTM trusted memory </td> </tr>
</table>

**_Note_** No other ECC curves supported.

## 10. [Error Codes](#errorcodes)

<table>
<tr> <td>0</td> <td> Success </td> </tr>
<tr> <td>100</td> <td> Device not registered </td> </tr>
<tr> <td>101</td> <td> Unable to detect a biometric object </td> </tr>
<tr> <td>102</td> <td> Technical error during extraction. </td> </tr>
<tr> <td>103</td> <td> Device tamper detected </td> </tr>
<tr><td>104</td> <td> Unable to connect to management server </td> </tr>
<tr><td>105</td> <td> Image orientation error </td> </tr>
<tr><td>106</td> <td> Device not found </td> </tr>
<tr><td>107</td> <td> Device public key expired </td> </tr>
<tr><td>108</td> <td> Domain public key missing </td> </tr>
<tr><td>109</td> <td> Requested number of biometric (Finger/IRIS) not supported</td> </tr>
<tr> <td>5xx</td> <td> Custom errors. The device provider is free to choose his error code and error messages. </td> </tr>
</table>