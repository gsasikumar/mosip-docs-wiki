# Pre-Registration
## 1. Authentication
### 1.1 Login
Log in to the pre-registration system with a mobile or email with OTP so that you can get access to the pre-registration system
### 1.2 Logout
Log out from the pre-registration system
## 2. Language Data Manager
### 2.1 Translation
Translation of the language as per the pre-configured primary and secondary language for a country
### 2.2 Transliteration
Transliteration of the language as per the pre-configured secondary language for a country
## 3. Pre-Registration Sync
### 3.1 Pre-Registration Data Sync
1. Synchronizes the pre-registration data with the registration-client 
1. Synchronizes status of pre-ID with registration processor
## 4. Appointment Scheduler
### 4.1 RC Identifier
Provides search facility for available registration centers so that applicant can book an appointment 
### 4.2 Availability Checker  
Getting availability of slots in the chosen registration center
### 4.3 Appointment Booking  
Booking\re-booking the selected slot in the chosen registration-center for registration
## 5. Pre-Registration Application Manager
### 5.1 Pre-Registration Application Manager
Collects (create\modify\delete) demographic data and documents (specific to the applicant type) from the user\applicant
### 5.2 Acknowledgment
Generates an acknowledgment (with QR Code) for successful pre-registration, which can then be printed or downloaded for future reference.
### 5.3 PRID Generator
Generates pre-registration ID
# Registration
## 1. Registration Client Setup
### 1.1 Registration Client Installation
Installs the registration-client on the machine 
### 1.2 Registration Client Launch
Helps in launching the registration-client
### 1.3 Registration Client Software Update
Updates the client software 
## 2. System Health Checker
### 2.1 Connectivity Checker
Checks if the client machine is connected to the network
### 2.2 Security Scan
Virus scan of the data packets and the application software
### 2.3 Disk Space Checker
Checks whether there is enough space in the client machine\dongle to store the registration packet
## 3. Registration Officer Authentication
### 3.1 Login
Enables logging in to the client machine by a password, OTP or biometrics
### 3.2 Logout
Logging out from the client application
## 4. User Onboarding/Manager
### 4.1 User Registration
Enables mapping between the user and machine\dongle. Allows a user to on-board themselves on a machine
## 5. Language Manager
### 5.1 Translation
Translates the static messages as per the configures primary and secondary languages
### 5.2 Transliteration
Translates the user entered text from primary to secondary language
## 6. Registration Application Manager - New
### 6.1 Location Geo tagging
Captures the GPS coordinates of the client machine to ensure data integrity
### 6.2 Individual Category Selection
Helps to distinguish if an applicant is an adult or a child
### 6.3 Demo Data Capture
Captures the demographic data of the applicant
### 6.4 Document Upload
Enables scan and upload supporting doc such as POA and POI
### 6.5 Fingerprint Capture
Captures the fingerprint data and determines the quality of the data
### 6.6 Iris Capture
Captures the iris data and determines the quality of the data
### 6.7 Face Capture
Captures the face photograph 
### 6.8 Biometric Exception Capture
1. Captures the exception photograph
1. Marks the biometric exceptions
### 6.9 Registration Checks
1. Preview of the registration details
1. Operator authentication for submitting the registration
1. Supervisor authentication for submitting registration with exception
1. End of day approval
1. Re-registration
### 6.10 Acknowledgment
Renders the acknowledgment page after successful registration and allows printing
### 6.11 Notification
Renders email and SMS notification for various events such as successful registration
## 7. Registration Officer Authorization
### 7.1 Registration Officer Authorization
Determines the user roles and provides access based on the privileges
## 8. Registration Packet Manager
### 8.1 Packet Creation
Creates the encrypted data packets
### 8.2 Packet Exporter
Allows sending packets to the processing server
1. Using the upload feature of the client
1. Copying packets to an external storage device
## 9. Sync Handler
### 9.1 Master Data Syncher
Synchronizes master data between a server to client
### 9.2 Packet Syncher
Send registration packet IDs from client to processor so that to ensure data security
### 9.3 Registration Packet Status-Reader
Read the status of the packets from processor into the client to ensure resend or deleting of packets as required
### 9.4 Registration Client Configuration Syncher
Synchronizes configuration data between a server to client
### 9.5 User Role Setup Syncher
Synchronizes user and role data between a server to client
### 9.6 Policy Syncher
Synchronizes encryptions Keys between a server to client
### 9.7 Pre-Registration Data Syncher
Synchronizes pre-registration data between a server to client
### 9.8 Login Credentials Syncher
Synchronizes login data (password) between a server to client
### 9.9 Audit Log Syncher
Synchronize the audit log from client to server
## 10. Individual UIN - Update
### 10.1 UIN Update
Allows the UIN holder to update their data (A specific set of data as defined by the country)
## 11. Reporting
### 11.1 Registration Reports
Generates reports on end of day process and re-registration
## 12. Clean Up
### 12.1 Data Clean Up
Deletes the following data from the client machine after successful registration:
1. Registration
1. Pre-registration
1. Audit
# Registration Processor
## 1. Registration Packet Handler
### 1.1  Packets Receiver
1. It receives the packet sent from the registration client
1. Performs various sanity checks on the packet
### 1.2  Virus Scanner Stage
Performs virus scan of the encrypted and de-crypted packet and stores the packet in the file system as per configuration
### 1.3 Archive Packets
Makes the data packets available for archival
## 2. Registration Status Service
### 2.1 Registration Status
As the per the stage driven architecture, this utility updates the status in the DB for the data packet at every stage
## 3. Registration Packet Processor
### 3.1 Packet Validator Stage
It performs integrity validation (checksum) and file validation 
### 3.2 OSI Validator Stage
Authenticate operator, supervisor and introducer information received in data packet, and validate the metadata captured during packet creation
### 3.3 Quality Check Stage
1. Checks the quality of biometric data against a configured threshold
1. Validates if photo, age and gender are in sync
1. Validates the document with the data captured using OCR
1. Performs fingerprint quality checks like a real finger or finger of the same person
### 3.4 Demo De-Dupe Stage
Demographic de-duplication of name, gender and DOB
### 3.5 Biometric De-Dupe Dummy ABIS 
It is a dummy ABIS which provides the failure and successful scenarios using Dummy Tags
### 3.6 Manual Verification
This is a pluggable stage where a manual verifier can verify the demographic and biometric data of an individual manually
## 4. UIN Generator 
### 4.1 UIN Generator Stage
1. Generates and allocates a UIN as per the defined logic
1. Stores the people biometric and demographic data in the identity repository
1. Notifies the resident that UIN is generated through the configured channels (SMS, Email etc.)
## 5. Print
### 5.1 Print Queue Stage
Make the UIN data and UIN card available for printing and postal services
## 6. UIN Lifecycle Manager
### 6.1 UIN Update Stage
1. Updates the data (demographic\biometric) of the resident
1. Updation of UIN status to re-activate
1. Updation of UIN status to deactivate
## 7. External System Integration
### 7.1 External System Integration
This stage interacts with various external systems such as CNIE and EC
# ID-Authentication
## 1. TSP/UA Authentication
### 1.1 TSP Authentication 
Validates if the TSP and UA are authenticated sources to initiate the individual's authentication request
### 1.2 Authentication Mode Verifier
Verifies if the UA holds permission to initiate the mode of authentication in the authentication request
## 2. TSP/UA Authorization 
### 2.1 TSP Authorization
Determines if the TSP and UA are authorised entities to initiate the individual's authentication request
## 3. Individual Authentication
### 3.1 Biometric Authentication
Verifies the authenticity of an individual using biometric attributes provided in the authentication request
### 3.2 Demographic Authentication
Verifies the authenticity of an individual using demographic attributes provided in the authentication request
### 3.3 OTP Authentication
1. Enables an individual to receive OTP
1. Verifies the authenticity of an individual using OTP provided in the authentication request
### 3.4 Static PIN Authentication
1. Enables storage of static pin set by an individual in MOSIP Resident Services Portal
1. Verifies the authenticity of an individual using static pin provided in the authentication request
### 3.5 E-KYC Authentication Services   
Provides E-KYC details of an individual to the UA post successful authentication of the individual
## 4. Integrated Individual Authentication 
### 4.1 Multiple Components
Verifies the authenticity of an individual using multiple attributes provided in the authentication request
# Admin Setup (TBD WIP)
# Resident Services (TBD WIP) 
# Reporting (TBD WIP)

