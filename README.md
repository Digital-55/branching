# branching
:warning: *Commit* your changes in your own branch *before* applying this :warning: (hint: _master_ is *not* your own branch) 

```sh
git checkout my-branch
git add .
git commit -m "<Commit message>"
git push origin my-branch # push changes to remote branch for safety
```

:wrench: Working with branches: merge to master :wrench:

```sh
git fetch # get upstream changes
git rebase -i origin/master # apply my-branch only commits on top of origin/master; this makes master changes fast-forward 

# If there are conflicts, git status shows (red colored) what files should be manually modified
# Once conflicts are resolved, run these commands
git add . # add files to stage
git rebase --continue # finish rebase

# If there are not conflicts, or are already resolved, continue with these commands  
git push origin my-branch --force # needs --force option because branch history has changed. Please, avoid force pushing if you've not set `git config push.default simple`
git checkout master && git pull origin master # change to master 
git merge my-branch # merge fast-forward changes from my-branch
git push origin master # push changes to upstream
