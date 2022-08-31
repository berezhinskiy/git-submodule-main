## Git Submodules - Main

Example of a product repository which uses git submodule

- `module` folder pointed to a specific git hash of another git repo
- `module-dev` folder pointed to `dev` branch of another git repo

### Init module

```bash
git submodule add git@github.com:berezhinskiy/git-submodule-module.git module
```

### Update module

```bash
cd module
git checkout <commitid>
git commit -m 'Updated submodule' module
```

### ⚠️ Potential problem with pointing to the branch name
After cloning the repo, submodules will be switched into a detached HEAD state. If you make changes in the submodule branch and commit, Git will create the commit and leave submodules with a detached HEAD.
