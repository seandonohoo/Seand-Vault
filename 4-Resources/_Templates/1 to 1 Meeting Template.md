<%*
  let title = tp.file.title
  const participant = await tp.system.prompt("Participant");
  if (title.startsWith("Untitled")) {
    title = tp.date.now("YYYY-MM-DD") + " - " + participant
    await tp.file.rename(title);
  }
  const location = await tp.system.prompt(prompt_text="Webex or In Person", default_value="Webex")
  
  tR += "---"
%>
Created: <% tp.date.now("YYYY-MM-DD HH:mm") %>
Modified: <% tp.file.last_modified_date("YYYY-MM-DD HH:mm") %>
Path: <% tp.file.path(relative=false) %>
Alias: 
Tags: Meeting 1to1 <% participant %> todo
---

# <%* tR += title %>

```start-multi-column
ID: ID_q1fx
Number of Columns: 2
Border: disabled
Shadow: on
Largest Column: standard
```

# 🏠 Logistics
Date: <% tp.file.creation_date("YYYY-MM-DD") %>
Time: <% tp.file.cursor(1) %>
Location:  <% location %>

--- column-end ---

# 🗣️ Participants
- Sean
- <% participant %>

--- end-multi-column

# 📅 Agenda - Things I want to bring up
1. <% tp.file.cursor(3) %>

# 🗒️ Notes
<% tp.file.cursor(4) %>

# ✅ Action Items

## Mine
- [ ] <% tp.file.cursor(5) %>

## Others
- [ ] 

 <% tp.file.move("/2-Work Areas/Meetings/1to1/" + title) %>