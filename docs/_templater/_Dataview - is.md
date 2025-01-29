```dataview
TABLE WITHOUT ID
  file.link AS "[[<% tp.file.cursor(1) %>]]",
  description AS "Description"
FROM [[]]
WHERE econtains(is, this.file.link)
SORT file.name
```
