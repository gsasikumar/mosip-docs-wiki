# Contributor's guide

- [Welcome note](#welcome-note)
- [How to begin your contribution?](#how-to-begin-your-contribution)
	- [Register yourself](#register-yourself)
	- [Contributor License Agreement(CLA)](#contributor-license-agreementcla)
	- [Code of conduct](#code-of-conduct)
	- [Feature wise development](#feature-wise-development)
	- [Roles](#roles)
	- [Developers handbook](#developers-handbook)
	- [Git workflow](#git-workflow)
	- [How Requirement, Code, testing, documents, configuration and infra comes together?](#how-everythings-comes-together)
	- [How to setup your development environment?](#how-to-setup-your-development-environment)
	- [Quality metrics](#quality-metrics)
- [Community](#community)


## Welcome note
First of all, congratulations and a warm welcome to the contributors. This guide be the starting point for any contrubutor and will help the contributors to contribute to MOSIP. 

Please go through the high level introduction about [MOSIP architecture and components](mosip-architecture-and-components.md)


## How to begin your contribution?
Help is always welcome with MOSIP! Documentation can be simplified, code can be clarified, and test coverage can be improved. 

If you want to get started on contributing, there are multiple ways to do so - 

a)  Contribute to code (fix bugs, implement new features, enhance features)

b)  Contribute to improve specifications.

c)  Suggest new features and feature enhancements.

d)  Test MOSIP and log bugs.

e)  Help us fix documentation errors.

f)   Help spread the word on MOSIP among interested developers.

There are multiple repositories within the MOSIP organization. To contribute to (a) Code, take a look at the Open Issues that are not assigned to anyone and put a comment saying “I would like to take this up” along with your approach and design preferably with pseudo code. The issue shall be assigned to you after review.  Alternatively, please join our [developer mailing list](https://groups.io/g/mosip-dev) and send an email there. The core contributors team will interact with you via Github Issue comments.  You may work in the forked version of the repository and send pull requests via Github.

For (b) - (e), i.e. new bugs, specs, features or documentation improvements, please log Github Issues under the appropriate repository, or join and write in at our [developer mailing list](https://groups.io/g/mosip-dev)

If you wish to begin your contribution, following steps are helpful. 

### Register yourself
Please refer the [User Registration guide](user-registration-guide.md)&lt;TODO&gt; register yourself in the MOSIP community.
	
### Contributor License Agreement(CLA)
Please refer the [Contributor License Agreement guide](contributor-license-agreement-guide.md)&lt;TODO&gt; for the instructions to sign the CLA.

### Code of conduct
Please go through the [Code of Conduct](code-of-conduct) before you begin the contribution. 

### Platform documentation
Check out [our repositories](https://github.com/mosip) and [Platform Documentation](https://github.com/mosip/mosip-docs/wiki/Platform-Documentation)
	
### Feature wise development
The development methodology is [Feature driven development](feature-driven-development.md)&lt;TODO&gt;

A feature consists of the following items, 
1.	Feature description or requirement
2.	Docs
3.	Application code
4.	Automation test cases
5.	Performance test cases
6.	Infra code

Once all the above items are completed, the feature will be signed-off for completion. 

### Roles
Following are the various roles in the MOSIP open source community,
 - Developer
 - Automation Tester
 - Performance Tester
 - Development Reviewer
 - Test Reviewer
 - Product Manager
 
The roles and responsibilities can be found [here](roles-and-responsibilities.md)&lt;TODO&gt;
	
### Developers handbook
If you are a developer, please refer to the the [Developer's Handbook](developers-handbook.md)&lt;TODO&gt;
	
### Coding standards
Please go through the coding standards for, 
	- [Java coding standards](java-coding-standards.md)&lt;TODO&gt;
	- [Micro services developer guidelines](micro-services-developer-guidelines.md)&lt;TODO&gt;
	- [Vert.x guidelines](vertx-guidelines.md)&lt;TODO&gt;
	
	
### Git workflow
MOSIP uses Github workflow. Refer [here](mosip-github-workflow.md)&lt;TODO&gt; for steps to take the code from MOSIP and contribute back. 
&lt;move the following to mosip-github-workflow.md file&gt;
 - How Github-workflow works?
 - Pull request
 - Review process
 - Closing the pull request

### How Requirement, Code, testing, documents, configuration and infra comes together?
This [link] gives a detailed description about how feature is completed from inception phase to completion phase. 
	
### How to setup your development environment?
As the contributor, if you decide to work on the following modules, the corresponding startup guide of be a great help. 

- Kernel
	- Services [Building and running kernel Services](building-and-running-kernel-services.md)&lt;TODO&gt;
- Pre-registration
	- Services [Building and running Pre Registration Services](building-and-running-pre-registration-services.md)&lt;TODO&gt;
	- UI [Building and running Pre Registration UI](building-and-running-pre-pregistration-ui.md)&lt;TODO&gt;
- Registration Client
	- Services [Building and running Pre Registration Services](building-and-running-pre-registration-services.md)&lt;TODO&gt;
- ID Repo
	- Services [Building and running ID Repo Services](building-and-running-id-repo-services.md)&lt;TODO&gt;
- Registration Processor
	- Verticles [Building and running Registration Processor verticles](building-and-running-registration-processor-verticles.md)&lt;TODO&gt;
- IDA
	- Services [Building and running IDA Services](building-and-running-ida-services.md)&lt;TODO&gt;
- Resident Services
	- Services [Building and running Resident Services](building-and-running-resident-services.md)&lt;TODO&gt;
	- UI [Building and running Resident Services UI](building-and-running-resident-services-ui.md)&lt;TODO&gt;

	
Out of scope: This document doesn't cover Jenkins, Docker and Kubernetes. It is upto the user to choose any of the build automation or virtualization technlogies. 
	
### Quality metrics

- You can use SONAR to check the code quality
- You can download the code quality rules from here [SONAR Code quality ruleset](code-quality-ruleset.md)&lt;TODO&gt;&lt;TODO&gt;

## Community

### Getting in touch

If you have questions about the development process 
* Feel free to jump into our [Gitter channel](https://gitter.im/mosip-community/community) or 
* Join the [mosip-dev@groups.io](https://groups.io/g/mosip-dev) mailing list. 
* Join us in our [chatroom](https://gitter.im/mosip-community/community) and [developer mailing list](https://groups.io/g/mosip-dev)
* For general queries, try info@mosip.io 

### Community Events

We actively organise online and in-person meetups and discussions. Keep an eye on [this page](https://www.mosip.io/news-events.php) for the latest.
