# Undo Changes

When undoing changes in Git, first decide what type of changes you are looking to undo. These changes fall into three categories:

* Discard uncommitted changes to a file, bringing the file back to the version in the last commit.
* Reset your local branch to a previous commit.
* Revert changes pushed to a remote branch and shared with others.

## Reset a branch to your previous commit

Use reset to bring a branch in your local repository back to the contents of a previous commit. The most common use of the reset command is to simply discard all changed files since the last commit and return the files to the state they were in at the most recent commit.

> Don't use rest on branches shared with others, use revert instead.

## Undo changes in Visual Studio

Open the Changes view and find the files you want to restore.  Unstage the files and then Undo changes.

![Visual studio undo chagnes](./_assets/vs-undo-changes.gif)

## Undo changes form the Command Line

To remove untracked files and untracked directories from the current directory use git clean with the -d and -f options.

```git
git clean -df
```

Use the `reset` command to reset the files to the state of the previous commit.

```git
git reset HEAD~1
```

Use with the `--hard` option to discard any staged changes, this cannot be undone.

```git
git reset HEAD~1 --hard
```


You can undo the last n commits by using HEAD~n e.g. to undo the last 3 commits use:

```git
git reset HEAD~3
```

## Revert change in shared commits

Use `revert` to undo the changes made in your commits pushed to shared branches. The revert command creates a new commit that undoes the changes on a previous commit. No history is rewritten in a revert, making it safe to use when working with others.

## Revert form the Command Line

This will undo any changes made in commit 8437fbaf and create a new commit on the branch.  Review your history to find the commits you want to revert.

```git
git revert 8437fbaf
git commit
```
