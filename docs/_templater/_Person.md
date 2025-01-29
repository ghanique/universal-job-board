# <% tp.file.title %>

created:: <% tp.date.now("YYYY-MM-DDTHH:mm") %>  
modified:: <% tp.date.now("YYYY-MM-DDTHH:mm") %>  
author:: Guillaume Hanique

#person 

Links:

- works_for:: <% tp.file.cursor(1) %>
- worked_for::
- team::
- title::
- email:: 
- phone::
- dob:: 

## References

- -
<%*
await tp.file.move(`docs/People/${tp.file.title}`);
-%>
