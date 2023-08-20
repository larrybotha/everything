```dataview
LIST rows.file.link
WHERE 
  file.path != this.file.path
  AND file.folder = this.file.folder
GROUP BY author
```
