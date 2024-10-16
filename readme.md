## Git Hidden Folder
The hidden folder ends in `.git` for example `project.git`. This mean that the project is an git repo.

Initialize an empty Git repository to a new project
* First, create a new folder
* Lasty, initalize the new repo

```
mkdri new-projects
cd new-projects
git init
touch readme.md
code readme.md
git status
git add readme.md
# Makes changes to readme.md
git commit -m "add readme.md file"
```

## Cloning
There are other ways to clone
* HTTPS
* SSH
* GitHub CLI

### HTTPS
```sh
git clone https://github.com/amprod2000/GitHub-Cert-Learning.git
cd GitHub-Cert-Learning
```

Generate a Personal Access Token (PAT)
https://github.com/settings/personal-access-tokens

Use the PAT as the password when you login
- Give access to contents for Commits

### SSH
Create the SSH Keys IF they do not exist, type enter three times.
```
cd ~/.ssh
ssh-keygen -b 4096 -t rsa
```

Save the public key to GitHub, login into GitHub and go to <b>settings</b> and open the tab <b>SSH and GFG Keys</b>. Paste the public key and give it a good name then click <b>New SSH Key</b>.
```
cat ~/.ssh/id_rsa.pub
```
Try this command now!!!
```ssh
git clone git@github.com:amprod2000/GitHub-Cert-Learning.git
cd GitHub-Cert-Learning
```

### GitHub CLI
The GitHub CLI is a command Line Interface to interact with your GitHub Account. You can quickly perform common GitHub actions without leaving your developer environment.

| Syntax | Description |
| ----------- | ----------- |
| `brew install gh` | The GitHub CLI can be installed on <b>Windows, Linux, and macOS</b>. |
| <div style="color:#990000; background:#D9D9D9; padding-left:5px; border:1px; border-radius: 5px; font-size: 15px; font-family: 'Noto Sans'"> "features": {<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"ghcr.io/devcontainers/features/github-cli:1": {}<br>} </div> | The GitHub CLI can be installed for GitHub Codespaces via Features. |
| `gh auth login` | Login |
| `gh repo clone amprod2000/GitHub-Cert-Learning` | Clone |
| `gh repo create github-examples --public` | Create a repo |
| `gh issue create --title "Issue title" --body "Issue body"` | Create an issue |
| `gh pr review --comment -b "Interesting"` | Reviewing a PR |

### Core Commands
| Commands | Description |
| ----------- | ----------- |
| `gh auth` | ... |
| `gh browse` | ... |
| `gh codespace` | ... |
| `gh gist` | ... |
| `gh issue` | ... |
| `gh org` | ... |
| `gh pr` | ... |
| `gh project` | ... |
| `gh release` | ... |
| `gh repo` | ... |

### Additional Commands
| Commands | Description |
| ----------- | ----------- |
| `gh alias` | ... |
| `gh api` | ... |
| `gh completion` | ... |
| `gh config` | ... |
| `gh extension` | ... |
| `gh gpg-key` | ... |
| `gh lable` | ... |
| `gh ruleset` | ... |
| `gh search` | ... |
| `gh secret` | ... |
| `gh ssh-key` | ... |
| `gh status` | ... |
| `gh variable` | ... |

GitHub Actions Commands
| Commands | Description |
| ----------- | ----------- |
| `gh cache` | ... |
| `gh run` | ... |
| `gh workflow` | ... |

## Commits
A Git commit represent incremental changes to a codebase represented with a git tree (graph) at a specific time.

A git commit contains
* Additions, <b>modifications</b>, and deletions of files.
* Additions and deletions of file contents.
* <b>Hash</b>: A unique SHA-1 hash identifier for each commit that acts as an ID, for example ```2840504c6e5315a2209797c55f6f042f5434d87f```.
* <b>Auther information</b>: The name and email of the person who made the commit.
* <b>Message</b>: A Description of what changes the commit contains. <b>Write good commit messages!</b>
* <b>Timestamp</b>: The date and time when the commit was made.
* <b>Parent Commit Hash(es)</b>: 
* <b>Snapshot of Content</b>: A snapshot of the project at the time of the commit not the files, but reference to them.

<div style="color:#000000; background:#FFD1B3; padding-left:5px; border:1px; border-style: solid; border-color: #FF6600; border-radius: 5px;">
Git does not store the whole files in each commit but stores the state of changes. This reduces the file size. To the developer the files will appear in full.
</div><br>

### Common Git Commands you should know!
| Syntax | Description |
| ----------- | ----------- |
| `git add FILE_NAME` | Files to be staged |
| `git add .` | Adds all files from current directory & subdirectory. |
| `git rm FILE_NAME` | Remove a specific file |
| `git commit` | To commit changes and opens the default editor to add a message. |
| `git commit -m "WRITE A GOOD COMMIT MESSAGE!!!"` | To commits staged changes with a message without opening an editor |
| `git commit -a -m "WRITE A GOOD COMMIT MESSAGE!!!"` | Automatically stages all tracked, modified files before the commit |
| `git commit --amend` | Modifies the most recent commit |
| `git commit -m "Initial commit" --allow-empty` | Creates an empty commit, useful as a placeholder |
| `git commit -m "WRITE A GOOD COMMIT MESSAGE!!!" --author="Author Name <email@example.com>"` | Commits with a specified author |
| `git checkout/switch 2840504c6e5315a2209797c55f6f042f5434d87f` | Checkout to a specific commit based on SHA hash |
| `git config --global core.editor EDITOR_NAME` | Set the global editor |

