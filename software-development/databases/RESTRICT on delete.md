---
aliases:
  - RESTRICT
---

Parent: [[+ databases]]

- prevents deletion of a referenced row when:
  - a parent is deleted
  - a child exists that has a reference to the parent
- usually the default foreign key relationship on DBMSes
- evaluated _before_ deletion of a row, as opposed to [[PROTECT on delete|PROTECT]]
  where the evaluation occurs _during_ the deletion
