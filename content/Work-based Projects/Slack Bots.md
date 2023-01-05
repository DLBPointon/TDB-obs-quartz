---
title: Slack Bots
date: 01@04-01-2023
tags: ["TDB", "workbased", "portfolio"]
type: ["Software Development", "Bot"]
---

GitHub:: [BTK-announcer](https://github.com/DLBPointon/btk_announcer), [Weekly-reporter](https://github.com/DLBPointon/weekly-report), [Priority-reporter](https://github.com/DLBPointon/priority_report)

Contribution:: Whole Project

Working with:: JMDW

Topic:: Software Development, CI-CD

KSBs:: B1 

---
Description:: Description of the slack bots developed to better inform GRIT and GEVAL-builders

### The Project
These three scripts were developed by a need for a simpler method of viewing important data from the sanger JIRA instance. These are automatically run on the internal GitLab repositories (the above github links are mirrors) via a gitlab-ci.yaml and using GitLab Secrets to pass JIRA credentials, see code block 1.

```
stages:
 - first

variables:
    JIRA_PASS: $JIRA_PASS
    JIRA_USER: $JIRA_USER
    TEST_HOOK: $SLACK_TEST
    PROD_HOOK: $SLACK_HOOK
    JIRA_INST: $JIRA_INST
    FLAG: $flag

before_script:
    - echo $PATH
    - apt-get update -qq && apt-get install -y python3.9 && apt-get install -y python3-pip
    - python3 -v
    - pip3 install jira
    - pip3 install datetime
    - pip3 install python-dotenv
    - pip3 install tabulate
    - pip3 install requests
    - pip3 install pandas

mrbtk:
  stage: first
  tags:
   - autoscale
  script:
    - python3 MrBTK.py $flag
  retry: 2
```
Code Block 1: The .gitlab-ci.yaml file used to run the GitLab pipeline at 9:00am. The variables denoted in the variables block (top to bottom) are: JIRA Password, JIRA Username, Slack webhook for private channel testing, Slack webhook for public channel posting, JIRA instance to scrape data from and a flag to specify whether the script posts to the private or public channel. This structure is used for all three bots. MrBTK is the BTK-anncouncer.

##### MrBTK
MrBTK is the Slack name for a bot that reads all JIRA tickets that are tagged `BlobToolKit` (BTK). This returns a dictionary with the ticket id of every ticket that has not made it through to the penultimate steps of curation. Subsequent steps then parse whether certain keywords are found in the comments, whether there is a colleuge assigned to the ticket, the workflow the ticket is in  as well as the stage at which the BTK has been assigned. All of these values populate a dictionary which is parsed by the modules `pandas` and `tabulator` to generate a "pretty" dataframe that can be sent via the `requests` module to the slack channel, see figure 1. 

![[images/mrbtk.png]]
Figure 1: A MrBTK slack post detailing the tickets that require a BTK being run, those being run and its assignee as well as those that have been completed and are waiting on post-BTK analysis.

BTK is a pipeline used in the identification of potential contamination. Based on the [BlobToolKit2](https://github.com/blobtoolkit/blobtoolkit) pipeline created by Richard Challis, the Sanger based implementation allows for a standarised and quick setup per genomic assembly. This speed is important, especially as DTOL scaled up to dozens of assebmlies per week, it was necessary to see what needed working on at a glance ranther than logging into JIRA and creating a query for this information.

##### Weekly-report
Also known as Miss Minutes, as it keeps an eye on the ins and outs of curation, the weekly reporting script was creating after a request by GRIT manager JMDW to enable a form of reporting of the weekly happenings in GRIT.

This bot generates a rather verbose output, see figure 2, detailing tickets new and old, as well as their status, date of status change, project as well as counts of tickets in the same projects. Due to the size of the output I have not as of yet updated it to use tabulator, shown in figure 1.

![[images/missminutes.png]]
Figure 2: A Miss Minutes slack post detailing the changes made to tickets over the previous week. Darwin is the main DTOL project, VGP and VGP+ are Vertebrate Genome Projects types and ASG is the Aquatic Symbiosis Genomics project.

##### Priority-report
Priority-report, also known as Rover, was developed to simply fetch all high-priority tickets due to a number of them "falling through the net" and spending a large amount of time waiting to be assigned. 

This results in a large amount of output much like Weekly-report, however due to the lack of segregration by project type it is possible to use `pandas` and `tabulator` to split the output in 15 entry chunks via a small code block that took advantage of splicing, see code block 2.

```
counter = 0
n = 15

for start in range(0, len(df), n):
    counter += 1
    prettier_df = tabulate_df(df[start:start+n])
    post_it(prettier_df, slack_add, counter)
```
Code block 2: A small function which uses splicing to split a large dataframe into 15 entry long segments and post them to slack numbered by the counter variable + 1, to result in **Report 1** rather than **Report 0**. The functions, tabulate_df and post_it, converts the pandas dataframe into a tabulate dataframe and posts the resulting tabulate dataframe to slack respectively.

This results in output that details the assembly id, ticket id, priority level, status and assignee (if any) attached to the ticket, see figure 3.

![[images/rover.png]]
![[images/rover2.png]]
Figure 4: An example of a slack report produced by Rover.

### Future Plans
Future plans include updating the weekly-reporting output in a format that is much cleaner such as that generated by BTK-announcer in figure 1. This will require a significant amount of refactoring that will result in at least one slack post per project type, more if there is more than 15 enteries per post due to limitations on the slack webhook API.


### Evidence

##### Conversation in setting up priority-report and weekly-report

**JMDW**
Mr_BTK..... can we do one for priority curations?

**DLBP**
Yeah sure, Just in general high priority cases that come in? Where would you like it posted?I'm also most of the way through one for the weekly reporting too, It has everything for what has been updated in the specified week. Also can have everything currently in Open and in Submission, but just by the sheer nature of Jira those can't be filtered by date otherwise you get some anomalies like we've seen before where they will disappear and reappear almost at will.

**JMDW**
ok thanks for manageing to pull everything!regarding the priority.. normal stuff tracks through at medium. would be good to get reports on High and Highest when in the system... track through Open, Decon, build and curation, post process, in submission.

Can you report who assigned to also?

**DLBP**
No problem, do you want it sent to a new channel or directly to you?

**JMDW**
can probably get pushed to the curation channel.  
Need people to see what is needing to be picked up quickly and if things are stuck at stages

Can you send the output here or to me to see before putting it in the channel

**DLBP**
added an integration to this channel: Rover

Hi Jo, the priority bot is ready to go live now. I can set it to default send a message to you and then you curl a command to get it to run for the curators if thats helpful?

**JMDW**
ok great! thanks

**Rover**
```
|-------- Rovers Priority Report for 2021-08-17 --------|  
|========================================|  
| RC-68      | Highest | Decontamination | James Torrance |  
| GRIT-469 | Highest | Decontamination | James Torrance |  
| GRIT-468 | Highest | Decontamination | James Torrance |  
| GRIT-464 | High       | Decontamination | James Torrance |  
| GRIT-463 | High       | Decontamination | James Torrance |  
| GRIT-447 | High       | Decontamination | James Torrance |  
| GRIT-446 | High       | Decontamination | James Torrance ||========================================|  
|--------------- END Report for 2021-08-17 -------------|
```

**DLBP**
Rover is set to go off at 9 and the curl command to send it off to the curators chat is:  

```
curl -X POST \
     -F token= {REMOVED} \
     -F ref=main \
     -F "variables[TOCURATORS]=CUR" \
	 [https://gitlab.internal.sanger.ac.uk/-{REMOVED}
```

The TOCURATORS variable can be set to JMDW, DLBP or CUR if you need it re-running or anything

There is also a reports channel for the weekly report, it spits out everything in the pipe at the minute + OPEN tickets which are status open and FIN which are submitted.It makes a pretty ugly and lengthy output which is why i've put it in its own channel

**JMDW**
Nice thanks