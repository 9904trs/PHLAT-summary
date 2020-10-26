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

1. Download and unpack **phlat-1.0.tar.gz** ([here](https://drive.google.com/drive/u/0/folders/0Bz-w5tutuZIYeHJTWjR5WW1pa1E))
2. Download and unpack index files (**index4phlat.tar.gz**) for Bowtie2 ([here](https://drive.google.com/drive/u/0/folders/0Bz-w5tutuZIYeHJTWjR5WW1pa1E))

### Setting option

1. Modify url parameters (see example.sh as template) to reflect your system configuration
    
    -phlatdir: the home directory of phlat-1.0
    
    -fastq1: fastq file of the first reads 
    
    -fastq2: fastq file of the second reads
    
    -indexdir: the index4phlat subfolder in phlat-1.0 package
    
    -b2url: url to bowtie2 executable
    
* Additional options :
    * -tag: name label for the sample associated with the fastq files
    * -p: number of threads for running Bowtie2 [default 8]
    * -o: url to a directory where results shall be stored
    * -pe: flag indicating whether the data shall be treated as paired-end(1) or single-end(0) [default 1]

 
### RUN PHLAT

**Run_PHALT.sh** :  
This script specifies the location of the result file to facilitate summary processing after analysis.  
To proceed with a large amount of analysis at a time, you can use a combination of script and repetitive statements.

## Result summary

This script converts multiple result files into a single csv file format. 

A typical run looks like this :

    Rscript PHLAT_summary.R \
    --input_path $result_directory \
    --output_path $summary_output_path \
    --name $output_name

* ```--input_path``` : Directory in which PHLAT_run.sh execution result files are saved.  
* ```--output_path``` : The directory to save the Summary results.  
* ```--name``` : Summary file label 


## Performance Accuaracy Calculation

Our project analyzed only the Caucasian population dataset of E-MATB-197.  
And we were only given the correct answer for HLA-A,B and C.  
To calculate the performance accuracy using this script, input_file must follow format below.

**Input file format**  
 `1st column` : dataset label  
 `2nd column` : HLA-A-Allele1  
 `3rd column` : HLA-A-Allele2  
 `4th column` : HLA-B-Allele1  
 `5th column` : HLA-B-Allele2  
 `6th column` : HLA-C-Allele1  
 `7th column` : HLA-C-Allele2  
 

A typical run looks like this :

    Rscript Performance.R \
        --standatd_file $gold_standard_file_path \
        --summary_file $PHLAT_summary_file_path \
        --output_path $output_file_path \
        --name $label_name

The output file is provided in .csv form.Last column is the number of 4 digit matches/ 6.  

**!** This script will only run if the input file is a file formatted by the PHLAT summary.R script or our corrected answer.



