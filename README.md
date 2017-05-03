## How can I remove a commit on GitHub?
Source: http://stackoverflow.com/questions/448919/how-can-i-remove-a-commit-on-github
```
git reset HEAD^ --hard
git push origin -f
```

## Changing git commit message after push <br/>(given that no one pulled from remote)
Source: http://stackoverflow.com/questions/8981194/changing-git-commit-message-after-push-given-that-no-one-pulled-from-remote
```
git commit --amend -m "New commit message"
git push --force-with-lease <repository> <branch>
```

## Push a new local branch to a remote Git repository and track it
```
git push --set-upstream <repository> <branch>
```
example:
```
git push --set-upstream origin patch-1
```

## How do I update a GitHub forked repository?
Source: http://stackoverflow.com/questions/7244321/how-do-i-update-a-github-forked-repository

Add the remote, call it "upstream":
```
git remote add upstream <repository>
```
Fetch all the branches of that remote into remote-tracking branches, such as upstream/master:
```
git fetch upstream
```
Make sure that you're on your master branch:
```
git checkout master
```
Rewrite your master branch so that any commits of yours that
aren't already in upstream/master are replayed on top of that
other branch:
```
git rebase upstream/master
```
If you don't want to rewrite the history of your master branch,
(for example because other people may have cloned it)
then you should replace the last command with git merge upstream/master.
However, for making further pull requests that are as clean as possible, it's probably better to rebase.

If you've rebased your branch onto upstream/master you may need to force the push 
in order to push it to your own forked repository on GitHub. You'd do that with:
```
git push -f origin master
```
