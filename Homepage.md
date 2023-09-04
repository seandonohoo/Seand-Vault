---
created_date: 2023-09-04
updated_date: 2023-09-04
---
# Home

<details>
<summary> Keyboard Shortcuts</summary>

</details>

##  Handovers
```dataview
table from "Meetings/Handover"
where file.name != "Homepage"
sort file.mtime desc
limit 2
```

## Recently Opened Networking NK
```dataview
table from "Networking NK"
where file.name != "Homepage"
sort file.mtime desc
limit 10
```

## Recent Code Snip It's
```dataview
table from "2-Work Areas/Code Snip It"
where file.name != "Homepage"
sort file.mtime desc
limit 10
```