# Pull Request

Pull Request is when you are going to publish changes to a repo that you have fork.

## Create Pull Request

TODO

## Checking Pull Request Locally

If you're owner of the original repo, you can check any pull request from your contributor and approved/declined their changes

`git fetch origin pull/ID/head:BRANCHNAME`

eg:

`git fetch origin pull/1/head:dev`

`ID` is a pull request Id and `BRANCHNAME` is the local branch you want to checkout containing changes from pull request.

when you're done testing with pull request local branch, you can delete that branch

`git branch -D BRANCHNAME`

eg:

`git branch -D dev`

`BRANCHNAME` is the pull request local branch

## Accept and Merge Pull Request

TODO

## References

* [Modifying an inactive pull request locally](https://docs.github.com/en/free-pro-team@latest/github/collaborating-with-issues-and-pull-requests/checking-out-pull-requests-locally#modifying-an-inactive-pull-request-locally)