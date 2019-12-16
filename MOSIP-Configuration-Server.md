# MOSIP Configuration Server

We will be using MOSIP config server (Spring cloud configuration Server) to manage configurations of all the services.<br/><br/>
**NOTE:** For the documentation purpose I have mentioned the config server URL as `http://localhost:8080` in this document, but you have to mention the URL where configuration server is running.

![Configuration Server](_images/arch_diagrams/MOSIP_config_server_setup.png)

## Git Repo
1. All the configuration files at the moment are stored inside git in<br/>
   **\git\mosip\config**<br/> (can be customized to take it from git repo of system owner. 
 Change spring.cloud.config.server.git.search-paths property in config server bootstrap.properties accordingly.)
2. For every module (specific to an environment such as dev, qa, test etc.) there will be a single property file (eg: for kernel)<br/>
   The nomenclature will be as follows:<br/>
   **_{module-name}-{profile-Name}.properties_**<br/>
   For example if the application name is kernel and microservice is kernel-idgenerator-vid and profile name can be 
   dev(to differentiate between different environments, eg: testing, dev, qa etc.), so the properties file name
   will be:<br/>
   **kernel-dev.properties**<br/>
3. If we are using multiple profiles, say one for dev and one for testing, we can create 2 properties files with names - **kernel-test.properties, kernel-dev.properties**, and can switch between multiple profiles through Microservice application.
4. Properties common across the modules will be stored in files named: **application-{profile-name}.properties**
5. For XML files, name them as follows:<br/>
   _**{NameOfFile}-{profileName}.xml**_
## Microservices Configuration Clients:<br/>
### Spring boot client<br/>
All the microservices will act as clients and reuqest configuration from config server.<br/>
1. Microservices should include _spring-cloud-starter-config_ dependency, which can be added through maven in their pom.xml.

`		<dependency>`<br/>
			`<groupId>org.springframework.cloud</groupId>`<br/>
			`<artifactId>spring-cloud-starter-config</artifactId>`<br/>
		`</dependency>`<br/>

  For actuators refresh endpoint (to refresh properties at runtime) we need actuator dependency in client

`               <dependency>`<br/>
			`<groupId>org.springframework.boot</groupId>`<br/>
			`<artifactId>spring-boot-starter-actuator</artifactId>`<br/>
			`<version>${spring.boot.version}</version>`<br/>
		`</dependency>`<br/>
2. There should be one **bootstrap.properties** file in the spring boot application(microservice) under resources which will contain the details for MOSIP config server. Inside the properties file following properties have to be mentioned:
* **spring.cloud.config.uri** key with the value of URL of config server that will be provided.
* **spring.cloud.config.label** which will define the branch from which we have to get properties from.
* **spring.profiles.active** which will contain the value of profile to be activated (Eg. dev for dev profile, when filename is kernel-dev.properties, and test for test profile when filename is kernel-test.properties).
* **spring.cloud.config.server.git.search-paths** which is the folder inside git repo which contains the configuration files.
*  **spring.application.name** name of the application/microservice <br/>
*  **spring.cloud.config.name** name of module to which the microservice belongs (eg. Kernel, Pre-Registration) <br/>

Sample Bootstrap.properties file:<br/>

`#Port where the application needs to run`<br/>
`server.port = 8081`<br/>
`# Application name - the name appended at starting of file name to differentiate`<br/>
`# between different property files for different microservices`<br/>
`spring.application.name=kernal-idgenerator-vid`<br/>
 
`#Active Profile - will relate to development properties file in the server.`<br/>
`#If this property is absent then default profile will be activated which is`<br/>
`#the property file without any environment name at the end. `<br/>
`spring.profiles.active=dev`<br/>


`# defining current branch in which we are working as label`<br/>
`spring.cloud.config.label=master `<br/>
 

`# url where spring cloud config server is running `<br/>
`spring.cloud.config.uri=http://localhost:8080`<br/>

 
`#spring.cloud.config.name=kernel`<br/>

`spring.cloud.config.server.git.search-paths=config`<br/>

`#exposing refresh endpoint so that whenevr configuration changes in git,`<br/>
`#post /actuator/refresh endpoint can be called for the client microservices`<br/>
`#to update the configuration`<br/>
`management.endpoints.web.exposure.include=refresh`<br/>
3. Once the setup is done, the microservice/application will be able to fetch the properties from config server. For Example:

`/** `<br/>
 `* `<br/>
 `* RefreshScope annotation is used such that all the rest APIs can be updated by calling`<br/>
 `* POST /actuator/refresh endpoint whenever configuration files change in git repo. `<br/>
 `*`<br/>
 `*/`<br/>
`@RefreshScope`<br/>
`@RestController`<br/>
`class MessageRestController {`<br/>
	
`	protected final Log logger = LogFactory.getLog(this.getClass());`<br/>
	
 `   @Value("${msg:Hello world - Config Server is not working..pelase check}")`<br/>
  `  private String msg;`<br/>
    
   ` @RequestMapping("/msg")`<br/>
    `String getMsg() {`<br/>
     `   return this.msg;`<br/>
        
   `  } `<br/>
