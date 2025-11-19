---
title: "ReleaseNotes"
layout: default
permalink: "/projects/SillyMix/wiki/ReleaseNotes"
tags: wiki, SillyMix
project: "SillyMix"
github_project: "https://github.com/VIBTOBIlab/SillyMix"
---

# ReleaseNotes

# Sillymix v1.1.0

Added the label process_double to seqtk_downsample module to give more memory to the process.

# Sillymix v1.0.0

Sillymix is a bioinformatics analysis pipeline used to perform in-silico mixtures of tumoral and healthy fastq files at specified sequencing depth (in number of reads) and tumoral fractions.

The pipeline is built using [Nextflow](https://www.nextflow.io/) (>=23.10.1) a workflow tool to run tasks across multiple compute infrastructures in a very portable manner. It uses Docker / Singularity containers making installation trivial and results highly reproducible.