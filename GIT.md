# GIT Management

This documentation is a guideline on how to do git management for this project. The process allows for the following:
* Create a uniform, reliable process for our team
* Allow for rapid feature developement and deployment
* Personal and group accountability
* Quick identification with branch names that allow rapid response

## Key branches
These branches share these things in common:
* No direct commits
* Locked against direct commits

### main
* This is production ready code. The `main` branch is what is deployed for production
* Only PRs from release are allowed to ensure that all branches remain synced
* All branches come from `main`

### testing
* This is QA code, ready to be tested.
* When a feature is ready for QA, PR into `testing` and ask for a review
* An additional PR to `main` is also done, but not merged
* A PR to `testing` must be reviewed by the main developer, unless given a "go ahead"

## Feature branches

### feature-[username]-[detail]
* New feature branches come from the `main` branch
* When ready for testing, PR to both `main` and `testing`
* PR to `main` is only merged after testing is done on QA and a go ahead is given

### devcon-feature-[username]-[detail]
If there is a merge conflict, these are the steps to follow:
* Make a copy of the feature branch.
```sh
git checkout feature-username-xyz
git checkout -b devcon-feature-username-xyz feature-username-xyz
git push origin devcon-feature-username-xyz
```

* PR the copy to `testing`, resolve the conflict and go through the review process
* The original feature branch is then PRed to `main`. Once ready, PR can be merged

If you are not comfortable resolving the conflict yourself (conflicts on work that is not yours or for any other reason), please reach out to someone who has either worked on it or can help resolve the conflict.

## Development process

To efficiently manage your development process, follow these guidelines in order to avoid conflicts and to maintain a structured workflow when working on an issue.
### Updating your local repository and creating a new branch

```sh
git checkout master
git pull
git checkout -b feature-name/username-xyz master
```

* Make sure to always update your local repository with master to keep updated with the latest changes.

### Adding, commiting, and pushing local changes

* Once you've made changes, you can add the files changed to the staging area. 
* When committing, include messages that accurately describes the changes and how it affects the main branch.

```sh
git add [file]
git commit -m [message]
git push origin [branch]
```

* To track all of the files changed, use

```sh
git add .
```

* Once pushing your changes locally, PR to both `testing` and `main`.

## Updating feature branches

In some cases, it may be necessary to update your feature branch if `main` has code/features you need since the branch was created. The branch can be updated by either `rebasing` or `merge`. The recommendation would be to use rebase, putting your features on top after merging.

```sh
git checkout master
git pull origin master
git checkout feature-username-xyz
git rebase master
```

## Deleting local branches

As part of maintaining a clean git repository, it may be necessary to delete local branches that are no longer needed. This helps to reduce clutter and avoid confusion with outdated branches. Periodically review and delete branches that are no longer needed.

* If a branch has already been approved and merged into `main` and `testing`, your branch is no longer required to be maintained in your local repository.

```sh
git branch -d feature-name/username-xyz
```

* It is also possible to delete multiple branches if needed.

```sh
git branch -d feature-name/username-xyz feature-name/username-abc
```

* If a branch has not been merged but you still want to delete it, you can force delete that branch.
* Please use with caution to avoid accidentally losing unmerged work.

```sh
git branch -D feature-name/username-xyz
```