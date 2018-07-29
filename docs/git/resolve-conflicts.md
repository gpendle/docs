# Resolve Conflicts

## Understand merge conflicts

When you merge one branch into another, file changes from commits in one branch can conflict with the changes the other. Git attempts to resolve these changes by using the history in your repo to determine what the merged files should look like. When it isn't clear how to merge changes, it halts the merge and tells you which files conflict.

![Master and bugfix branch have changes that conflict](./_assets/master-and-bugfix-branch-have-changes-that-conflict.png)

This image shows a very basic example of how changes conflict in Git. Both the master and bugfix branch make updates to the same lines of source code. If you try to merge the bugfix branch into master, Git can't determine which changes to use in the merged version. You may want to keep the changes in the master branch, the bugfix branch, or some combination of the two. Resolve this conflict with a merge commit on the master branch that reconciles the conflicting changes between the two branches.

![Create a merge commit to resolve the conflict between the two branches](./_assets/create-a-merge-commit-to-resolve-the-conflict-between-the-two-branches.png)

The most common merge conflict situation is when you pull updates from a remote branch to your local branch, for example from origin/bugfix into your local bugfix branch. Resolve these conflicts is the same way-create a merge commit on your local branch reconciling the changes and complete the merge

> With an effective branching strategy and using pull --rebase and cherry picks we can reduce the number of merge commits. 

## What does Git do to prevent merge conflicts

Git keeps an entire history of all changes made in your repo. Git uses this history as well as the relationships between commits to see if it can order the changes and resolve the merge automatically. Conflicts only occur when it's not clear from your history how changes to the same lines in the same files should merge.

## Preventing merge conflicts

Git is very good at automatically merging file changes in most circumstances, provided that the file contents don't change dramatically between commits. Consider rebasing branches before you open up a pull request if your branch is far behind your main branch. Rebased branches will merge into your main branch without conflicts.

## Resolving Merge Conflicts

Scenario is pulling updates from a remote branch (__origin features/featureA__) to your local branch (__features/featureA__)

> Don't forget to build and run unit tests after merging to verify your conflict resolution.

## Resolve conflicts in Visual Studio

> Close the solution before merging

1. If there are conflicts you will get a notification, click the Conflicts link to resolve file conflicts. ![Prompt when there is a merge conflict when you pull a change](./_assets/vs-branches-conflicts.png)
1. This will bring up a list of files with conflicts. Selecting a file lets you accept the changes in the source branch you are merging from with the Take Source button or accept the changes in the branch you are merging into using Keep Target. You can manually merge changes by selecting Merge, then entering the changes directly into the Result editor.
1. Use the checkboxes next to the lines modified to select between remote and local changes entirely, or edit the results directly in the Result editor under the Source and Target editor in the diff view.
1. When done making changes, click Accept Merge . Repeat this for all conflicting files.
1. Open the Changes view in Team Explorer and commit the changes to create the merge commit and resolve the conflict. 

![Resolving Merge Conflicts in Visual Studio](./_assets/resolving-merge-conflicts-in-visual-studio.gif)

## Resolve conflicts from the Command Line

Before performing a pull, merge or rebase make sure your repo is clean by using `git status`. Perform a `pull` to update your local branch.  Use git status to see which files did not merge properly.

```git
git status
git pull --rebase
git status
```

Update the conflicted files listed in git status. Git adds markers to files that have conflicts. These markers look like:

```git
<<<<<<< HEAD
console.log("Writing changes to dev console");
=======
debug("Writing changes to debug module);
>>>>>>> dev-updates
```

The <<<<<<< section are the changes from one commit, the ======= separates the changes, and >>>>>>> for the other conflicting commit. Edit the files so they look how they should (i.e. resolve the conflicts).  Remove the markers and the code that version of the code you don't want.  Use git add to stage the resolved changes. Resolve file deleting conflicts with git add (keep the file) or git rm (remove the file).

If you are performing a merge/pull commit the changes.

If you are performing a rebase use `git rebase–continue` to proceed.

```git
git rebase --continue
```
