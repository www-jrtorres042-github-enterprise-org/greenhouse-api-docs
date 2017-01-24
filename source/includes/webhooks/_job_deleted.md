## Job deleted

This web hook only fires when jobs are deleted from the Greenhouse system. This only happens when a job is closed, and then the "Delete" button is clicked from the Job Dashboard.

```json
{
  "action": "job_deleted",
  "payload": {
    "job": {
      "id": 209256,
      "name": "Project Manager"
    }
  }
}
```

### Noteworthy response attributes

| Attribute | Note |
|------------|--------|
| `id` | The internal Greenhouse Job id |
| `name` | The name of the job that was deleted |
