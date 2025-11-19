---
title: "SillyMix pipeline"
project: "SillyMix"
github_project: "https://github.com/VIBTOBIlab/SillyMix"
description: "Sillymix is a bioinformatics analysis pipeline used to perform in-silico mixtures of tumoral and healthy fastq files at specified sequencing depth (in number of reads) and tumoral fractions."
layout: default
tags: project_home, SillyMix
permalink: /projects/SillyMix
---
[![Nextflow](https://img.shields.io/badge/nextflow%20DSL2-%E2%89%A523.10.1-23aa62.svg)](https://www.nextflow.io/)
[![run with docker](https://img.shields.io/badge/run%20with-docker-0db7ed?labelColor=000000&logo=docker)](https://www.docker.com/)
[![run with singularity](https://img.shields.io/badge/run%20with-singularity-1d355c.svg?labelColor=000000)](https://sylabs.io/docs/)

# Introduction

Sillymix is a bioinformatics analysis pipeline used to perform in-silico mixtures of tumoral and healthy fastq files at specified sequencing depth (in number of reads) and tumoral fractions.

The pipeline is built using [Nextflow](https://www.nextflow.io/) (>=23.10.1) a workflow tool to run tasks across multiple compute infrastructures in a very portable manner. It uses Docker / Singularity containers making installation trivial and results highly reproducible.

# Usage

> **NOTE**
> If you are new to Nextflow and nf-core, please refer to [this page](https://nf-co.re/docs/usage/getting_started/installation) on how to set-up Nextflow.

## Tumoral fractions

First, prepare a .txt file with your tumoral fractions:

`tum_fractions.txt`:

```plaintext:
0.1
0.2
0.5
```

## Sequencing depth (number of reads)

Prepare a .txt file with the sequencing depth values:

`num_reads.txt`

```plaintext:
100000
500000
555000
```

## Run the pipeline

Now you can run the NextFlow (>=23.10.1) pipeline. You need to allocate at least 12 CPUs and 72 GB of RAM to make the pipeline running.

You can run the pipeline using docker profile:

```plaintext:
nextflow run main.nf --healthy_dir data/healthy tumor_dir data/nbl --tumor_fractions data/tum_fractions.txt --seq_depths data/num_reads.txt --outdir results -profile docker
```

Or using singularity profile:

```plaintext:
nextflow run main.nf --healthy_dir data/healthy tumor_dir data/nbl --tumor_fractions data/tum_fractions.txt --seq_depths data/num_reads.txt --outdir results --fasta data/hg19.fa -profile singularity
```

The params.yaml file looks like the following:

`params.yaml`:

```plaintext:
tumor_fractions: data/tum_fractions.txt
seq_depths: data/num_reads.txt
healthy_dir: data/healthy
tumor_dir: data/nbl
nrepl: 3
outdir: results
```

The healthy and tumor directories must contain the .bam files that will be used to perform the mixtures.
All the parameters specified in the file can also be specified in the command line using the corresponding flags.

# Credits

The scripts and containers have been written and built by Edoardo Giuili ([@edogiuili](https://github.com/edogiuili)) who is also the maintainers.

# Citations

If you use this pipeline for your analysis, please cite it using the following doi: (...).
You can cite the nf-core publication as follows:

> The nf-core framework for community-curated bioinformatics pipelines.
>
> Philip Ewels, Alexander Peltzer, Sven Fillinger, Harshil Patel, Johannes Alneberg, Andreas Wilm, Maxime Ulysse Garcia, Paolo Di Tommaso & Sven Nahnsen.
>
> Nat Biotechnol. 2020 Feb 13. doi: [10.1038/s41587-020-0439-x](https://www.nature.com/articles/s41587-020-0439-x).