## Branches
Branches are copies of a point in time that have been modified to be different.

All repositories start with the <b>main branch</b>.

Create branches for
* <b>Specific environments</b>: Staging, Development, Production
* <b>Specific to developers</b>: andrew, bayko, cindy
* <b>Per feature</b>: payment-gateway-feature
* <b>Per bug</b>: hotfix-blank-homepage

| Syntax | Description |
| ----------- | ----------- |
| `git branch` | List all local branches |
| `git branch NAME` | Creates a new branch |
| `git checkout/switch BRANCH_NAME` | Checkout (Switch to) a branch |
| `git checkout/switch -b BRANCH_NAME` | Creates and checkout (Switch to ) a branch |
| `git branch -d BRANCH_NAME` | Delete a branch |
| `git branch -m OLD_BRANCH_NAME NEW_BRANCH_NAME` | Rename a branch |
| `git branch -a` | Lists both remote and local branches |

A <b>common workflow</b> for developers is to create a branch or a feature, and they need to push their branch upstream to the remote name origin.
```sh
# Creates and checkout (Switch to ) a branch.
git checkout -b BRANCH_NAME

# Developer makes changes to files.

# Adds all files from current directory & subdirectory.
git add .

# To commits staged changes with a message without opening an editor.
git commit -m "WRITE A GOOD COMMIT MESSAGE!!!"

# ...
git push -u origin BRANCH_NAME
```

## Remotes
* A git <b>remote</b> represents the reference to remote location where a copy of the repository is hosted.
* You can have multiple remote entries for your git repo.
* The most common is called `origin` as a remote name, it indicates the central or golden repo everyone is working from and represents the source of truth.

### The remote entries are stored in `.git/config`
```sh
[core] repositoryformatversion = 0
        filemode = true
        bare = false
        logallrefupdates = true
[remote "origin"]
        url = git@github.com:amprod2000/GitHub-Cert-Learning.git
        fetch = +refs/heads/*:refs/remotes/origin/*
[branch "main"]
        remote = origin
        merge = refs/heads/main
        vscode-merge-base = origin/main
[remote "upstream"]
        url = git@github.com:CODE33301/GitHub-Cert-Learning.git
        fetch = +refs/heads/*:refs/remotes/upstream/*
        gh-resolved = base
[branch "dev"]
        vscode-merge-base = origin/main
        remote = origin
        merge = refs/heads/dev
```

### Common Git Remote Commands you should know!
| Syntax | Description |
| ----------- | ----------- |
| `git remote -v` | Lists all remote repositories along with their URLs. |
| `git remote add NAME URL` | ... |
| `git remote remove NAME` | ... |
| `git remote rename OLD_NAME NEW_NAME` | ... |
| `git push REMOTE_NAME BRANCH_NAME` | Pushes a branch and it's commits to the specific remote |
| `git pull REMOTE_NAME BRANCH_NAME` | Pulls updates from a remote branch |
| `git fetch REMOTE_NAME` | Fetch updates without pulling |

### Upstream & Downstream
| Key Term | Description |
| ----------- | ----------- |
| Downstream | A repository that pulls or clones from another repository. <b>Pull</b>ing is downstream |
| Upstream | The repository to which we push changes. <b>Push</b> is upstream. |

## Stashing

```
git stash list
git stash
git stash save STASH_NAME
git stash apply
git stach pop
```

## Merging
If you want to merge the <b>dev branch</b> to the <b>main branch</b>, you need to be in dev first for example, ...
```
git switch/checkout dev
git merge main
```

## Add
To stage changes that will be included in the commit, the ```.``` adds all possible files.
```
git add readme.md
git add .
```

## Git Reset
Reset moves files from stage to unstage, preventing from files being commited.

```
git add .
git reset
```

## Status
Shows files that will not will not be commited
```
git status
```

## Gitconfig File
What stores the global configurtion for git.
```
git config --list --show-origin
```

Set 
```sh
git config --global user.name "First Last"
git config --global user.email email@example.com
```

## Log
Shows recent git commits to the tree
```
git log
```

## Push
To push a repo to our remote origin
```
git push
```

## Flow
Github Flow is a <b>light-weight workflow</b> for multiple developers working on a single repository.
* <b>Create a branch</b>: for each new task or feature. create a new branch off the main branch.
* <b>Add Commits</b>: Make changes and commit them to your branch.
* <b>Open a Pull Request</b>: Start a discussion about your commits, reviewing code in the pull request.
* <b>Discuss and Review</b>: Share your pull request with teammates for feedback.
* <b>Deploy</b>: Test your changes in a production environment.
* <b>Merge</b>: Once your changes are verified, merge them into the main branch.