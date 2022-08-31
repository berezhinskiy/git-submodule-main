## Git Submodules - Main

Example of a product repository which uses git submodule

- `module` folder pointed to a specific git hash of another git repo
- `module-dev` folder pointed to `dev` branch of another git repo

### Init and update module

#### Specific git commit
```bash
git submodule add git@github.com:berezhinskiy/git-submodule-module.git module
cd module
git checkout <commitid>
git commit -m 'Update module to <commitid>' module
```

#### Specific git branch
```bash
git submodule add -b dev git@github.com:berezhinskiy/git-submodule-module.git module-dev
```

### ⚠️ Potential problem with pointing to the branch name
After cloning the repo, submodules will be switched into a detached HEAD state. If you make changes in the submodule branch and commit, Git will create the commit and leave submodules with a detached HEAD.

```
> git status
HEAD detached at f74a7bb
nothing to commit, working tree clean
```

`submodule.<name>.update` and `submodule.<name>.branch` parameters in `.gitmodules` config can solve this potential problem. 

More info is [here](https://git-scm.com/docs/git-submodule#Documentation/git-submodule.txt-update--init--remote-N--no-fetch--no-recommend-shallow-f--force--checkout--rebase--merge--referenceltrepositorygt--depthltdepthgt--recursive--jobsltngt--ltpathgt82308203)
