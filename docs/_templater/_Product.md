# <% tp.file.title %>

created:: <% tp.date.now("YYYY-MM-DDTHH:mm") %>  
modified:: <% tp.date.now("YYYY-MM-DDTHH:mm") %>  
author:: Guillaume Hanique

#product

Links:

- product_of:: [[]]
- category:: <% tp.file.cursor(1) %>
- description::

## References

- 
<%*
await tp.file.move(`docs/Products/${tp.file.title}`);
-%>