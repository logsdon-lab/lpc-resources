# LPC
To read general LPC docs, check out resources [here](https://wiki.pmacs.upenn.edu/public/LPC).

### Connecting to the LPC
```bash
ssh $USER@sarlacc.pmacs.upenn.edu
```

### Connecting to the LPC (Without Password)
This will require creating an SSH key and copying it to the cluster under `~/.ssh`.

```bash
# Add a comment (-C) to distinguish multiple. An email is common.
ssh-keygen -t rsa -C "$USER@pennmedicine.upenn.edu"

# Go through the prompt and keep the key as id_rsa
# Enter your passphrase or not.
```

Copy the key to the cluster. You will need to enter your password here.
```bash
ssh-copy-id -i ~/.ssh/id_rsa $USER@sarlacc.pmacs.upenn.edu
```

Then try again. You should not need to enter your password at this point.
```bash
ssh $USER@sarlacc.pmacs.upenn.edu
```

### Longer Jobs
Should be submitted to the `epistasis_long` queue as `epistasis_normal` only allows jobs to last one day.
* https://wiki.pmacs.upenn.edu/public/Epistasis_lab

This is particularly important when running any pipelines via `Snakemake`.
```bash
snakemake -j 4 --cluster 'bsub -q epistasis_long' ...
```

### `rambo`
`rambo` is a compute host within the epistasis queues used for jobs that require large amounts of compute.

To view its status.
```bash
bhosts | grep -P "HOST|rambo"
```

To view its specs.
```bash
lshosts | grep -P "HOST|rambo"
```

To run an interactive job on rambo.
* This allots 10 cores and 8GB for an interactive shell.

```bash
bsub -Is -q epistasis_interactive -n 10 -R "rusage[mem=8GB] -m rambo 'bash'
```

To submit a job.

```bash
bsub -q epistasis_long -n 10 -R "rusage[mem=4GB]” -m rambo <cmd_goes_here>
```

> [!NOTE]
> Rambo is also the name of Keith's tortoise.
