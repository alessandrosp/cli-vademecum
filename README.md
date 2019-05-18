# CLI Vademecum

My personal cheat sheet for when I work via CLI. Vademecum is a latin word that describes a handbook or guide that is kept constantly at hand for consultation.

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
