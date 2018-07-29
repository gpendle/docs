# Clone Repo

Create a complete local copy of an existing Git repo using by cloning it. Cloning a repo downloads all commits and branches in the repo and sets up a named relationship  (`origin`) with the existing repo you cloned. Use this relationship to interact with the existing repo, fetching and pushing changes to share code with your team. To `clone` a repo you needs its URL.

## Clone from VSTS

Navigate to the __Code__ hub and look for the __Clone__ action in the top right.

![VSTS Clone Repo](./_assets/vsts-clone-repo.png)

Click __Clone in Visual Studio__ or copy the URL to clone using the command line.

## Command Line

Open a command prompt at the directory where you want to store your local repo and run git clone.

```
git clone {url to repo}
```

> If `git` is not on you PATH update your environment  e.g.:  `set PATH=%PATH%;c:\Program Files\Git\cmd\` and restart the command prompt.

## Visual Studio

Using __Team Explorer__ pick __Manage Connections__ and select the account you want to see the hosted repositories for.  Locate the Team Project that contains the repo you want and select the repo. The Connect button will change to __Clone__.  You can change the path for the local repo before cloning.

![Visual Studio Clone Repo](./_assets/vs-clone-repo.jpg)

If you don't see the VSTS Account, use the account drop down to add the account that you use to sign into the missing VSTS Account with.

## Default Repo Location

In Visual Studio use __Team Explorer__, __Settings__ and Git __Global Settings__ to set the __Default Repository Location__.

![Visual Studio Git Repo Location Setting](./_assets/vs-git-settings.jpg)
