# `tmux`
Is a terminal multiplexer that allows the user to open multiple terminals within a single session. Sessions persist even after exiting a terminal making it useful for long-running jobs.

Read the docs here:
* https://github.com/tmux/tmux/wiki/Getting-Started

### Configuration.
Some useful configuration I use.
```
# https://hamvocke.com/blog/a-guide-to-customizing-your-tmux-conf/

# remap prefix from 'C-b' to 'C-a'
unbind C-b
set -g prefix C-a
bind-key C-a send-prefix

# split panes using | and -
bind | split-window -h
bind - split-window -v
unbind '"'
unbind %

# switch panes using Alt-arrow without prefix
bind -n M-Left select-pane -L
bind -n M-Right select-pane -R
bind -n M-Up select-pane -U
bind -n M-Down select-pane -D
```