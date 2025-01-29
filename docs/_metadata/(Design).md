---
aliases:
  - Design
  - Designs
---

# Design

created:: 2025-01-28T21:40  
modified:: 2025-01-28T21:40  
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
TABLE WITHOUT ID file.link AS "[[Design]]"
FROM [[]]
WHERE econtains(category, this.file.link)
SORT file.name
```

## References

- -
