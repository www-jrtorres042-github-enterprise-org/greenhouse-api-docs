## Candidate deleted

This web hook will fire when a candidate or prospect is deleted from Greenhouse.  This occurs when the Harvest delete candidate methods are used, when a candidate is merged into another candidate, when a candidate is deleted in the application, and once for each candidate in a bulk delete operation.  Deleting a candidate will cause other deletes within Greenhouse but we will not fire an individual web hook for those deletions.  In the case of the applications that this delete causes, we will include an array of those Application IDs that will be removed from Greenhouse.

```json
{
  "action": "delete_candidate",
  "payload": {
    "id": 1234,
    "first_name": "Jack",
    "last_name": "Sparrow",
    "company": "Pirate Shipping",
    "title": "Captain",
    "created_at": "2013-03-22T00:00:00Z",
    "headline": "Eager to find a new commission",
    "is_private": false,
    "recruiter_user_id": 123,
    "coordinator_user_id": 456,
    "can_email": false,
    "application_ids": [123,678,987]
}
```

### Noteworthy response attributes

| Attribute | Note |
|------------|--------|
| `is_private` | True or false; if this candidate has been marked private in Greenhouse. |
| `recruiter_user_id` | The Greenhouse user_id of this candidate's recruiter |
| `coordinator_user_id` | The Greenhouse user_id of this candidate's coordinator |
| `can_email` | True or false; if this candidate can be e-mailed. |
| `application_ids` | This is an array containing the Greenhouse application ids that will be deleted as a consequence of this candidate being deleted |