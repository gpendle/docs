# Save Work with Commits

Git does not automatically snapshot your code as you make edits to files in your repo. You must tell Git exactly which changes you want to add to the next snapshot by staging those changes. After staging your changes, create a commit to save the snapshot to your repo.

Git tracks file changes in your repo as you work, and separates the files in your repo into three categories:

* Unmodified files – These files haven’t changed since your last commit.
* Modified files – These files have changes since your last commit, but you aren't yet staged for the next commit.
* Staged files – These files have changes that will be added to the next commit.

![Lifecyle of files in your repo between the three states](./_assets/git-file-life-cycle.png)

When you create a commit, only the staged changes and unchanged files are used for the snapshot. Changes to unstaged but modified files are kept, but the commit uses the unmodified version from the previous commit in its snapshot.

Commits are created in your local Git repository, so you don't have to worry about your changes being perfect. Continue to create commits as you work, pushing your changes to then team when they are ready to share.

## What's in a commit

Commits include the following information

* A snapshot of the files saved in the commit. Git snapshots the contents of all files in your repo at the time of the commit—this makes switching versions very fast and helps Git merge changes.
* A reference to the parent commit(s). Commits with multiple parents occur when branches are merged together.
* A short and to the point message describing the changes in the commit. You enter this message when you create the commit.

Git uses the references between commits along with the file snapshots to maintain a complete record of development in your repo.

Learn more about Git history and how to review history to investigate changes made to your code.

## Stage your changes

Git does not automatically add changed files to the snapshot when you create a commit. You must first stage your changes to let Git know which updates you want to add to the next commit. Staging lets you selectively add files to a commit while excluding changes made in other files.

Ignore temp files, logs, and other files that might change on your local machine but you don't want to add to version control

### Stage your changes using Visual Studio

> You can use the status bar at the bottom in Visual Studio to see what branch you are on and how may edits you have. Click the pencil (edits) to open the Changes window. If your branch says master, you will want to checkout a different branch before committing. ![Visual Studio Git Tray](./_assets/vs-git-tray.png)

Visual Studio keeps track of file changes to your project as you do your work. When you are ready to stage changes, open up the Changes view in Team Explorer.

Stage individual file changes by right-clicking a file in the Change view and selecting Stage.

![Team Explorer - Changes](./_assets/vs-team-explorer-git-changes.jpg)

Staging a change creates a Staged Changes section in Team Explorer. Only changes in the Staged Changes section are added to the next commit

![Team Exploer - Staged Changes](./_assets/vs-team-explorer-git-changes-staged.jpg)

> You do not need to link a work item to your commit at this point, that will happen during the pull request.

### Stage your changes using command line

To stage changes use:

```git
git add .
```

## Create a commit

Now that you have staged your changes you can commit them to your repo.  Commit regularly, this will give you roll back points in your local branch.  If you have done a logical piece of work commit it.

### Commit in Visual Studio

Open the __Changes__ tab in Team Explorer, enter a commit message describing your changes and select __Commit Staged__.

![Visual Studio Commit](./_assets/vs-team-explorer-git-commit.png)

You will get a commit hash.

![Visual Sudio Commit Hash](./_assets/vs-team-explorer-git-commit-hash.jpg)

And you have unpushed changes.cmd

![Visual studio Git Tray Unpushed](./_assets/vs-git-tray-unpushed.png)

### Commit from the command line

To commit staged changes to your repo use:

```git
git commit -m "Initial checkin"
```

To see unpushed changes you need to set the upstream branch for your local branch to track.

```git
git branch --set-upsteam-to origin {branch name}
```

Then you can see unpushed commits using `log` with `@{u}` as an alias for the upstream branch. 

```git
git log @{u}..
```