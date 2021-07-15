# GitCheatSheet
A small summary of git important commands

## Commit  
`git commit -–amend` – for re-commit a commit, for example, fixing errors in the last commit. The new commit will be aside the last commit (instead of ahead of it).    

## Checkout  
`git checkout -b <brach name>` - create a new branch (named "brach name"), and checkout to it.  
`git checkout -f <branch name> <new position>` - -f stand for "force",  
`git checkout <branch>^<n>` - if the corrent branch on top of a merge (means it has more than one parent), the n will determine to which parent we will checkout.  

## Reset and Revert  
`git reset HEAD^` / `git reset HEAD~1` – reset the current branch to past commit locally.  
`git revert HEAD` – revert changes remotely.  

## Move and Rebase commits  
`git cherry-pick <c1> … <cn>` - take the commits c1 … cn and put them on top of the HEAD (the corrent place in the repository).  
`git rebase -i HEAD~<n>` – rebase the n last commit to a new branch and let user to edit the commits.  

## Other Useful Commands
`git tag <tag name> <commit name, default – HEAD>` - create a tag named "tag name".  
`git describe <ref>` - describe properties of a branch, the output is \<last tag\>_\<commits number from this tag\>_g\<current commit serial number\>.  
