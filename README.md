# Genomics Variant Calling Pipeline

This repository contains a bash script designed to automate the process of downloading sequencing reads, aligning them to a reference genome, processing the alignment files, and performing variant calling using GATK's HaplotypeCaller. Variant statistics such as the number of SNPs and indels will be printed to the terminal.

## Pipeline Overview

The script performs the following steps:
1. **Download SRA Reads** using `prefetch`
2. **Convert SRA to FASTQ** using `fastq-dump`
3. **Align Reads** to a reference genome using `BWA`
4. **Process BAM Files** (sorting, indexing, and marking duplicates) using `SAMtools` and `GATK`
5. **Base Quality Score Recalibration (BQSR)** using `GATK`
6. **Variant Calling** using `GATK HaplotypeCaller`
7. **Print Variant Statistics**

## Requirements

Ensure the following tools are installed and accessible in your system's PATH:
- [SRA Toolkit](https://github.com/ncbi/sra-tools) (`prefetch`, `fastq-dump`)
- [BWA](http://bio-bwa.sourceforge.net/)
- [SAMtools](http://www.htslib.org/)
- [GATK](https://gatk.broadinstitute.org/)

## Files Needed

- **Reference Genome**: `GRCh38.genome.fa` (indexed for BWA and GATK)
- **Known Sites VCF**: `known_sites.vcf` (for BQSR, with index files)
- **SRA Accession**: Accession number for the sequencing reads


## Usage

Run the script with the SRA accession as an argument:
```bash
./gatk_pipeline SRR019438
```

Replace `SRR019438` with your SRA accession. The script will handle downloading, processing, and variant calling.

## Output

- Aligned BAM files (`aligned_reads.bam`, `marked_duplicates.bam`, `final_recalibrated.bam`)
- Index files for BAMs (`.bai`)
- Recalibration data table (`recal_data.table`)
- Variant call file (`SRR019438_output.g.vcf.gz`)
- Generate variant statistics (`variant_stats.txt`)

## Notes

- Make sure the `GATK` executable path is correctly set in the script if it's not globally accessible.
- Modify the `PROJECT_DIR` in the script if using a different directory structure.

