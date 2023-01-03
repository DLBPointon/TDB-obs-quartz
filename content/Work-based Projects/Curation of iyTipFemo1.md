---
title: Curation of iyTipFemo1
date: 51@22-12-2022
tags: ["TDB", "workbased", "portfolio"]
type: ["Curation"]
---

GitHub:: https://gitlab.com/wtsi-grit/rapid-curation

Contribution:: Curation of a reference quality genome.

Working with:: AT, JMDW, KK, MUS

Topic:: Data driven decision making, team work

KSBs:: K5-5, K3-3, S6, S7, B3

---
Description:: How I have curated the reference genome for _Tiphia femorata_.

### The Project
The aims of the DTOL project include the production of reference quality genomes for the 77,000 organisms that call the British Isles and Ireland their home. A part of this mamoth task is ensuring that practically anyone can perform such a task with only some help from the professional curators in GRIT.

This portfolio peice will focus on the curation attempt of _Tiphia femorata_, known internally as iyTipFemo1 or commonly as the beetle-killing wasp (as it is the parasitoid of the scarab beetle), see Figure 1.

![[Tiphia_femorata.png]]
Figure 1: A female _Tiphia femorata_, commonly known as the beetle-killing wasp. Picute taken by Hectonichus (2010).

### My Contribution
The data received by myself and the other members of ToLa is "pre-assembled", meaning that automated pipelines have already taken the raw read data from the Sequencing Team and generated a best-guess assembly. This assembly is then evaluated by those in ToLa with the help of [TolQC](https://tolqc.cog.sanger.ac.uk/darwin/insects/Tiphia_femorata/), a website produced to collate assembly statistics as well as preliminary contamination reports and includes graphs as shown in Figure 2 and 3.

![[images/iyTipFemo1-kmerplot.png]]
FIgure 2: A Kmer multiplicity plot, that highlights a fairly well assembled diploid genome---e.g. the first red peak is >50% of the larger peak and the grey peak being kmers that have been removed but have no impact on the quality of the genome

The iyTipFemo1 assembly it self was unremarkable---apart from two noticable regions of highly repetitive regions---and the size of the genome (~300MBp) was small enough that it assembled well via the automated processes, see Figure 3. This isn't a perfect process and misjoins (where contigs that do not actually need joining are joined by the assembler) may need correcting with a break (the breaking of a scaffold into it's component contigs). BUSCO was also run, as standard, on the reads for this assembly resulting in the scores found in Table 1.

| Field | Score (%) |
|---|---|
| Completeness | 99.5% |
| Single Copy | 99.1% |
| Duplicate | 0.4% |
| Fragmented | 0.1% |
| Missing | 0.4% |
Table 1: The BUSCO summary results showing that the assembly is estimated to be 99.5% complete with another 0.1% of sequnce being fragmented BUSCO genes. This analysis was performed across the 1367 reads that make up the iyTipFemo1 assembly.

