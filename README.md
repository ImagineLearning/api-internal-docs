# Pushing changes to an IL GitHub service master branch
## Overview
Before you can push changes to the master branch you will need to create a branch, push the branch to GitHub, and create a pull request.  Once the pull request is approved you will be able to merge the branch into the master branch.

## Branching
To create a local branch:
```
$ git checkout -b feat/myNewFeature
```
To push a local branch to github first time:
```
$ git push --set-upstream origin feat/myNewFeature
```
After you have pushed your local branch to the remote GitHub repo you can simplify the push to this:
```
$ git push
```

## Pull Requests
From the GitHub website you will be able to create a pull requests.  General details about creating pull requests can be found [here](https://help.github.com/articles/creating-a-pull-request/).

For a pull requests to be approved you will need to meet two requirements:
1. Your build needs to pass the service unit and integration tests (See the [Teamcity and Branches](#teamcity-and-branches) section).
2. Your build will need to be approved by someone in the 'ILServiceDevs' GitHub.  

### What do I do now that my pull request is approved?
Once your pull request is approved you can merge it into the master branch.  You can find instructions on how to do this [here](https://help.github.com/articles/merging-a-pull-request/).  Merging the branch will cause a new build to create, tested and deployed to the test environment.

_**Note:** It is recommended that you [delete](https://help.github.com/articles/deleting-unused-branches/) the branch from GitHub once you have merged your changes into the master branch.  You will be given the option to do this after merging in your branch._

# Reviewing IL GitHub service Pull Requests
Our GitHub repositories use an integration called [PullApprove](https://pullapprove.com).  This integration follows a slightly different workflow than the out-of-the-box pull requests approval mechanism from GitHub.  The major difference is you will not be given a button to approve or reject a pull request.  Instead you will add a comment with the text "Approved" or "Rejected".  The regular expression for this is case sensitive.

You can find out more about approving pull requests [here](https://help.github.com/articles/approving-a-pull-request-with-required-reviews/).  Just keep in mind the difference explained in the previous paragraph.

# TeamCity and Branches
Only branches matching the following build specifications will be tested and built:
- master
- feat/*
- bug/*

Master is the only branch the will be promoted to the test environment through Octopus Deploy.  The other branches will only be built and tested by TeamCity.

# Applicable GitHub Repositories
- https://github.com/ImagineLearning/api-auth
