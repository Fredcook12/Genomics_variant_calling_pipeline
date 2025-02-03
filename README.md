# Genomics_variant_calling_pipeline
This repository contains a bash script designed to automate the process of downloading sequencing reads, aligning them to a reference genome, processing the alignment files, and performing variant calling using GATK's HaplotypeCaller.

Pipeline Overview

The script performs the following steps:

Download SRA Reads using prefetch

Convert SRA to FASTQ using fastq-dump

Align Reads to a reference genome using BWA

Process BAM Files (sorting, indexing, and marking duplicates) using SAMtools and GATK

Base Quality Score Recalibration (BQSR) using GATK

Variant Calling using GATK HaplotypeCaller

Requirements

Ensure the following tools are installed and accessible in your system's PATH:

SRA Toolkit (prefetch, fastq-dump)

BWA

SAMtools

GATK

Files Needed

Reference Genome: GRCh38.genome.fa (indexed for BWA and GATK)

Known Sites VCF: known_sites.vcf (for BQSR, with index files)

SRA Accession: Accession number for the sequencing reads
