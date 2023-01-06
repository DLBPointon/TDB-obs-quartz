---
title: Curation of idCriBerb1
date: 05@3-02-2022
tags: ["TDB", "workbased", "portfolio"]
type: ["Curation"]
---

GitHub:: NA

Contribution:: Curation of a reference quality genome.

Working with:: AT, JMDW

Topic:: Data driven decision making, team work

KSBs:: K5-5, K3-3, S6, S7, B3

---
Description:: Detailing the curation of idCriBerb1

### The Project
The aims of the DTOL project include the production of reference quality genomes for the 77,000 organisms that call the British Isles and Ireland their home. A part of this mamoth task is ensuring that practically anyone can perform such a task with only some help from the professional curators in GRIT.

This portfolio peice will focus on the curation attempt of [_Criorhina berberina_](https://www.ncbi.nlm.nih.gov/data-hub/taxonomy/2663927), known internally as idCriBerb1 or commonly as the Dimorphic Bearfly, a bumblebee mimic, see Figure 1.

![content/images/idcriberb1.png]
![/content/idcriberb1.png]

Figure 1: An image of _Criorhina berberina_, taken by Martin Anderson (2011).

### My Contribution
Genome curation is very much like working with a very complex puzzle, except each piece is a puzzle unto itself. This is best visualised with the Pretext map visualised in PretextView2 (Figure 2). Each square is currently a scaffold and the goal is to assign each to a chromosome using off-diagonal signals (which infer association, depending on the brightness of the colour), coverage, HiGlass (a higher resolution HiC data visualiser, which does not allow editing of the map) and gEVAL analysis (which includes alignments to closely related organisms, telomeric signals, gaps and more). Using this data, and along with help from a seasoned curator in GRIT, I was able to produce around 1 curation Pretext Map, this is a separate map to the pre-curation Pretext map with changes. After consulting with a second member of the curation team, there were some large scale structural errors I had missed whilst correcting the smaller ones, see Figure 3. This required me to go back to the pre-curation map to make the additional changes which were evidenced with gap information from gEVAL (this gives evidence for making a break).

![[images/idCriBerb-precuration.png]]
Figure 2: The pre-curation pretext map, each square is a scaffold and the diagonal line is a linearised 2d representation of HiC data which when used with other data such as coverage graphs (shown as the line plot at the bottom of the figure) can be used to create a chromosome level genomic assembly.

![[images/idCriBerb-curationfixes.png]]
Figure 3: The end result of round 1 of curation, where all “obvious” changes have been made (e.g. regions of high association have been moved into their “natural” location). The above figure has also been annotated by a second curator  (JMDW), to show large scale issues with this draft curation Blue shows locations where breaks should be introduced, hinted at by the long curved signal off the diagonal (which I mistook for a centromeric signal). Green points towards two scaffolds which need to be swapped around and yellow covering a region that requires “flipping” as it is currently inverted. The colour scheme has been changed from Figure 2 to increase the contrast and allow better visualisations of the association signals.

![[images/idCriBerb-postcuration.png]]
Figure 4: The fully curated assembly, the pink, red, green and blue are chromosomes 1, 2, 3 and X respectively. The white circles show centrosomal sequences, those circles off the diagonal show areas of high association (where the sequences are similar) and are reflected on the opposite side of the figure. The white line is evidence that these signals are all in line with each other, further evidencing they are repeats, their location in the chromosomes shows they are centromeric rather than telomeric (which are absent in dipterans).

In order to generate a final pretext map, the map to be saved as evidence, the pretext instance showing with the map from Figure 4 must be “dumped”. Dumping the TPF (Tile Path Format) allows for comparison between the edited genome and that in the gEVAL database (which will be pre-curation). This allows for a FASTA file to be generated which represents, what we believe to be, the fully curated genome which will go on to become the reference genome of this species, as will be the case for the majority of organisms passing through the Darwin Tree of Life Program. Using GRIT-realtime, we can view the changes made to this genome in Table 1. This shows how the removal of various types of sequence such as; haplotypic duplications, contaminants and false duplications affects the statistics of the genome. Removed sequence, in this case, was primarily haplotypic duplication which made up the smallest 22 scaffolds that sit to the right of the sex (labelled blue) chromosome in Figure 4, these have been zoomed in Figure 5.

![[images/idCriBerb-haplotypicduplication.png]]
Figure 5: A figure to better show the haplotypic duplication of the Criorhina berberina. The blue underlined chromosome is the expected X chromosome also shown in Figure 4. Boxed in white is the 22 scaffolds of haplotypic duplication, which can be seen to have some limited association with the sex chromosome.

![[images/idCriBerb-grit-realtime.png]]
Figure 6: A graph taken from [[Portfolio Pieces/GRIT-realtime]] which shows how the curation of _Criorhina berberina_, shown here as idChiBerb1, compares to other dipterans that have been curated. The Y-axis is the number of Manual interventions per GB of genome (including breaks and joins of sequence).

| Category | Value |
|---|---|
| Sample ID | idCriBerb1 |
| Project ID | GRIT |
| Latin Name | _Criorhina berberina_ |
| Prefix DL | id |
| Prefix FL | Diptera |
| Family Name | Xylotini |
| Length Before (curation, bp) | 411039249 |
| Length After (curation, bp) | 410454260 |
| Length Change (%) | -0.1 |
| Scaffold Number Before (curation) | 49 |
| Scaffold Number After (curation) | 27 |
| Scaffold Number Change (%) | -44.8 |
| Scaffold N50 Before (curation, bp) | 85810835 |
| Scaffold N50 After (curation, bp) | 136888952 |
| Scaffold N50 Change (%) | 59.5 |
| Manual Interventions | 29 |
| Sequence to Chromosome (%) | 99.7 | 
| Chromosome Naming Style | By Size |
| Expected Sex | Female |
| Observed Sex | Female |
| Curated Allosomes | X |
| Curated Autosomes | 3 |
Table 1: The statistics of idCriBerb1, the internal name for Criorhina berberina, collected by grit-realtime. Showing that ~0.1% of the pre-curation genome was removed to generate the curated genome. The number of scaffolds was reduced by ~44.8% whilst the scaffold N50 increased by ~59.5%.

Upon final checks, this genome is then submitted to Ensembl and NCBI, the Primary assembly is found here: https://www.ncbi.nlm.nih.gov/assembly/GCA_917880715.1#/st.

### Future Plans
Future plans include improving skills in curation and running more of the assembly-curation pipelines, such as in the case of [[Work-based Projects/Curation of iyTipFemo1]].

### Evidence

##### Conversation about the first draft curation
**JMDW**
idCriBerb.  
You have two misjoins in PRTXT_2 and PRTXT_3. You have connected arms of different chrms together, q1-q2 and p1-p2

See Figure 3.

Some small cent sequence contigs probably can be placed but not really a problem.

_Explainer: PRTXT\_{int} is an identifier given to pre-curation chromosomes_

**DLBP**
Hi JMDW,  
I made these changes last night, i think i thought that those curved off diagonal chunks were odd centromeric signals. It also took me a while to find that first bit added to chr 2, then found it by accident, i've added a couple of other tiny bits too. But i think i'm picking at straws now.

**JMDW**
Sorry. realise I didn't really explain much or even give break coords. ...
You are right there is association between centromeres. but that lump of contacts is real linking between the two arms of each chromosome.
How you did have it the linking is very weak across those bad joins.

#### References
Anderson, M. 2011.  File\:Törneblomfluga02216.jpg \[Online\]. https://commons.wikimedia.org/wiki/File:T%C3%B6rneblomfluga02216.jpg. Accessed 04-01-2023