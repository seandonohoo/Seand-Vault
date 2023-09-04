<%*
  let title = tp.file.title
  const l1l2 = await tp.system.prompt(prompt_text="L1 or L2")
  if (title.startsWith("Untitled")) {
    title = tp.date.now("YYYY-MM-DD") + " - " + l1l2 + " Handover"
    await tp.file.rename(title);
  }
  const location = await tp.system.prompt(prompt_text="Webex or In Person", default_value="Webex")

  
  tR += "---"
%>
Created: <% tp.date.now("YYYY-MM-DD HH:mm") %>
Modified: <% tp.file.last_modified_date("YYYY-MM-DD HH:mm") %>
Path: <% tp.file.path(relative=false) %>
Alias: 
Tags: Handover <% l1l2 %> todo
---

# <%* tR += title %>


# 🏠 Logistics
Date: <% tp.file.creation_date("YYYY-MM-DD") %>
Time: <% tp.date.now("HH:mm") %>
Location:  <% location %>

# 📅 Things I want to bring up
1. <% tp.file.cursor(1) %>

#  ‼️ Problems
- Circuits
	- Flaps
	- [ ] <% tp.file.cursor(2) %>
	- Outage
	- [ ] ⏫ <% tp.file.cursor(3) %>
- Hardware
	- [ ] 🔼 <% tp.file.cursor(4) %> 

# ✅ Follow up

## Mine
- [ ] 🔼 <% tp.file.cursor(5) %> 

 <% tp.file.move("/2-Work Areas/Meetings/Handover/" + title) %>