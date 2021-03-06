---
title: 'make.file'
tags: 'commands'
redirect_from: '/wiki/Make.file.html'
---
Tired of creating the input files for make.contigs? Let mothur do that
for you! The **make.file** command takes a input directory and creates a
file containing the fastq or gz files in the directory.


## Default Settings

The make.fastq command parameters are inputdir and type. Inputdir is
required.

    mothur > make.file(inputdir=fastqTest)

The resulting fileList.paired.file looks like:

    /Users/sarahwestcott/Desktop/fastqTest/F8D0_S345_L001_R1_001.fastq /Users/sarahwestcott/Desktop/fastqTest/F8D0_S345_L001_R2_001.fastq  
    /Users/sarahwestcott/Desktop/fastqTest/F8D125_S358_L001_R1_001.fastq   /Users/sarahwestcott/Desktop/fastqTest/F8D125_S358_L001_R2_001.fastq    
    /Users/sarahwestcott/Desktop/fastqTest/F8D141_S359_L001_R1_001.fastq   /Users/sarahwestcott/Desktop/fastqTest/F8D141_S359_L001_R2_001.fastq    
    /Users/sarahwestcott/Desktop/fastqTest/F8D142_S360_L001_R1_001.fastq   /Users/sarahwestcott/Desktop/fastqTest/F8D142_S360_L001_R2_001.fastq    
    /Users/sarahwestcott/Desktop/fastqTest/F8D143_S361_L001_R1_001.fastq   /Users/sarahwestcott/Desktop/fastqTest/F8D143_S361_L001_R2_001.fastq    
    ...

You can use this file as a start and add your group names. If there were
unpaired fastq files in the directory as well mothur would create an
additional file called fileList.single.file.

## Options

### type

The type parameter is used to indicate what file type you would like
mothur to look for. Options are gz or fastq. Default=fastq.

     mothur > make.file(inputdir=gzTest, type=gz)

The resulting fileList.paired.file looks like:

    /Users/sarahwestcott/Desktop/gzTest/F8D0_S345_L001_R1_001.fastq.gz /Users/sarahwestcott/Desktop/gzTest/F8D0_S345_L001_R2_001.fastq.gz  
    /Users/sarahwestcott/Desktop/gzTest/F8D125_S358_L001_R1_001.fastq.gz   /Users/sarahwestcott/Desktop/gzTest/F8D125_S358_L001_R2_001.fastq.gz    
    /Users/sarahwestcott/Desktop/gzTest/F8D141_S359_L001_R1_001.fastq.gz   /Users/sarahwestcott/Desktop/gzTest/F8D141_S359_L001_R2_001.fastq.gz    
    /Users/sarahwestcott/Desktop/gzTest/F8D142_S360_L001_R1_001.fastq.gz   /Users/sarahwestcott/Desktop/gzTest/F8D142_S360_L001_R2_001.fastq.gz    
    /Users/sarahwestcott/Desktop/gzTest/F8D143_S361_L001_R1_001.fastq.gz   /Users/sarahwestcott/Desktop/gzTest/F8D143_S361_L001_R2_001.fastq.gz    
    ...

### numcols

The numcols parameter allows you to set number of columns you mothur to
make in the file. Options 2 or 3. Default=3, meaning groupName
forwardFastq reverseFastq. The groupName is made from the beginning part
of the forwardFastq file. Everything up to the first '' or if no ''
is found then the root of the forwardFastq filename.

### prefix

The prefix parameter allows you to enter your own prefix for the output
filename. Default=stability.

     mothur > make.file(inputdir=gzTest, type=gz, prefix=myReallyAwesomeData)

Would create a file containing the list of gz files in gzTest named
myReallyAwesomeData.files.

## Revisions

-   1.36.0 - First Introduced
-   1.37.0 Adds numcols parameter
    [\#162](https://github.com/mothur/mothur/issues/162)
-   1.38.1 Adds more flexibility to input file names.
    [\#243](https://github.com/mothur/mothur/issues/243)
-   1.38.1 Adds prefix parameter.
    [\#251](https://github.com/mothur/mothur/issues/251)
-   1.39.0 Fixes Windows bug - unable to find files
-   1.39.0 Creates unique group names for 3 column format
-   1.39.0 Fixes bug with "find" command for Linux user
-   1.40.0 Bug Fix: Fixes group names.


