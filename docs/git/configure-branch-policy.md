# Configure Branch Policies

Use [Branch Policies](https://www.visualstudio.com/en-us/docs/git/branch-policies) to protect the important branches in your repo and enforce code qualiy and change management.

## Branch policies

On your team project open the _Code__ hub for your repo and navigate to __Branches__.  Use the action menu (...) for the branch you want to protect and choose __Branch policies__.

![select branch policy](./_assets/select-branch-policy.png)

### Protect this branch

Check __Protect this branch__ and configure the following based on your contribution model. 

![protect this branch](./_assets/protect-this-branch.png)

### Require a minimum number of reviewers

Should be enabled and have at least one reviewer.  It is an exception to allow users to approve their own changes, when working in a team users should not be reviewing their own changes.

![branch policy reviewers](./_assets/branch-policy-reviewers.png)

### Check for linked work items

This should be on and set to Required, no exceptions.

![branch policy work items](./_assets/branch-policy-work-items.png)

### Check for Comment resolution

This should be on and set to __Required__.

![branch policy comments](./_assets/branch-policy-comments.png)

### Enforce a Merge Strategy

This depends on the contribution model.  If you are going to delete the source branch when completing the pull request use a [squash merge](https://www.visualstudio.com/en-au/docs/git/merging-with-squash).  As a starting point use a Squash merge strategy and use no-fast-forward merge as the exception.

![branch policy merge strategy](./_assets/branch-policy-merge-strategy.png)

### Build Validation

Add a build policy and choose your CI build.

> Don't forget to save changes.

