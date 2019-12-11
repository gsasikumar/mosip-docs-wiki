
## Build and release process
### Project management tool?
Open JIRA will be used as the project management tool. <TODO>

### “Definition of Done” of a feature

Feature --> JIRA Story --> Design documents, API spec

--> Development

--> Automation test scripts

--> Performance test scripts

--> Infra

--> Config, if applicable

### Usage of Git repository

<TODO>

Is the repository structure finalized with the various repository style? If yes, put the same.

### How the Fork, branches, Tags and Releases are used?

<TODO>

### Continuous integration

<TODO>

### List Server environments

#### Development:
<TODO>

#### Dev environment (Used for CI)
<TODO>

#### FunctionalQA
<TODO>

#### PerformanceQA
<TODO>

#### SecurityQA
<TODO>

#### Production
<TODO>

### Workflow description. How the code flow happens from the contributor till production?

<TODO>

### Release management process

 1. Release manager plans the release
 2. Features are created in JIRA
 3. Contributor picks up the story
 4. Code comes from the contributor
 5. Reviewer reviews the code
 6. The moderator checks all the artifacts for feature completion, such as

		a. Application Code
		
			<TODO>
		
		b. Automation tests
			<TODO>

		c. Performance tests
			<TODO>

		d. Security tests
			<TODO>

		e. Documents
			<TODO>

		f. Configurations
			<TODO>

		g. Infra
			<TODO>

 7. Submits the build

	 	<TODO>

 8. CI kicks in

 	 	<TODO>

 9. Tests occur in FunctionalQA, PerformanceQA and SecurityQA

	 	<TODO>
	 	
 10.  Once all the features are finalized, the features are moved to the release(How we mark a version or release is discussed in another section)

 	 	<TODO>
