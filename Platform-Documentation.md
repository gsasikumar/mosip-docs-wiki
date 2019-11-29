## Table Of Contents
- [1. INTRODUCTION](#1-introduction)
- [2. FUNCTIONAL OVERVIEW](#2-functional-overview)
- [3. ARCHITECTURE OVERVIEW](#3-architecture-overview)
  * [3.1 Principles](#31-principles)
  * [3.2 Logical View](#32-logical-view)
  * [3.3 Technology Stack](#33-technology-stack)
  * [3.4 Data Architecture](#34-data-architecture)
  * [3.5 High Level Design](#35-high-level-design)
  * [3.6 Deployment Architecture](#36-deployment-architecture)
- [4. FEATURES](#4-requirement-specifications)
- [5. ARCHITECTURALLY SIGNIFICANT COMPONENTS](#5-architecturally-significant-components)
  * [5.1 ID Object Definition](#51-id-object-definition)
  * [5.2 Configurations](#52-configurations)
  * [5.3 Registration Packet Structure](#53-registration-packet-structure)
  * [5.4 ABIS Middleware](#54-abis-middleware)
  * [5.5 Biometric Data Standards](#55-biometric-data-standards)
  * [5.6 MOSIP Device Specification](#56-mosip-device-specification)
  * [5.7 Core Data Management](#57-core-data-management)
  * [5.8 Integration with External Systems](#58-integration-with-external-systems)
- [6. APIs](#6-mosip-apis)
- [7. PRIVACY AND SECURITY](#7-privacy-and-security)
- [8. HOW TO CONTRIBUTE](#8-contributing)
- [9. BUILDING AND DEPLOYING (WIP)](#9-building-and-deploying-mosip)
  * [9.1 Getting Started Guide](#91-getting-started-guide)
  * [9.2 Tester Documentation](#92-tester-documentation)
  * [9.3 Developer Document](#93-developer-document)
  * [9.4 Customization (WIP)](#94-customization-wip)
- [10. INFRASTRUCTURE RECOMMENDATIONS](#10--infrastructure-recommendations)
  * [10.1 Data Center Architecture (WIP)](#101-data-center-architecture-wip)
- [11. List Of Acronyms](#11-list-of-acronyms)
- [12. Hardware Sizing and Software Requirements](https://github.com/mosip/mosip-docs/wiki/Hardware-Software-requirements)


## 1. INTRODUCTION
This document describes the objectives and explicit functional requirements of MOSIP. It also gives an overview of architecturally significant features, APIs and standards followed in MOSIP. Lastly, it provides necessary information on implementation, customization and set up.

## 2. FUNCTIONAL OVERVIEW[**[↑]**](#table-of-contents)
Further details are available on each modules under [Requirement Specifications](#4-requirement-specifications) 
### 2.1 Pre-Registration

Pre-registration is the web channel of the MOSIP. This module enables a user to:  
1. Book an appointment for registration 
1. Enter demographic data & upload supporting documents 
1. Appointment notification, rescheduling and cancellation 
1. Send resident data to registration center before appointment, which can be used during registration 

[Detailed functional specifications of pre-registration module](FRS-Pre-Registration) 

### 2.2 Registration Services
Registration Client application captures the demographic and biometric details of an individual along with supporting information (proof documents & information about parent/guardian/introducer) and packages the information in a secure way. This module provides the following capabilities:
1. Provides a secure way of capturing an individual's demographic and biometric data
1. Provides interfaces to biometric devices that comply to industry standards
1. Works in online and offline mode to capture data
1. Provides option to transfer data to server when online and helps in uninterrupted registrations
1. Client has the ability to update itself for patch upgrades (bug fixes/enhancements) in a remote way. There could be hundreds of client instances running on laptops/desktops. Updates on all of them are controlled by the client and a central server.
1. Registration client is secured such that it cannot be tampered with or misused

[Detailed functional specifications of registration services](FRS-Registration-Services)


### 2.3 Registration Processor
Registration Processor processes the data (demographic and biometric) of an individual for quality and uniqueness and then issues a Unique Identification Number (UIN). The source of data are primarily from:
1. MOSIP Registration Client
1. Existing ID system(s) of a country

This module has the following capabilities:
1. Provides guaranteed packet processing - Not lose the packet once received on the server
1. Handle server failure, recovery and re-submission of packets for processing automatically
1. Add new processing step(s) without changing existing steps as different countries may have different processing requirements
1. Integrate with multiple ABIS providers. Accommodate sending one or more biometric modality to one or more ABISs and calculate a composite fusion score and then take a decision on the processing
1. Each processing step is scalable independently based on the load

[Detailed functional requirement specifications of Registration Processor](FRS-Registration-Processor)
### 2.4 ID Authentication

ID Authentication in MOSIP provides services through APIs that validates the authenticity of a resident based on one or more factors (demographic and biometric). The authentication services are integrated with TSPs (Trusted Service Providers) for delivering eKYC services to residents via user agencies.

This module provides the following capabilities:
1. Authenticate an individual in a secure and trusted way
1. Capture the biometric data as per the defined standards
1. Authenticate an individual based on their basic identity data captured via MOSIP
1. In addition to demographic and biometric authentication, an individual can also be authenticated based on the following parameters:
   * Temporary One Time Password (TOTP) based 
   * Challenge response
5. Authentication APIs
1. High Availability (HA) to ensure smooth service
1. Scalable to cater to the growing population of a country
1. Protects an Individual's identity from request-replay attacks
1. Audited for reporting and fraud management checks

[Detailed functional requirement specifications for authentication services](FRS-Authentication-Services)

### 2.5 Kernel
Kernel is a platform to build higher-level services as well as a secure sandbox. Functionally it caters to the following services:
* [UIN Generation](UIN-Generation)
* [Configuration Server](Configuration-Server)
* [Audit Manager](Audit-Manager)
  * [Log manager](Audit-Manager#log-manager)
* [Authentication and Authorization](Authentication-and-Authorization)
* [Common Services](FRS-Common-Services)
* [Data Services](FRS-Data-Services)
* [Admin Services](FRS-Admin-Services)

### 2.6 Admin Portal and Administrator Services (WIP)
Admin Portal allows an MOSIP Administrator to manages administrative activities of MOSIP through either the back-end process with the help of available APIs or the UI screens. 

These administrative activities are:

 * Set up Platform Data, Process Flows, ID Definition, Configuration, and Security Policy (Through back-end process).
 * Manage (Create, Update, View, Activate/Deactivate, Map/Un-map/Re-map/Decommission) the resources. (Through API and UI Screens)
 * Map the resources (Users, Machines, and Devices) to a registration center.(Through APIs)
 * Manage the master data (Create/Update/Activate/Deactivate).(Through APIs)
 * Manage approval requests for creation and updation of resources and master data.
 * Manage personal account details (Reset Password, Forgot User Name, Change Password, Unlock Account, and Edit Personal 
   Details.
 * Activate/deactivate UIN
 * View status of packets

[Detailed functional specifications of administrator services module](FRS-Administrator-Services) 
<!--- 
### 2.7 Resident Services (WIP)

Resident Services module will provide a host of services for a user which he/she can utilize after generation of his/her UIN. The list of services a user can avail are outlined below:

1. Download e-UIN.
2. Retrieve lost UIN.
3. Initiate UIN Update.
4. Request re-print UIN.
5. Track status of UIN update.
6. View history of Authentication Requests.
7. Lock or Unlock UIN/VID for each ‘Auth’ type(s).

Additionally a user can also track status of his/her UIN generation after registration. 
These services include:

1. Retrieve Lost RID (registration ID).
2. Track Status of UIN Generation via RID.

[Detailed functional specifications of resident services module](FRS-Resident-Services)
### 2.8 Partner Management (WIP)

Partner Management provides services for Partner and MISP (MOSIP Infrastructure Service Provider) Registration and Authentication. Only Registered Partners and MISP are allowed to access MOSIP Authentication services. Partners and MISP are registered using Partner Management Services.  Authentication services of MOSIP will internally use the Partner Management Services to authenticate Partner and MISP and validate if only the registered entities are accessing the services.

Partner Management also involves policy management for Partners. Each partner can access authentication services only based on a defined policy. Authentication services of MOSIP will internally use the Partner Management Services to authenticate a partner based on the policy.

Partners send authentication request and receive authentication responses in a secured setup. Public/Private keys are used for encryption/decryption/signing the request/response. A few of the key management activities are managed in the Partner Management Services.

Further Certificates are used by Partners for signing the authentication request. Partner Management Services is used for a few of the signature related services.

[Detailed functional specifications of Partner Management module](FRS-Partner-Management)
--->

### 2.9 ID Repository
[Detailed functional specifications of ID Repository](FRS-ID-Repository) 

## 3. ARCHITECTURE OVERVIEW[**[↑]**](#table-of-contents)

### 3.1 [Architectural Principles and Platform Goals](Architecture-Principles-&-Platform-Goals) 
### 3.2 [Logical Architecture](Logical-Architecture) 
### 3.3 [Technology Stack](Technology-Stack)
### 3.4 [Data Architecture](MOSIP-Data-Architecture)
### 3.5 High Level Design
#### 3.5.1 [Pre-Registration](Pre-Registration)
#### 3.5.2 [Kernel](Kernel)
#### 3.5.3 [Registration Services](Registration-Client)
#### 3.5.4 [Registration Processor](Registration-Processor)
#### 3.5.5 [Authentication Services](ID-Authentication)
<!---  #### 3.5.6 [Resident Services](Resident-services) --->
#### 3.5.7 [Administrator Services](Admin)
#### 3.5.8 [ID Repository](ID-Repository)
### 3.6 [Deployment Architecture](Deployment-Architecture)

## 4. REQUIREMENT SPECIFICATIONS[**[↑]**](#table-of-contents)
### 4.1 Functional Requirement Specifications
#### 4.1.1 [Pre-Registration](FRS-Pre-Registration)
#### 4.1.2 [Data Services](FRS-Data-Services)
#### 4.1.3 [Common Services](FRS-Common-Services)
#### 4.1.4 [Admin Services](FRS-Admin-Services)
#### 4.1.5 [UIN Generation](UIN-Generation)
#### 4.1.6 [Configuration Server](Configuration-Server)
#### 4.1.7 [Audit Manager](Audit-Manager)
#### 4.1.8 [Authentication and Authorization](Authentication-and-Authorization)
#### 4.1.9 [Registration Services](FRS-Registration-Services)
#### 4.1.10 [Registration Processor](FRS-Registration-Processor)
#### 4.1.11 [Authentication Services](FRS-Authentication-Services)
<!---! #### 4.1.12 [Resident Services](FRS-Resident-Services) --->
#### 4.1.13 [Administrator Services](FRS-Administrator-Services)
<!--- #### 4.1.14 [Partner Management](FRS-Partner-Management)--->
#### 4.1.15 [ID Repository](FRS-ID-Repository)

### 4.2 [Non-Functional Requirement Specifications](Non-Functional-Requirements)

## 5. ARCHITECTURALLY SIGNIFICANT COMPONENTS[**[↑]**](#table-of-contents)
### 5.1 ID Object Definition
ID definition describes the attributes a Country or entity intends to capture from an Individual, which will formulate the definition of ID for a Country. This section elaborates on the mechanism MOSIP adopts, in order to provide the flexibility for each Country to define its preferred ID definition and ID object definition schema.

[More details on ID Object Definition](MOSIP-ID-Object-definition)

### 5.2 Configurations
MOSIP as a platform will have multiple applications running and each application will have a set of configurations.
This section details:
1. The key configuration files a system owner has to create before starting the platform – with a centralized Config Server.
1. Launcher component which will read the configuration files, validate and launch the platform.

[More details on Configurations](MOSIP-configuration-&-launcher)

### 5.3 Registration Packet Structure
This section illustrates the packet creation flow along with the encryption process, as part of Registration Client.

[More details on Registration Packet](Registration-Packet)

### 5.4 ABIS Middleware
This section provides details on the ability of MOSIP to support a single or multi-ABIS solution, specifics on the Components & APIs of ABIS Middleware, Strategies for Biometric data management in ABIS and Strategies for de-duplication in case of multiple ABIS systems.

[More details on ABIS Middleware](MOSIP-ABIS-Middleware)
### 5.5 Biometric Data Standards
This section details out the specifications for Biometric data during data acquisition and verification. 

[More details on Biometric Data Specifications](MOSIP-Biometric-Data-Specifications)

### 5.6 MOSIP Device Specification
This section illustrates the VDM technical specifications to be adhered by a vendor, who intends to adopt their devices to the MOSIP platform, so as to capture the biometric data and process the same. 

[More details on MOSIP Device Specification](MOSIP-VDM-Specifications)

### 5.7 Core Data Management
ID Repository module contains the golden record of Identity for an Individual. Once new/update packets are processed by Registration Processor, the Identity details of an Individual are added/updated in ID Repository. The Identity information available in ID Repository is then used by ID Authentication to authenticate an Individual.

This module exposes few REST APIs which can be used to create/update/retrieve identity of an individual. Please refer to the [ID Repository API](ID-Repository-API) for more details.

### 5.8 Integration with External Systems
[This section](/mosip/mosip-platform/wiki/Registration-Processor-External_System_Integration_Guide) illustrates the integration specifications of MOSIP with an external system.

## 6. MOSIP APIs[**[↑]**](#table-of-contents)
### 6.1	External APIs

* [Pre-Registration APIs](Pre-Registration-Services)
* [Registration Processor APIs](Registration-Processor-APIs)
* [ID Authentication APIs](ID-Authentication-APIs).
<!--- * [Resident Services APIs (WIP)](Resident-Service-APIs).--->
<!--- * [Partner Management APIs (WIP)](Partner-Management-APIs) --->
* [ABIS APIs](ABIS-APIs).
* [Biometric APIs](MOSIP-Biometric-APIs)
* [OTP Manager API](Kernel-APIs#otp-manager-private)

### 6.2	Internal APIs
* [Kernel APIs](Kernel-APIs)---
* [ID Repository API](ID-Repository-API)
* [Admin APIs](Admin-APIs)
* [AuthN & AuthZ APIs](AuthN-&-AuthZ-APIs)
* Master Data APIs
    1. [Internal Biometric APIs](Biometric-APIs)
    1. [Document APIs](Document-APIs)
    1. [Device APIs](Device-APIs)
    1. [Machine APIs](Machine-APIs)
    1. [Packet APIs](Packet-APIs)
    1. [Template APIs](Template-APIs)
    1. [Common APIs](Common-APIs)
    1. [Registration Center APIs](Registration-Center-APIs)

## 7. PRIVACY AND SECURITY[**[↑]**](#table-of-contents)
Multiple aspects of Security like Confidentiality, Privacy, and Integrity of data are key in ensuring an Individual's identity is not compromised. This section illuminates on the [privacy and security](Privacy-and-Security) design principles MOSIP follows. Please also take a look at [Security Tools](Security-Tools) to know more about the tools used for security testing.

## 8. CONTRIBUTING[**[↑]**](#table-of-contents)
To get started on contributing to MOSIP, read our [Contributor Guide](contributor-guide) and our [Code of Conduct](code-of-conduct)


## 9. BUILDING AND DEPLOYING MOSIP[**[↑]**](#table-of-contents)
### 9.1 [Getting Started Guide](Getting-Started)
### 9.2 Tester Documentation

Useful information for the tester community. [Tester Documentation](tester-documentation)

Test Rig represents a one click automation to build, deploy and test a software module. Successful execution of test rig would ascertain complete setup of the MOSIP platform. More details on [Test Rig Design](Test-Rig-Design).

More details on [Test Automation](Tester-Documentation)

### 9.3 [Developer Documentation](Developer-Documentation)
### 9.4 [Customization (WIP)]

- [UI Customization (WIP)](https://github.com/mosip/mosip-docs/wiki/Customization-of-UI---How-to-Guide)

## 10.  INFRASTRUCTURE RECOMMENDATIONS[**[↑]**](#table-of-contents)
### 10.1 Data Center Architecture (WIP)
## 11. List Of Acronyms

|Acronym|Expanded Form|
|-----|------|
| ABIS|  Automated Biometric Identification System |
| API | Application Programming Interface|
| ID |Identity|
|IDA|Identity Authentication|
| MOSIP | Modular Open Source Identity Platform|
| NFR | Non-Functional Requirements|
| OTP | One Time Password|
| SDK | Software Development Kit|
| TBD | To Be Determined|
|TOTP|Temporary One Time Password|
| UIN | Unique Identification Number|
| WIP | Work In Progress|
| CBEFF |Common Biometric Exchange Formats Framework|
| HSM |Hardware Security Module|
| TPM |Trusted Platform Module|


