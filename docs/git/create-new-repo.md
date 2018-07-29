# Create a new Repository in the Team Project

> You can create a local repo and push to VSTS but this guide shows how to create a new Repo in VSTS.

New repos should be created using VSTS.  If you are working on a codebase that is not intended to be shared with anyone, e.g a private piece of code, or following some tutorials, then you can create a local git repo and get the benefits of a version control system without the server component. Using VSTS to create the project allows you to choose a .gitignore template as part of the repo creation which doesnt happen when creating a local repo.

> Do not use spaces in the repo name.

## Visual Studio Team Services
Go to your Team Project and navigate to the Version Control admin page. (/_admin/_versioncontrol)

![VSTS new repo](./_assets/vsts-new-repo.png)

Select __New Repository__ and choose __Git__ as the type.  Provide a name, __include the README option__ and select an appropriate __.gitignore template__ e.g. VisualStudio.

![VSTS new Git Repo properties](./_assets/vsts-new-git-repo.png)

This will create the repo with a __master__ branch.

Next protecte the master branch using a branch policy.

## Local Git Repo

From the Command line use git init.  

```git
git init {repoName}
```

Or you can use Visual Studio to create a new repo using the __Team Explorer__ window.

> A Git repo is a folder with a valid .git subfolder.  The name of the folder is the name of the repo.