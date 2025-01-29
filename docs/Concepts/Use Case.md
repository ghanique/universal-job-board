---
aliases:
  - Use Cases
---

# Use Case

created:: 2025-01-28T21:39  
modified:: 2025-01-28T21:39  
author:: Guillaume Hanique

#concept

Links:

- category:: [[(Design)]]
- description:: Detailed descriptions of how **Actors** interact with the **System** to achieve a specific **Goal**.

## JobBoard Use Cases

```dataview
TABLE WITHOUT ID
  id AS "ID",
  file.link AS "[[Use Case]]",
  description AS "Description"
FROM [[]]
WHERE econtains(is, this.file.link) AND !econtains(file.path, "_templater")
SORT file.name
```

## Why Are Use Cases Important?

- Help define **functional requirements** clearly.
- Improve **communication** between business and IT teams.
- Serve as a **basis for testing** scenarios.
- Ensure **user expectations** are met.

## Key Components of a Use Case

1. **Actors:** Users or systems that interact with the system.
2. **Preconditions:** Conditions that must be true before the use case begins.
3. **Flow of Events:** Step-by-step interactions between the actor and the system.
    - **Main Flow (Happy Path):** The expected successful scenario.
    - **Alternative Flows:** Variations of the main flow.
    - **Exception Flows:** What happens when something goes wrong.
4. **Postconditions:** The state of the system after the use case is completed.
## References

- -
