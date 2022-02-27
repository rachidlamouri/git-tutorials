# Branches

As shown in [Creating a Tree of Commits](./creating-and-updating-commits.md#creating-a-tree-of-commits), a git history is a tree datastructure.
This tree structure has chains of commits that branch off of one another (like tree branches).

A branch is reference to a commit. There is a special branch called `HEAD` that is used to populate
your current working directory. `HEAD` is where you are in the tree.

Other branches can be used as bookmarks to quickly get to different parts of the tree.
Switching to a branch simply moves the `HEAD` reference to the same place as that branch.

## Seeing Your Current Branch

```bash
# shows "main" or "master" since that is typically the default branch
git branch
```

## Creating a New Branch and Viewing Branches

```bash
# create a new branch
git switch -c your-branch-name

# lists local branches and highlights the current branch
git branch

# lists the branch that HEAD is pointing to
git branch --show-current

# shows what commit each branch is on
git branch -v

touch a.txt
git commit -m "your commit message"

# shows your new branch and master are on different commits
git branch -v
```

## Switching Branches

```bash
# shows multiple branches (create a new branch if it doesn't)
git branch

git switch <branch-name>
```

## Deleting a Branch

```bash
# take not of your current branch name

git switch -c potato

git switch <previous-branch-name>

# deletes the potato branch
git branch -D potato
```

## Tracking a Branch

Tracking a branch is useful for viewing your current work in relation to a specific place on the tree.

```bash
git switch -c branch-a

echo potato > a.txt
git add .
git commit -m "my reference commit"

git switch -c branch-b

# -u is short for --set-upstream-to which sets a tracking branch
git branch -u branch-a

# shows that branch-b is up to date with branch-a
git status

echo soup >> a.txt
git add .
git commit -m "potato soup"

# Shows "Your branch is ahead of 'branch-a' by 1 commit"
git status
```

## Changing the Location of a Branch

This example uses the [`git reset]`](https://git-scm.com/docs/git-reset) command with the `--hard` flag. `--hard` will wipe any untracked changes.
Read the reference docs to understand how to use `git reset` with no flag, with the `--soft` flag and with the `--hard` flag.

```bash
git switch -c my-branch
echo sandwich > a.txt
git add .
git commit -m "first commit"

echo sandwich > a.txt
git add .
git commit -m "second commit"

# shows we are on "my-branch" at commit "second commit"
git branch -v

# note the commit ids of commit 1 and commit 2. Let's call them ID_1 and ID_2
git log -2

git reset --hard <ID_1>

# shows we are on "my-branch" at commit "first commit"
# we have effectively orphaned the "second commit" commit
git branch -v

git reset --hard <ID_2>

# shows we are on "my-branch" at commit "second commit"
git branch -v
```
