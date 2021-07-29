### In-house pipeline for HiC analysis

We created snakemake workflows for separate steps of the HiC analysis. The snakemake version used here is 5.3.0 (the scripts will not work with versions >= 6 ). Please note that this is work in progress. 

## Mapping with HiCPro

The steps Preprocessing and Processing rely on [HiCPro](https://github.com/nservant/HiC-Pro). You'll need to supply a singularity container with a working HiCPro instance and have singularity installed.

# Preprocessing

Go to the Preprocessing directory and edit the config file. Run:

```
snakemake all --cores $(nproc)
```