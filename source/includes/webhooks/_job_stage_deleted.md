## Job Stage deleted

This web hook only fires when interview stages on a job are removed.  This occurs when the remove stage link is used in the Job Setup section of the application. This will not fire when a job is deleted. A job being deleted implies all of its stages have been deleted with them.

```json
{
  "action": "job_interview_stage_deleted",
  "payload": {
    "job_interview_stage": {
      "id": 430608,
      "job_id": 60453,
      "created_at": "2015-03-11T13:25:25.313Z",
      "updated_at": "2016-08-16T09:29:33.650Z",
      "name": "Phone Screen",
      "active": true
    }
  }
}
```
