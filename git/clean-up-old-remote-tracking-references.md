# Clean Up Old Remote Tracking References

After working on a project with git verisoning for a while you will find that each time you fetch the remote origin, there are a bunch of references to remote branches that don't exist: 

```zsh 
➜  aws-zero git:(master) gl
From https://git.sagacitysolutions.co.uk/git-ops/aws-zero
 * [new branch]      UnusedCredsCleanUp-Oct'24 -> origin/UnusedCredsCleanUp-Oct'24
Already up to date.
```
You can reconcile this discrepancy with one command:

```zsh
git fetch origin --prune
```
This will prune all those non-existent remote tracking references which is sure to clean up your git log (`git log --graph`).

[source](http://stackoverflow.com/a/3184742/535590)
