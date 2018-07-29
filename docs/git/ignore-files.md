# Ignore Files

Not every file created or updated in your code should be committed to Git. Temporary files from your development environment, test outputs and logs are all examples of files that you create but are not part of your codebase. Customize which files Git tracks through the gitignore feature.

## Customize your .gitignore

Modify your .gitignore to include files types, paths, and file patterns in your repo. Git starts ignoring these files as soon as the .gitignore is updated, but be sure to commit the changes if others on your team need the same set of ignored files.

## Ignore files only on your system

Your .gitignore is shared across team members as a file committed and pushed to the Git repo. To exclude files only on your system without pushing the changes to the rest of your team, edit the .git/info/exclude file in your local repo. Changes to this file will not be shared with others and only apply to the files in that repo. The syntax for this file is the same as the one used in .gitignore.
