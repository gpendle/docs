# Work in Branches

Git branches aren't much more than a small reference that keeps an exact history of commits, so they are very cheap to create. Committing changes to a branch will not affect other branches

Since the branches are lightweight, switching between branches is quick and easy. Git does not create multiple copies of your source when working with branches - it uses the history information stored in commits to recreate the files on a branch when you start working on it. Your Git workflow should create and use branches for managing features and bugfixes. The rest of the Git workflow, such as [sharing code](./merging-and-rebasing.md) and [review code with pull requests](./review-code-with-pull-requests.md) all work through branches. Isolating work in branches makes it very simple to change what you are working on by simply changing your current branch.

## Git Branches

Create a branch using the `branch` command.  Branch creates a reference in Git for the new branch and a pointer back tot the parent commit so Git can keep a history of changes as you add commits to the branch. When you are working with a branch that someone else shared, Git keeps an upstream tracking relationship to associate the branch on the local repo with the corresponding branch on the remote repo. This makes it very simple to sync changes with others using `push` and `pull`.

> `pull` is shorthand for doing a `fetch` and `merge`.

![Visual of a branch off master in Git](./_assets/branch.png)

In this image, a new branch is created from the main branch. Work continues on both branches and commits are added to both branches.

Git always adds new commits to the current local branch. Check what branch you are working on before you commit so that you don't commit changes to the wrong branch.

Swap between local branches using the `checkout` command. Git will change the files on you computer to match the latest commit on the checked out branch. When your work in the branch is ready to share with the rest of the team, you `push` the changes to update the remote branch.

A common mistake is to make some changes and commit them, realize you are on an incorrect branch, then checkout to the correct branch. Your most recent changes will no longer be on the filesystem since each branch has its own version of code. Git will bring the state of the files back to the last commit on the branch you swapped into, not the previous branch where you made your changes. You'll need to either cherry-pick the commits from the branch or merge the changes into the correct branch.

> Your branches are local and untracked until you `push` them to the `origin` server.

## Create a Branch

Create a branch for your work, the branch you base it on depends on your branching strategy and the work you are doing.

### Visual Studio

In Visual Studio open the __Branches__ tab in __Team Explorer__.  Right click master and choose __New Local Branch From...__ or use __New Branch__.

![Visual Studio new local branch](./_assets/vs-new-local-branch.jpg)

Give the branch a name (note this is using a users topic to indicate that the branch is not meant to be used for collaboration) and click __Create Branch__.

This will create a new local branch that is not tracking a remote branch.  Note that there is no green arrow on the branch.

> You can see what branch you have checked out in the bottom status bar. ![Visual Studio Git Tray](./_assets/vs-git-tray.png)

### Command Line

To create a local branch and check it out use:

```git
git branch feature1
git checkout feature1
```

To create and checkout a branch in one step use the `checkout` command with the `-b` option:

```git
git checkout -b users/gpe/feature1
```

Note that the current branch is used to create the users/gpe/feature1 branch.  

Before creating a branch `pull` to make sure your local soure branch is up to date with the remote.

```git
git checkout master
git pull
git checkout -b users/gpe/feature1
```

> When ckecking out master you will get two messages, the first is the branch you are on and the second is your merge status. __Your branch is up to date with origin\master__ means all fetched commits have been merged, you still need to `pull` to get newer commits from the server.  

## Delete a Branch

> Deleting a branch in your local repo doesn't remove the branch on the remote.

To delete a branch checkout another branch (e.g. master) first.

### Delete a Branch from Visual Studio

In the Branches tab right click the branch you want to delete and select delete, or select it and press the delete key.

![Visual Studio Delete Branch](./_assets/vs-git-delete-branch.jpg)

### Delete a Branch from the Command Line

To delete a local branch use the `branch` command with the `-d` option.

```git
git branch -d users/gpe/bugfix
```

To `--force` delete the branch use the upper case option:

```git
git bracnch -D users/gpe/bugfix
```

## Use branches to manage development

Git keeps track of which branch you are working on and makes sure that when you checkout a branch your files match the most recent commit on the branch. Branches let you work with multiple versions of the source code in the same local Git repository at the same time. Tell Git which branch you want to work on with checkout, and Git takes care of setting the right file versions for that branch.

You shouldn't need more than one repo on your system when you use branches to isolate your work. Set up your development environment one time after you clone, and then use Git branches to swap between feature work and bug fixing.