## Candidate unhired

```json
{
  "action": "unhire_candidate",
  "payload": {
    "application": {
      "id": 265293,
      "rejected_at": null,
      "prospect": false,
      "status": "active",
      "applied_at": "2013-03-22T00:00:00Z",
      "last_activity_at": "2015-03-18T20:28:09Z",
      "url": "https://app.greenhouse.io/people/265788?application_id=265293",
      "source": {
        "id": 27,
        "public_name": "LinkedIn"
      },
      "credited_to": null,
      "rejection_reason": null,
      "rejection_details": null,
      "current_stage": {
        "id": 678901,
        "name": "Application Review",
        "interviews": [
          {
            "id": 989099,
            "name":"Application Review",
            "status": "collect_feedback",
            "interview_kit": {
              "url": "http://app.greenhouse.io/guides/67656/people/265788",
              "content": "",
              "questions": []
            },
            "interviewers": []
          }
        ]
      },
      "custom_fields": {
        "custom_application_field": {
          "name": "Custom Application Field",
          "type": "short_text",
          "value": null
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
        "photo_url": "https://prod-heroku.s3.amazonaws.com/...",
        "url": "https://app.greenhouse.io/people/265788",
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
              "id": 14501,
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

This web hook only fires when the "Unhire" button is clicked in Greenhouse.  This button is only available on the candidate profile page after a candidate has been hired.

See web hook [common attributes](#common-attributes).