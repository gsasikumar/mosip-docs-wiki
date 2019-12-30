
### Deployment Checklist
This checklist should be verified once the environment is ready, and before it can be consumed.

Deployment checklist is divided into 2 parts - 
 1. `Infrastructure Checklist` – This checklist lists the required installations for all the modules.
 2. `Application Checklist` – This checklist lists the dependent services, configurations, required roles, any explicit permissions, etc. for all the modules.

***1. Infrastructure Checklist***    
Below are the list of infrastructure items which should be checked per module, before using them.

<table>
    <thead>
        <tr>
            <th>Module Name</th>
            <th>Infrastructure Checklist</th>
            <th>Additional Information</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td rowspan=5>Kernel</td>
            <td rowspan=1>PostgreSQL</td>
            <td></td>
        </tr>
        <tr>
            <td rowspan=1>SMTP Server</td>
            <td>If mail notification is enabled</td>
        </tr>
        <tr>
            <td rowspan=1>SMS Gateway</td>
            <td>If SMS notification is enabled</td>
        </tr>
        <tr>
            <td rowspan=1>HDFS</td>
            <td></td>
        </tr>
        <tr>
            <td rowspan=1>LDAP</td>
            <td>Import ldif</td>
        </tr>
       <tr>
            <td rowspan=5>Pre-Registration</td>
            <td rowspan=1>PostgreSQL</td>
            <td></td>
        </tr>
        <tr>
            <td rowspan=1>SMTP Server</td>
            <td>If mail notification is enabled</td>
        </tr>
        <tr>
            <td rowspan=1>SMS Gateway</td>
            <td>If SMS notification is enabled</td>
        </tr>
        <tr>
            <td rowspan=1>HDFS</td>
            <td></td>
        </tr>
        <tr>
            <td rowspan=1>LDAP</td>
            <td></td>
        </tr>
        <tr>
            <td rowspan=5>Registration</td>
            <td rowspan=1>TPM</td>
            <td></td>
        </tr>
        <tr>
            <td rowspan=1>SMTP Server</td>
            <td>If mail notification is enabled</td>
        </tr>
        <tr>
            <td rowspan=1>SMS Gateway</td>
            <td>If SMS notification is enabled</td>
        </tr>
        <tr>
            <td rowspan=1>Devices</td>
            <td>Fingerprint Slab, Iris, Webcamera, Printer, Scanner</td>
        </tr>
        <tr>
            <td rowspan=1>LDAP</td>
            <td></td>
        </tr>
     <tr>
            <td rowspan=7>Registration Processor</td>
            <td rowspan=1>Virus Scanner</td>
            <td>ClamAV virusscanner service should be accessible from dmz and secure zone using IP:Port</td>
        </tr>
        <tr>
            <td rowspan=1>SMTP Server</td>
            <td>If mail notification is enabled</td>
        </tr>
        <tr>
            <td rowspan=1>SMS Gateway</td>
            <td>If SMS notification is enabled</td>
        </tr>
        <tr>
            <td rowspan=1>HDFS</td>
            <td>HDFS should be accessible, and write permission to regproc user should be provided</td>
        </tr>
        <tr>
            <td rowspan=1>ActiveMQ</td>
            <td>ActiveMQ should be installed and accessible using IP:Port</td>
        </tr>
         <tr>
            <td rowspan=1>LDAP</td>
            <td></td>
        </tr>
         <tr>
            <td rowspan=1>PostgresSQL</td>
            <td></td>
        </tr>
       <tr>
            <td rowspan=3>ID Repository</td>
            <td rowspan=1>HDFS</td>
            <td></td>
        </tr>
        <tr>
            <td rowspan=1>LDAP</td>
            <td></td>
        </tr>
        <tr>
            <td rowspan=1>PostgresSQL</td>
            <td></td>
        </tr>
       <tr>
            <td rowspan=4>ID Authentication</td>
            <td rowspan=1>SMTP Server</td>
            <td>If mail notification is enabled</td>
        </tr>
        <tr>
            <td rowspan=1>SMS Gateway</td>
            <td>If SMS notification is enabled</td>
        </tr>
        <tr>
            <td rowspan=1>LDAP</td>
            <td></td>
        </tr>
        <tr>
            <td rowspan=1>PostgresSQL</td>
            <td></td>
        </tr>    
    </tbody>
</table>


***2. Application Checklist***     
Below are list of items to be checked for each module to work.    

