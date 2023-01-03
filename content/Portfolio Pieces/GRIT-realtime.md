---
title: GRIT-realtime
date: 50@16-12-2022
tags: ["TDB", "workbased", "portfolio"]
type: ["Full-stack Project", "Database-PostreSQL", "Software Development"]
---

GitHub:: [https://github.com/DLBPointon/grt-v5](https://github.com/DLBPointon/grt-v5)

Contribution:: JavaScript, HTML, Python 3.9, bash, Project Management, APIs, Database

Working with:: Solo project reporting to manager

Topic:: Designing new systems to meet organisational goals.

KSBs:: K5-3, S6, B1, K3-3, B1, B6

---

Description:: A Full-stack project to generate graphical summaries of post-curation data

### The Project
GRIT-realtime—grt, [https://grit-realtime.tol.sanger.ac.uk/](https://grit-realtime.tol.sanger.ac.uk/)—was originally developed as coursework for the Bioinformatics in the Workplace module. Prior to this project, statistics and graphs would be gathered by: downloading a csv of data, importing this into Microsoft Excel and then manually curating the data (line by line), and, then generating the statistics and graphs required for reports and papers. This resulted in a significant time sink for management and so a more modern and automated solution was required.

The project, see figure 1, uses Python 3.9 with the jira_python module to interact with the Jira Database and pull data that meets built in requirements, e.g., belongs to a GRIT project and has made it the post-curation step of the workflow.

The data is then parsed to pull the correct information from free text fields, and calculate statistics such as manual interventions per 1Gb of genome. The output tsv file, is then ingested by a PostgreSQL database which can then serve a frontend via a PostgREST API layer. The graph views can then be altered via a series of drop-down menus to tailor the view, see figure 2.

![grt-v5 schematic](https://lh3.googleusercontent.com/HxWonAXDQfPcStDizOTl3BGOmcTN4hF-wwym_LW41MqfxQ31G6GywzSadzPcbuw3YesN8NUJM6neE60HTDnxxQAjbUaRPchhw-8njxkLq-W_5wFLej_X-qSUUDTntle09mH8T2XR8tJiLUSQ96m28a64tiM_SUk-KdP6yqB_v7KZ648Z4Fd3kfDc2FvIzw)
Figure 1: An overview of the GRIT-realtime architechture. Blue is a script, Green a source of data and orange colours the webserving components.

**![](https://lh4.googleusercontent.com/svXpOUgTFa12HqLgOPlmGRRTuZNFjhTJ46R6HdEP4OTkRJGZODrcYZgQ9D1uoR3mDjWX6uiIt4Uj45lnfVHEVhyc7CdBYT9OpygsuMFkhy1ficffdxeisIhCj6l0LHv25CA9xNxcshSSm4-OMYV-7uhtJ6qTMVS2ri5y8EAgAC6ZBjMqcoi86Z_p25GBnA)**
Figure 2: The main page of the GRIT-realtime site, showcasing the graphs with drop-down menu’s as well as simple database stats (three boxes across the top).

Currently, grt is used for curation poster presentations (both the front-end and the API have been used for data) as well as for the current genome note pipeline (as by default, grt parses much of the data that the genome note writer needs to complete a note). This data, as it is real-world post-curation data, can be used to imply the relative difficulty of genomic curation of the clades (see figure 3, where the Boxplot shows how many changes are made to an assembly of any clade), currently as some clades a represented by a low number of genomes there maybe an inherent sample bias towards the easier to assemble and curate (currently, those which are poorly assembled and non-curatable are re-submitted for sequencing and are not included in grt).

### My Contribution
I built the entirty of grt, originally as coursework for the Bioinformatics in the Workplace. The original was based in R for display in RShiny and is still hosted [here](https://grit-realtime.shinyapps.io/scripts/), the loading time alone (around 5 minutes) required a different approach and so the aforementioned containerised version was produced. This was also during a time where Sanger-IT were encouraging people to move away from RShiny due to the amount of time taken to compile a Shiny Container as well as the poor scaling and porformance of the framework.

### Future Work
Sanger contains a group that soley work on platforms, their role over the past 3 years has been creating a ReactJS based framework for sample management throught out DTOL. As that project has grown, so have the ambitions for it. It is currently being rolled out company wide and is now based on a Sanger specific framework in which a number of projects will be converted too. This will, however, require learning ReactJS so will represent a significant learning curve from vanilla JavaScript.

I will eventually be commiting grt over to this new platform, where it will be further expanded on by including [[TeloSearch]] results from Jira as well as BUSCO from [TolQC](https://tolqc.cog.sanger.ac.uk/index.html) (one of the site) and/or [[TreeVal - md team and tracking time]] to better act as a post-curation summary site.

