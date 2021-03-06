---
title: 'sparcc'
tags: 'commands'
redirect_from: '/wiki/Sparcc'
---
The **sparcc** command allows you to \.... To run this tutorial please
download: [
fake\_data.1.subsample.shared.zip](https://mothur.s3.us-east-2.amazonaws.com/wiki/fake_data.1.subsample.shared.zip).

## Default

The shared parameter is required.

    mothur > sparcc(shared=fake_data.1.subsample.shared)

## Options

### samplings

The samplings parameter is used to \.... Default=20.

    mothur > sparcc(shared=fake_data.1.subsample.shared, samplings=10)

### iterations

The iterations parameter is used to \....Default=10.

    mothur > sparcc(shared=fake_data.1.subsample.shared, iterations=100)

### permutations

The permutations parameter is used to \....Default=1000.

    mothur > sparcc(shared=fake_data.1.subsample.shared, permutations=10000)

### method

The method parameter is used to \....Options are relabund and dirichlet.
Default=dirichlet.

    mothur > sparcc(shared=fake_data.1.subsample.shared, method=relabund)

### groups

The groups parameter is used to select groups from your shared file. The
default value for groups is all the groups in your shared file. Group
names may be separated by dashes.

    mothur > sparcc(shared=fake_data.1.subsample.shared, groups=0-1-2)

### label

The label parameter is used to analyze specific labels in your shared
file.

### processors

The processors parameter allows you to run the command with multiple
processors. Default processors=Autodetect number of available processors
and use all available.

    mothur > sparcc(shared=fake_data.1.subsample.shared, processors=2)

## Revisions

-   1.31.0 - First Introduced
-   1.39.0 - Fixes floating point exception
-   1.40.0 - Speed and memory improvements for shared files.
    [\#357](https://github.com/mothur/mothur/issues/357) ,
    [\#347](https://github.com/mothur/mothur/issues/347)
-   1.40.0 - Rewrite of threaded code. Default processors=Autodetect
    number of available processors and use all available.
-   1.40.3 - Improves speed with threaded code and corrects small bug.


