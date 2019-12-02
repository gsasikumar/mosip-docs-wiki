* **Authentication and Authorization** _(AUT_FR_1)_

In MOSIP, Authentication largely falls into the below categories:
* Authentication via web channel (for Pre-Registration web app, Admin web app and Resident services portal)
* Authentication via local system i.e., offline authentication (for Registration client)

In MOSIP, Authorization falls into the below categories:
* Authorization of API's accessed via web channel
* Authorization to access specific data (will be implemented in v2)

A country will have its own hierarchy of system users especially the Registration staff and system administration staff. So, instead of defining a fixed hierarchy, by default MOSIP will depend on an LDAP implementation to manage users, organizational hierarchy and roles for users in the hierarchy. MOSIP will use an open source LDAP server as the LDAP implementation. Administrators can create hierarchy and users using Apache Directory Studio.
([**Refer to Wiki for more details on Authentication and Authorization API**](AuthN-&-AuthZ-APIs)).

MOSIP system can handle Authorization across core services and restricts access to Web-services as per the roles defined. 

[**Please refer Git for more details on the roles and Privileges of a user**](_files/requirements/MOSIP_Roles%20and%20Responsibility_Matrix_16Jan19.xlsx). 

### List of Configurable Parameters and Processes 
1. Configurable Parameters

   [**Link to Configurable Parameters of Kernel**](/mosip/mosip-config-mt/blob/master/config-templates/application-env.properties)

   [**Link to Kernel Application Properties**](/mosip/mosip-config-mt/blob/master/config-templates/kernel-env.properties)

### Kernel API 
[**Refer to Wiki for more details on Kernel API**](Kernel-APIs)
