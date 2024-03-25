# Conda
[Conda](https://docs.conda.io/en/latest/) is a package manager that allows installation of programs in a reproducible fashion.


### Via `miniconda`
Conda can be accessed via the `miniconda` module.

```bash
module load miniconda
eval "$(/appl/miniconda3-22.11/bin/conda shell.bash hook)"
```


#### `logsdon` environment
PMACS has created the global `logsdon` environment with most of the required software the lab needs.
* See the [Bash Aliases - Conda](bash_aliases#conda) section for a quick alias.
* **This environment cannot be updated by a non-root user.**

```bash
conda activate logsdon
conda list
```

To install/update software in this environment, open a ticket [here](https://helpdesk.pmacs.upenn.edu/userui/ticket_list.php).


### Via `mamba`
For a faster conda alternative, consider [`mamba`](https://mamba.readthedocs.io/en/latest/index.html).

To install locally to your user, follow [this](https://mamba.readthedocs.io/en/latest/installation/mamba-installation.html).
