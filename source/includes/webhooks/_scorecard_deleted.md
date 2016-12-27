## Scorecard deleted

This web hook only fires when individual scorecards are destroyed.  This occurs when the Harvest API delete endpoint is used, or when the delete scorecard link is used in the application. This will not fire when a candidate or application is deleted. A candidate or application being deleted implies all their scorecards have been deleted with them.

```json
{
  "action": "scorecard_deleted",
  "payload": {
    "scorecard": {
      "id": 6036082,
      "interview_kit_id": 3113678,
      "person_id": 29843264,
      "interviewer_id": 844,
      "interviewed_at": "2016-12-27T17:00:00.000Z",
      "notes": "test",
      "created_at": "2016-12-27T15:39:22.440Z",
      "updated_at": "2016-12-27T15:39:22.440Z",
      "submitter_id": 844,
      "candidate_rating_id": 2,
      "note_id": 170950993,
      "private_notes": "",
      "status": 1,
      "original_scorecard_id": null,
      "total_focus_attributes": 0,
      "focus_attributes_completed": 0,
      "public_notes": ""
    }
  }
}
```
