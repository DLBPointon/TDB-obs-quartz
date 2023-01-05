---
title: Data driven decision making
date: 50@16-12-2022
tags: ["TDB", "workbased", "portfolio"]
type: ["Learning"]
---

Contribution: Nextflow DSL2, Python 3.9, bash

Working with: ToL

Topic: Collaborative Projects, Decision making, Data science

KSBs:: K3-3

---

Description:: How data has effected how a project has gone forward.

Through my work in DTOL, data driven decision making has been ubiquitous. Through Tree Of Life Research and Development (ToL RnD) meetings we see the effects of data driven decision making on:

- The Core Labs team and their experiments in attemping to improve sequencing pipelines, and the effect on sequencing yield due to the complex genomes of polyploid plants and highly repetitive genomes.

- The Faculty Research groups in where they must decide on the best ways in which to massage their data to produce informative results. The Merian Unit Analysis (not yet published), which is being added to the [[TreeVal - md team and tracking time]] Project, needed iterative refinement to best identify putative ancestral units. This will go on to be used in [[TreeVal - md team and tracking time]] to better improve both curation and Lepidopteran genetics.

- GRIT require the use of a multitude of data in order to correctly identify scaffolds which may require breaking, joining or even removing depending on a variety of features such as: coverage changes, telomeric sequence, and strength of HiC signal. All of these impact the quality of the final genomic assembly.
	-  [[Work-based Projects/Curation of iyTipFemo1]]
	- [[Work-based Projects/Curation of idCriBerb1]]

	This data is also entered into Jira, for ingestion into other data-driven projects, such as [[GRIT-realtime]]. This takes the curation data and collates it into a form usable for management decisions and publications.

- ToLa has been testing the use of Ultra-Low Input sequencing methods and comparing these against the current suite of sequencing methods already in use at Sanger. This is acheived by taking the raw reads from both methods, assembling the filtered reads and then collecting stats on those final assemblies.
	- Image of assembly graphs from ksenia?

- [[TreeVal - md team and tracking time]] has required data driven decision making too, the documentation for some methods and functions---performed by the gEVAL/ensembl database---have been lost and so could not be replicated in JBrowse (the front-end component of TreeVal). The selfcomp (Self complementary sequence) track is a prime example, Minimap2 resullts in blocks of hits which has required iterative refinements to mimic the results shown on gEVAL.
	- Images of gEVALs output as well as JBrowse pre and post selfcomp fix.

	This project has also involved close co-operation with GRIT in order to ensure that the curators could reach the same conclusions given the gEVAL build or the TreeVal build. 