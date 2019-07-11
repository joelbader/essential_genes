# Snakemake workflow: Tn-seq

[![Snakemake](https://img.shields.io/badge/snakemake-≥3.12.0-brightgreen.svg)](https://snakemake.bitbucket.io)

This workflow, using Snakemake, seeks to reproduce our results presented in our upcoming paper: "Identifying the essential genes of Mycobacterium avium subsp. hominissuis with Tn-Seq using a rank-based, frequentist approach." Following the steps below should allow you to get identical results to what we reported in our paper.

## Authors

* William Matern (@wmatern)

## Dependencies

You will need to install the following packages (and their dependencies) in order to run this workflow:
* snakemake (tested with version: 5.5.1)
* conda (tested with version: 4.6.14)

For simplicity I have also provided a singularity container (https://sylabs.io/singularity/) build script that can be used to run these workflows in any environment where singularity is installed (e.g. your local cluster). Note that you will need root access to build the singularity container from the provided recipe (see: https://sylabs.io/guides/3.0/user-guide/build_a_container.html).

## Usage

### Step 1: Download workflow

If you simply want to use this workflow, download and extract the [latest release](https://github.com/snakemake-workflows/tn-seq/releases).

### Step 2: Build Singularity container

If using singularity you will need to run the following commands in order to build the necessary image file:

    cd singularity_container
    sudo singularity build conda_smake.simg conda_smake_recipe.txt

### Step 3: Execute workflow
Change directory to essential\_genes\_mav or essential\_genes\_mtb.

If not using singularity:
Test your configuration by performing a dry-run via:

    snakemake --use-conda -n

Execute the workflow via

    snakemake --use-conda -j

See the [Snakemake documentation](https://snakemake.readthedocs.io/en/stable/executable.html) for further details.

If using singularity:
    singularity exec ../singularity\_container/conda\_smake.simg snakemake -j --use-conda

## Report Issue
If you have any questions or issues reproducing our results please send me an email at maternwill@gmail.com.
