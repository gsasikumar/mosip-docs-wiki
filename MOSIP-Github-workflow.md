### 1. Fork the MOSIP repository

 a. Choose any of the following respositories for which you wish to contribute, 

	https://github.com/mosip/mosip-platform

	https://github.com/mosip/mosip-ref-impl

	https://github.com/mosip/mosip-functional-tests

	https://github.com/mosip/mosip-docs


 b. From the github website in the browser, click the Fork button on the right top of the page, to fork MOSIP repository

### 2. Clone the fork to local machine
 - Go to github website in browser and switch to forked repository. Click the button "Clone or download" from the top right area. Copy the clone URL. 
 - Create your directory and clone the repository for which you wish to contribute. For example, if you wish to contribute to "mosip-platform", execute the following command. 

```sh
git clone https://github.com/kumarps/mosip-platform.git
cd mosip-platform
git remote add upstream https://github.com/mosip/mosip-platform.git
```
NOTE: 
 - You are cloning the forked repository in the above step. 
 - You are adding the upstream of the main git repository. 

Go inside the newly created cloned folder and execute the 

#### Never push to upstream master
 - IMPORTANT: Make sure that you never push to upstream master
 
```sh
git remote set-url --push upstream no_push
```

#### Confirm that your remotes make sense:
```sh
git remote -v
```

### 3. Creating your feature branch to work on

 - Naming conventions for the branch is a must. 

a. First, update your master with the latest changes from the community.

```sh
git fetch upstream
git checkout master
git rebase upstream/master
```

b. Create your own feature branch, in case, if you want to add a feature. 

```sh
git checkout -b feature/${JIRA_ID}
```

c. Create your own issue branch, in case, if you want are working in a issue fix. 

```sh
git checkout -b issue/${JIRA_ID}
```

### 4. Keeping your branch synced

```sh
# While on your feature branch
git fetch upstream
git rebase upstream/master
```

DON'Ts: 
 - Don't use `git pull` command. 
 - Execute the following command to ensure that you don't use the pull command. 
 - `git config branch.autoSetupRebase always`

 
### 5. Commit
 - Once you are done with the work, commit your changes using the following command, 

```sh
git commit -m "${JIRA_ID}_${your_meaningful_commit_message}
```

For example, 

```sh
git commit -m "MOS-2346_Adding new upload feature in Pre registration module for POA documents"
```

DOs:
 - Start your comment with JIRA id, followed by an underscore '_' and then your comments. If the JIRA ID and the underscore is not there, your pull request will be rejected. 
 - Give meaningful comments.

### 6. Push
 - you can push your branch to remote, in case of, 
	 - Whenever you are done with the work or issue, 
	 - Or in case, if you want to back up your on the remote repository
 - Use the following command to push the code, 

```sh
git push -f ${your_remote_name} feature
```

For example, 
```sh
git push -f origin feature/${JIRA_ID}
```

### 7. Pull request
When the feature or issue is completed, the contributor have to raise a pull request for the change to be merged to the MOSIP. Following are the DOs and DONTs

#### Checklist before your submit a pull request
 - In case of code contribution, ensure that your code completely builds with the necessary checklists as mentioned in the [Developer's Handbook](developers-handbook.md) such as Coding standards, Quality metrics, Documentation standards etc., 
 - If any of the items in the checklist is not covered, your pull request will be rejected. 

#### Get your code reviewed
 - Following are the steps to raise a pull request, 
	1. Visit your fork in the URL, `https://github.com/${user}/${repo-name}`. For example, `https://github.com/kumarps/mosip-platform`
	2. Switch to your branch
	2. Click the `Pull Request` button.
#### 