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

### Split multi-fasta
Split a multi-fasta file into single-fasta files.
```bash
# Split multifasta file by header.
fasta_split() {
    infile="${1}"
    outdir="${2:.}"
    awk -v OUTDIR="${outdir}" '{
        if (substr($0, 1, 1) == ">") {
            fname=OUTDIR "/" substr($0,2) ".fa"
        } print > fname
    }' "${infile}"
}
```

###  Download all files recursively from an FTP index page
Download all files from an index page (ex. `index.html`)
```bash
wget_index_recursive() {
    url="${1}"
    output_dir="${2:-.}"
    processes="${3:-4}"
    # Skip n rows. Defaults to 1 for header.
    skip_n="${4:-1}"
    # https:// <- 2 /'s
    npaths=$(echo "${url}" | grep -o "/" | wc -l | xargs -I {} echo "{}-2" | bc)

    # Output index html to stdout
    # Extract all href elements.
    # Strip first / if href is directory.
    # Filter to matches with alphanumeric, period, underscore, and hyphen characters.
    # Add url to string and skip n rows.
    # Download recursively to output directory.
    wget "${url}" -O - | \
    grep -Po '(?<=href=")(.*?)(?=\")' | \
    grep -P '^[A-Za-z0-9\.\/_-]*$' | \
    awk -v SKIP_N=$(echo "${skip_n}+1" | bc) -v URL="${url}" 'NR > SKIP_N { print URL"/"$1 }' | \
    xargs -P "${processes}" -I {} wget -nH --cut-dirs="${npaths}" --reject="index.html*" --no-parent -r {} -P "${output_dir}"
}
```
