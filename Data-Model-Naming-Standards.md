## Audience
* Data Modelers
* DBAs
* Database Deverlopers
* Application Developers

A simple and consistent naming convention for database objects, when followed rigorously, can help database application developers greatly.  This is because developers, once they get used to the convention, can quickly identify objects belonging to their application and are less likely to make mistakes regarding the contents of columns.  In fact, an inadequate or improperly followed convention can actually increase the development effort by unnecessarily tying the application code to intricacies of the database physical design and by making application developers overly dependent on the DBA’s.

The purpose of this document is to propose a simple and consistent naming mechanism for all the objects in a database schema.  The naming convention is aimed at reducing the dependence of the application developers on the database administrator by naming objects in a way that unambiguously defines their contents.  Where applicable, there is also a mention of how not to name the object and the reasons for this.

Of course, there can be no one absolute convention that will solve all naming problems and have universal appeal.  The conventions offered in this document are merely one way of naming things that are followed in MOSIP project.

# Common Naming Standards

To name an object within the DB, the following common standards are followed

* **Singular Names to the entities**
* **Object name length to be less than 30 chars:** To be compliant with other databases, the maximum length of the object name is restricted to 30 characters.
* **Lower case object names separated by underscore (_)**
* **Only defined abbreviations are used**
* **No prefix or suffix to the table names:** Since most of the objects of MOSIP is created on their own databases, we will not have any prefix or suffix of the application / module name or abbreviation to the table or object name.
* **Each table is defined an alias, this alias is used in constraints and index names**


# Database Naming Standards

The database names will follow the below naming convention
**mosip_**<abbreviated value of the application/module name>


# Schema Naming Standards
Schema name is named after the DB name, by default, without mosip_. If there are more than one schemas in a DB, then a proper single word name is assigned, either full word or an abbreviated word.

# Table Naming Standards

The table name can have one or two words that describe the contents of the table separated by underscore (_). If there are more words then those can be abbreviated based on the standards. Making sure the table name length is less than 30.
 
The description should always be in singular (for example, REGISTRATION, REG_TRANSACTION) since they are easier to use and are shorter.  Storing the name in plural could be cumbersome, especially in the case of tables used to resolve many-to-many relationships as these could have two plurals in the name.

Table names should NOT denote whether the underlying object is a table or a view because this could change during the application cycle (for example, a join view may be converted to a pre-populated table for performance reasons or a table may be converted to a view to show some extra computed columns).  

An alias for each table is defined, this alias can be used in various other places like reference keys, indexes, constraints, etc.

# Index Naming Standards

Indexes are named as <table_name alias>_< col abbreviation > _idx_ < n >
Here n is a number of 2 digits like 01, 02,... and column abbreviation is optional

# Key Naming Standards (Primary, Unique, Foreign Keys)

**Primary Key:**
Each table should have a primary key, the key should be named as “pk_<table_alias>_<column_name>”. If it is a composite key, then in place of column name any meaning full name can be provided. PK should be defined on business key, in case for some reason a business key fields cannot be used to define a PK then add a surrogate key to the table.

**Unique Key:**
If a surrogate is used as PK then create a unique key, on fields that uniquely defines a business key. The naming of the unique key should be “uk_<table_alias>_<column_names>”.


**Foreign Key:**
Any references from a table with the master / other tables, the creating a foreign key is mandatory. This helps maintain referential integrity. Foreign key can be named as FK_<referring table alias>_<referred table alias>

# Datatype Domains

PostgreSQL has an inbuilt support to domains (standard datatypes) which other commercial / open source databases doesn’t support. So, in MOSIP we are not defining any domains. But to standardize the datatypes implementation we have defined the following common datatypes used across mosip system. The datatype sizes are defined to consider multi language storage support, which may vary based on the implementation

|Attribute |Attribute Description|Type|Size|
|-------------------- |-------------------------------------------|--------------------------------|----------------|
|vid|Virtual ID|character varying|28|
|uin|Unique Identification Number|character varying|28|
|enrl_id|Enrolment ID|character varying|28|
|_code|Code|character varying|64|
|_descr|Description|character varying|256|
|_type|Type|character varying|128|
|_name|Name|character varying|128|
|_id|Identification Code / Number|character varying|36|
|_addr_line|address line|character varying|256|
|_loc_line|location line|character varying|128|
|country|country|character varying|64|
|pin|pin|character varying|16|
|_comment / _remarks| Comments / remarks captured as part of a transaction|character varying|1024|
|count | |smallint| |
|_by| |character varying|32|
|ref_id|Reference id |character varying|64|
|ref_id_type|Reference ID Type|character varying|64|
|is_active | |boolean| |
|cr_by | |character varying|32|
|cr_dtimes | |timestamp| |
|upd_by  | |character varying|32|
|upd_dtimes | |timestamp| |
|is_deleted | |boolean| |
|del_dtimes | |timestamp||

# Acronyms 

The following acronyms are used in the data model

|Abbreviation|Description||Abbreviation|Description|
|----------------------|----------------------|---|----------------------|----------------------|
|ack|Acknowledgement||active|Active|
|addr|Address||autn|Authentication|
|bio|Biometric||cd|Code|
|cr|Created||del|Deleted|
|demo|Demographic||descr|Description|
|dob|Date of Birth||dt|Date|
|dtime|Date Time||dtimes|Date Timestamp|
|expiry|Expiry||fk|Foreign Key|
|ibio|Individual Biometric||id|Identifier|
|ida|Identity and authentication||idem|Individual Demographic|
|idsvr|ID Issuance Server||idsw|ID Issuance Software|
|Idx|Index||ins|Insert|
|ip|IP Address||lang|Language |
|last|Last||lh|Left Hand|
|lst|List||mref|Master Reference|
|msg|Message||mstr|Master|
|ntv |Native||nxt|Next|
|otp|One Time Password||parent|Parent|
|pct|Percentage||pk|Primary Key|
|pkt|Packet||preid|Pre ID Issuance|
|prev|Previous||pwd|Password|
|rcvd|Received||regn|Registration|
|remark|Remarks||rh|Right Hand|
|seq|Sequence ||status|Status|
|tkn|Token||total|Total|
|trn|Transaction ||ttyp|Transaction Type|
|typ|Type||uin|Unique Identification Number|
|upd|Update||usrl|User Login|
|vid|Virtual ID||wfl|Workflow|
|audit|Audit||dtimesz|Date Timestamp with Time Zone.|
|kernel|Kernel||reg|Registration|
|regprc|Registration Processor||prereg|Pre Registration|
