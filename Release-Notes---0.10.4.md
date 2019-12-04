## Table Of Contents

- [Scope](#scope-)
- [Documentation](#documentation-)
- [Key Points](#key-points-)
- [Code](#code-)
- [Test Reports](#test-reports-)
  * [1. In scope](#1-in-scope-)
  * [2. Not in scope](#2-out-of-scope--mosip-v01215-platform-)
  * [3. Executive Summary – Consolidated Quality Status](#3-executive-summary--consolidated-quality-status-)
  * [4. Types of Testing](#4-types-of-testing-)
  * [5. Test Execution Summary](#5-test-execution-summary-)
  * [6. Automation Test Reports](#6-automation-test-reports-)
- [Known Issues](#known-issues-)
- [Support Process (To Be Determined)](#support-process-to-be-determined-)
- [List Of Acronyms](#list-of-acronyms-)
## Scope [**[↑]**](#table-of-contents)
This release is with **real biometrics**. This means that MOSIP Platform is now integrated with SDK, MDS (MOSIP  Device Service), ABIS (Automated Biometrics Identification System) and Biometric devices. Also, this version is tested for Biometric functionalities. Non-functional requirements (Performance, Scale and Security) will be taken up in subsequent releases.

* Modules included – Pre-Registration, Registration Client, Registration Processor, ID Authentication, Administration, Reference GUI implementation of Pre-Registration and Registration Client. 
* Modules not included – Partner Management, Resident Services, Reference GUI implementation of Administration

Module-wise features released as part of this release can be found [here]()

## Documentation [**[↑]**](#table-of-contents)
### 1. Platform Documentation 
Includes Functional requirements, Process flows, Architecture and High level design, Getting started and Deployment guide, Developer documentation etc.  
   [**Link to Platform Documentation**](Platform-Documentation)
### 2. Detailed Documentation
[**Low Level design**](https://github.com/mosip/mosip-platform/tree/master/design) and [**Test cases excel**](https://github.com/mosip/mosip-functional-tests/wiki/_files/testing/Test_automation/MOSIP-TCs-V1.0.xlsx)

## Key Points [**[↑]**](#table-of-contents)

|Key Points|	Details|
|----|----|
|Pre Registration - Browser support |	Chrome 74.0.3729)|
|Deployment Script Environment|	Microsoft Azure|
|Registration Client – OS version|	Windows 10 (English version)  with TPM 2.0|
|Camera|	Logitech / Default windows camera|
|Scanner|	Canon lide 120|
|GPS|	GlobalSat BU-353-S4|
|Biometrics standard|	CBEFF format (Version - 0.9.0)|
|MOSIP Device Service (MDS)|	[Version - 0.9.2](https://github.com/mosip/mosip-docs/wiki/MOSIP-Device-Service-Specification/5495eff4efe79718b4bb57cd95178e917d517671)|
|SMS gateway|	MSG91, Infobip|
|Registration Client – face capture |	OpenImaj - This is licensed for demo purpose only|
|Keystore|	SoftHSM|
|Antivirus|	ClamAV|
|Maps	|OpenstreetMap|
|Supporting key based digital signatures, not using digital certificates||	
|Transliteration|	ICU4J (Library with French, Arabic languages)|

## Code [**[↑]**](#table-of-contents)
The [code](https://github.com/mosip/mosip-platform/releases/tag/0.10.3) and [automation tests](https://github.com/mosip/mosip-functional-tests) are available on GitHub. The code needs to be built and deployed as per the procedure documented in [**Building And Deploying MOSIP**](Platform-Documentation#9-building-and-deploying-mosip). We will actively support System Integrators during their first deployment.

## Tests [**[↑]**](#table-of-contents)
**Testing Scope**
#### 1. In Scope [**[↑]**](#table-of-contents)

|Title	|Description|
|------|------|
|Modules Tested|<li> Pre-registration (UI & Server) <li> Registration Client (UI & APIs) <li> Kernel (APIs) <li> Registration Processor (Server) <li> ID Authentication (APIs) <li> ID Repo (APIs)|
| Version Tag Tested|	0.9.0|
|Test Methodology| <li>  Manual <li>  Test Automation|
|Types of testing|<li>	 Smoke <li> Functional <li>  Integration <li> 	Regression|
|Testing Levels|![Image](_images/test_rig_automation/image1.jpg) |
|Configuration Parameters tested for| Refer to QA env properties file with suffix ‘qa’ in the filename, at [**Link**](https://github.com/mosip/mosip-config)|
|Browser Support|**Pre-Registration**    <li> Chrome – 74.0.3729.169|
|OS Support|**Registration Client**    <li> Windows 10|
|Language Support|French, Arabic, English|

#### 2. Not in Scope [**[↑]**](#table-of-contents)

|Title|	Description|
|------|------|
|NFR Testing| <li> Scalability Testing <li> Performance Testing <li> Security Testing|
|Configuration Testing|<li> Testing is done for one set of approved production configuration <li> Changing the configuration parameters for various values (boundary values) and testing the impact of each such value on the platform code will be taken up in subsequent releases.|

#### 3. Executive Summary – Consolidated Quality Status [**[↑]**](#table-of-contents)

|Sl. No.|	Module / Activity|Test Methodology|	Test Status|
|------|------|------|------|
|1|	Kernel	|<li> Test Automation	|PASS|	
|2|	Pre-Registration|<li> Tested Manually <li> Test Automation|PASS |
|3|	Registration Client|<li> Tested Manually <li> Test Automation|PASS|
|4|Registration Processor|<li> Tested Manually <li> Test Automation	|PASS |
|5|	ID Authentication	|	<li>  Test Automation	|PASS|
|6|	ID Repo	|	<li> Test Automation	|PASS|	
|7|Pre-Registration to Registration Client integration testing|	<li> Tested Manually|PASS	|	
|8|	Registration Client to Registration Processor integration testing|	<li> Tested Manually|PASS|	
|9|	Registration Processor to Pre-Registration integration testing|<li>  Tested Manually|PASS	|	
|10|	Registration Processor to Registration Client integration testing|<li> 	Tested Manually|PASS|
|11|	Registration Client to IDA integration testing|<li> 	Tested Manually|PASS		|
|12|	Registration Processor to IDA integration testing|<li> 	Tested Manually|PASS|
|13|	IDA to ID Repo|<li> 	Tested Manually|PASS	|
|14|Kernel API integration|	<li> Tested Manually <li> Test Automation|	PASS|
|15|	End to end functional testing|	<li> Tested Manually|PASS|	

#### 4. Types of Testing [**[↑]**](#table-of-contents)

|Testing Type| Description|
|------|------|
|Smoke Testing|Tests to ensure basic workflows work fine|
|Functional Testing|Tests to ensure functionality of each module and overall system work fine in accordance with the given requirements|
|Integration Testing|Tests to ensure the inter module functionality works fine and in accordance with the integration requirements|
|Regression Testing|Tests to ensure that any change doesn't break existing functionality|
	
#### 5. Test Execution Summary [**[↑]**](#table-of-contents)
![Image](_images/test_rig_automation/Capture.JPG)  

#### 6. Automation Test Reports [**[↑]**](#table-of-contents)
[**Automation report run on 0.9.0 on QA env**](/mosip/mosip/tree/master/docs/testing/Automation%20Test%20Reports)
## Known Issues [**[↑]**](#table-of-contents)
![Image](_images/test_rig_automation/image4.jpg) 
To Be updated

|Module|Issue Description|Issue ID|
|----|----|----|
|ID-Repository|ID tag in response should be mosip.vid.deactivate or reactivate for Deactivate/Reactivate VID Api|MOS-28700|
|ID-Authentication|Internal OTP Authentication not working|MOS-28722|
|ID-Authentication|Incorrect error message is displayed when there is a mismatch in the identity type in OTP Authentication|MOS-28208|
|ID-Authentication|OTP Generate service with for internal authentication does not validate allowed ID Types|MOS-28663|
|ID-Authentication|Email content should properly template it for OTP and auth email notfication|MOS-28713|
|ID-Authentication|Valid response should come for internal/authtypes/status api|MOS-28966|
|ID-Authentication|There should not be "null" value in lock and unlock UIN or VID response|MOS-28965|
|ID-Authentication|ID Validation should happen for Lock and Unlock  UIN/VID Api|MOS-28964|
|Registration-Client|Scan pop up gets retained after app gets logout|MOS-27928|
|Registration-Client|Not all QA property value changes are getting synced using "Sync" in-home screen|MOS-27986|
|Registration-Client|Exception photo is displayed in preview and acknowledgment screen for non-exception packets|MOS-28007|
|Registration-Client|File status pop up gets retained after app gets logout|MOS-27986|
|Registration-Client|Unable to download pre-registration data either by fetching PRID or by bulk download|MOS-28667|
|Registration-Client|Application fails to displays navigation away alert when a user clicks new registration on ack screen|MOS-28808|
|Registration-Client|Application fails to alert the user to capture exception photo for low-quality biometric exception scenario|MOS-28807|
|Registration-Client|Unable to create a packet with low-quality biometric scenario|MOS-28805|
|Registration-Client|Iris count for child packet is displayed as "3" when the user captures low quality biometric|MOS-28958|
|Registration-Client|User is able to create update packet without capturing biometrics|MOS-28962|
|Registration-Client|Scan button gets enabled though user has marked all biometrics as exception |MOS-28967|
|Registrtaion-Client|Face photo capture is not working as expected |MOS-23698|

## Support Process (To Be Determined) [**[↑]**](#table-of-contents)
Process to be followed for support required, escalation matrix, etc.

## List Of Acronyms [**[↑]**](#table-of-contents)
[**Refer to List Of Acronyms**](Platform-Documentation#12-list-of-acronyms)




