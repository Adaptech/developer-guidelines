# developer-guidelines
Developer guidelines for best results

## Git Practices

### Abstain from Back-Merges

If you want to do continuous integration, do that in a designated branch like `integration`. Do not use `git merge master` or an other higher order branch to update a WIP (work in progress) branch.
