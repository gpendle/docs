# Merging and Rebasing

Update code in your local repo with changes from the remote repo.

## Merge

When you want to include changes from the remote branch use the following commands:

* `fetch` - downloads the changes from the remote repo but does not apply them
* `merge` - applies the change taken from fetch to a branch on your local repo
* `pull` - combines the fetch and merge

Avoid merge commits that result from git pull by using the `--rebase` option.

> You should always pull with `git pull --rebase`.  
>
> Git can be configured to make it the default behavior:  
> `git config --global --bool pull.rebase true`

### Merge/Pull in Visual Studio

In the __Syncronization__ tab use the Fetch link to pull down the incoming commits.

Team Explorer merges when you do a __Pull__ from the __Changes__ view.

### Merge/Pull from the Command Line

When pulling use the `--rebase | -r` option to avoid merge commits.  This will keep the history cleaner and more understandable.

```git
git pull --rebase
```

To resolve conflicts see Resolve conflicts

## Rebase

> This is different to the `pull` command with the `--rebase` option.

Use rebase to address the problem of updating your branch with the latest changes from the main branch. Rebase takes the changes made in the commits in your current branch and replays them on the history of another branch. The commit history of your current branch will be rewritten so that it starts from the most recent commit in the target branch of the rebase.

Rebasing your changes in your user branch off the latest changes in the main branch lets you test your changes on the most recent version in the main branch while keeping a clean Git history.

### Use caution

Rebasing is a powerful tool for catching up changes a main branch but you must be careful about its use. Some things to keep in mind before you rebase:

1. Never rebase commits that have been pushed and shared with others. The only exception to this rule is when you are certain no one on your team is using the commits or the branch you pushed. e.g. a user topic branch.
1. Use rebase to catch up with the commits on another branch as you work with a local branch. This is especially useful when working in long-running braches to check how your changes work with the latest updates on the master branch.
1. You can't update a published branch with a push after you've rebased the local branch. You'll need to force push the branch to rewrite the history of the remote branch to match the local history. Never force push branches in use by others.

> Do not use rebase on a shared branch. You can rebase a local branch that hasn't been shared or your user topic branch that has been published.

During a rebase, Git attempts to reconcile the changes recorded in the commits on your branch and the changes in the commits in the target branch. Resolve any conflicts between the commits in the same way that you resolve merge conflicts.

### Rebase from the Command Prompt

If you are working in branch users/gpe/featureA you can rebase it by:

```git
git checkout master
git pull --rebase
git checkout @{-1}
git rebase master
```

> The @{-n} is the nth previous branch you had checked out, in this case @{-1} is users/gpe/featureA

This will replay the current branches commits onto the latest commit in master.  It will make it look like you started your work from the lastest commit in master instead of an earlier commit.

After a successful rebase, your local branch will have a different history than your remote branch. You must force push your local branch to update your remote branch.

```git
git push --force-with-lease
```

Do this for user topic branches.