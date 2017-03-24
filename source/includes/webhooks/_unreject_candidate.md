## Candidate/Prospect unrejected

```json
{
  "action": "unreject_candidate",
  "payload": {
    "application": {
      "id": 265293,
      "rejected_at": null,
      "prospect": false,
      "status": "active",
      "applied_at": "2013-03-22T00:00:00Z",
      "last_activity_at": "2015-02-11T15:50:41Z",
      "url": "https://app.greenhouse.io/people/265788?application_id=265293",
      "source": {
        "id": 27,
        "public_name": "LinkedIn"
      },
      "credited_to": null,
      "rejection_reason": null,
      "rejection_details": null,
      "current_stage": {
        "id": 2708728,
        "name": "Offer",
        "interviews": []
      },
      "custom_fields": {
        "custom_application_field": {
          "name": "Custom Application Field",
          "type": "short_text",
          "value": "Example123"
        }
      },
      "candidate": {
        "id": 265788,
        "first_name": "Hector",
        "last_name": "Porter",
        "title": null,
        "company": null,
        "created_at": "2013-10-04T01:24:48Z",
        "external_id": null,
        "photo_url": "www.example.com/photo.png",
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
        "educations": [
          {
            "school_name": "Harvard University",
            "degree": "Bachelor's Degree",
            "discipline": "Information Systems",
            "start_date": "01/01/2012",
            "end_date": "01/01/2016"
          }
        ],
        "recruiter": null,
        "coordinator": null,
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
              "id": 9099,
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

The Unreject Candidate event occurs when a prospect or candidate is unrejected.

See web hook [common attributes](#common-attributes).