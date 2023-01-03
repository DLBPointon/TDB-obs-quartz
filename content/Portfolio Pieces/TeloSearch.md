---
tag: ["workbased", "portfolio"]
date: 50@16-12-2022
type: ['Pipeline', 'Software Development']
---


GitHub:: [https://github.com/AlanTracey99/TeloSearch](https://github.com/AlanTracey99/TeloSearch)

Contribution:: Nextflow DSL2, Python 3.9, bash

Working with:: AT (colleague at Sanger)

Topic:: Collaborative Project, Scaling a project to meet organisational goals

KSBs:: S6, S7, B1, B3, B4

---

Description:: A pipeline to find putative telomeric sequence in good quality scaffolded assemblies

### The Project
The TeloSearch project was originally started by a member of GRIT (AT) who had written a python script to pull putative telomeres from a scaffolded genomic assembly. This would be a very useful tool in the curation team but would need scaling up in order to be run across the hundreds of genomic assemblies expected to move through the ToL genome engine on a weekly basis.

This project involved a significant amount of collaboration between the two of us, talking through what was required for converting a singular python script into a automatic and horizontally scalable Nextflow DSL2. This has involved creating a series of scripts—which were not originally part of the project—that handles the input, massages multiple intermediary files, creates a summary output file and takes the best putative telomere and enters it into the Jira Ticket for that assembly.

### My Contribution
My contributions to the project consisted of writing a significant amount of the Nextflow DSL2 Pipeline as this was also being used as a way to train AT on how Nextflow works, the correct syntax as well as how to modularise a pipeline.

As we had very similar Python skills, I also helped in writing of the list comprehensions and lambda functions used in the main TeloSearch Python scripts.

A number of the projects I have written whilst at Sanger have involved using the Jira-Python module, because of this I also suggested we write a module to take the final output and insert this into the ticket related to the input genome.

### Future Work
As part of [[TreeVal - md team and tracking time]] this project will be updated, as some functions related to identifying putative sequences are too broad, and then used as part of the standard TreeVal pipeline. This will allow us to collect a database of telomeric sequences that have yet been seqeunces and further improve curation outcomes.

Some parts that I could update significantly include the `jira_telo_push.py` script (found [here](https://github.com/AlanTracey99/TeloSearch/blob/main/scripts/jira_telo_push.py)), which would benfit from the use functional programming. This would reduce the amount of code and simultaneously making it easier to read.

A simple example is the `get_length` funtion, this could be changed as below:

```python
# This code block can be run locally if the repo is downloaded and opened in Obsidian with the jupyter plugin installed and the python code block converted into a jupyter code block.

putative_telo = 'ATTATTATT'

# Current implementation
def get_length_current(motif):
	"""
	Function returns the lengthe of a motif. !!! indicated no telo so
	returns 0.
	"""
	if motif == '!!!':
		motif_value = 0
	else:
	motif_value = len(motif)
	return int(motif_value)

# Proposed implementation
def get_length_proposed(motif):
	"""
	Function returns the lengthe of a motif. !!! indicated no telo so
	returns 0.
	"""
	return int(motif_value) if motif == '!!!' else len(motif)

get_length_current(putative_telo)
# 9

get_length_proposed(putative_telo)
# 9
```

### Evidence of Team work
Some of this evidence includes where I am teaching AT how to use GitHub and teaching them the Nextflow DSL2 syntax.

##### Evidence 1
On setting up and using GitHub - Slack Chat.
```markdown
DamonLBP
Oh yes, wrong word at the wrong time then say goodbye to your work. This is why you almost can't push too often.

That way you can revert any damaging changes you do

AT
you almost want push running every 30 seconds in the background...

DamonLBP  
Yep, but then pushing code to main which doesn't work is bad practise and just as likely to annoy. So branches are a safe space.

AT
ok,  I need to remember that and get used to working in branches.  Would you say each branch should have a task associated with it and then when that task is done you pull it back into main?


DamonLBP  
Yes precisely.

This is also where using GitHub Issues and the integrated KanBan board can be useful
```


##### Evidence 2
On reporting updates I have made and a discussion on further changes.

Part 1 - Slack Chat
```markdown
DamonLBP  
Morning Alan,  
There's not much i'll be able to do today due to university stuff. But i thought i'd let you know that the JIRA integration works... kind of. Running the script outside of the pipeline works and posts to GRIT-280 but inside the pipeline it fails due to 'Being outside of the Sanger Network' So this maybe a systems issue. I've detailed what I can here: [https://github.com/AlanTracey99/TeloSearch/issues/2](https://github.com/AlanTracey99/TeloSearch/issues/2)It wouldn't be alot of work to make my script take the cannon and noncannon files and spit out what it thinks is best and run it separately but it would be a pain.

AT
Thanks Damon - sounds like progress.  Happy to chat about the best way to utilise the results if you want at some point...

DamonLBP
It is done, the pipeline now passes to JIRA. The python script needed to pass the JIRA request through the sanger cache system in order to connect.

AT 
Nice!
Are there any telo-populated tickets?

DamonLBP
I did GRIT-470, you can see where the changes occurred at the bottom of the history tab. I'm changing it so the length is actually the length of the sequence, currently measuring the wrong bit of the report.

Part 2 (see below) was attached.

```

Part 2 - Screenshot of the incorrect upload to JIRA
![[images/evidence_of_jira_integration_telosearch.png]]

Part 3 - Slack Chat (following on from Part 2)
```markdown
AT
only thing I don't like is 'CAN' looks like DNA sequence, eg CA[*]

DamonLBP  
That is a fair point

AT
not sure why it say length 3 - but I think from what you said above that you're fixing that

DamonLBP  
I put an argument in the wrong place, so it was measuring CAN. That's fixed now, although i've managed to kill my connection to the farm.

AT
ok.  Just so you know, Bethan has a hymenopteran with 2 motifs, one length 9 and one length 5 - how will you deal with this?

DamonLBP  
At the minute, it won't. It is taking the top result and using that.  
Need to sort out the logic for which to pick

AT 
I think we need to be able to pick and deal with multiple motifs

It can be the biological reality

DamonLBP  
Yes i thought so, but at the time I was just focused on just getting the Jira posting to work.

What if I were to change CAN and NONCAN to ! and ? respectively. I think those would make sense and also makes clear what sequence to use. It'll just make it easier for me to parse it for downstream.

AT
sounds ok - you may want to send an explanation to the curators at some point?

DamonLBP
Sure as soon as it hits production. I'm writing it up on the README too.
```