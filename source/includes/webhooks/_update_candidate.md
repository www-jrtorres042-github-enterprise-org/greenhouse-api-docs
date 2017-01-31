## Candidate/Prospect updated

```json
{
  "action": "update_candidate",
  "payload": {
    "candidate": {
      "id": 15696179,
      "first_name": "Ronald",
      "last_name": "Ronnie",
      "title": "Director of Strategic Janitorial Initiatives",
      "company": "Example",
      "created_at": "2016-08-23T17:51:27Z",
      "external_id": "946aa514658",
      "photo_url": null,
      "phone_numbers": [
        {
          "value": "911",
          "type": "mobile"
        }
      ],
      "email_addresses": [
        {
          "value": "123456email@email.com",
          "type": "work"
        }
      ],
      "addresses": [
        {
          "value": "99-99 5th Ave.\nNew York, NY 101-11",
          "type": "home"
        }
      ],
      "website_addresses": [
        {
          "value": "google.com",
          "type": "personal"
        }
      ],
      "social_media_addresses": [
        {
          "value": "@ronaldronnie99999"
        }
      ],
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
        "id": 169779,
        "email": "hank.hollandaise.169779@example.com",
        "name": "Hank Hollandaise"
      },
      "coordinator": {
        "id": 83637,
        "email": "sterling.kang.83637@example.com",
        "name": "Sterling Kang"
      },
      "attachments": [
        {
          "filename": "resumeA.pdf",
          "url": "https://prod-heroku.s3.amazonaws.com/...",
          "type": "resume"
        },
        {
          "filename": "resumeB.pdf",
          "url": "https://prod-heroku.s3.amazonaws.com/...",
          "type": "resume"
        }
      ],
      "tags": [
        "foo",
        "File Import"
      ],
      "custom_fields": {
        "current_salary": {
          "name": "Current Salary",
          "type": "short_text",
          "value": null
        },
        "desired_salary": {
          "name": "Desired Salary",
          "type": "short_text",
          "value": null
        }
      }
    }
  }
}
```

The Candidate or Prospect Updated event occurs when a candidate or prospect's standard field or custom field is updated.  For instance, an update to a candidate's first name would trigger this event.

See web hook [common attributes](#common-attributes).