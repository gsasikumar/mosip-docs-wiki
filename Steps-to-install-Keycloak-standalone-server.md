## 1. Setup Keycloak Standalone Server setup 6.0.1
**documentation for setting up keycloak server**
### Before you begin

1. Install java (java-8-openjdk) to all the machines in the cluster and setup the JAVA_HOME environment variable for the same.
```
sudo yum install java-1.8.0-openjdk-devel
``` 
Get your Java installation path.
```
update-alternatives --display java
```

**NOTE :** Take the value of the current link and remove the trailing /bin/java. <br/>
For example on RHEL 7, the link is /usr/lib/jvm/java-1.8.0-openjdk-1.8.0.191.b12-1.el7_6.x86_64/jre/bin/java, <br/>
so JAVA_HOME should be /usr/lib/jvm/java-1.8.0-openjdk-1.8.0.191.b12-1.el7_6.x86_64/jre.

#### Edit ~/bashrc.sh:
export JAVA_HOME={path-tojava} <br/>
with your actual java installation path. For example on a Debian with open-jdk-8:
```
export JAVA_HOME=/usr/lib/jvm/java-1.8.0-openjdk-1.8.0.191.b12-1.el7_6.x86_64/jre
```

### Download keycloak 
Download and unzip keycloak
```  
sudo wget "https://downloads.jboss.org/keycloak/6.0.1/keycloak-6.0.1.tar.gz" 
sudo tar xzf keycloak-6.0.1.tar.gz
```
**Here we are installing postgres as a database with keycloak you can use any database supported by keycloak**

[Keycloak Database Setup](https://www.keycloak.org/docs/latest/server_installation/index.html#_database)

Install Postgres in your vm

```
refer postgres
```
Within the  _…​/modules/_  directory of your Keycloak distribution, you need to create a directory structure to hold your module definition. The convention is use the Java package name of the JDBC driver for the name of the directory structure. For PostgreSQL, create the directory  _org/postgresql/main_. Copy your database driver JAR into this directory and create an empty  _module.xml_  file within it too.

Module Directory

![db module](https://www.keycloak.org/docs/latest/server_installation/keycloak-images/db-module.png)

After you have done this, open up the  _module.xml_  file and create the following XML:

Module XML

```
<?xml version="1.0" ?>
<module xmlns="urn:jboss:module:1.3" name="org.postgresql">

    <resources>
        <resource-root path="postgresql-9.4.1212.jar"/>
    </resources>

    <dependencies>
        <module name="javax.api"/>
        <module name="javax.transaction.api"/>
    </dependencies>
</module>
```

The module name should match the directory structure of your module. So,  _org/postgresql_  maps to  `org.postgresql`. The  `resource-root path`  attribute should specify the JAR filename of the driver. The rest are just the normal dependencies that any JDBC driver JAR would have.



**Create a service to start keycloak**


```
sudo cat > /etc/systemd/system/keycloak.service <<EOF

[Unit]
Description=Jboss Application Server
After=network.target

[Service]
Type=idle
User=root
Group=root
ExecStart=/opt/keycloak-6.0.1/bin/standalone.sh -b 0.0.0.0
TimeoutStartSec=600
TimeoutStopSec=600

[Install]
WantedBy=multi-user.target
```
**Enable ssl for keycloak server**

To enable ssl we need a certificate which here in example we will use Lets encrypt

Follow the steps in this link to create a certificate for your domain

[https://certbot.eff.org/lets-encrypt/](https://certbot.eff.org/lets-encrypt)

We will create a keystore in which we will store certificate chain and private key and give them an alias

```
openssl pkcs12 -export -inkey{{private key pem path}} -in {{certificate pem path}} -password pass:{{keystore password}} -out {{output keystore name}} -name {{alias}}
```


**Configure standalone xml**

1. Go to {{keycloak folder}}/standalone/configuration
2. Open Standalone.xml and make following changes


2.1  Add a driver for postgres(Or your database)
```
<driver  name="postgresql"  module="org.postgresql">
<xa-datasource-class>org.postgresql.xa.PGXADataSource</xa-datasource-class>
</driver>
```
2.2  Change the datasource properties
```
<datasource  jndi-name="java:jboss/datasources/KeycloakDS"  pool-name="KeycloakDS"  enabled="true"  use-java-context="true">
<connection-url>jdbc:postgresql://localhost:9001/{{database_name}}</connection-url>
<driver>{{}drivername}</driver>
<pool>
<max-pool-size>pool size</max-pool-size>
</pool>
<security>
<user-name>database username</user-name>
<password>database password</password>
</security>
</datasource>

```
2.3 Register the datasource

While registering change the schema name if you want.
```
<spi  name="connectionsJpa">
<provider  name="default"  enabled="true">
<properties>
<property  name="dataSource"  value="java:jboss/datasources/KeycloakDS"/>
<property  name="initializeEmpty"  value="true"/>
<property  name="migrationStrategy"  value="update"/>
<property  name="migrationExport"  value="${jboss.home.dir}/keycloak-database-update.sql"/>
<property  name="schema"  value="public"/>
</properties>
</provider>
```

2.4 Change network configuration

1. Inet address for both public and management profile to access it remotely


```
<interfaces>
<interface  name="management">
<inet-address value="0.0.0.0"/>
</interface>

<interface  name="public">
<inet-address value="0.0.0.0"/>
</interface>
</interfaces>
```
2. Default ports from 8080 -> 80 and 8443 -> 443 to not give ports at time of accessing keycloak
```
<socket-binding  name="http"  port="${jboss.http.port:80}"/>

<socket-binding  name="https"  port="${jboss.https.port:443}"/>
```

2.5 Adding a ssl certificate to keycloak

Here we will give the keystore we created to keycloak

```
<ssl>
<keystore  path="your key store pass relative to the next property"  relative-to="jboss.server.config.dir"  keystore-password="yourpassword"  alias="your alias"/>
</ssl>
```