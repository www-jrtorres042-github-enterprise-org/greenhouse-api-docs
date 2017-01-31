## Department deleted

This web hook fires when departments are deleted from the Greenhouse system from the Configure &raquo; Organization screen. This only happens when the "Remove" button is clicked after clicking the "X" next to an office name.

```json
{
  "action": "department_deleted",
  "payload": {
    "department": {
      "id": 106,
      "name": "Creative",
      "child_ids": [
        23328
      ],
      "parent_id": 5
    }
  }
}
```

### Noteworthy response attributes

| Attribute | Note |
|------------|--------|
| `id` | The Greenhouse id for the department |
| `name` | The name of the department deleted |
| `child_ids` | Any former child department ids (this includes all descendants); will be [] if empty |
| `parent_id` | The department's parent department id; will be null if empty |
