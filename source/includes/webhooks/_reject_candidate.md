## Candidate/Prospect rejected

```json
{
  "action": "reject_candidate",
  "payload": {
    "application": {
      "id": 265293,
      "rejected_at": "2015-02-11T15:50:41Z",
      "prospect": false,
      "status": "rejected",
      "applied_at": "2013-03-22T00:00:00Z",
      "last_activity_at": "2015-02-11T15:50:41Z",
      "source": {
        "id": 27,
        "public_name": "LinkedIn"
      },
      "credited_to": null,
      "rejection_reason": {
        "id": 14,
        "name": "Too Junior",
        "type": {
          "id": 3,
          "name": "Wrong skill set"
        }
      },
      "candidate": {
        "id": 265788,
        "created_at": "2013-10-04T01:24:48Z",
        "first_name": "Hector",
        "last_name": "Porter",
        "title": null,
        "company": null,
        "phone_numbers": [
          {
            "value": "330-281-8004",
            "type": "home"
          }
        ],
        "email_addresses": [
          {
            "value": "hector.porter.265788@example.com",
            "type": "personal"
          }
        ],
        "addresses": [],
        "website_addresses": [],
        "social_media_addresses": [],
        "recruiter": null,
        "coordinator": null,
        "photo_url": "www.example.com/photo.png",
        "attachments": [
          {
            "filename": "resume.pdf",
            "url": "https://prod-heroku.s3.amazonaws.com/...",
            "type": "resume"
          }
        ],
        "tags": [
          "Imported"
        ],
        "custom_fields": {
          "favorite_color": {
            "name": "Favorite Color",
            "type": "short_text",
            "value": "Blue"
          }
        }
      },
      "job": {
        "id": 3485,
        "name": "3D Digital Rendering Artist",
        "requisition_id": null,
        "notes": "Looking for the best!",
        "status": "open",
        "created_at": "2013-10-02T22:59:29Z",
        "opened_at": "2015-01-23T00:25:04Z",
        "closed_at": null,
        "departments": [
          {
            "id": 237,
            "name": "Community"
          }
        ],
        "offices": [
          {
            "id": 54,
            "name": "New York",
            "location": "New York, NY"
          }
        ],
        "custom_fields": {
          "employment_type": {
            "name": "Employment Type",
            "type": "single_select",
            "value": "Full Time"
          }
        }
      }
    }
  }
}
```

The Reject Candidate event occurs when a prospect or candidate is rejected for a position.

See web hook [common attributes](#common-attributes).