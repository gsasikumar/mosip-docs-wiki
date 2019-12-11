Any open source contributor can pick up any feature which is available in the OpenJIRA. This document mentions various aspects of a feature in MOSIP. 

## Solution

**The key solution considerations are**

 - A feature is decided by the Product manager. 
 - The product manager also consider a list of features which are combined to form a MOSIP release with a new version. 

### Aspects of a feature
 - A feature contains the following aspects, 

  1. JIRA issue
		- A feature is created as a JIRA issue. 
		- The subtasks should be as follows, 
		
			a. design 
			
			b. code
				- Must comply to the coding standards
				
			c. unit test cases
				- Unit test case coverage should be above 85%
				
			d. function test cases
			
			e. automation test cases
			
			f. security test cases
			
			g. infra code

 
### Definition of done
 
 - All the sub tasks of a feature, which is a JIRA issue, must have been in CLOSED status to consider the feature is completed. 
 - If any of the sub tasks are not required for that particular feature, proper comments are put and closed. 
 
### Workflow

 - The Product Owner creates the JIRA issue and the necessary sub tasks. 
 - The subtasks are assigned to the contributors
 - Once, all the necessary subtasks are closed, the feature is considered to be complete. 
 - The product manager decides when to tag a version for release with the list of features. 
	