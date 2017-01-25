# developer-guidelines
Developer guidelines for best results

## Git Practices

### Abstain from Back-Merges

If you want to do continuous integration, do that in a designated branch like `integration`. Do not use `git merge master` or an other higher order branch to update a WIP (work in progress) branch.

You can keep your work in sync with the master or other higher order branch like this:

#### Rebase

Repeat this as ofter as needed. It's usually signaled by someone on the team announcing they changed something significant that may affect others.
```
git checkout my-feature
git fetch
git rebase origin/master
# continue hacking
```
#### Make a New Personal Integration Branch

This is a safe way for someone to check that their work is going well with the rest of the code changes and not worry about affecting anyone else.
```
git fetch
git checkout -b bob-smith-integration bob-smith-feature
git merge origin/master
# run your tests, see if things are ok
git checkout -
# continue hacking
```

##### Update an Existing Shared Integration Branch

This is the preferred way and has a simple workflow.

```
git checkout intergration
git pull
git merge my-feature
# test if things are working together
# if they work, update it so others can test with your latest
git push
git checkout -
# continue hacking
```
### Where to Start Branches

If the infrastructure is stable, you can start all of your work for the next week or two from the same place. This will make it easy to mix and match features. This is an advantage as work can be cut if it's not going well. Without it, there is a tremendous rabbit hole of making everything work together or everyone is blocked.

```
git tag start master
git checkout -b feature1 start
# hack, continuously integrate, finish, or pause
git checkout -b feature2 start
# hack, etc
```
This will ensure that all branches can be maneuvered with the most ease. Move the start tag when enough features are finished. 
