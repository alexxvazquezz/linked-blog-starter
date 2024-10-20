
## Fleeting Notes
```dataview
LIST
FROM "FleetingNotes"
WHERE created_date = date({{title}}) 
```

## Tasks from Fleeting Notes
```dataview
TASK
FROM "FleetingNotes"
WHERE !completed
```

## My Notes
