# LPC
To read general LPC docs, check out resources [here](https://wiki.pmacs.upenn.edu/public/LPC).

### Connecting to the LPC
```bash
ssh $USER@rambo.pmacs.upenn.edu
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
ssh-copy-id -i ~/.ssh/id_rsa $USER@rambo.pmacs.upenn.edu
```

Then try again. You should not need to enter your password at this point.
```bash
ssh $USER@rambo.pmacs.upenn.edu
```


### Transferring Data
Use [`sftp`](https://www.digitalocean.com/community/tutorials/how-to-use-sftp-to-securely-transfer-files-with-a-remote-server) or [`scp`](https://linuxize.com/post/how-to-use-scp-command-to-securely-transfer-files/).

Consider [FileZilla](https://filezilla-project.org/) or similar for an easier user experience.


### Longer Jobs
Should be submitted to the `epistasis_long` queue as `epistasis_normal` only allows jobs to last one day.
* https://wiki.pmacs.upenn.edu/public/Epistasis_lab

This is particularly important when running any pipelines via `Snakemake`.
```bash
snakemake -j 4 --cluster 'bsub -q epistasis_long' ...
```

### Checking specific hosts
To view its status.
```bash
bhosts | grep -P "HOST|$HOSTNAME"
```

To view its specs.
```bash
lshosts | grep -P "HOST|$HOSTNAME"
```

To run an interactive job on `$HOSTNAME`.
* This allots 10 cores and 8GB for an interactive shell.

```bash
bsub -Is -q epistasis_interactive -n 10 -R "rusage[mem=8GB]" -m $HOSTNAME 'bash'
```

To submit a job.

```bash
bsub -q epistasis_long -n 10 -R "rusage[mem=4GB]” -m $HOSTNAME <cmd_goes_here>
```
