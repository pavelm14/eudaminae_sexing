# eudaminae_sexing
This is our repository where we describe the bioinformatic steps to obtain primers to amplify a fragment of the kettin loci (Z chromosome) in Eudaminae.

We use low-coverage whole genome resequencing data to extract the locus of interest. Then, we align the resulting sequences and public transcriptomic data to assess for any potential intron/exon breaks in the genomic sequences. Finally, we use the Primer BLAST algorithm to point out potential conserved regions across Eudaminae where primers can anneal.

Once we design the primers, we will follow the qPCR approach to determine the sex of butterflies described in, for example, [Belousova et al. (2019)](https://doi.org/10.1016/j.jinsphys.2019.02.005).

## step 1: Transcriptomic data
We will download the transcriptomic sequences of the kettin gene available at NCBI: https://www.ncbi.nlm.nih.gov/gene/?term=kettin+lepidoptera

By October 11, 2022, the data include transcriptomes of B. mori, B. anynana, and P. brassicae.

These sequences will be used as target baits to pull out contigs of interest from the genome assemblies of Eudaminae. Moreover, the transcriptomic sequences will be again used during the multiple sequence alignment step, where we aim to distinguish exon/intron boundaries in the genomic sequences.

The transcriptomic sequences are localted at the [data/targets folder](https://github.com/pavelm14/eudaminae_sexing/blob/master/data/targets).

## step 2
