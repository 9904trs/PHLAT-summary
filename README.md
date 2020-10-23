# PHLAT-summary

## PHLAT

**PHLAT** is a bioinformatics algorithm that offers HLA typing at four-digit resolution (or higher) using genome-wide transcriptome and exome sequencing data over a wide range of read lengths and sequencing depths. It has been benchmarked using multiple large scale public datasets and achieved ~93% and ~99% accuracies at four-digit and two-digit resolutions, respectively. PHLAT is also applicable to amplicon sequencing data targeting the HLA loci.


## Installation
### Dependencis
PHLAT requires the following utilities :

  * Linux (preferrably Ubuntu)
  * Python 2.7 & midules pysam(0.8.3), cPickle
  * Bowtie2 (version 2.0.0-beta7 is strongly recommended as this version was used when downstream algorithm was optimized)
    
### Downloads

1.Download and unpack **phlat-1.0.tar.gz** ([here](https://drive.google.com/drive/u/0/folders/0Bz-w5tutuZIYeHJTWjR5WW1pa1E))
2.Download and unpack index files (**index4phlat.tar.gz**) for Bowtie2 ([here](https://drive.google.com/drive/u/0/folders/0Bz-w5tutuZIYeHJTWjR5WW1pa1E))

This script converts the resulting files into a single csv file form.

A typical run looks like this :

    Rscript PHLAT_summary.R \
    --input_path $result_directory \
    --output_paht $summary_ouput_path \
    --name $file_name

Asumming ```sungmin``` is true

