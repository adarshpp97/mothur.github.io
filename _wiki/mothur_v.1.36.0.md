---
title: 'mothur v.1.36.0'
redirect_from: '/wiki/Mothur_v.1.36.0.html'
---
We're excited to announce the release of
[mothur\_v.1.36.0](/wiki/mothur_v.1.36.0)! This release has a
number of exciting new commands and features. The new commands include
[set.seed](/wiki/set.seed), which allows you to peg the seed for
the random number generator that is used by a number of other commands
(e.g. cluster) to improve reproducibility. We've also added
[make.file](/wiki/make.file), which will generate the files file
that you use in [make.contigs](/wiki/make.contigs) based on the
sequence files in your directory. On the new features, there are a
number of things we've done to tidy up the overall package. More
meaningful, however, is that in the mac and linux versions of mothur you
can now give [make.contigs](/wiki/make.contigs) your uncompressed
fastq.gz files as input. We are working on this feature for windows, but
\... windows. This should save you a bunch of hard drive space :).
We've also added a feature to [pre.cluster](/wiki/pre.cluster) so
that you do not need to provide a full multiple sequence alignment.
Instead, you can provide it unaligned sequences and it will carry out
the typical algorithm but will also do a pairwise alignment. I \*think\*
this will be useful for people doing ITS sequencing.

We have a number of other features on our docket for the next release.
As always, don't hesitate to email us or use the forum to propose new
features and commands. As I mentioned in an earlier email, I will be
hosting a mothur [workshop](/wiki/workshop) in the Detroit area in
early September, holler if you are interested or have questions.

Pat

## New commands

-   [set.seed](/wiki/set.seed) - allows you to seed random.
-   [make.file](/wiki/make.file) - creates a file containing list
    of fastq or gz files for input to make.contigs.

## Feature updates

-   [pre.cluster](/wiki/pre.cluster) - added cluster method for
    unaligned sequences. Added align, mismatch, match, gapopen,
    gapextend parameters.
-   [set.dir](/wiki/set.dir) - if output directory does not exist
    mothur will create it for you.
-   [chimera.uchime](/wiki/chimera.uchime) - adds method tag to
    output files. -
    [https://forum.mothur.org/viewtopic.php?f=5&t=3636&p=10748#p10748](https://forum.mothur.org/viewtopic.php?f=5&t=3636&p=10748#p10748)
-   [chop.seqs](/wiki/chop.seqs) - adds qfile option to allows for
    chopping quality files.
-   [classify.otu](/wiki/classify.otu) - adds threshold parameter.
    The threshold parameter allows you to specify a cutoff for the
    taxonomy file that is being inputted.
-   [rename.seqs](/wiki/rename.seqs) - adds count, delim, and
    placement parameters.
-   seed parameter added to all commands to allow you to easily seed
    random while running commands.
-   [make.shared](/wiki/make.shared) - mothur no longer checks for
    biom matrix type to allow for more flexibility.
-   [make.shared](/wiki/make.shared) - rabund files are no longer
    outputted. mothur will create a rabund file with the
    [get.rabund](/wiki/get.rabund) command.
-   [set.dir](/wiki/set.dir) - if output directory does not exist
    it will be created.
-   no longer create a log file simple command line option runs of
    mothur
-   [make.sra](/wiki/make.sra) - allow for assigning multiple sets
    of files to the same group in 3 column format.
-   [make.contigs](/wiki/make.contigs) - allow for missing reads in
    files.
-   [metastats](/wiki/metastats) - remove qvalues. Also removes
    fortran source from mothur.
-   automatically adjust number of processors when fork() fails
-   Removes extra white spaces from mothur's print to make output files
    more compatible with other software packages. -
    [https://forum.mothur.org/viewtopic.php?f=4&t=3703](https://forum.mothur.org/viewtopic.php?f=4&t=3703)
-   [degap.seqs](/wiki/degap.seqs) - adds the processors option.
-   Adds column headers to [design\_file](/wiki/Design_File)
-   [phylo.diversity](/wiki/phylo.diversity) - adds sampledepth
    parameter. - [https://forum.mothur.org/viewtopic.php?f=3&t=3320](https://forum.mothur.org/viewtopic.php?f=3&t=3320)
-   [set.dir](/wiki/set.dir) - Sets tempdefault location to
    mothur's executable location to help reduce "unable to find file"
    errors.
-   [make.contigs](/wiki/make.contigs) - allow for gzipped version
    for fastq files as inputs.
-   Added file parameter to saved files by mothur. file=current can now
    be used.

## Bug fixes

-   [metastats](/wiki/metastats) - infinite loop with certain
    datasets - [https://forum.mothur.org/viewtopic.php?f=3&t=3701](https://forum.mothur.org/viewtopic.php?f=3&t=3701)
-   [cluster.split](/wiki/cluster.split) - did not allow you to use
    the classic option with the file option.
-   [make.biom](/wiki/make.biom) - repeat labels when combining
    mothur OTU labels with non mothur OTU labels, this can results in a
    duplicate "simple" label. This causes an incorrect taxonomy to be
    assigned to the OTU.
-   [remove.groups](/wiki/remove.groups) - not creating a list file
    for each label.
-   [make.biom](/wiki/make.biom) - remove paths from filenames to
    make compliant with qiime parser. -
    [https://forum.mothur.org/viewtopic.php?f=3&t=3781&p=11241#p11241](https://forum.mothur.org/viewtopic.php?f=3&t=3781&p=11241#p11241)
-   [sffinfo](/wiki/sffinfo) - off by one in right side trimming.
    [https://forum.mothur.org/viewtopic.php?f=4&t=3764](https://forum.mothur.org/viewtopic.php?f=4&t=3764)
-   [make.contigs](/wiki/make.contigs) - Bug Fix - when using index
    files in version 1.35 quality data was over trimmed by the length of
    the barcode.

## Download

[https://github.com/mothur/mothur/releases/tag/v1.36.0](https://github.com/mothur/mothur/releases/tag/v1.36.0)

## Registered users

3306
