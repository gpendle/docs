# Push Changes

Share changes made in commits and branches using the `push` command. Push your branches to the remote repository, where Git takes the commits and adds them to an existing branch on the remote or creates a new branch with the same commits as your local branch

> Pushed branches that have finished work are reviewed and merged into the main branch of the your repo through a pull request.

## Create the remote branch

Before you can push your changes you need to create the remote branch.  Your commits on your local branch are added to the branch on origin, and a upstream tracking relationship will be set up in Git so that next time you `push` (or `fetch`) from this local branch, you won't have to specify the remote branch name.

## Push from Visual Studio

There are a few ways to publish your branch for the first time.

You can use the __sync__ command to open the __Synchronization__ tab and __push__ the branch for the first time to publish to a new remote branch.

![Visual Studio Git Sync](./_assets/vs-git-sync.gif)

Or you can use the __Branches__ tab and the context menu to __push__ your branch.

![Visual Studio Git Branch Push](./_assets/vs-git-branch-push.gif)

## Push from the Command Line

Use the `push` command with the `--set-upstream | -u` option and the name for the remote branch.  Use the same name as the local branch.

```git
git push -u origin users/gpe/feature1
```

To set the upstream branch to track without pushing use the `branch` command and the `--track | --set-upstream-to` option.

```git
git branch --set-upstream-to origin users/gpe/feature1
```

Once the tracking is established you can push additional comitts using the `push` command.

```git
git push
```

## Rebase local commits before pushing

Run this every time before pushing a set of `commits`

```git
git rebase @{u}
```

Use the `--interactive | -i` option for an interctive rebase.