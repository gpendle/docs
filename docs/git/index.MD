# Git Tutorial

## [1 - Get Started with Git from the command line](./get-started-from-the-command-line.md)

Before you can use git from the command line you need to install it

## [2 - Create a New Git Repo](./create-new-repo.md)

New repos should be created using VSTS.  If you are working on a codebase that is not intended to be shared with anyone, e.g a private piece of code, or following some tutorials, then you can create a local git repo and get the benefits of a version control system without the server component.

## [3 - Create a CI Build Definition](./create-ci-build-definition.md)

Create a new build definition for the Master branch to enforce a level of code quality.  

## [4 - Configure Branch Policy](./configure-branch-policy.md)

Use Branch Policies to protect the important branches in your repo and enforce code qualiy and change management.

## [5 - Clone a Repo](./clone-repo.md)

Create a complete local copy of an existing Git repo using by cloning it. Cloning a repo downloads all commits and branches in the repo and sets up a named relationship (origin) with the existing repo you cloned. Use this relationship to interact with the existing repo, pushing and pulling changes to share code with your team. To clone a repo you needs its URL.

## [6 - Work in Branches](./work-in-branches.md)

Git branches aren't much more than a small reference that keeps an exact history of commits, so they are very cheap to create.Committing changes to a branch will not affect other branches

Since the branches are lightweight, switching between branches is quick and easy. Git does not create multiple copies of your source when working with branches - it uses the history information stored in commits to recreate the files on a branch when you start working on it. Your Git workflow should create and use branches for managing features and bugfixes. The rest of the Git workflow, such as sharing code and Review code with pull requests all work through branches. Isolating work in branches makes it very simple to change what you are working on by simply changing your current branch.

## [7 - Save work with commits](./save-work-with-commits.md)

Git does not automatically snapshot your code as you make edits to files in your repo. You must tell Git exactly which changes you want to add to the next snapshot by staging those changes. After staging your changes, create a commit to save the snapshot to your repo.

Git tracks file changes in your repo as you work, and separates the files in your repo into three categories:

## [8 - Push changes](./push-changes.md)

Share changes made in commits and branches using the push command. Push your branches to the remote repository, where Git takes the commits and adds them to an existing branch on the remote or creates a new branch with the same commits as your local branch

Pushed branches that have finished work are reviewed and merged into the main branch of the your repo through a pull request.

## [9 - Review code with pull requests](./review-code-with-pull-requests.md)

Git's workflow uses branches to isolate work until you're ready to merge the changes into your default branch, such as master. The pull request is the collaborative process that lets the rest of the team discuss changes in a branch and agree to merge them once everyone approves. Use pull requests to get early feedback from others on work in progress, even if you're not ready to merge the changes into another branch.

## [10 - Merging and Rebasing](./merging-and-rebasing.md)

Update code in your local repo with changes from the remote repo.

## [11 - Resolve conflicts](./resolve-conflicts.md)

When you merge one branch into another, file changes from commits in one branch can conflict with the changes the other. Git attempts to resolve these changes by using the history in your repo to determine what the merged files should look like. When it isn't clear how to merge changes, it halts the merge and tells you which files conflict.

## [12 - Undo changes](./undo-changes.md)

When undoing changes in Git, first decide what type of changes you are looking to undo. These changes fall into three categories:

Discard uncommitted changes to a file, bringing the file back to the version in the last commit.
Reset your local branch to a previous commit.
Revert changes pushed to a remote branch and shared with others.

## [13 - Ignore files](./ignore-files.md)

Not every file created or updated in your code should be committed to Git. Temporary files from your development environment, test outputs and logs are all examples of files that you create but are not part of your codebase. Customize which files Git tracks through the gitignore feature.

## [14 - Deleting Branches](./deleting-branches.md)

Branching is cheap in Git and we have to delete branches that are no longer needed.