<table>
    <thead>
        <tr>
            <th>Module Name</th>
            <th>Application Checklist</th>
            <th>Additional Information</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td rowspan=1>Kernel</td>
            <td rowspan=1>Configurations</td>
            <td>kernel.properties, application.properties</td>
        </tr>
       <tr>
            <td rowspan=5>Pre-Registration</td>
            <td rowspan=1>Virus Scanner</td>
            <td></td>
        </tr>
        <tr>
            <td rowspan=1>HDFS</td>
            <td></td>
        </tr>
        <tr>
            <td rowspan=1>Configurations</td>
            <td>pre-registration.properties, application.properties</td>
        </tr>
        <tr>
            <td rowspan=1>HDFS</td>
            <td></td>
        </tr>
        <tr>
            <td rowspan=1>Kernel Services</td>
            <td>Authmanager, AuditManager, MasterData, CryptoManager, KeyManager, SmsNotifier, EmailNotifier, Config Server, OTPManager</td>
        </tr>
        <tr>
            <td rowspan=6>Registration</td>
            <td rowspan=1>Kernel Services</td>
            <td>AuthManager, Sync Data Service, Key Manager,  
Notification Manager, Master Data, User Salt Service,  
User Detail Service</td>
        </tr>
        <tr>
            <td rowspan=1>Pre-Registration Services</td>
            <td>Pre-Registration Sync Service</td>
        </tr>
        <tr>
            <td rowspan=1>Registration  
Processor Services</td>
            <td>Packet Receiver, Packet Sync Status, Packet Status</td>
        </tr>
        <tr>
            <td rowspan=1>ID Authentication Services</td>
            <td>Internal Authentication Service</td>
        </tr>
        <tr>
            <td rowspan=1>Devices and/or MDS</td>
            <td>Fingerprint/Iris/Webcamera/Printer/Scanner</td>
        </tr>
        <tr>
            <td rowspan=1>Configurations</td>
            <td>registration.properties, application.properties,  
spring.properties  
Required properties for library URL, HealthCheck URL, TPM availability needs to be changed in the file present at -  
"Registration-services/src/main/resources  
/spring.properties"</td>
        </tr>
     <tr>
            <td rowspan=5>Registration Processor</td>
            <td rowspan=1>Kernel Services</td>
            <td>AuthManager, AuditManager, MasterData,  
CryptoManager, KeyManager, Signature,  
RidGenerator, SmsNotifier, EmailNotifier</td>
        </tr>
        <tr>
            <td rowspan=1>ID Authentication Services</td>
            <td>Internal Authentication Service</td>
        </tr>
        <tr>
            <td rowspan=1>ID Repository Services</td>
            <td>IDRepo Identity and VID Services</td>
        </tr>
        <tr>
            <td rowspan=1>ABIS</td>
            <td></td>
        </tr>
        <tr>
            <td rowspan=1>Configurations</td>
            <td>registration-processor.properties,  
RegistrationProcessorAbis.json  
These configurations should be updated with correct hdfs, activemq, virusscanner ip/port, etc.</td>
        </tr>
       <tr>
            <td rowspan=3>ID Repository</td>
            <td rowspan=1>Kernel Services</td>
            <td>AuditManager, CryptoManager, Config Server, AuthManager</td>
        </tr>
        <tr>
            <td rowspan=1>Configurations</td>
            <td>ID Schema, VID Policy Schema, id-repository.properties</td>
        </tr>
        <tr>
            <td rowspan=1>Job</td>
            <td>Salt Generator</td>
        </tr>
        <tr>
            <td rowspan=1>LDAP Roles</td>
            <td>roles=REGISTRATION_PROCESSOR, ID_AUTHENTICATION, REGISTRATION_ADMIN, REGISTRATION_SUPERVISOR, REGISTRATION_OFFICER</td>
        </tr>
       <tr>
            <td rowspan=4>ID Authentication</td>
            <td rowspan=1>Kernel Services</td>
            <td>AuditManager, CryptoManager, AuthManager,  
Config Server, OTPManager, Email Notifier, SMS Notifier, Signature, Master Data, TokenID Generator</td>
        </tr>
        <tr>
            <td rowspan=1>ID Repository Services</td>
            <td>ID Repo Identity and VID Services</td>
        </tr>
        <tr>
            <td rowspan=1>Configurations</td>
            <td>ID Auth Mapping, id-authentication.properties</td>
        </tr>
        <tr>
            <td rowspan=1>Job</td>
            <td>Salt Generator</td>
        </tr>    
        <tr>
            <td rowspan=1>LDAP Roles</td>
            <td>roles=REGISTRATION_PROCESSOR, ID_AUTHENTICATION, REGISTRATION_ADMIN, REGISTRATION_SUPERVISOR, REGISTRATION_OFFICER</td>
        </tr>    
    </tbody>
</table>






