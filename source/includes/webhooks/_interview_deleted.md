## Interview deleted

This web hook fires when an interview record in the Greenhouse database is deleted. This is not the same as when an interview is deleted in the application, because sometimes interview records are cleared and repurposed. This web hook will not fire if an interview is deleted because a candidate, application, or hiring plan is deleted.

```json
{
  "action": "interview_deleted",
  "payload": {
    "interview": {
      "id": 31087450
    }
  }
}
```
