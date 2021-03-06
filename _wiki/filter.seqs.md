---
title: 'filter.seqs'
tags: 'commands'
redirect_from: '/wiki/Filter.seqs.html'
---
**filter.seqs** removes columns from alignments
based on a criteria defined by the user. For example, alignments
generated against reference alignments (e.g. from RDP, SILVA, or
greengenes) often have columns where every character is either a '.'
or a '-'. These columns are not included in calculating distances
because they have no information in them. By removing these columns, the
calculation of a large number of distances is accelerated. Also, people
also like to mask their sequences to remove variable regions using a
soft or hard mask (e.g. Lane's mask). This type of masking is only
encouraged for deep-level phylogenetic analysis, not fine level analysis
such as that needed with calculating OTUs. This tutorial uses the data
files in [ amazondata.zip](https://mothur.s3.us-east-2.amazonaws.com/wiki/amazondata.zip).


## Default settings

To run **filter.seqs** you need to provide your sequences to be filtered in
either fasta, nexus, clustal, or phylip format. The output will be in
fasta format. By default, any column with a '-' in every sequence is
removed from the alignment and put into a \*.filter.fasta file. For
example the sequences in the file amazon.unique.align are the sequences
in amazon.unique.fasta aligned to the **greengenes alignment**. The
sequences in amazon.unique.fasta are generally less than 1 kb, but vary
considerably in length. We'd like to only consider those columns in the
alignments that overlap. Also, considering the overall alignment length
is 7682 characters, we can probably remove a lot of positions from the
alignment to speed up our distance calculations. Try the following
command:

    mothur > filter.seqs(fasta=amazon.unique.align)

The resulting alignment in the amazon.unique.filter.fasta file will be
2305 characters long and the average unaligned sequence is about 400 bp
long. The file, amazon.unique.filter, is a series of 0's and 1's that
indicate, which columns were included in the filtered alignment. This
file can be used with the [ hard option](/wiki/filter.seqs#hard)
below. Also, a series of statistics are written to the screen that
indicate how many columns were used in generating the filter and the
number of sequences that the filter was based on:

    Length of filtered alignment: 1898
    Number of columns removed: 5784
    Length of the original alignment: 7682
    Number of sequences used to construct filter: 96

You can also enter multiple files to filter together. You do this by
separating the fasta files with '\|' characters. mothur creates a
filter and filters the sequences as if they were all in the same file,
but outputs separate .filtered.fasta files.

    mothur > filter.seqs(fasta=amazon.unique.align|core_set_aligned.imputed.fasta)

## Options

### vertical

By default vertical option is set to T, and any column that only
contains gap characters (i.e. '-' or '.') is ignored.

    mothur > filter.seqs(fasta=amazon.unique.align, vertical=T)

This can be turned off by setting vertical to F:

    mothur > filter.seqs(fasta=amazon.unique.align, vertical=F)

    Length of filtered alignment: 7682
    Number of columns removed: 0
    Length of the original alignment: 7682
    Number of sequences used to construct filter: 96

Note that nothing was removed from the alignment.

### trump

The trump option will remove a column if the trump character is found at
that position in any sequence of the alignment. You can use any
character with the trump setting ('.', '-', 'N', etc). NOTE:
having one or two sequences included that don't align with the bulk of
your sequences may lead to all columns being removed by the trump
option!

The [align.seqs](/wiki/align.seqs), NAST, and SILVA aligners will
precede the first base of the sequence with a string of periods and the
columns from the last base to the end of the alignment will also be a
string of periods. You may want to remove these columns:

    mothur > filter.seqs(fasta=amazon.unique.align, trump=., vertical=F)

    Length of filtered alignment: 2305
    Number of columns removed: 5377
    Length of the original alignment: 7682
    Number of sequences used to construct filter: 96

Sometimes for protein coding sequences people like to remove any column
that contains a gap in any sequence. This can be achieved with the
command:

    mothur > filter.seqs(fasta=amazon.unique.align, trump=-, vertical=F)

    Length of filtered alignment: 2030
    Number of columns removed: 5652
    Length of the original alignment: 7682
    Number of sequences used to construct filter: 96

This does nothing:

    mothur > filter.seqs(fasta=amazon.unique.align, trump=,  vertical=F)

    Length of filtered alignment: 7682
    Number of columns removed: 0
    Length of the original alignment: 7682
    Number of sequences used to construct filter: 96

It is suggested that the trump and vertical options be used together for
maximum speed up of downstream distance calculations:

    mothur > filter.seqs(fasta=amazon.unique.align, trump=., vertical=T)

or

    mothur > filter.seqs(fasta=amazon.unique.align, trump=.)

Because 'vertical=T' is the default, both commands will produce the
following output:

    Length of filtered alignment: 577
    Number of columns removed: 7105
    Length of the original alignment: 7682
    Number of sequences used to construct filter: 96

Thus, the final alignment is only 577 columns long. This is more than a
13-fold reduction in the alignment length and will result in a speed up
of more than 13-fold in the distance calculation. **Notice:**In 1.20
vesion, the result of "filter.seqs(fasta=amazon.unique.align,
trump=.)" is same of "filter.seqs(fasta=amazon.unique.align, trump=.,
**vertical=F**)"

### soft

A soft mask removes any column where the dominant base (i.e. A, T, G, C,
or U) does not occur in at least a designated percentage of sequences.
For resolution of deep branching in phylogenetics, it is common to
require that the dominant character occur in at least 50% of the
sequences. Such a filter can be done in mothur as follows:

    mothur > filter.seqs(fasta=amazon.unique.align, soft=50, vertical=F)

    Length of filtered alignment: 440
    Number of columns removed: 7242
    Length of the original alignment: 7682
    Number of sequences used to construct filter: 96

The value given to soft must be an integer between 0 and 100. Again,
this filter option is only suggested for resolving the relationships
between deep branches in the phylogenetic trees, not for calculating
OTUs.

### hard

Use of the file option will allow one to apply a hard mask to the
sequences (e.g. the [lane mask](/wiki/Lane_mask)). The inputted
file should only contain one line consisting of 0's and 1's. A "0"
indicates that the column should be excluded and a "1" indicates that
the column should be included. To use a hard mask you would enter:

    mothur > filter.seqs(fasta=amazon.unique.align, hard=Lane1349.gg.filter, vertical=F)

    Length of filtered alignment: 1232
    Number of columns removed: 6450
    Length of the original alignment: 7682
    Number of sequences used to construct filter: 96

Again, this filter option is only suggested for resolving the
relationships between deep branches in the phylogenetic trees, not for
calculating OTUs.

### processors

The processors parameter allows you to run the command with multiple
processors. Default processors=Autodetect number of available processors
and use all available.

    mothur > filter.seqs(fasta=amazon.unique.align, processors=2)

## Revisions

-   1.24.0 - Paralellized for Windows.
-   1.25.0 - When run with "current", it generated ".filter" and not
    "filename.filter" file.
-   1.40.0 - Rewrite of threaded code. Default processors=Autodetect
    number of available processors and use all available.
-   1.44.0 - Changes **filter.seqs** fasta file deliminator from '-' to
    '\|' to allow for '-''s in filenames.


