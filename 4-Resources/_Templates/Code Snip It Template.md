<%*
  let title = tp.file.title
  const language = await tp.system.suggester(["Ansible", "Bash", "Go", "Python", "SQL", "Yaml", "Other"], ["Ansible", "Bash", "Go", "Python", "SQL", "Yaml", "Other"])
  const desc = await tp.system.prompt(prompt_text="Enter a short description",default_value="Change Me")
  if (title.startsWith("Untitled")) {
    title = tp.date.now("YYYY-MM-DD") + " - " + language
    await tp.file.rename(title);
  }

  
  tR += "---"
%>
Created: <% tp.date.now("YYYY-MM-DD HH:mm") %>
Modified: <% tp.file.last_modified_date("YYYY-MM-DD HH:mm") %>
Path: <% tp.file.path(relative=false) %>
Tags: SnipIT <% language %>
---
# <%* tR += title %>

## Code SnipIt
Description: <% desc %>

```<% language %>
<% tp.system.clipboard() %>
```

 <% tp.file.move("/2-Work Areas/Code Snip It/" + title) %>