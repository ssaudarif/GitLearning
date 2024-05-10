# Submodule learning.

## How to change the branch of a submodule ?

For this to happen you need to change the source of truth in .gitmodules.
For example, from
```
[submodule "api"]
    path = api
    url = https://github.com/<original_repo>/api.git
```
to
```
[submodule "api"]
    path = api
    url = https://github.com/<another_repo>/api.git
    branch = work-in-progress
```
To do this using command - `git submodule set-branch --branch Syed/new-branch api` 

`git submodule sync`: Updates the description of submodules cached by git in `.git/modules` from the just-edited source of truth specified in `.gitmodules`
Now we need to take update from this branch you need to do - `git submodule update --init --recursive --remote` adding the `--remote` option will take update from remote, i.e. the branch head commit.
But if you wanted to take only the update of the commited submodule sha and do not want the latest head of branch - `git submodule update --init --recursive`.



