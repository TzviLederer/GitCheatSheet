# GitCheatSheet
A small summary of git important commands

## Local Repository
### Commit  
`git commit -–amend` – for re-commit a commit, for example, fixing errors in the last commit. The new commit will be aside the last commit (instead of ahead of it).    

### Checkout  
`git checkout -b <brach name>` - create a new branch (named "brach name"), and checkout to it.  
`git checkout -f <branch name> <new position>` - -f stand for "force",  
`git checkout <branch>^<n>` - if the corrent branch on top of a merge (means it has more than one parent), the n will determine to which parent we will checkout.  

### Reset and Revert  
`git reset HEAD^` / `git reset HEAD~1` – reset the current branch to past commit locally.  
`git revert HEAD` – revert changes remotely.  

### Move and Rebase commits  
`git cherry-pick <c1> … <cn>` - take the commits c1 … cn and put them on top of the HEAD (the corrent place in the repository).  
`git rebase -i HEAD~<n>` – rebase the n last commit to a new branch and let user to edit the commits.  

### Other Useful Commands
`git tag <tag name> <commit name, default – HEAD>` - create a tag named "tag name".  
`git describe <ref>` - describe properties of a branch, the output is \<last tag\>_\<commits number from this tag\>_g\<current commit serial number\>.  

## Remote Repository
### fetch  
`git fetch` - copy the whole remote repository state to the local computer. However, the command does not change any local repository files.  
`git fetch origin <branch>` - will fetch only \<branch\> from the remote repository to the local one. Note that it will not overwrite the branch, but download it to the origin/\<branch\> branch, then you can merge it to the local \<brach\>.  
To copy the branch to a specific local brach (and overwrite it), one can use `git fetch origin <source>:<destination>`, when \<source\> is the remote branch and \<destination\> is the local one. 

### pull
`git pull` - combine the two commands `git fetch` and  `git merge`.  
`git pull --rebase` - will replace the default `merge` command with `rebase`, means that it combine `fetch` and `rebase`.  
`git pull \<remote\> \<source\>:\<destination\>` will run `git fetch \<remote\> \<source\>:\<destination\>` and then merge it to the local brach.    

### push
`git push <remote> <place>` - remote and place are optional, but if you specify them, git will push the brach \<place\> in the local repository to the branch \<place\> in the \<remote\> repository.  
If you want to push a specipic branch of the local repo to another branch on the remote, just use `git push origin <source>:<destination>` when \<source\> and \<destinations\> are the branches names (of the source and destination of course). Moreover, the source does not have to be a brach, it can be a locatio, HEAD~3 for example.  
Moreover, the destination can be a *new brach* that will be created automatically on the remote repo.  
If the source is empty, it will delete the remote brach.  

`git branch -u origin/main <branch name>` - connect the main branch in the remote repository to the corrent branch (even if is not the main branch locally), or to the branch specified on \<branch name\>.  
