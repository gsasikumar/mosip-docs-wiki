### MOSIP Configurability for Real Biometrics
With Real Biometrics Release (RBR), MOSIP can be configured to work with multiple biometric modalities (viz. Fingerprint, Iris and Face). Below are configurations to enable biometrics in MOSIP.

#### 1. Registration Client - 
1.	Configuration change 
a.	Enable Biometric Auth
b.	Enable Local de-duplication
c.	Adding SDK in classpath
d. Adding MDS URLs
2.	Register Device for registrations


#### 2. Registration Processor
1.	Configure ABIS queue
2.	Configure Biometric Dedupe stage

#### 3. ID Authentication
1.	Add SDK details in classpath
`ida.fingerprint.provider=<fully qualified classname of Biometric SDK>`
`ida.face.provider=<fully qualified classname of Biometric SDK>`
`ida.iris.provider=<fully qualified classname of Biometric SDK>`
`ida.composite.biometric.provider=<fully qualified classname of Biometric SDK>`

2.	Register Biometric Devices for authentication