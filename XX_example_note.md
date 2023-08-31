From Severin Project managment 


* Title
* Date
* Computername and path of working directory
* Description of what you are trying to do and why
* Code block of the commands you used
* Description of the result


# Quality check on Unicorn RNASeq data             (What)

* Jan 19, 2021                                     (When)
* /work/GIF/severin/Unicorn_RNASeq/01_QC           (Where)
                                                   (Why)
I want to make sure that the quality of my reads obtained from the Illumina Novaseq look good before proceeding.   


## FASTQC                                          (How)

```
module load fastqc/0.11.7-d5mgqc7
module load parallel/20170322-36gxsog

mkdir fastqcOutput
  parallel "fastqc {} -o fastqcOutput" ::: ../00_rawdata/*.fastq.gz
```

## MultiQC                                         (How)

```
#load python 3.6
module load python/3.6.3-u4oaxsb
# multiqc wasn't working so I reinstalled it
pip uninstall multiqc
pip install multiqc
multiqc --version
multiqc, version 1.8
multiqc .
```
                                                    (Result)
The output from FASTQC and multiqc look good!  Proceeding to differential expression analysis of unicorn horn between activated and unactivated samples.
