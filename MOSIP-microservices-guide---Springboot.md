MOSIP uses microservices architecture. All the microservices are written in Java programming language. This document gives the overall picture about the java microservices in MOSIP. 

## Solution


**The key solution considerations are**

- Following are the key considerations for the sandbox environment setup,

### Pre-Requisties

When a microservice starts, it looks for 3 main things, 

	a. Config server details
	
	b. Auth server details
	
	c. Database server details

		
In order for a Springboot microservice to start, the following components should be up and running, 

1. Config server
	- The config server details are mentioned in the bootstrap.properties
	- If you are running the service in the local machine and you want to use the properties in the "\src\main\resources\application-local.properties" file, set the following property in the "\src\main\resources\bootstrap.properties"
	
	```sh
	spring.profiles.active=local
	```
	or in the run time arguments, when you start the springboot application, pass the below parameter, 
	
	```sh
	-Dspring.profiles.active=local
	```

2. Auth server
	- The Auth server should be up and running. 
	- All microservices are protected. You need a JSON Web Token(JWT) to be passed in the cookie. Without the JWT, you will get UnAuthorized errors. 
	
	- First find the roles who can access this microservice. The user with corresponding role should be present in the Auth server. When the user auhentictes, he/she gets a JWT. Then the microservice can be called passing the JWT in the cookie as, 
	
	```sh
	Authorization=<token_from_auth_server>
	```
	
	For example, 
	
	```sh 
	Authorization=0734U#$E$AKJA987345&8ASLF987&^*&9LHS
	```
	
	- The Auth server details can be found in the Spring Cloud Config server or in "\src\main\resources\application-local.properties" file
	
3. Corresponding database
	- The corresponding database, if required, should be up and running with the data populated. 
	- The database connection properties are mentioned in the bootstrap.properties
	- The database related scripts can be found in https://github.com/mosip/mosip-platform/tree/master/db_scripts
	
### How to start a MOSIP springboot microservice

Below command should be executed to run any service locally in specific profile and local configurations - 

`java -Dspring.profiles.active=local -jar <jar-name>.jar`

Below command should be executed to run any service locally in specific profile and `remote` configurations - 

`java -Dspring.profiles.active=<profile> -Dspring.cloud.config.uri=<config-url> -Dspring.cloud.config.label=<config-label> -jar <jar-name>.jar`

Below command should be executed to run a docker image - 

`docker run -it -p <host-port>:<container-port> -e active_profile_env={profile} -e spring_config_label_env= {branch} -e spring_config_url_env={config_server_url} <docker-registry-IP:docker-registry-port/<docker-image>`
