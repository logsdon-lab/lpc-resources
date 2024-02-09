# Bash Aliases
These are a few useful bash aliases to make long commands easier to run.

### Globus Connect Personal
This command starts Globus Connect Personal as a background process.
```bash
alias gcp='nohup globusconnect -start > globuspersonalconnect.log 2>&1 &'
```

> **Be sure to kill this process at some point.**

### Conda
This command activates the `miniconda` module, attach conda to the existing shell, and activate the `logsdon` conda environment.
* https://askubuntu.com/a/1254409

```bash
alias condalab='module load miniconda >/dev/null 2>&1 && eval "$(/appl/miniconda3-22.11/bin/conda shell.bash hook)" && conda activate logsdon'
```