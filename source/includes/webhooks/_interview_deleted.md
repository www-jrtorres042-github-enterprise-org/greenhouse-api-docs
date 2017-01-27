## Interview deleted

This web hook fires when a scheduled interview is cancelled or the interview is deleted directly. This web hook will not fire if an interview is deleted because a candidate, application, or hiring plan is deleted.

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
