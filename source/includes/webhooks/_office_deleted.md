## Office deleted

This web hook fires when offices are deleted from the Greenhouse system from the Configure &raquo; Organization screen. This only happens when the "Remove" button is clicked after clicking the "X" next to an office name. This will not fire individually when an organization is deleted.

```json
{
  "action": "office_deleted",
  "payload": {
    "office": {
      "id": 16492,
      "name": "New York",
      "location": {
        "name": "New York, NY"
      },
      "child_ids": [
        123,
        456
      ],
      "parent_id": 789
    }
  }
}
```

### Noteworthy response attributes

| Attribute | Note |
|------------|--------|
| `id` | The Greenhouse id for the office |
| `name` | The name of the office deleted |
| `location` | The location for the office |
| `child_ids` | Any former child office ids |
| `parent_id` | The office's parent office id |
