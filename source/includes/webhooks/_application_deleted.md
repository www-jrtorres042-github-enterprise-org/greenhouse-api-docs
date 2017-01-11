## Application deleted

This web hook only fires when individual applications are destroyed.  This occurs when the Harvest API delete endpoint is used, when a candidate is removed from a specific job, or when two duplicate candidates on the same job are merged together.  This will not fire when a candidate is deleted.  A candidate being deleted implies all their applications have been deleted with them.

```json
{
  "action": "delete_application",
  "payload": {
    "application": {
        "id": 46194062,
        "candidate_id": 37031511,
        "job_id": 371417,
        "created_at": "2013-03-22T00:00:00Z",
        "source_id": 2,
        "candidate_rejection_reason_id": null,
        "rejection_note_id": 123,
        "rejected_at": "2014-04-22T01:00:00Z",
        "referrer_id": 158104,
        "prospect": false,
        "rejected_by_user_id": 158103
        }
    }
}
```

### Noteworthy response attributes

| Attribute | Note |
|------------|--------|
| `rejected_by_user_id` | The Greenhouse user who rejected this application, if the application is rejected. |
