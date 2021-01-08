# gitops-poc

## Basically
This project uses an action that allows a user to perform a simple commit and push. Any changes to the codebase prior this action can be included in the commit, e.g lint fix a file, copy a file around, etc. After the push, any github event hooks on the branch will run just like github works and the branch checks are verfied success, and then the branch is deleted.

## Support Multiple CircleCI Workflows
The GitHub workflow included in this project will copy the CircleCI config file that matches the name of the event and event type to replace the default config.yml and push a branch with that name. It watches the checks, which include the CircleCI workflow run and ensure they pass, and then deletes the branch from github as if nothing happened.

### Caveats? 
It will only work if the user that triggers the event has write permissions to the repo since you need to be able to push a branch directly to the repository. This would definitely work for enterprise users or people on private repos, however, this could be problematic or insecure for public repos.
