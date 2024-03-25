# LPC
To read general LPC docs, check out resources [here](https://wiki.pmacs.upenn.edu/public/LPC).

### Connecting to the LPC
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
