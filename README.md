# eudaminae_sexing
This is our repository where we describe the bioinformatic steps to obtain primers to amplify a fragment of the kettin loci (Z chromosome) in [Eudaminae](https://github.com/pavelm14/lab_miscellaneous/tree/main/website).

We use low-coverage whole genome resequencing (WGS) data to extract the locus of interest. Then, we align the resulting sequences and public transcriptomic data to assess for any potential intron/exon breaks in the genomic sequences. Finally, we use the Primer BLAST algorithm to point out potential conserved regions across Eudaminae where primers can anneal.

Once we design the primers, we will follow the qPCR approach to determine the sex of butterflies described in, for example, [Belousova et al. (2019)](https://doi.org/10.1016/j.jinsphys.2019.02.005).

## step 1: transcriptomic data
We download the transcriptomic sequences of the kettin gene available at NCBI: https://www.ncbi.nlm.nih.gov/gene/?term=kettin+lepidoptera

By October 11, 2022, the data include transcriptomes of B. mori, B. anynana, and P. brassicae.

These sequences are used as target baits to pull out contigs of interest from the genome assemblies of Eudaminae. Moreover, the transcriptomic sequences are again used during the multiple sequence alignment step, where we aim to distinguish exon/intron boundaries in the genomic sequences.

The transcriptomic sequences are localted at the [data/targets folder](https://github.com/pavelm14/eudaminae_sexing/blob/master/data/targets).

## step 2: genome assemblies
We assemble contigs de novo using the SECAPR pipeline ([Andermann et al. 2018](https://doi.org/10.7717/peerj.5175)). The latest implementation of SECAPR includes the software SPAdes, which is very convenient when assembling whole genome resequencing data ([Ribeiro et al. 2021](https://doi.org/10.1111/mec.16240)).

You can find in the [SECAPR tutorial](http://htmlpreview.github.io/?https://github.com/AntonelliLab/seqcap_processor/blob/master/docs/documentation/main_doc.html) how to install and use its different functions in the command line.

We work mainly in the MetaCentrum computer cluster. For more information on getting an account and tutorials how to run programs, see their [website](https://metavo.metacentrum.cz/).

We use our unpublished low-coverage WGS data:
- PM0178	Entheus	priassus (Entheini)
- XXXXXX Spicauda (Eudamini: Eudamina)
- PM0105	Autochton	itylus (Eudamini: Eudamina)
- PM-RN02-01	Cecropterus	dorantes (Eudamini: Eudamina)
- PM0278	Chioides	catillus (Eudamini: Eudamina)
- PM0297	Epargyreus	socus (Eudamini: Eudamina)
- PM0309	Narcosius	nazareus (Eudamini: Eudamina)
- PM0212	Telegonus	fulgerator (Eudamini: Eudamina)
- PM0243	Urbanus	pronta (Eudamini: Eudamina)
- PM0293	Aguna sp (Eudamini: Loboclina)
- PM0301	Ectomis	auginus (Eudamini: Telemiadina)
- PM0205	Cogia	undulatus (Oileidini: Typhedanina)
- PM0314	Bungalotis sp (Phocidini)
- PM0313	Dyscophellus	erythras (Phocidini)
- PM0312	Euriphellus	euribates (Phocidini)
- PM0311	Nascus	phocus (Phocidini)
- PM0318	Porphyrogenes (Phocidini)
- PM0310	Pseudonascus	solon (Phocidini)

We complement the taxonomic scope of Eudaminae by using published low-coverage WGS ([Li et al. 2019](https://doi.org/10.1073/pnas.1821304116)):
- SRR7174386	Drephalys	kidonoi (Entheini)
- SRR7174447	Cephise	aelius (Eudamini: Cephisina)
- SRR7174559	Udranomia	kikkawai (Entheini)
- SRR7174529	Oileides	vulpinus (Oileidini: Oileidina)

After checking that the Illumina reads are trimmed and clean, we use the following command in the SECAPR environment to assemble contigs using SPAdes:

```console
user@metacentrum:~$
secapr assemble_reads --assembler spades --input /data/processed/cleaned_trimmed_reads/ --output /data/processed/contigs
```

