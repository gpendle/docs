# Deleting Branches

Branching is cheap in Git and we have to delete branches that are no longer needed.

## Delete stale remote tracking branches

> Visual Studio has a Git setting to auto prune origin when fetching

If a branch is deleted on the remote repo (origin) and you had a copy in your local repo it will be stale. To delete the stale branches use `git remote prune`.

```git
git remote prune origin
```

## Delete a local branch

Use git `branch` command with the `-D` option to `--force` delete.

```git
git branch -D users/gpe/featureA
```
