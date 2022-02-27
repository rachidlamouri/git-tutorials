# Remotes

Git is a distributed version control system.
"distributed" here means that many developers can work on the same repository
by maintaining a local copy of it.

A remote is a reference to a git repository on an external system.

## Adding a Remote

Any local git repository can have a remote to any system.
First you need a remote repository.
Follow the [GitHub instructions](https://docs.github.com/en/get-started/quickstart/create-a-repo) to make a repository or you can use any other tool.

After making a remote repository you should see a git url like `https://example.com/example.git`

In the below example `name` can be whatever you want.
The conventional name for the primary remote is `origin`.

```bash
git remote add <name> <url>

# lists remotes
gt remote -v
```

## Downloading Remote Information

When working with remotes, you update your local `.git` folder to know about
information on the remote.

Your local repository cannot stay up to date with the remote repository in real time because it doesn't have a constant connection.
You will have to run this command any time the remote has changes that your local repository
does not.

```bash
git fetch
```

## Seeing Remote Branches

```bash
# shows all branches including remote ones
git branch --all
```

## Creating/Updating a Remote Branch

```bash
# create/update a remote branch with the same name as your current branch
git push <remote-name> HEAD

# create/update a remote branch with the same name as a branch
git push <remote-name> <current-branch-name>

# create/update any remote branch
git push <remote-name> <local-commit-reference>:<remote-branch-name>
```

## Deleting a Remote Branch

```bash
git push <remote-name> --delete <branch-name>
```
