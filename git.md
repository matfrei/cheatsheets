# Useful git commands

## A nice introduction to git
[https://missing.csail.mit.edu/2020/version-control/](https://missing.csail.mit.edu/2020/version-control/)

## Create a new branch in a repository
git checkout -b branchname

## Set repo to a previous commit without changing head
git revert --no-commit <commitid>

## Update a forked repo with changes upstream

```
git remote add upstream https://github.com/ORIGINAL_OWNER/ORIGINAL_REPOSITORY.git
git fetch upstream

# then: (like "git pull" which is fetch + merge)
git merge upstream/master master

# or, replay your local work on top of the fetched branch
# like a "git pull --rebase"
git rebase upstream/master
```
[Best practices on when to use merge and when rebase](https://www.simplilearn.com/what-is-git-rebase-command-article)
