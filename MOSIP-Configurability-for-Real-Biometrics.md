### MOSIP Configurability for Real Biometrics
With Real Biometrics Release (RBR), MOSIP can be configured to work with multiple biometric modalities (viz. Fingerprint, Iris and Face). Below are configurations to enable biometrics in MOSIP.

#### 1. Registration Client -   
- **Enable Biometric Auth**    
- **Enable Local de-duplication** - Below properties should be enabled for de-duplication. These properties are present in config file config/registration-{env}.properties    
`mosip.registration.mds.fingerprint.dedup.enable.flag=Y`    
`mosip.registration.mds.iris.dedup.enable.flag=Y`    
`mosip.registration.mds.face.dedup.enable.flag=Y`    
- **Adding SDK in classpath** - Place SDK jar file in `lib` folder after extracting the reg client zip file if we are running through run.bat     
- **Enable MDS** - Below property should enabled to enable MDS integration. This property is present in config file config/registration-{env}.properties
`mosip.mdm.enabled=Y`    
- **Register Device for Registration**     
   a. `Register Device Provider` - Device Provider should be registered with MOSIP using [Register Device Provider API](https://github.com/mosip/mosip-docs/wiki/Device-Management#post-deviceprovider)    
   b. `Register Device` - Biometric device should be registered using MOSIP using [Register Device API](https://github.com/mosip/mosip-docs/wiki/Device-Management#post-registereddevices)    
   c. `Register MDS` - MDS should be registered with MOSIP using [Register MDS API](https://github.com/mosip/mosip-docs/wiki/Device-Management#post-mds)    
#### 2. Registration Processor    
1.	Configure ABIS queue       
2.	Configure Biometric Dedupe stage       


#### 3. ID Authentication
- **Add SDK details in classpath** - Below properties should be set in id-authentication-{env}.properties
`ida.fingerprint.provider=<fully qualified classname of Biometric SDK>`    
`ida.face.provider=<fully qualified classname of Biometric SDK>`    
`ida.iris.provider=<fully qualified classname of Biometric SDK>`    
`ida.composite.biometric.provider=<fully qualified classname of Biometric SDK>`    
- **Register Biometric Devices for Authentication**   
   a. `Register Device Provider` - Device Provider should be registered with MOSIP using [Register Device Provider API](https://github.com/mosip/mosip-docs/wiki/Device-Management#post-deviceprovider)    
   b. `Register Device` - Biometric device should be registered using MOSIP using [Register Device API](https://github.com/mosip/mosip-docs/wiki/Device-Management#post-registereddevices)    
   c. `Register MDS` - MDS should be registered with MOSIP using [Register MDS API](https://github.com/mosip/mosip-docs/wiki/Device-Management#post-mds)  