# PHLAT-summary

## PHLAT
==========

PHLAT is a bioinformatics algorithm that offers HLA typing at four-digit resolution (or higher) using genome-wide transcriptome and exome sequencing data over a wide range of read lengths and sequencing depths. It has been benchmarked using multiple large scale public datasets and achieved ~93% and ~99% accuracies at four-digit and two-digit resolutions, respectively. PHLAT is also applicable to amplicon sequencing data targeting the HLA loci.


This script converts the resulting files into a single csv file form.

A typical run looks like this :

    Rscript PHLAT_summary.R \
    --input_path $result_directory \
    --output_paht $summary_ouput_path \
    --name $file_name

Asumming ```sungmin``` is true

