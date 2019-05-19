# CLI Vademecum

My personal cheat sheet for when I work via CLI. Vademecum is a latin word that describes a handbook or guide that is kept constantly at hand for consultation.

## Cheat sheet

### Git

|  Command |       Explanation       |
|:--------:|:-----------------------:|
| `git init` | Initiate git in the current repository  |
| `git status` | Check the status  |
| `git branch [name]` | Create a new branch called [name] off current HEAD |
| `git branch -v` | List all available branches |
| `git checkout [name]` | Move to branch [name] |
| `git add [files]` | Add files to the staging areas |
| `git commit` | Create a commit |
| `git commit -m` | Create a commit with only a short message |
| `git push` | Push the commits to *origin* |
| `git fetch` | Fetch information from *origin* |
| `git merge [name]` | Merge branch [name] into current branch |
| `git merge origin/[name]` | Merge branch [name] on *origin* into current branch |
| `git pull` | Equivalent of `git fetch` + `git merge origin/master` |
| `git stash` |  Store the current changes into a new *stash*  |
| `git stash list` |  List all available stashes  |
| `git reset --hard HEAD` |  Remove all changes since last commit  |

List of Git best practices, most of which come from [Learn Version Control with Git](https://www.goodreads.com/book/show/22437589-learn-version-control-with-git) by Tobias Günther:

- Commit related changes.
- Commit often.
- Don't commit half-done work.
- Test before you commit.
- Write good commit messages.
- Version control is not a backup system.
- **Use branches**.
- Agree on a [workflow](https://guides.github.com/introduction/flow/) with your team.

List of Git terms:

|  Command |       Explanation       |
|:--------:|:-----------------------:|
| **Branch** | A "branch" is an active line of development. The most recent commit on a branch is referred to as the tip of that branch. The tip of the branch is referenced by a branch head, which moves forward as additional development is done on the branch. A single Git repository can track an arbitrary number of branches, but your working tree is associated with just one of them (the "current" or "checked out" branch), and HEAD points to that branch.  |
| **Commit** | As a noun: A single point in the Git history; the entire history of a project is represented as a set of interrelated commits. The word "commit" is often used by Git in the same places other revision control systems use the words "revision" or "version". Also used as a short hand for commit object. As a verb: The action of storing a new snapshot of the project’s state in the Git history, by creating a new commit representing the current state of the index and advancing HEAD to point at the new commit. |
| **HEAD** | See **Branch**. |
| **Master** | The default development branch. Whenever you create a Git repository, a branch named "master" is created, and becomes the active branch. In most cases, this contains the local development, though that is purely by convention and is not required. |
| **Merge** | To bring the contents of another branch (possibly from an external repository) into the current branch. In the case where the merged-in branch is from a different repository, this is done by first fetching the remote branch and then merging the result into the current branch. This combination of fetch and merge operations is called a pull. Merging is performed by an automatic process that identifies changes made since the branches diverged, and then applies all those changes together. In cases where changes conflict, manual intervention may be required to complete the merge. |
| **Origin** | The default upstream repository (i.e. a *remote*). Most projects have at least one upstream project which they track. By default origin is used for that purpose. New upstream updates will be fetched into remote-tracking branches named origin/name-of-upstream-branch, which you can see using `git branch -r`. |
| **Pull** | Pulling a branch means to fetch it and merge it. |
| **Push** | Pushing a branch means to get the branch’s head ref from a remote repository, find out if it is an ancestor to the branch’s local head ref, and in that case, putting all objects, which are reachable from the local head ref, and which are missing from the remote repository, into the remote object database, and updating the remote head ref. If the remote head is not an ancestor to the local head, the push fails. |
| **Stash** | Where changes are stored to be later retrieved (see `git stash`). Note that these changes are not attached to any branch in particular. |
| **Working Tree** | The tree of actual checked out files. The working tree normally contains the contents of the HEAD commit’s tree, plus any local changes that you have made but not yet committed. |



### TMUX

|  Command |       Explanation       |
|:--------:|:-----------------------:|
| `tmux` | Start a nameless TMUX session |
| `tmux new -s [name]` | Start a TMUX session with name [name] |
| `tmux a -t [name]` | Attach to the session with name [name] |
| `tmux ls` | List all TMUX active sessions |
| `CTRL+b "` | Split pane horizontally |
| `CRTL+b %` |  Split pane vertically  |
| `CRTL+b x` |  Kill the active pane  |
| `CRTL+b [` |  Activate scroll mode  |

## Set-up your CLI

1. Install `tree` (via `sudo apt-get install tree`).
1. Install `tmux` (via `sudo atp-get install tmux`).
1. Install `micro`.

## How Tos

### How to make sure TMUX uses 256 colors

First, check whether TMUX is not using colors at all or if the issue it's only with the prompt. In the latter case, simply add a new line at the beginning of `.bashrc` with `force_color_prompt=yes` ([source](https://unix.stackexchange.com/questions/360545/tmux-not-colorizing-ps1-prompt)).

In the former case instead start by checking whether you have a TMUX config file:

```bash
ls -l ~ | grep tmux
```

If not, just create one:

```bash
tmux show -g > ~/.tmux.conf
```
Open the config file and add `set -g default-terminal "screen-256color"` to the end of the file.

### How to reset bash

```bash
exec bash
```
