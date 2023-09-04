<%*
  let title = tp.file.title
  const network_device = await tp.system.suggester(["Arista", "Cisco", "Fortinet", "Palo", "Avocent", "Other"], ["Arista", "Cisco", "Fortinet", "Palo", "Avocent", "Other"],placeholder="Other")
  const desc = await tp.system.prompt(prompt_text="Enter a short description",default_value="Change Me")
  if (title.startsWith("Untitled")) {
    title = network_device + " - " + desc
    await tp.file.rename(title);
  }
  
  tR += "---"
%>
Created: <% tp.date.now("YYYY-MM-DD HH:mm") %>
Modified: <% tp.file.last_modified_date("YYYY-MM-DD HH:mm") %>
Path: <% tp.file.path(relative=false) %>
Tags: NK <% network_device %>
---
# <%* tR += title %>

## Prerequisites 
* 
## Description
<% tp.file.cursor(1) %>
#### Purpose
## Steps
1. 

<% tp.file.move("/2-Work Areas/Networking NK/How Tos/" + title) %>