In the above snippet we are using @RefreshScope annotation which will help the client application to get lastest configuration from config server without restarting the application (by calling the refresh API /actuator/refresh on the application endpoint) <br/>
4. For any other configuration file such as xml/json etc. you can directly get the entire file through the following url:<br/>
**http://{mosip-config-server URL}/{spring.cloud.config.name} /{label} /{branch}/{filename}.(xml/json).** 
<br/>
<br/>
### Vert.x client:
1. For Vert.x application we need the following dependencies to be added to our Maven project:
        `<dependency>`<br/>
		  `<groupId>io.vertx</groupId>`<br/>
		  `<artifactId>vertx-config-spring-config-server</artifactId>`<br/>
		  `<version>3.5.4</version>`<br/>
	`</dependency>`<br/>
	`<dependency>`<br/>
	`	  <groupId>io.vertx</groupId>`<br/>
	`	  <artifactId>vertx-config</artifactId>`<br/>
	`	  <version>3.5.4</version>`<br/>
	`</dependency>`<br/>
2. We will be using **ConfigRetrieverOptions **in Vert.x and set the store type to "spring-config-server" and we will provide configuration for this type, by giving URL in the following format:<br/>
**_{config-server-url}/{applicationname}-{microservicename}/{profile-name}/{branchname}_**<br/>
   ` protected Future<Void> readConfig(String hoconConfigPath) {`<br/>
         `Future<Void> future = Future.future();`<br/>
         `/ **`<br/>
          `* Adding config options for vert.x application`<br/>
          `*/`<br/>
         `ConfigRetrieverOptions options = new ConfigRetrieverOptions();`<br/>
         `options.addStore(new ConfigStoreOptions()`<br/>
         `		/**`<br/>
         `		 *  Vert.x provides different stores to choose from, right now we are selecting`<br/>
         `		 *  spring-config-server to connect to our server`<br/>
         `		 */`<br/>
           `      .setType("spring-config-server")`<br/>
             `    /**`<br/>
               `   * We are providing URL in the following format - `<br/>
                 ` * <config-server-url>/<application-name-microservicename>/<profile-name>/<branch-name>`<br/>
                 ` * /`<br/>
                 `.setConfig(new JsonObject().put("url", "http://localhost:8080/kernal-kernel-idgenerator-vid/uin/DEV")`<br/>
                 `		.put("timeout", 10000)));`<br/>


3. Once the setup is done we can use the ConfigRetriever class object to fetch the configuration as follows:<br/>
        `/**`<br/>
         `* ConfigRetriever object to retrieve the configuration stored`<br/>
         `*/`<br/>
        `ConfigRetriever retriever = ConfigRetriever.create(vertx, options);`<br/>
        `retriever.getConfig(ar -> {`<br/>
         `   if (ar.succeeded()) {`<br/>
          `  	/**`<br/>
           ` 	 * All the configuration is stored in this configuration object, we can use it anywhere`<br/>
            `	 * to fetch the values by providing the keys`<br/>
            `	 */`<br/>
             `   this.configuration = ar.result();`<br/>
              `  future.complete();`<br/>
            `} else {`<br/>
             `   LOG.error("Failed to read configuration", ar.cause());`<br/>
              `  future.fail(ar.cause());`<br/>
            `}`<br/>
        `});`<br/>
         `return future;`<br/>
    ` }`<br/>
4. Lets assume I put port number in which the application will be running in the properties file, and I need to get that port value while initiating the application, I can get it as follows:<br/>
       ` Integer port = Integer.parseInt(configuration.getString("port"));`<br/>
        `server = vertx.createHttpServer()`<br/>
        		`.requestHandler(req -> `<br/>
        			`	req.response().end("I am running on the port fetched from the configuration "`<br/>
        						`+ "stored in Spring config server")).listen(port);`<br/>

**NOTE:** <br/>**Whenever there is a change in the configuration in GIT Repo, every microservice/application which  is using that particular configuration has to call the refresh endpoint in order to get that latest configuration without restarting. If the client doesn't call the refresh API, it will keep on getting the old configuration.** <br/>
The refresh end point is following:<br/>
**POST  {Microservice-URL} /actuator/refresh**


**For Encryption and Decryption of properties** you need to generate Keystore, For more information look [here](//cloud.spring.io/spring-cloud-config/single/spring-cloud-config.html#_creating_a_key_store_for_testing)

To setup and configure keystore for config server refer to the configuration server [README](/mosip/mosip/blob/0.9.0/kernel/kernel-config-server/README.md) (under mosip -> kernel -> kernel-config-server -> README.md)

**To Encrypt any property:** <br/>
Run the following command : <br/>
`curl http://<your-config-server-url>/<config-server-application-context-path-if-any>/encrypt -d <value-to-encrypt>`

And place the encrypted value in client application properties file with the format: <br/>
`password={cipher}<encrypted-value>`

**To Decrypt any property manually:** <br/>

`curl /<config-server-application-context-path-if-any>/decrypt -d <encrypted-value-to-decrypt>`

**NOTE** There is no need to write decryption mechanism in client applications for encrypted values. They will be automatically decrypted by config server as long as `{cipher}` is prefixed with encrypted value.




