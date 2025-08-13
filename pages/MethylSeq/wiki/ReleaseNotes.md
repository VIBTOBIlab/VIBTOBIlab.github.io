---
title: "ReleaseNotes"
layout: default
permalink: "/projects/MethylSeq/wiki/ReleaseNotes"
tags: wiki, MethylSeq
project: "MethylSeq"
github_project: "https://github.com/VIBTOBIlab/MethylSeq"
---

# ReleaseNotes

## [v2.6.2](https://github.com/VIBTOBIlab/MethylSeq/releases/tag/2.6.2) - 2025-07-15
### In-house modifications applied to nf-core/methylseq pipeline version [v2.6.0](https://github.com/nf-core/methylseq/releases/tag/2.6.0)
- Added parameter to deactivate PicardMarkduplicates module
- Added parameter to specify which sequencer has been used for PicardMarkduplicates module.
- Reordered the main Bismark Workflow.
- Added the optional Sequencing Saturation plots.
- Picard Markduplicates module has been added to Bismark subworflow(look at the module for more information).
- Bismark `filter_non_conversion` function has been added to the Bismark subworkflow. It can be activated specifing the flga `--filter_non_conversion` together with the `minimum_count` and `percentage_cutoff` parameters (see nextflow.conf and filter_non_conversion module for more information). When activated, it creates an output folder where it saves 3 files. The fitlered bam file is then used for the subsequent modules. 
It needs to be updated with a new version of Bismark (and the corresponding biocontainer) when it is released (there is a bug in the current version, see the issue [#688](https://github.com/FelixKrueger/Bismark/issues/688)) since now it's not using an official Bismark biocontainer.

## [v2.6.0](https://github.com/nf-core/methylseq/releases/tag/2.6.0) - 2024-01-05

### Bug fixes & refactoring

- 🛠 Copy methylKit-compatible files to publishDir [#357](https://github.com/nf-core/methylseq/pull/357)
- 🐛 fix `ignore_r1` and `ignore_3prime_r1` variable expansion [#359](https://github.com/nf-core/methylseq/pull/359)

## [v2.5.0](https://github.com/nf-core/methylseq/releases/tag/2.5.0) - 2023-10-18

### Pipeline Updates

- 🔄 Updated template to nf-core/tools v2.9
- 🔄 Updated template to nf-core/tools v2.10
- 🔧 Updated nf-core modules for FastQC, samtools sort, samtools flagstat
  - ❌ Removes problematic `-m` memory assignment for samtools sort [#81](https://github.com/nf-core/methylseq/issues/81)
- 🧾 Use `fromSamplesheet` from nf-validation [#341](https://github.com/nf-core/methylseq/pull/341)
- 🚀 Update Maintainers and add CODEOWNERS [#345](https://github.com/nf-core/methylseq/pull/345)
- ⚙️ Update schema to utilize exists and add more patterns [#342](https://github.com/nf-core/methylseq/pull/342)
- 📁 Support pipeline-specific configs [#343](https://github.com/nf-core/methylseq/pull/343)

### Bug fixes & refactoring

- 🛠️ Added publishing of coverage (`*cov.gz`) files for NOMe-seq filtered reads for `coverage2cytosine`
- 🛠️ Wrong display values for "zymo" and "em_seq" presets on help page [#335](https://github.com/nf-core/methylseq/pull/335)
- 📚 Use new Citation tools functions [#336](https://github.com/nf-core/methylseq/issues/336)

## [v2.4.0](https://github.com/nf-core/methylseq/releases/tag/2.4.0) - 2023-06-02

### Pipeline Updates

- Updated template to nf-core/tools v2.8
- Add `--bamqc_regions_file` parameter for targeted methylation sequencing data #302
- ✨ Add NF-TEST tests and snapshots for the pipeline test profile #310

### Bug fixes & refactoring

- 🛠️ update index file channels to explicit value channels #310
- 🐛 fix `params.test_data_base` in test and test_full configs #310
- 🤖 GitHub Actions CI - pull_request to `dev` tests with NXF_VER `latest-everything` #310
- 🤖 GitHub Actions CI - pull_request to `master` tests with NXF_VER `22.10.1` & `latest-everything` #310
- 🤖 GitHub Actions CI - `fail-fast` set to false #310
- 🐛 get to the bottom of index tests #278
- ✨ Support for Bismark methylation extraction `ignore` and `ignore_3prime` parameters when `ignore_r1` or `ignore_3prime_r1` are greater than 0. #322
- 🛠️ rename `ignore` -> `ignore_r1` and `ignore_3prime` -> `ignore_3prime_r1` params #322
- 🐛 fix `ignore_3prime_r2` param #299
- 🐛 removed unused directory #297

## [v2.3.0](https://github.com/nf-core/methylseq/releases/tag/2.3.0) - 2022-12-16

### Pipeline Updates

- ⚙️ Dramatically increase the default process time config requests for Bismark and bwa meth alignment
- ✨ Add a `tower.yml` file to enable Reports in Nextflow Tower
- 🤖 GitHub Actions CI - download the test data prior to running tests

### Bug fixes & refactoring

- 🧹 Refactor genome indices preparation into a separate workflow
- 🧹 Refactor subworkflow logic out of alignment subworkflows, for later sharing
- 🐛 Fix a bug with using a local genome reference FASTA file
- 🐛 Fix a bunch of problems in the CI tests using nf-test ([#279](https://github.com/nf-core/methylseq/pull/279))

## [v1.0](https://github.com/nf-core/methylseq/releases/tag/1.0) - 2018-04-17

Version 1.0 marks the first release of this pipeline under the nf-core flag. It also marks a significant step up in the maturity of the workflow, with everything now in a single script and both aligner workflows fully supported.

- Renamed and moved [SciLifeLab/NGI-MethylSeq](https://github.com/SciLifeLab/NGI-MethylSeq/) to [nf-core/methylseq](https://github.com/nf-core/methylseq/)
- Merged bwa-meth and bismark pipeline scripts, now chosen with `--aligner` flag
- Refactored multi-core parameters for Bismark alignment and methylation extraction
- Rewrote most of the documentation
- Changed the Docker container to use Bioconda installations

---

Previous to these releases, this pipeline was called [SciLifeLab/NGI-MethylSeq](https://github.com/SciLifeLab/NGI-MethylSeq):
