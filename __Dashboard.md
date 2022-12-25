---
subject : main dashboard
category: personal
---
>Links: [[personal]]

## College Notes
```dataview
TABLE subject, tags, status
FROM ""
WHERE category="lecture-notes"
```

---
## Other shit
```dataview
TABLE subject
FROM ""
WHERE category="MOC" AND file.name!="MOC template"
```

