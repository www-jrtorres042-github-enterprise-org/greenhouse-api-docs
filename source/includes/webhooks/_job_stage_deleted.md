## Job Stage deleted

This web hook only fires when interview stages on a job are removed.  This occurs when the remove stage link is used in the Job Setup section of the application. This will not fire when a job is deleted. A job being deleted implies all of its stages have been deleted with them.

```json
{
  "action": "hiring_plan_interview_stage_deleted",
  "payload": {
    "hiring_plan_interview_stage": {
      "id": 1001340,
      "hiring_plan_id": 140288,
      "created_at": "2015-11-10T16:56:13.567Z",
      "updated_at": "2016-08-29T19:25:00.844Z",
      "name": "Google Hangout",
      "active": true
    }
  }
}
```
