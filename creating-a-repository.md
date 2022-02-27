# Creating a Repository

A git repository is a folder with a `.git` folder in it. The `.git` folder is managed by the `git` command.

```bash
# from anywhwere
mkdir myFolder

cd myFolder

# shows "not a git repository"
git status

git init

# lists a .git folder meaning that git can track your changes within this folder
ls -la

# shows "no commits yet"
git status
```
