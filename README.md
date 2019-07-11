# Snakemake workflow: Tn-seq

[![Snakemake](https://img.shields.io/badge/snakemake-≥3.12.0-brightgreen.svg)](https://snakemake.bitbucket.io)

This workflow, using Snakemake, seeks to reproduce our results presented in our upcoming paper: "Identifying the essential genes of Mycobacterium avium subsp. hominissuis with Tn-Seq using a rank-based filter procedure." Following the steps below should allow you to get identical results to what we reported in our paper.

## Authors

* William Matern (@wmatern)

## Dependencies

You will need to install the following packages (and their dependencies) in order to run this workflow:
* snakemake (tested with version: 5.5.1)
* conda (tested with version: 4.6.14)

For simplicity I have also provided a singularity container (https://sylabs.io/singularity/) build script that can be used to run these workflows in any environment where singularity is installed (e.g. your local cluster). The container automatically provides snakemake and conda. Note that you will need root access to build the singularity container from the provided recipe (see: https://sylabs.io/guides/3.0/user-guide/build_a_container.html).

## Raw Data

You will need to download a number of data files and place them into the corresponding input folders. A list of commands using the SRA Toolkit is provided in each input folder as a guide for how to download .fastq files from SRA. Genbank files (.gb, .gbff) along with corresponding FASTA files (.fa, .fna) can be downloaded [here](ftp://ftp.ncbi.nlm.nih.gov/genomes/all/GCA/003/408/535/GCA_003408535.1_ASM340853v1) and [here](ftp://ftp.ncbi.nlm.nih.gov/genomes/all/GCA/000/195/955/GCA_000195955.2_ASM19595v2). You will need to rename the files to use the prefix MAC109 and H37Rv. The expected file names are:

    essential_genes_mav/input/MAC109.fa
    essential_genes_mav/input/MAC109.gb
    essential_genes_mav/input/SRX5532235_1.fastq
    essential_genes_mav/input/SRX5532235_2.fastq
    essential_genes_mav/input/SRX5532236_1.fastq
    essential_genes_mav/input/SRX5532236_2.fastq
    essential_genes_mav/input/SRX5532237_1.fastq
    essential_genes_mav/input/SRX5532237_2.fastq
    essential_genes_mav/input/SRX5532238_1.fastq
    essential_genes_mav/input/SRX5532238_2.fastq
    essential_genes_mav/input/SRX5532239_1.fastq
    essential_genes_mav/input/SRX5532239_2.fastq

    essential_genes_mtb/input/H37Rv.fa
    essential_genes_mtb/input/H37Rv.gb
    essential_genes_mtb/input/SRR4113427_1.fastq
    essential_genes_mtb/input/SRR4113427_2.fastq
    essential_genes_mtb/input/SRR4113428_1.fastq
    essential_genes_mtb/input/SRR4113428_2.fastq
    essential_genes_mtb/input/SRR4113429_1.fastq
    essential_genes_mtb/input/SRR4113429_2.fastq
    essential_genes_mtb/input/SRR4113430_1.fastq
    essential_genes_mtb/input/SRR4113430_2.fastq
    essential_genes_mtb/input/SRR4113431_1.fastq
    essential_genes_mtb/input/SRR4113431_2.fastq
    essential_genes_mtb/input/SRR4113432_1.fastq
    essential_genes_mtb/input/SRR4113432_2.fastq
    essential_genes_mtb/input/SRR4113433_1.fastq
    essential_genes_mtb/input/SRR4113433_2.fastq
    essential_genes_mtb/input/SRR4113434_1.fastq
    essential_genes_mtb/input/SRR4113434_2.fastq
    essential_genes_mtb/input/SRR4113435_1.fastq
    essential_genes_mtb/input/SRR4113435_2.fastq
    essential_genes_mtb/input/SRR4113436_1.fastq
    essential_genes_mtb/input/SRR4113436_2.fastq
    essential_genes_mtb/input/SRR4113437_1.fastq
    essential_genes_mtb/input/SRR4113437_2.fastq
    essential_genes_mtb/input/SRR4113438_1.fastq
    essential_genes_mtb/input/SRR4113438_2.fastq
    essential_genes_mtb/input/SRR4113439_1.fastq
    essential_genes_mtb/input/SRR4113439_2.fastq
    essential_genes_mtb/input/SRR4113440_1.fastq
    essential_genes_mtb/input/SRR4113440_2.fastq

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

    singularity exec ../singularity_container/conda_smake.simg snakemake -j --use-conda

## Report Issue

If you have any questions or issues reproducing our results please send me an email at maternwill@gmail.com.
