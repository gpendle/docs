# Review code wtih Pull Requests

Git's workflow uses branches to isolate work until you're ready to merge the changes into your default branch, such as master. The pull request is the collaborative process that lets the rest of the team discuss changes in a branch and agree to merge them once everyone approves. Use pull requests to get early feedback from others on work in progress, even if you're not ready to merge the changes into another branch.

![Merging a Git branch into its parent via a pull request](./_assets/branch-pull-request.png)

In this image, the purple branch is merged into the blue branch through a pull request. The changes are discussed by reviewers in the pull request before the code is merged. When you complete the pull request, there is a merge commit (seen here as the filled blue commit) where the changes in the purple branch are now merged in the blue branch.

## Creating Pull Requests

After you have pushed your local branch and you are ready to have your work merged you can create a pull request.

From Visual Studio navigate to the __Pull Requests__ tab and choose __New Pull Request__.

![Visual Studio Team Explorer Pull Requests](./_assets/vs-pull-requests.png)

From VSTS navigate to the __Pull Requests__ page in the __Code__ hub and choose __Create a Pull Request__.

![VSTS New Pull Request](./_assets/vsts-new-pull-request.jpg)

Confirm the source and target branch

![Pull request source and targt branch](./_assets/pull-request-topic-to-master.jpg)

Give your request a __title__ and __description__.

![Pull Request title and description](./_assets/pull-request-title.jpg)

Add any additional reviewers.  If the branch poilcy has reviewers configured they will be added.  If not the team for the current context will be added.

![Pull request add reviewers](./_assets/pull-request-add-reviewers.jpg)

Associae a __work item__ and click __Create__.

![Pull request work item linkage](./_assets/pull-request-work-items.jpg)

## Who reviews the pull request?

When you create the pull request, you can add others who need to review your changes. You can add users and groups to the pull request after it is created if the scope of the review needs to expand. You can also associate the pull request with a task in Team Services to let others working with the task know changes are ready for review.

## How does the code review work

Pull request reviewers will see the proposed updates to the branch in the form of file differences between the two branches. Reviewers can add comments on any of the changes and include notifications for other team members to answer a question or give other feedback. You can make changes and push commits to resolve issues brought up in the feedback and these changes are immediately reflected in the pull request.

![Pull request add comment](./_assets/pull-request-add-comment.jpg)

The reviewers will approve or reject the pull request.

![Pull request vote](./_assets/pull-request-vote.png)

If the changes need much more development to complete, you can abandon the pull request. You can later open up a new pull request to revisit the changes and link to the conversations that took place in the abandoned pull request.

You can also open up a pull request on a very early version of your code to ask for feedback from others, even if the code isn't ready to merge yet. Once you get the team's feedback, you can keep the pull request open to continue the conversation or abandon the pull request until your code is ready to be shared again.

## Completing a Pull Request

Once all polices are resolved

![Pull request policies](./_assets/pull-request-policies.jpg)

you can now complete the pull request.  

![Complete pull request](./_assets/pull-request-complete.jpg)

> You can __set auto-complete__ before the votes are done so you dont have to return to the pull request when it meets the policy requirements.

You'll be prompted for a descriptive message about the changes proposed by the pull request. You can choose to delete the pull request branch when the pull request is complete. Git retains the commit history in the master branch after the pull request is complete, so unless you plan on doing more work in the branch, it is safe to remove.

![complete merge pull request](./_assets/pull-request-complete-merge.jpg)

## What happens when a pull request is merged

You must resolve any merge conflicts between the pull request branch the target branch. Git adds a new commit (the merge commit) to the end of the master branch. This merge commit links the earlier history of both the master branch and the commits for the branch that was merged as part of the pull request.
