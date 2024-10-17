# Bash Aliases
These are a few useful bash aliases to make long commands easier to run.

### Globus Connect Personal
This command starts Globus Connect Personal as a background process.
```bash
alias gcp='nohup globusconnect -start > globuspersonalconnect.log 2>&1 &'
```

> **Be sure to kill this process at some point.**

### Conda
This command activates the `miniconda` module, attaches conda to the existing shell, and activates the `logsdon` conda environment.
* https://askubuntu.com/a/1254409

```bash
alias condalab='module load miniconda >/dev/null 2>&1 && eval "$(/appl/miniconda3-22.11/bin/conda shell.bash hook)" && conda activate logsdon'
```

### Interactive Job
This function spawns an interactive job with given memory and threads.
```bash
ibash2() {
    threads="${1:-32}"
    mem="${2:-50}"
    bsub -Is -q epistasis_interactive -n "${threads}" -R "rusage[mem=${mem}GB]" -M "${mem}GB" "bash"
}
```
To use the function.
```bash
# With defaults
ibash2

# With 12 threads and 30GB of memory.
ibash2 12 30
```
