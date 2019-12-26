When a reviewer gets a pull request from a contributor, the reviewer have to do necessary tests, before accepting the pull requests. 

## Solution
 
 - Following approaches are considered to test the pull requests,

### Manual approach
 - Open the pull request in Github web site. You will find the pull request \# number and branch name. Please note those. 
 - Open git bash console and make sure your directory is clean by executing the following command, 
 ```sh
 git status
 ``` 
 - Get a copy of the pull request branch by executing the command, ``` git fetch upstream pull/<id>/head:<branch> ```. For example, if the pull request number is \#823 and the branch name is MOS-123,
 ```sh
 git fetch upstream pull/823/head:MOS-123
 ```
 
 - The branch should be available in your local repository. So, switch to that branch ``` git checkout MOS-123``` and you can compile, run tests etc.,
 
 NOTE: For one feature, there can be multiple changes in multiple repositories. When you accept a pull request, identify the other dependent pull request in other repositories also. For example, for one feature, there can be changes in mosip-platform and mosip-config repositories. To functionally run the feature in your local machine, you might have to test the pull requests from both mosip-platform and mosip-config repositories. 
 
### Automatic approach &lt; TODO: following approach is yet to be developed &gt;
 - When a pull request is received, a Jenkins job is triggered, which does the following, 
	1. Compiles the code. 
	2. Unit test cases are run and checked for unit test case compliance [Unit test case compliance](unit-test-case-compliance.md) &lt;TODO&gt;
	3. The deployables are deployed to the test environment. 
	4. The test rig is executed for the quality. 
	5. The result is published to the subscribers list. 
	
 - The above steps are done in the sequential order. If one step fail, the sequence is terminated and the notification is sent to corresponding people. 