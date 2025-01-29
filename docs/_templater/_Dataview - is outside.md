```dataview
TABLE WITHOUT ID file.link AS "[[<% tp.file.cursor(1) %>]]"
WHERE econtains(is, [[<% tp.file.cursor(2) %>]])
SORT file.name
```
