+++
authors = ["Harshal Rathore"]
title = "Git for Beginners by Me"
date = "2023-07-05"
description = "Learn git tips & tricks "
tags = [
    "git",
    "version-control",
    "github",
]
+++

# Git for beginners by me

Set git user info (assuming that you are the only user of this System)

```
git config --global user.name <name>
git config --global user.email <email>
```

User info for a certain Repository only

```
git congig user.name <name>
git config user.email <email>
```

Initialize git before using git commands

```
git init
```

Add files on staging area to be committed/Save

```bash
git add <file_name>
git add . (stages all the files all together)
```

See current git status

```bash
git status
```

Unstages file(s) from staging area

```
git restore --staged <file_name> OR .
```

Untrack a file/directory permanently from git

```
git rm --cached <file_name>
```

Untrack a file/directory temporarily from git

```
git update-index --assume-unchanged path/to/file
```

Track files which were set to Untrack temporarily in git

```
git update-index --no-assume-unchanged path/to/file
```

see the list of files set to Untrack temporarily in git

```
git ls-files -v | grep "^h "
```

`git ls-files -v |? {$_ -cmatch '^h '}`//Windows friendly

Restore deleted file(s) or reverse the Change in file to last commit.

`git restore <file_name> OR` . (Note that files to be restored should have been commited)

Create a Branch

```
git branch <name_of_branch>
```

Visit/Enter a Branch

```
git checkout <name_of_branch>
```

Visit a commit from logs

```
git checkout <SHA256_key_of_the_commit>
```

See logs of the branch

```
git log
```

To checkout the branch when creating it, use

```
git checkout -b branchname <sha1-of-commit or HEAD~3>
```

Note:- if you created a branch and committed some changes you can't directly push it to remote, first you have to publish it and also set git to auto track it so you can use `git push` `git pull` directly.

`git push -u origin <branch>` (-u is short for --set-upstream)

Note:- You can only create a single PR from a same branch. For how to create more PR for the same repository if your previous PRs are still not merged [click-here](https://community.atlassian.com/t5/Bitbucket-questions/If-a-pull-request-is-not-yet-closed-can-I-create-one-more-pull/qaq-p/1345302).

Merge branch

```
git merge <name_of_branch>
```

Delete a Branch

`git branch -d <name_of_branch>` (it'll only work if branch to be deleted is already merged with master branch)

Force delete a Branch

`git branch -D <name_of_branch>`  (It'll give error if you are in the branch while deleting it)

See all the files on staged area.

```bash
git diff --name-only --cached
```

See git index

```bash
git ls-files
```

see only modified files

```bash
git ls-files -m
```

Stage only modified files

```bash
git add -u
```

Commit only modified files

```bash
git commmit -a
```

See status of only tracking files in git

```bash
git status -uno
```

In case of multiple SSH Github account keys check which one is being used by default

```bash
ssh -T git@github.com
>>> Hi, HarshalRathore
ssh -T git@college.github.com
>>> Hi, HarshalRathore007
```

- For using multiple SSH keys associated with different github account

  Create a ~/.ssh/config file

  ```bash
  Host college.github.com
    HostName github.com
    PreferredAuthentications publickey
    IdentityFile ~/.ssh/id_ed25519_harshal24ai017
  
  Host github.com
    HostName github.com
    PreferredAuthentications publickey
    IdentityFile ~/.ssh/id_ed25519_harshalrathore2014
  
  Host ec2-13-234-110-107.ap-south-1.compute.amazonaws.com
    HostName ec2-13-234-110-107.ap-south-1.compute.amazonaws.com
    IdentityFile ~/harshal/newkeypair.pem
    User ec2-user
  ```

  So when you want to Clone college id repo replace [git@github.com](mailto:git@github.com).... to [git@college.github.com](mailto:git@college.github.com)... and everything will work like same. pushing will not give error

**Git Cheat Sheet**