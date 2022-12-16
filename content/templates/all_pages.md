---
<%*
let new_title = await tp.system.prompt("Title ")
tp.file.rename(new_title)
-%>
title: <%new_title%>
date: <% tp.date.now("WW@DD-MM-yyyy")%>
tags: ["TDB"]
type: []
---

GitHub::

Contribution::

Working with::

Topic:: 

KSBs:: 

---
<%*
let description = await tp.system.prompt("Description of Project")
-%>
Description:: <%description%>

### The Project

### My Contribution

### Future Plans

### Evidence
