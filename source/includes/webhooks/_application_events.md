# Application Events

## Application created

```json
{
  "action": "new_candidate_application",
  "payload": {
    "application": {
      "id": 265293,
      "rejected_at": null,
      "prospect": false,
      "prospect_detail": {
        "prospect_owner": null,
        "prospect_pool": null,
        "prospect_stage": null
      },
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

The New Candidate Application event occurs when a new application is created for a candidate.

See web hook [common attributes](#common-attributes).

## Application deleted

This web hook only fires when individual applications are destroyed.  This occurs when the Harvest API delete endpoint is used, when a candidate is removed from a specific job, or when two duplicate candidates on the same job are merged together.  This will not fire when a candidate is deleted.  A candidate being deleted implies all their applications have been deleted with them.

```json
{
  "action": "delete_application",
  "payload": {
    "application": {
        "id": 46194062,
        "candidate_id": 37031511,
        "job_id": 371417,
        "created_at": "2013-03-22T00:00:00Z",
        "source_id": 2,
        "candidate_rejection_reason_id": null,
        "rejection_note_id": 123,
        "rejected_at": "2014-04-22T01:00:00Z",
        "referrer_id": 158104,
        "prospect": false,
        "rejected_by_user_id": 158103
        }
    }
}
```

### Noteworthy response attributes

| Attribute | Note |
|------------|--------|
| `rejected_by_user_id` | The Greenhouse user who rejected this application, if the application is rejected. |

## Application updated

```json
{
  "action": "application_updated",
  "payload": {
    "application": {
      "id": 22202940,
      "rejected_at": null,
      "prospect": false,
      "prospect_detail": {
        "prospect_owner": null,
        "prospect_pool": null,
        "prospect_stage": null
      },
      "status": "active",
      "applied_at": "2015-12-03T06:31:26Z",
      "last_activity_at": "2015-12-03T06:31:26Z",
      "url": "https://app.greenhouse.io/people/13857579?application_id=22202940",
      "source": {
        "id":2,
        "name": "Jobs page on your website"
      },
      "credited_to": {
        "id": 3695,
        "email": "beauregard.blacksmith.3695@example.com",
        "name": "Beauregard Blacksmith"
      },
      "rejection_reason": null,
      "rejection_details": null,
      "current_stage": {
        "id": 711020,
        "name": "Application Review",
        "interviews": [
          {
            "id": 1063685,
            "name": "Application Review",
            "status": "collect_feedback",
            "interview_kit": {
              "url": "http://app.greenhouse.io/guides/1063859/people/13857579",
              "content": "",
              "questions":[]
            },
            "interviewers": []
          }
        ]
      },
      "custom_fields": {
        "custom_application_field": {
          "name": "Custom Application Field",
          "type": "short_text",
          "value": "Example"
        }
      },
      "candidate": {
        "id": 13857579,
        "first_name": "Hank",
        "last_name": "Von Diablo",
        "title": null,
        "company": null,
        "created_at": "2015-12-03T06:31:26Z",
        "external_id": null,
        "photo_url": "https://photo.com/photo.jpg",
        "url": "https://app.greenhouse.io/people/13857579",
        "phone_numbers": [
          {
            "value": "330-281-8004",
            "type": "other "
          }
        ],
        "email_addresses": [
          {
            "value": "hank.von diablo.13857579@example.com",
            "type": "personal"
          }
        ],
        "addresses": [],
        "website_addresses": [
          {
            "value": "http://www.example.com/",
            "type": "other"
          }
        ],
        "social_media_addresses": [
          {
            "value": "https://twitter.com/TheRock"
          }
        ],
        "educations": [],
        "recruiter":null,
        "coordinator": null,
        "attachments":[],
        "tags":[],
        "custom_fields": {
          "current_salary": {
            "name": "Current Salary",
            "type": "short_text",
            "value": null
          },
          "desired_salary": {
            "name": "Desired Salary",
            "type": "short_text",
            "value":null
          }
        }
      },
      "jobs": []
    }
  }
}


```

The Application Updated event occurs when an application is updated.

See web hook [common attributes](#common-attributes).

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
