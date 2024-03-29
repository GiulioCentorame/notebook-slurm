# Run RStudio or Jupyter notebooks on Bunya (BETA)
Small wrapper to launch an interactive job for notebooks within the Slurm scheduler on UQ HPC's Bunya

## Development status

- JupyterLab support is in **BETA**
- ~~RStudio support is in **ALPHA**~~ Currently not supported. If you got it working on Bunya, please do [get in touch](mailto:g.centorame@uq.edu.au)!
## Requirements

- `git`
- A default installation of `conda` or `mamba`, with an environment containing [JupyterLab](https://jupyter.org/install). You can create one with e.g.
  ```shell
  conda create -n jupyter-notebook -c conda-forge jupyterlab
  ```

If your environment is called anything but `jupyter-notebook`

## Setup

Clone this repository:

``` shell
git clone git@github.com:GiulioCentorame/notebook-slurm.git
```

Set up your options using `config.yaml`. Specifically, you will need to add your account string on `account` (e.g., `a_groupname`):

``` shell
nano notebook-slurm/nb-slurm/config.yaml
```

Then, copy the files in this directory somewhere in your `$PATH`. E.g.,

``` shell
cd notebook-slurm
cp * -r ~/bin/
```

From there, you should be able to run Jupyter with `launch_jupyter`, or RStudio with `launch_rstudio`. The `-h` option provides some (hopefully useful) information on how to use the wrapper

```
$ launch_jupyter -h
Usage: launch_jupyter [OPTION]

  -m [memory]   request memory (default: 10G)
  -c [cores]    request number of cores (default: 8)
  -t [time]     request time (default: 08:00:00)
  -d            run in debug mode (1GB memory, 1 core, 1h)
  -h            display this message

NOTE: long-form options (e.g., --memory 10G) are not supported
```


## Acknowledgements

This wrapper uses various snippets from:
- Xiao Tan for the basic Jupyter script
- Stefan Farestam's [YAML parser for Bash](https://stackoverflow.com/a/21189044/10798015)
- The Rocker project for their [container and running instructions](https://rocker-project.org/use/singularity.html#running-a-rocker-singularity-container-localhost-no-password)
