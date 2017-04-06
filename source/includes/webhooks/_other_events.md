# Other Events

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
## Job Post deleted

This web hook fires when a job post is deleted.  This occurs when the delete link is clicked on a job post. Only job posts that are not live may be deleted. This will not fire if a job itself is deleted; a job being deleted implies all of its posts have been deleted with them.

```json
{
  "action": "job_post_deleted",
  "payload": {
    "job_post": {
      "id": 258341,
      "job_id": 284999,
      "title": "Software Engineer",
      "location": "Dallas",
      "content": "<p>A pretty interesting job post!</p>",
      "updated_at": "2017-01-19T20:01:53.146Z",
      "internal_content": null,
      "questions": [
        {
          "required": false,
          "private": false,
          "label": "LinkedIn Profile",
          "type": "input_text",
          "values": []
        },
        {
          "required": false,
          "private": false,
          "label": "Website",
          "type": "input_text",
          "values": []
        },
        {
          "required": false,
          "private": false,
          "label": "How did you hear about this job?",
          "type": "input_text",
          "values": []
        },
        {
          "required": true,
          "private": true,
          "label": "Are you a cool engineer?",
          "type": "multi_value_single_select",
          "values": [
            "Yes",
            "No",
            "As a cucumber"
          ]
        }
      ],
      "external": true,
      "internal": false,
      "live": false
    }
  }
}
```

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
## Offer deleted

This web hook only fires when offers are deleted from the Greenhouse system.  This only happens when the "Delete" link is clicked on an individual offer or when the anonymize candidate process is run with the "all_offer_versions" option selected.  This will not fire individually when an application is deleted.

```json
{
  "action": "offer_deleted",
  "payload": {
    "offer": {
      "id": 506406,
      "application_id": 46194062,
      "offering_user_id": 158104,
      "offer_status": "Created",
      "version": 1,
      "sent_on": "2013-03-22T00:00:00Z",
      "resolved_at": "2013-03-25T00:00:00Z",
      "notes": "These are notes on the offer.",
      "job_id": 371417
  }
}
```

### Noteworthy response attributes

| Attribute | Note |
|------------|--------|
| `offer_status` | One of Created, Accepted, Rejected, or Deprecated. |
| `version` | This is the version of the offer in Greenhouse.  New versions are triggered when certain fields are updated. |
| `sent_on` | When the offer was sent to the candidate |
| `resolved_at` | When this version was either accepted, rejected, or deprecated (a new version was made) |

## Scorecard deleted

This web hook only fires when individual scorecards are destroyed.  This occurs when the Harvest API delete endpoint is used, or when the delete scorecard link is used in the application. This will not fire when a candidate or application is deleted. A candidate being deleted implies all their scorecards have been deleted with them. An application being deleted does not cause scorecards to be deleted.

```json
{
  "action": "scorecard_deleted",
  "payload": {
    "scorecard": {
      "id": 6036088,
      "candidate_id": 29843272,
      "interviewed_at": "2016-12-28T17:00:00.000Z",
      "created_at": "2016-12-28T22:58:03.552Z",
      "updated_at": "2016-12-28T22:58:03.552Z",
      "scorecard_status": "complete"
    }
  }
}
```