## Prospect created

```json
{
  "action": "new_prospect_application",
  "payload": {
    "application": {
      "id": 979554,
      "rejected_at": null,
      "prospect": true,
      "status": "active",
      "applied_at": "2014-12-02T23:10:16Z",
      "last_activity_at": "2014-12-02T23:10:16Z",
      "current_stage": null,
      "source": {
        "id": 13,
        "public_name": "Referral"
      },
      "credited_to": {
        "id": 2622,
        "email": "carl.buddha.2622@example.com",
        "name": "Carl Buddha"
      },
      "rejection_reason": null,
      "candidate": {
        "id": 968190,
        "created_at": "2014-12-02T23:10:16Z",
        "first_name": "Trisha",
        "last_name": "Troy",
        "title": null,
        "company": null,
        "phone_numbers": [
          {
            "value": "123456",
            "type": "other"
          }
        ],
        "email_addresses": [
          {
            "value": "t.troy@example.com",
            "type": "personal"
          }
        ],
        "addresses": [],
        "website_addresses": [],
        "social_media_addresses": [],
        "recruiter": {
          "id": 3128,
          "email": "alicia.flopple.3128@example.com",
          "name": "Alicia Flopple"
        },
        "coordinator": null,
        "photo_url": "https://prod-heroku.s3.amazonaws.com/...",
        "attachments": [
          {
            "filename": "resume.pdf",
            "url": "https://prod-heroku.s3.amazonaws.com/...",
            "type": "resume"
          }
        ],
        "tags": [
          "Import from Previous ATS"
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
        "id": 7347,
        "name": "Summer Internship",
        "requisition_id": "",
        "notes": "Looking for the best!",
        "status": "open",
        "created_at": "2014-01-06T22:18:15Z",
        "opened_at": "2014-01-06T22:18:15Z",
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

The New Prospect Application event occurs when a new prospect application is created.

See web hook [common attributes](#common-attributes).