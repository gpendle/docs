# Create a CI Build Definition

Create a new build definition for the Master branch to enforce a level of code quality.  At a minimum your CI build is responsible for checking that code compiles and it passes all unit tests.  Your CI build should also be fast and robust as it is required to run before people can share code.

Steps to include:

1. Checking that the code compiles
1. Running unit tests and publishing results

Optional steps:

1. artefact publishing
1. test deployment
1. automated integration (code) testing

If you have long running steps or steps that may fail due to external dependencies consider running these steps in a release definition and have this release automatically queued when a build is successful. This allows you to rerun a failed deployment without having to rerun the build process.

## Create a new build definition

Navigate to the Build & Release hub and choose Builds to view the list of build definitions.

1. Create a New build definition choose from a template or start with an Empty process. ![Select Build Process](./_assets/build-template-select.png)
1. __Name_ the definition
1. Choose a __default agent queue__ e.g. Hosted VS2017
1. Configure __Get Sources__ (see below)
1. Add the __GitVersion Task__ to your process. This task will modify the $(Build.BuildNumber) and uses [semantic versioning](http://semver.org/).  You can use the varables it creates to version your assemblies. ![Build Git Version Task](./_assets/build-git-version.jpg)
1. Set the Triggers to be CI (batched) for the master branch. ![Build Triggers](./_assets/build-triggers.jpg)
1. Configure __Options__ to __automatically link new work in this build__. ![biuild link work items](./_assets/build-options-workitems.jpg)
1. Define your process (see below)

### Define Your Process

The process is up to you, extend the pipeline as required.

### Get Sources

Modify the advanced options to Tag sources on success.  If you are using submodules or LFS then turn those options on.

![Build Sources advanced settings](./_assets/build-advanced-settings.png)

### Git Version

GitVersion looks at your Git history and works out the [semantic version](http://semver.org/) of the commit being built.  

For more information see [GitVersion in the marketplace](https://marketplace.visualstudio.com/items?itemName=gittools.gitversion).

### Triggers

Triggers control when a new build is queued.  We want to build whenever we merge into master, so enable CI for the master branch.  For more information see [build dfinition triggers](https://www.visualstudio.com/en-us/docs/build/define/triggers)

### Debugging Builds

To get verbose logging set the __system.debug__ variable to true.  You can also add this variable to relese definitions.

![Debugging Builds](./_assets/builds-system-debug.jpg)

### Multiple Definitions

You are not restricted to a single build definition, but unlike TFVC you can use filters with wildcards and apply a single build definition to multiple branches.

You might want to have a cutdown CI build that is used for pull requests.
