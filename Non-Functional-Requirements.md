WIP
## Table Of Contents
- [1. Performance](#1-performance-) _(NFR_1)_
  * [1.1 Responsiveness(Under Different Load Conditions)](#11-responsiveness-Under-Different-Load-Conditions) _(NFR_1.1)_
- [2. Availabiity](#2-availability-) _(NFR_2)_
- [3. Scalability](#3-scalability-) _(NFR_3)_
- [4. Security](#4-security-) _(NFR_4)_
  * [4.1 Network Security](#41-network-security) _(NFR_4.1)_
  * [4.2 Privacy](#42-privacy) _(NFR_4.2)_
  * [4.3 Confidentiality](#43-confidentiality) _(NFR_4.3)_
- [5. Internationalization](#5-internationalization-) _(NFR_5)_
  * [5.1 Number Format](#51-number-format) _(NFR_5.1)_
  * [5.2 Date Format](#52-date-format) _(NFR_5.2)_
  * [5.3 Languages](#53-languages) _(NFR_5.3)_
- [6. Maintainability](#6-maintainability-) _(NFR_6)_
  * [6.1 Monitoring](#61-monitoring) _(NFR_6.1)_
  * [6.2 Software Upgrades/Updates](#62-software-upgrades-updates) _(NFR_6.2)_
  * [6.3 Configuration](#63-configuration) _(NFR_6.3)_
- [7. Recovery (Individual Modules)](#7-recovery-individual-modules-) _(NFR_7)_
  * [7.1 Data Recovery (in flight transaction data and data at rest)](#71-data-recovery-in-flight-transaction-data-and-data-at-rest) _(NFR_7.1)_
- [8. Data Backup](#8-data-backup-) _(NFR_8)
  * [8.1 Backup Policy](#81-backup-policy) _(NFR_8.1)_
- [9. Data Archival](#9-data-archival) _(NFR_9)
  * [9.1 Archival Policy](#91-archival-policy) _(NFR_9.1)_

## 1. Performance [**[↑]**](#table-of-contents)
Performance plays a very important role in the MOSIP platform. The services and the UI have to adhere to the agreed SLAs. Following are the important factors in the peformance section, 
### 1.1 Response Time
 - Any response of the API service does not exceed 300 milliseconds.
 - Any UI page load in the supported browsers does not exceed 2 seconds.
### 1.2 Throughput
 - The Pre-Registration module does support 100 transactions per second
 - The Registration processor module does support 2 transactions per second
 - The IDA module does support at least 100 transactions per second
### 1.3 Concurrent requests
 - The Pre-Registration module does support 1000 concurrent users at a time. 
 - The IDA module does support 100 concurrent users at a time. 

## 2. Availability [**[↑]**](#table-of-contents)
Most of the services and the applications are available at all time. Whenever there is a upgradation, few instances are taken out and traffic is redirected to the live servers. Once the application upgradation is done, the traffic is redirected to the upgraded systems. This redirection happens at the same instance for all the modules in the platform. Following are the availability of the various modules, 
### 2.1 Kernel
- All the Kernel API services are available 24/7 throughout the year. 

### 2.2 Pre-Registration
- The Pre-Registration module are available 24/7 throughout the year. However, there are certain schedules downtimes for the application maintenance. 

### 2.3 Registration client
- The Registration client module are available only during the registration center timings

### 2.4 IDA
- The IDA services are available 24/7 throughout the year.  

## 3. Scalability [**[↑]**](#table-of-contents)
Whenever, a module is unable to adhere to the agreed response time, more instances are spun up to manage the increase in the traffic or load. The following modules does have the capability to scale up or scale down, 
1. Kernel components
2. Pre-Registration components
3. IDA service components

Virtualization techniques are used to scale up or down. Based on the load, the system automatically does be able to scale up or scale down. 

## 4. Security [**[↑]**](#table-of-contents)
Security is the prime concern in the platform. Security comes above all other Non-functional requirements. Following are the main areas in which the security had been looked into, 
### 4.1 Network Security
The various machines and devices in the network are differentiated and located in segregated zones. These zones has separate policy and network parameters for better accesibility. Please refer to the <TODO> document for the network architecture diagram. 
### 4.2 Privacy
The privacy of individuals data is maintained. None of the PII data is kept in plain human readable format. 
### 4.3 Confidentiality
The communication network packets across the network are encrypted using the Asymmetric keys. 
The key sensitive data are stored in an encrypted format in the database. 
Keys are rotated periodically to keep the keys itself as confidential. The keys are encrypted by the master key. The master key itself are saved in the Hardware Security Module. 

## 5. Internationalization [**[↑]**](#table-of-contents)
### 5.1 Number Format
English numerals are used in the MOSIP platform. Integers with no decimal points and decimal points upto 2 places are used as standards. 
### 5.2 Date Format
#### 5.2.1 Time standards
In all the places wherever the time is saved in the persistent layer, UTC time standard is used. All the webservices, wherever the date is passed, UTC time standard is used. However, in the front-end layer, the applications can decide the time zones and formats. 
Only the Gregorian calendar is used in the entire platform. 
#### 5.2.2 Format in ISO standards
In the web services,  UTC standard ISO8601 format is used. However, in the logs and the application front end, various date and time format are used according to the needs. 
### 5.3 Languages
In the webservices and in the persistent layer, ISO 639_2 standards is used to represent the language. Internationalization are used in the front end application by i18 properties files. From the persistent layer, languages are saved as the attribute for the entities. 

## 6. Maintainability [**[↑]**](#table-of-contents)
Once the application is live, following items are considered for the maintenance, 
### 6.1 Monitoring
Critical services health are monitored manually. No monitoring tool and no automatic triggers and notifications are configured. 
### 6.2 Software Upgrades/Updates
Periodic scanning of the libraries and code are done to get the latest vulnerabilities and the bug fixes. Following are the components which have to be checked for the upgrades, 
1. Operating Systems
2. 3rd party Java libraries
3. Virus scanner databases
4. Database applications
### 6.3 Configuration
The configuration are maintained in a centralized location for easy maintenance. A configuration server serves the configuration required for the modules in the platform. There is a "Global configuration" file which is used commonly across all the modules and each configuration file for the entries used only for a specific module. 

## 7. Recovery (Individual Modules) [**[↑]**](#table-of-contents)
### 7.1 Data Recovery (in flight transaction data and data at rest)
- NA -

## 8. Data Backup [**[↑]**](#table-of-contents)
### 8.1 Backup Policy
- NA -

## 9. Data Archival [**[↑]**](#table-of-contents)
### 9.1 Archival Policy
- NA -