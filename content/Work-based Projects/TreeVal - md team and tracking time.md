---
title: TreeVal
date: 50@16-12-2022
tags: ["TDB", "workbased", "Portfolio"]
type: ["Pipeline", "Software Development"]
---

GitHub:: https://github.com/sanger-tol/treeval

Contribution:: Nextflow, Python 3.9, Agile

Working with:: Directly with yy5 and we3, ToL-IT, GRIT and sm15 (ToLa Manager)

Topic:: Collaborative work, Meeting Organisational Goals

KSBs:: S6, S7, B1, B2, B3, B4, B6

---
Description:: A Nextflow DSL2 pipeline + Jbrowse Front end to replace gEVAL

### The Project
Born out of a need to replace the aging---and no longer fit for purpose---[gEVAL](https://academic.oup.com/gigascience/article/10/1/giaa153/6072294), TreeVal is designed to be a modern replacement in a modern framework. As ToL-IT, at the time of starting TreeVal, was introducing Nextflow as the first standardised workflow language for use in ToL, it was decided that our small working group would follow suite and adopt Nextflows DSL2 language.

We would also be using a modern framework called JBrowse for displaying the genomic data generated via this pipeline. The benefits of JBrowse include: it being a drop in replacement and improvement of the gEVAL browser, there is an active plugin community and we are able to create plugins for any data required by the curation team.

TreeVal as of 16-12-2022 is in Phase 2. This means we have completed the pipelining of previously non-pipelined softwares (Phase 1) and have also completed a round of bug fixes and high priority changes (Phase 1.5), see figure 1. 

![[TreeVal Phase 1.5 (2).png]]
Figure 1: The Phase 1.5 pipeline diagram for TreeVal


#### Multidisciplinary Team
ToL is a very multi-discipliniary team, and the TreeVal team exemplifies this. Whilst all three of us are programmers in the usual assortment of languages (Python 3, JavaScript, R), yy5 specialises in prototyping and algorithms, we3 was previously a web developer and I work on the pipelining logic and tracking, see figure 2. During the time TreeVal has been in developement, and because of this multi-discipliniary background, we have managed to learn a significant amount from each other.

~~#~~#~~#~~#######
Figure 2: An Iteration of the Kanban Board we use for TreeVal tracking.

This goes even further when taking into account the wider ToL infrastructure teams which have members which specialise in Piplining with Nextflow (who help with the more niche issues we encounter), others who are Kubernetes experts (who enable the running of the TreeVal instructure) and a team of software developers who we can rely on to make changes where needed and help meet the standards given by ToL-IT and NF-Core.

#### Tracking
Through-out the project, we have used Kanban boards to keep track of open tickets and items which require further research. We avoided the use of more heavily strucutred methods such as Agile due to the highly varied time requirements of day-to-day work, this meant that one week could result in no work completed for TreeVal and another could result in multiple sub-worksflows being completed.

This was started during Phase 1, and due to the number of requests we were receiving about software to test and implement it was decided to create research and development queue an


### Future Plans

### Evidence