# Platform Level Features and Utilities
## Utilities 
### Exception Handler 
* Ability to provide base exception framework
* Framework to include base exception parameters (Message, throwable, cause)

### Log Manager (mosip-logging)
Provide the following logging utility
* Generate logs for implementation events across the application
* Stores the genrated logs in configured location
* Each log can be genrated as a file/console
* Raise an alert in case of listed exceptions (File not found, No such file exists, to be identified)
* Links various logs associated to one applicant

### mosip-utils
MOSIP provides the following utilities
* String utility
* Calendar utility
* Math utility
* File utility
* Hash utility

### Data Access Manager(dataaccess-hibernate)
Provides a interface for DAO (Data Access Manager) interface 

### Data Mapper
Facilitate data mapping between DTO (Data Transfer Object) and Entity
 
### Mobile validator
Performs the pattern validation on the mobile number based on the configured length

### Email validator
Performs the pattern validation on email ID based on the configured parameters

### Blacklisted Words Validator
Performs a word to word validation against a configured list of blacklisted words

### RID Generator
Genetares and validates RID(Registration ID) as per defined logic

### PRID Generator
Genetares and validates PRID(Pre-Registration ID) as per defined logic

### VID Generator
Genetares and validates VID(Virtual ID) as per defined logic

### Token ID Generator
Genetares and validates token ID (Token ID) as per defined logic for TSPs(Third praty service provider)

### Static PIN Generator
Generates and Validate static PIN for user authentication

### Registration Center ID Generator
Generates a registration center ID

### Machine ID generator
Generates a machine ID of the client machine

### TSP ID Generator
Generates and validates a TSP ID

### virusscanner-clamav
Performs virus scan on registration and pre-registration packet

### Template Merger
Merges an pre-configured template with dynamic values

### pdfgenerator
This utility enables PDF file creation of received contente.g.acknowledge and notification templates

### QR Code Generator
This utility enable QR code generation for Pre-reg,reg and UIN acknowledgement

### FTP - Upload packet
Provides a upload portal for registration client to upload packets for sending it to registration processor

## Features
### Notification Manager-notification-sms
Provides an interface to send a SMS notification

### Notification Manager-notification-email
Provides an interface to send a Email notification

### Sync Handler-Master data
Syncs master data between the MOSIP master data server and the client local database

### Sync Handler-Public keys
Syncs public keys between the MOSIP DB and client DB

### Sync Handler-Configuration changes
Syncs the configuration stored in  MOSIP config server with the locally stored configs of client

### Sync Handler-List of Roles and users
Syncs user role data between the MOSIP  server and the client local database
