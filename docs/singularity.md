# Singularity
[Singularity](https://docs.sylabs.io/guides/3.5/user-guide/introduction.html) enables portable and reproducible programs via containerization.

It is the standard for LPC/HPCs over Docker as it runs programs as your user rather than root.
* https://docs.sylabs.io/guides/3.5/user-guide/introduction.html#why-use-singularity


### Getting Started
Load the `singularity` module.
```bash
module load singularity
```

### Dockerfiles
`Dockerfile`s are generally preferred in industry over `.sif` files. Fortunately, `Docker` is supported by `singularity`.
* https://docs.sylabs.io/guides/2.6/user-guide/singularity_and_docker.html


#### Development
Generally, projects and their images should be coupled.
* WIP - Example

CI workflows are a WIP.


### Images
All of our images will be stored on Dockerhub under the [`logsdonlab` organization](https://hub.docker.com/u/logsdonlab).

Any pulled images will be located in `/project/logsdon_shared/tools`.


#### RepeatMasker70
This is a [fork](https://github.com/logsdon-lab/RepeatMasker/tree/fix/v4.1.0-id-length-fix) of [`RepeatMasker`](https://github.com/rmhubley/RepeatMasker) that allows [sequence IDs larger than the default, hard-coded 50 characters](https://github.com/rmhubley/RepeatMasker/issues/12).

**The default is now 70 characters.**

##### Run
```bash
singularity run /project/logsdon_shared/tools/RepeatMasker70 RepeatMasker --help
```

##### Pull
```bash
singularity pull docker://logsdonlab/repeatmasker70:latest
singularity run repeatmasker70_latest.sif RepeatMasker --help
```