The mitochrondial genome required more investigation. My collegue, MUS, developed a python based workflow called [MitoHiFi](https://github.com/marcelauliano/MitoHiFi), in order to tease out putative mitochondrial reads (HiFi data) via the annotation and whether or not they circularise. In the case of _T. femorata_ multiple potential mitochondrial sequences were identified, an issue that has become rather common particularly in wasp genomes.

![[iytipfemo-precuration.png]]
Figure 3: The [PretextView](https://github.com/wtsi-hpag/PretextView) of the iyTipFemo1 assembly pre-curation.

In order to narrow our search (myself, KK and MUS at this point) we employed the use of MBG (Rautiainen, 2021), CD-HIT (Fu, 2012) and Bandage (Wick, 2015). Using CD-HIT, we were able to cluster together scaffolds which were similar to a reference (a mito previously found in a wasp, determined by MitoHiFi) which resulted in two scaffolds being identified as potential mitochondrial reads, ptg00002l and ptg00003. Using MitoHiFi, MBG and Bandage it was then possible to visualise these and see their length and number of genes annotated, this required the use of multiple re-runs, modifying variables such as the clustering cut-offs in CD-HIT to ge the most optimal results. ptg00003 was then assigned as the mitochondrial sequence due to its completeness---e.g. it was a standard mitochondrial length (16kbp), carried the correct number of genes (37) and was circular---the other sequence may have been neomite (mitochondrial sequence adopted into the host genome) or a product of heteroplasmy.

| Scaffold A | Scaffold B |
|---|---|
|scaffold_14.13  | scaffold_1.65   |
|scaffold_2.1    | scaffold_2.20_2 |
|scaffold_5.49   | scaffold_5.1    |
|scaffold_6.1    | scaffold_6.20_2 |
|scaffold_15.1   | scaffold_10.28  |
|scaffold_16.4_1 | scaffold_11.26  |
|scaffold_9.1    | scaffold_12.1   |
Table 2: A table showing the scaffolds which were joined together manually. Scaffold id's ending with a '\_1' or '\_2' are the products of broken scaffold

| Scaffold broken | At base pair position |
| --------------- | -------- |
| scaffold_2.20   | 9776444  |
| scaffold_5.33   | 16411527 |
| scaffold_6.20   | 9954728  |
| scaffold_16.4   | 1629000  | 
Table 3: A table showing the scaffolds which required breaking and the base pair position where the break was introduced.

The curation of this assembly was relatively straight forward, requiring seven scaffold joins (see Table 2), four scaffold breaks (see Table 3), and one haplotypic sequence removal (these are moved into the assemblies haplotype file). These were all evidenced by the PretextView map (See figure 3 and 4) and HiGlass map (no longer availble due to size constraints). These contact maps make up the back bone of modern curation, allowing for high resolution interigation of HiC data (HiGlass) as well as for fast and easy manipulation of the assembly in a visual environment (PretextView).

![[iytipfemo-postcuration.png]]
Figure 4: The [PretextView](https://github.com/wtsi-hpag/PretextView)  for the iyTipFemo1 assembly, post-curation. Centromeres, if found, have also been orriented to the left of their respective chromosome.

Once these changes have been made, the PretextView is then sent to another curator for verification. If they agree that your changes were correct then the curation is complete and the last steps of GRIT involve the submittion of the final genomic fasta file for upload to NCBI. In the case of _T. femorata_ this is [here](https://www.ncbi.nlm.nih.gov/genome/?term=txid330862[Organism:noexp]) and statistics are found on [GRIT-realtime](https://grit-realtime.tol.sanger.ac.uk/table.html).

![[iyTipFemo-nucmer.png]]
Figure 5: A Nucmer plot of the pre-curation iyTipFemo1 assembly against the _Orussus abietinus_ (a sawfly, basal to wasps and bees) assembly.

The process of manually curating a genome is iterative, relying on evidence (such as the contact maps or syntenic alignments such as those produced with Nucmer, see figure 5) and can sometimes feel like playing Soduko. In any place you may need to make multiple moves and changes based on a educated guesses and these changes may be genuine or may need completely reverting.

### Future Plans
I plan on furthering my skills in genomic curation by taking on more tickets in GRIT. Allowing my to get a greater grasp of the shear complexity of genomes through the Hymenopteran genomes as well as the how this compares across the three of life.

### References
Fu, L., Niu, B., Zhu, Z., Wu, S., Li, W. 2012. CD-HIT: accelerated for clustering the next-generation sequencing data. _Bioinformatics_. 28(23). pp. 3150–3152. DOI: [10.1093/bioinformatics/bts565](https://doi.org/10.1093%2Fbioinformatics%2Fbts565)

Hectonichus. 2010. Tiphiidae - Tiphia femorata. _Wikipedia_.  https://en.wikipedia.org/wiki/Tiphia_femorata#/media/File:Tiphiidae_-_Tiphia_femorata..jpg. 

Rautiainen, M., Marschall, T. 2021. MBG: Minimizer-based sparse de Bruijn Graph construction. _Bioinformatics_. 37(16). pp. 2476–2478. DOI: [10.1093/bioinformatics/btab004](https://doi.org/10.1093/bioinformatics/btab004). 

Wick, RR., Schultz, MB., Zobel, J., Holt, KE. 2015. Bandage: interactive visualization of de novo genome assemblies. _Bioinformatics_. 31(20). pp. 3350–3352. DOI: [10.1093/bioinformatics/btv383](https://doi.org/10.1093/bioinformatics/btv383)