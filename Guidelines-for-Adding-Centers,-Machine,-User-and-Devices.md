## List of Contents
- [1. Sample Seed Data](#1-seed-data-source-files-in-csv-format)
- [2. Steps to add seed data](#2-steps-to-add-seed-data)
  * [2.1 Create roles in LDAP](#21-create-roles-in-ldap)
  * [2.2 Create a Registration Center](#22-create-a-registration-center)
  * [2.3 Create a Machine](#23-create-a-machine)
  * [2.4 Create a User](#24-create-a-user)
  * [2.5 Create a Device](#25-create-a-device)
  * [2.6 Map the User to a Zone](#26-map-the-user-to-a-zone)
  * [2.7 Map the Machine to a Center](#27-map-the-machine-to-a-center)
  * [2.8 Map the User to a Center](#28-map-the-user-to-a-center)
  * [2.9 Map the Device to a Center](#29-map-the-device-to-a-center)
  * [2.10 Map Center-Machine-Device](#210-map-center-machine-device)
  * [2.11 Map Center-Machine-User](#211-map-center-machine-user)
  * [2.12 Store History of MasterData](#212-store-history-of-masterdata)
- [3. Load updated CSVs to the database using dml sql script](#3-Load-updated-CSVs-to-the-database-using-dml-sql-script)

## 1. Seed Data Source files (in csv format):
1. Registration Centers: [**master-registration_center**](/mosip/mosip-platform/blob/master/db_scripts/mosip_master/dml/master-registration_center.csv)
1. Machines: [**master-machine_master**](/mosip/mosip-platform/blob/master/db_scripts/mosip_master/dml/master-machine_master.csv)
1. Users: [**master-user_detail**](/mosip/mosip-platform/blob/master/db_scripts/mosip_master/dml/master-user_detail.csv)
1. Devices: [**master-device_master**](/mosip/mosip-platform/blob/master/db_scripts/mosip_master/dml/master-device_master.csv)
1. Center-Machine Mapping: [**master-reg_center_machine**](/mosip/mosip-platform/blob/master/db_scripts/mosip_master/dml/master-reg_center_machine.csv)
1. Center-Device Mapping: [**master-reg_center_device**](/mosip/mosip-platform/blob/master/db_scripts/mosip_master/dml/master-reg_center_device.csv)
1. Center-User Mapping: [**master-reg_center_user**](/mosip/mosip-platform/blob/master/db_scripts/mosip_master/dml/master-reg_center_user.csv)
1. Center-Machine-Device Mapping: [**master-reg_center_user_machine**](/mosip/mosip-platform/blob/master/db_scripts/mosip_master/dml/master-reg_center_user_machine.csv)
1. Center Machine User Mapping: [**master-reg_center_machine_device**](/mosip/mosip-platform/blob/master/db_scripts/mosip_master/dml/master-reg_center_machine_device.csv)
1. User Zone Mapping: [**master-zone_user**](/mosip/mosip-platform/blob/master/db_scripts/mosip_master/dml/master-zone_user.csv)
## 2. Steps to Add seed data:
### 2.1 Create Roles in LDAP
Before creating the Masterdata, Roles used across MOSIP are needed to be created in LDAP.

Following roles have to be created using the process as mentioned above.([Refer here](https://github.com/mosip/mosip-docs/wiki/Apache-Directory-Studio-user-guide#create-a-new-role) for help on how to create roles in LDAP.)
   1. REGISTRATION_ADMIN
   2. REGISTRATION_SUPERVISOR
   3. REGISTRATION_OFFICER
   4. ZONAL_ADMIN
   5. GLOBAL_ADMIN
   6. AUTH
   7. PREREG
   8. REGISTRATION_PROCESSOR
   9. ID_AUTHENTICATION
   10. PRE_REGISTRATION_ADMIN
### 2.2 Create a Registration Center:
1. **Center ID**: This should be a 5-digit ID and should be in an incremental sequence for each center added. The sequence should start from 10000. Keeping the length other than 5 digits will fail validations as the same Center ID is used to generate the Request ID (Registration ID). For each Center created, Center ID should be incremented sequentially to avoid inconsistency in data. 
1. **Center Name**: Country defined name for the Center
1. **Center Type Code**: (Should be kept as “REG”). Center Type Code will come from a Center Type Masterdata which currently have one center Type defined as “Regular” and Code as “REG”. More Center Types can be defined by the country in the Center Type Masterdata.
1. **Address Line 1**: It is an Optional Field but should be defined to be visible to the resident on the Pre-Registration UI
1. **Address Line 2**: It is an Optional Field
1. **Address Line 3**: It is an Optional Field
1. **Latitude**: Should be defined in format **XX.XXXX**. minimum 4 digits are need after the decimal for the accuracy to be atleast 11 meters on the GPS map on Pre-Registration Portal
1. **Longitude**: Should be defined in format **XX.XXXX**. minimum 4 digits are need after the decimal for the accuracy to be atleast 11 meters on the GPS map on Pre-Registration Portal
1. **Location Code**: Maps the Registration Center to a Location. Should be a location code referring to a location defined in the location Masterdata table. Should always be the code of the location which is at the lowest hierarchy level
1. **Contact Phone**: An optional field. Usually a point of contact for a Registration Center
1. **Contact Person**: Name of the person who is a point of contact for a Registration Center
1. **Number of Kiosk**: Number of Registration Kiosk a Registration Center will have to register residents. This number is used by the pre-registration to calculate appointment slots for Registration. This should always be equal to the number of machines assigned to the Center or will be assigned to the Center. Refer [**point 2.5**](#25-map-the-machine-to-a-center) in steps below
1. **Working Hours**: Should be the difference of “**Center Start Time**” and “**Center End Time**”. Should be in format **hh:mm:ss**
1. **Per Kiosk Processing time**: Duration of Registration Appointment defined as per the country requirement. This attribute is used by pre-Registration to calculate appointment slots. Should be in format **hh:mm:ss**
1. **Center Start Time**: Time when Center would start taking registration of Residents. This time is used by Pre-Registration to calculate appointment slots. Should be in format **hh:mm:ss**
1. **Center End Time**: Time when the Center closes. This time is used by Pre-Registration to calculate appointment slots. Should be in format **hh:mm:ss**
1. **Lunch Start Time**: Starting of Lunch Time the Center would have in-between the Working hours. It is used by Pre-Registration to calculate appointment slots. Should be in format **hh:mm:ss**
1. **Lunch End Time**: Ending of Lunch Time the Center would have in-between the Working hours. It is used by Pre-Registration to calculate appointment slots. Should be in format **hh:mm:ss**
1. **Time Zone**: (GTM+01:00) CENTRAL EUROPEAN TIME
1. **Holiday Location Code**: Refers to the location to which country defined holidays are mapped in holiday location table. Should come from the Holiday master table. Current values can only be “**KTA**” or “**RBT**” as holidays are only defined for these two location codes.
1. **Zone Code**: Contains the Zone code to which the Registration Center should be tagged to. The Administrative Zones are defined by a country to better manage the resources(Centers, Machines and Devices) used in Registration Process. These are defined in Masterdata table 'zone' in hierarcical fasion similiar to Location masterdata
1. **Language Code**: Should be the language code for the languages supported by the Country as primary/secondary Language. (E.g English - eng, French - fra, Arabic - ara)
1. **Is_Active**: TRUE. If set as false, this Registration will not be shown up in Pre-Registration UI and no appointments will be generated for this Center
1. **Cr_by**: `<username>` ideally name of the admin
1. **cr_dtimes**: The time at which the Center is getting created
<br>**Note**: A Registration Center is needed to be created in all the languages supported by the country. if a country supports primary language as French and Secondary language as arabic, create the same registration center twice. One with language code as **fra** for French and one with language code as **ara** for Arabic. Center ID should be same for both the records as both the records are for one center only.<br>
### 2.3 Create a Machine:
1. **Machine ID**: This should be a 5-digit ID and Ideally should be in an incremental sequence for each machine added. The sequence should start from 10000. Keeping length other than 5 digits will fail validations as the same Machine ID is used to generate the Request ID(Registration ID)
1. **Machine Name**: Machine Host name
1. **Machine Mac-Address**: Machine’s Mac-Address
1. **Serial Number**: `<serial number of machine>`
1. **IP Address**: Leave it blank
1. **Mspecid**: 1001. These values come from a Machine Spec table. Putting any value other than these will throw an error
1. **Zone Code**: Should come from a pre-defined list of Administrative Zone codes created in Zone Masterdata. Current values can be “RBT”, “KTA”, “SAL”, “BSN”, “CSB”, ”STT”, ”NDR”, ”BRK”, “JRD”, “SAF“, “YSF“, “TTA“, “TZT”.
1. **Lang_code**: eng
1. **Is_active**: True
1. **cr_by**: `<username>` ideally name of the admin'
1. **cr_dtimes**: now()
### 2.4 Create a User
1. Create a User in LDAP (User ID/Password)
1. Create a User in DB
   1. **Id**: ID used in LDAP
   1. **UIN**: Leave it black
   1. **Email**: Email used in LDAP
   1. **Mobile**: Mobile used in LDAP
   1. **Status Code**: ACT
   1. **Lang_code**: eng
   1. **last_login_method**: PWD
   1. **Is_active**: True
   1. **cr_by**: `<username>` ideally name of the admin
   1. **cr_dtimes**: now()
### 2.5 Create a Device
1. **Device ID**: This can be a random ID.
1. **Device Name**: `<Name of the device>`
1. **Device Mac-Address**: `<mac-address of device>`
1. **Serial Number**: `<serial number of device>`
1. **IP Address**: Leave it blank
1. **Dspecid**: Can be either 165(fingerprint scanner), 327 (iris scanner), 736(web camera), 801(Document scanner) or 920(Printer). These values come from a Device Spec table. Putting any value other than these will throw an error
1. **Zone Code**: Should come from a pre-defined list of Administrative Zone codes created in Zone Masterdata. Current values can be “RBT”, “KTA”, “SAL”, “BSN”, “CSB”, ”STT”, ”NDR”, ”BRK”, “JRD”, “SAF“, “YSF“, “TTA“, “TZT”.”
1. **Lang_code**: eng
1. **Is_active**: True
1. **cr_by**: `<username>` ideally name of the admin
1. **cr_dtimes**: now()
### 2.6 Map the User to a Zone
1. **User ID**: from master_userdetail
1. **Zone_code**: Should come from a pre-defined list of Administrative Zone codes created in Zone Masterdata. Current values can be “RBT”, “KTA”, “SAL”, “BSN”, “CSB”, ”STT”, ”NDR”, ”BRK”, “JRD”, “SAF“, “YSF“, “TTA“, “TZT”.”

**Note**: While mapping Machine, User, Device to a Center in points 2.6, 2.7, 2.8, 2.9, 2.10, these resources should belong to the same zone code. For example, while mapping a machine to a Center, both machine and a center should belong to same zone.

### 2.7 Map the Machine to a Center
1. **Center ID**: from **master-registration_center**
1. **Machine ID**: from **master-machine_master** (newly created machine)
1. **Lang_code**: eng
1. **Is_active**: True
1. **cr_by**: `<username>` ideally name of the admin
1. **cr_dtimes**: now()
### 2.8 Map the User to a Center
Follow the above example in [**point 2.4**](#24-create-a-device).
### 2.9 Map the Device to a Center
Follow the above example in [**point 2.4**](#24-create-a-device).
### 2.10 Map Center-Machine-Device
Follow the above example in [**point 2.4**](#24-create-a-device).
### 2.11 Map Center-Machine-User
Follow the above example in [**point 2.4**](#24-create-a-device).
### 2.12 Store History of MasterData 
After adding all these data in the DB, we would need to create the same records in all the History tables for every table mentioned in the “**Tables Names**” section.
1. Each history table has an extra attribute “effective date” other than the standard attributes mentioned for each table. 
1. The Effective date should be now().and all the attributes should be same as they are stored in the standard tables.
1. Find the table names below for history tables
   1. Registration Centers: [**master-registration_center_h**](/mosip/mosip-platform/blob/master/db_scripts/mosip_master/dml/master-registration_center_h.csv)
   1. Machines: [**master-machine_master_h**](/mosip/mosip-platform/blob/master/db_scripts/mosip_master/dml/master-machine_master_h.csv)
   1. Users: [**master-user_detail_h**](/mosip/mosip-platform/blob/master/db_scripts/mosip_master/dml/master-user_detail_h.csv)
   1. Devices: [**master-device_master_h**](/mosip/mosip-platform/blob/master/db_scripts/mosip_master/dml/master-device_master_h.csv)
   1. Center-Machine Mapping: [**master-reg_center_machine_h**](/mosip/mosip-platform/blob/master/db_scripts/mosip_master/dml/master-reg_center_machine_h.csv)
   1. Center-Device Mapping: [**master-reg_center_device_h**](/mosip/mosip-platform/blob/master/db_scripts/mosip_master/dml/master-reg_center_device_h.csv)
   1. Center-User Mapping: [**master-reg_center_user_h**](/mosip/mosip-platform/blob/master/db_scripts/mosip_master/dml/master-reg_center_user_h.csv)
   1. Center-Machine-Device Mapping: [**master-reg_center_user_machine_h**](/mosip/mosip-platform/blob/master/db_scripts/mosip_master/dml/master-reg_center_user_machine_h.csv)
   1. Center Machine User Mapping: [**master-reg_center_machine_device_h**](/mosip/mosip-platform/blob/master/db_scripts/mosip_master/dml/master-reg_center_machine_device_h.csv)
   1. User Zone Mapping: [**master-zone_user_h**](/mosip/mosip-platform/blob/master/db_scripts/mosip_master/dml/master-zone_user_h.csv)

## 3. Load updated CSVs to the database using dml sql script:
Run dml sql scripts on DB server where master seed data needs to be updates.

`mosip_master=#\ir '/mosip/mosip-platform/blob/master/db_scripts/mosip_master/mosip_master_dml_deploy.sql'`

