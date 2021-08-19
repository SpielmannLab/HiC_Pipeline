# In-house pipeline for HiC analysis

We created snakemake workflows for separate steps of the HiC analysis. The snakemake version used here is 5.3.0 (the scripts will not work with versions >= 6 ). Please note that this is work in progress. 

## Mapping with HiCPro

The steps Preprocessing and Processing rely on [HiCPro](https://github.com/nservant/HiC-Pro). You'll need to supply a singularity container with a working HiCPro instance and have singularity installed.

### Preprocessing

Go to the Preprocessing directory and edit the config file. Run:

```
snakemake all --cores $(nproc)
```

### Processing

Go to the Processing directory and edit the config file. Input files of each sample must be in .fq.gz or fastq.gz format. You'll need give the path to a juicer tools .jar which you can download [here](https://github.com/aidenlab/juicer/wiki/Download). You'll also need a HiCPro configuration file. Get a local copy by running:

```
singularity exec <YOUR_HICPRO.img> cp /HiC-Pro-devel/config-hicpro.txt .
```

Don't forget to edit the HiCPro configuration. Then run:

```
snakemake all --cores $(nproc) 
```

### IntraChrAnalysis

This step uses [CHESS](https://github.com/vaquerizaslab/chess) for an automatic feature extraction. We compare a sample / patient and a control data set and look for intrachromosomal differences. Go to the IntraChrAnalysis directory, edit the configuration file and run:

```
snakemake all --use-conda --cores $(nproc) 
```

