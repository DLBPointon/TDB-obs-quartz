
GitHub: [https://github.com/AlanTracey99/TeloSearch](https://github.com/AlanTracey99/TeloSearch)
Contribution: Nextflow DSL2, Python 3.9, bash
Working with: Alan Tracey (AT)
Topic: Collaborative Project, Scaling a project to meet organisational goals
KSB:

---


### The Project
The TeloSearch project was originally started by a member of GRIT (AT) who had written a python script to pull putative telomeres from a scaffolded genomic assembly. This would be a very useful tool in the curation team but would need scaling up in order to be run across the hundreds of genomic assemblies expected to move through the ToL genome engine on a weekly basis.

This project involved a significant amount of collaboration between the two of us, talking through what was required for converting a singular python script into a automatic and horizontally scalable Nextflow DSL2. This has involved creating a series of scripts—which were not originally part of the project—that handles the input, massages multiple intermediary files, creates a summary output file and takes the best putative telomere and enters it into the Jira Ticket for that assembly.

### My Contribution
My contributions to the project consisted of writing a significant amount of the Nextflow DSL2 Pipeline as this was also being used as a way to train AT on how Nextflow works, the correct syntax as well as how to modularise a pipeline.

As we had very similar Python skills, I also helped in writing of the list comprehensions and lambda functions used in the main TeloSearch Python scripts.

A number of the projects I have written whilst at Sanger have involved using the Jira-Python module, because of this I also suggested we write a module to take the final output and insert this into the ticket related to the input genome.

### Future Work
As part of [[TreeVal]] this project will be updated, as some functions related to identifying putative sequences are too broad, and then used as part of the standard TreeVal pipeline. This will allow us to collect a database of telomeric sequences that have yet been seqeunces and further improve curation outcomes.