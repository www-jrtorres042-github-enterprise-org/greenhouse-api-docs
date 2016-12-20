## Offer deleted

This web hook only fires when offers are deleted from the Greenhouse system.  This only happens when the "Delete" link is clicked on an individual offer or when the anonymize candidate process is run with the "all_offer_versions" option selected.  This will not fire individually when an application is deleted.

```json
{
  "action": "offer_deleted",
  "payload": {
    "id": 1234,
    "application_id": 2344,
    "offer_status": "Created",
    "version": 1,
    "sent_on": "2013-03-22T00:00:00Z",
    "resolved_at": "2013-03-25T00:00:00Z",
    "notes": "These are notes on the offer.",
    "job_id": 4567
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