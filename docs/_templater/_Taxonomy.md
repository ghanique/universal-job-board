<%*
const title = tp.file.title.replace(/\(?(.+?)\)?$/gm, '$1');
const filename = `(${title})`;
-%>
---
aliases:
  - <% title %>
  - <% title %>s
---

# <% title %>

created:: <% tp.date.now("YYYY-MM-DDTHH:mm") %>  
modified:: <% tp.date.now("YYYY-MM-DDTHH:mm") %>  
author:: Guillaume Hanique

#taxonomy

Links:

- parent:: 

## Taxonomy

### Parent categories

```dataview
TABLE WITHOUT ID p.file.link AS "Parent categories"
WHERE file.name = this.file.name
FLATTEN parent AS p
SORT file.name
```

### Subcategories

```dataview
TABLE WITHOUT ID file.link AS "Subcategories"
FROM [[]]
WHERE econtains(parent, this.file.link)
SORT file.name
```

### Documents

```dataview
TABLE WITHOUT ID file.link AS "[[<% tp.file.title %>]]"
FROM [[]]
WHERE econtains(category, this.file.link)
SORT file.name
```

## References

- -
<%*
await tp.file.move(`docs/_metadata/${filename}`);
-%>
