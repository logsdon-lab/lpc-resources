# Bash Config and Profile 
## [Differences](https://linuxize.com/post/bashrc-vs-bash-profile/#difference-between-bashrc-and-bash_profile)
* A `~/.bashrc` lets you define configuration for each non-login shell created.
* A `~/.bash_profile` is loaded once on login

## `~/.bashrc`
Should not be modifed according to PMACS as regularly overwritten.

## `~/.bash_profile`

### Better Tab Completion
Autocompletes and cycles through the menu of possible commands.
```bash
bind TAB:menu-complete
```

### Load Modules on Login
PMACS docs make it pretty clear.
```bash
# User specific environment and startup programs

## Load user specified modules on login.
# SAMPLE: Modules are space seperated.
#export USER_MODULES="R/3.2.2 perl/5.20.2"

export USER_MODULES="tmux/3.1b"
module load ${USER_MODULES}
```
