---
<%*
let new_title = await tp.system.prompt("Title ")
tp.file.rename(new_title)
-%>
project: <% new_title %>
date_started: <% tp.date.now("WW@DD-mm-yyyy") %>
status: Waiting on Time
tags: ["TDB", "personal"]
---

# <% tp.file.title %>
Repo::
Description:: 

## What is it for?
<%*
let description = await tp.system.prompt("Description of Project")
-%>

<% description %>

Project_type:: []

---
## What will it be used for?


---
## What do i need to do this? What cost?


---
## What do i need to learn? 


---
## Resources