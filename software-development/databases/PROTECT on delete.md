---
aliases:
  - PROTECT
---

Parent: [[+ databases]]

- appears to be non-standard, but may be implemented via an ORM for databases
  that do not support it
- prevents deletion of a referenced row when by raising an error:
  - a parent is deleted
  - a child exists that has a reference to the parent
- run during deletion of a row, as opposed to [[RESTRICT on delete|RESTRICT]] which runs _before_
  deletion begins
