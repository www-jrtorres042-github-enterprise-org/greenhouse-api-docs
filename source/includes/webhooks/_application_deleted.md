## Application deleted

This web hook only fires when individual applications are destroyed.  This occurs when the Harvest API delete endpoint is used, when a candidate is removed from a specific job, or when two duplicate candidates on the same job are merged together.  This will not fire when a candidate is deleted.  A candidate being deleted implies all their applications have been deleted with them.

```json
{
  "action": "delete_application",
  "payload": {
    "id": 1234,
    "candidate_id": 2345,
    "job_id": 3456,
    "rejected_by_user_id": 1234,
    "created_at": "2013-03-22T00:00:00Z",
    "rejection_note_id": 123,
    "rejected_at": 2014-04-22T01:00:00Z",
    "referrer_id": 1234,
    "prospect": false
}

### Noteworthy response attributes

| Attribute | Note |
|------------|--------|
| `rejected_by_user_id` | The Greenhouse user who rejected this application, if the application is rejected. |