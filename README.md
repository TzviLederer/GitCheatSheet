# Git Cheat-Sheet
A small summary of git important commands

## Local Repository
### Commit  
`git commit -–amend` – for re-commit a commit, for example, fixing errors in the last commit. The new commit will be aside the last commit (instead of ahead of it).    

### Checkout  
`git checkout -b <brach name>` - create a new branch (named "branch name"), and checkout to it.  
`git checkout -f <branch name> <new position>` - the flag `-f` stand for "force". It could be dangerous because it will delete all uncommited files.  
`git checkout <branch>^<n>` - if the current branch is on top of a merge (means that it has more than one parent), the n will determine to which parent we will checkout.  
`git checkout filename` will remove all changes made in `filename`.  

### Reset and Revert  
`git reset HEAD^` / `git reset HEAD~1` – reset the current branch to past commit locally.  
`git revert HEAD` – revert changes remotely.  

### Move and Rebase commits  
`git cherry-pick <c1> … <cn>` - take the commits c1 … cn and put them on top of the HEAD (the current place in the repository).  
`git rebase -i HEAD~<n>` – rebase the n last commit to a new branch and let user to edit the commits (you can change the order of the commits or remove some of them).  

## Merge  
`git merge --abort` will abort the merge.  
`git merge --continue` will continue an aborted merge (after solving the conflicts).  


## Remote Repository
### fetch  
`git fetch` - copy the whole remote repository state to the local computer. However, **the command does not change any local repository files**.  
`git fetch origin <branch>` - will fetch only &lt;branch> from the remote repository to the local one. Note that it will not overwrite the branch, but download it to the origin &lt;branch> branch, then you can merge it to the local &lt;branch>.  
To copy the branch to a specific local branch (and overwrite it), one can use `git fetch origin <source>:<destination>`, when &lt;source> is the remote branch and &lt;destination> is the local one. 

### pull
`git pull` - combine the two commands `git fetch` and  `git merge`.  
`git pull --rebase` - will replace the default `merge` command with `rebase`, means that it combine `fetch` and `rebase`.  
`git pull <remote> <source>:<destination>` will run `git fetch <remote> <source>:<destination>` and then merge it to the local branch.    

### push
`git push <remote> <place>` - remote and place are optional, but if you specify them, git will push the branch &lt;place> in the local repository to the branch &lt;place> in the &lt;remote> repository.  
If you want to push a specific branch of the local repository to another branch on the remote, just use `git push origin <source>:<destination>` when &lt;source> and &lt;destinations> are the branches names (of the source and destination of course).  
Note that the source does not have to be a branch, it can be a location, HEAD~3 for example.  
Moreover, the destination can be a *new branch* that will be created automatically on the remote repository.  
If the source is empty, it will delete the remote branch.  

## Other Useful Commands
`git tag <tag name> <commit name, default – HEAD>` - create a tag named "tag name".  
`git describe <ref>` - describe properties of a branch, the output is &lt;last tag>_&lt;commits number from this tag>_g&lt;current commit serial number>.  
`git branch -u origin/main <branch name>` - connects the main branch in the remote repository to the current branch (even if is not the main branch locally), or to the branch specified on &lt;branch name>.  

`git init` - initiate a new git repository. it will create the `.git` dir where all git data will be stored.  
`git status` - print the current status.  
`git log` - visualize the git status.  One can add the "--all --graph --decorate" flags to visualize it differentely. The "--oneline" argument will present a more compact representation.  
`git diff filename` shows all changes in the file.  

