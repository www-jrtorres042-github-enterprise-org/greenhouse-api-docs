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
      "url": "https://app.greenhouse.io/people/968190?application_id=979554",
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
      "rejection_details": null,
      "current_stage": null,
      "custom_fields": {
        "custom_application_field": {
          "name": "Custom Application Field",
          "type": "short_text",
          "value": null
        }
      },
      "candidate": {
        "id": 968190,
        "first_name": "Trisha",
        "last_name": "Troy",
        "title": null,
        "company": null,
        "created_at": "2014-12-02T23:10:16Z",
        "external_id": null,
        "photo_url": "https://prod-heroku.s3.amazonaws.com/...",
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
        "educations": [
          {
            "school_name": "Harvard University",
            "degree": "Bachelor's Degree",
            "discipline": "Information Systems",
            "start_date": "01/01/2012",
            "end_date": "01/01/2016"
          }
        ],
        "recruiter": {
          "id": 3128,
          "email": "alicia.flopple.3128@example.com",
          "name": "Alicia Flopple"
        },
        "coordinator": null,
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
      "jobs": [
        {
          "id": 371417,
          "name": "Designer",
          "requisition_id": null,
          "notes": "Digital and print",
          "job_post_id": 54321,
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
      ]
    }
  }
}
```

The New Prospect Application event occurs when a new prospect application is created.

See web hook [common attributes](#common-attributes).