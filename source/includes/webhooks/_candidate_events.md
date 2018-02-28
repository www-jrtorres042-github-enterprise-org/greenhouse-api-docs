# Candidate Events

## Candidate deleted

This web hook will fire when a candidate or prospect is deleted from Greenhouse.  This occurs when the Harvest delete candidate methods are used, when a candidate is merged into another candidate, when a candidate is deleted in the application, and once for each candidate in a bulk delete operation.  Deleting a candidate will cause other deletes within Greenhouse but we will not fire an individual web hook for those deletions.  In the case of the applications that this delete causes, we will include an array of those Application IDs that will be removed from Greenhouse.

```json
{
  "action": "delete_candidate",
  "payload": {
    "person": {
        "id": 37031511,
        "first_name": "Jack",
        "last_name": "Sparrow",
        "company": "Pirate Shipping",
        "title": "Captain",
        "created_at": "2013-03-22T00:00:00Z",
        "headline": "Eager to find a new commission",
        "is_private": false,
        "recruiter_user_id": 123,
        "coordinator_user_id": 456,
        "can_email": false,
        "deleted_application_ids": [
                46196263,
                46196258
            ]
        }
    }
}
```

### Noteworthy response attributes

| Attribute | Note |
|------------|--------|
| `is_private` | True or false; if this candidate has been marked private in Greenhouse. |
| `recruiter_user_id` | The Greenhouse user_id of this candidate's recruiter |
| `coordinator_user_id` | The Greenhouse user_id of this candidate's coordinator |
| `can_email` | True or false; if this candidate can be e-mailed. |
| `application_ids` | This is an array containing the Greenhouse application IDs that will be deleted as a consequence of this candidate being deleted |

## Candidate hired

```json
{
  "action": "hire_candidate",
  "payload": {
    "application": {
      "id": 46194062,
      "opening": {
        "opening_id": "1234-56"
      },
      "credited_to": {
        "id": 158104,
        "email": "bob_johnson1@localhost.com",
        "name": "Robert Johnson"
      },
      "source": {
        "id": 25,
        "public_name": "Monster"
      },
      "url": "https://app.greenhouse.io/people/35897443?application_id=46194062",
      "candidate": {
        "id": 35897443,
        "first_name": "Johnny",
        "last_name": "Smith",
        "title": "Previous Title",
        "external_id": 00000,
        "url": "https://app.greenhouse.io/people/35897443",
        "phone_numbers": [
          {
            "value": "518-555-1212",
            "type": "work"
          },
          {
            "value": "212-555-1212",
            "type": "home"
          }
        ],
        "email_addresses": [
          {
            "value": "personal@example.com",
            "type": "personal"
          },
          {
            "value": "work@example.com",
            "type": "work"
          }
        ],
        "addresses": [
          {
            "value": "455 Broadway New York, NY 10280",
            "type": "home"
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
        "employments": [
          {
            "company_name": "Greenhouse",
            "title": "Engineer",
            "start_date": "01/01/2012",
            "end_date": "01/01/2016"
          }
        ],
        "recruiter": {
          "id": 55,
          "email": "bob_johnson@localhost.com",
          "name": "Bob Johnson"
        },
        "coordinator": {
          "id": 56,
          "email": "bob_johnson_approver1@localhost.com",
          "name": "Robert J Approver"
        },
        "attachments": [
          {
            "filename": "resume.pdf",
            "url": "https://prod-heroku.s3.amazonaws.com/...",
            "type": "resume"
          }
        ],
        "custom_fields": {
          "desired_level": {
            "name": "Desired Level",
            "type": "short_text",
            "value": "Senior"
          },
          "favorite_programming_language": {
            "name": "Favorite Programming Language",
            "type": "short_text",
            "value": "Rails"
          }
        }
      },
      "job": {
        "id": 323753,
        "name": "Developer",
        "open_date": "2014-11-20T22:49:14Z",
        "close_date": "2014-11-25T22:49:14Z",
        "requisition_id": null,
        "departments": [
          {
            "id": 7,
            "name": "Technology"
          }
        ],
        "offices": [
          {
            "id": 13,
            "name": "New York City",
            "location": "New York, NY"
          },
          {
            "id": 14,
            "name": "St. Louis",
            "location": null
          }
        ],
        "custom_fields": {
          "approved": {
            "name": "Approved",
            "type": "boolean",
            "value": true
          },
          "employment_type": {
            "name": "Employment Type",
            "type": "single_select",
            "value": "Full-time"
          },
          "salary_range": {
            "name": "SalaryRange",
            "type": "currency_range",
            "value": {
              "unit": "USD",
              "min_value": "10000.0",
              "max_value": "20000.0"
            }
          }
        }
      },
      "jobs": [
        {
          "id": 323753,
          "name": "Developer",
          "requisition_id": null,
          "opened_at": "2014-11-20T22:49:14Z",
          "closed_at": "2014-11-25T22:49:14Z",
          "departments": [
            {
              "id": 7,
              "name": "Technology"
            }
          ],
          "offices": [
            {
              "id": 13,
              "name": "New York City",
              "location": "New York, NY"
            },
            {
              "id": 14,
              "name": "St. Louis",
              "location": null
            }
          ],
          "custom_fields": {
            "approved": {
              "name": "Approved",
              "type": "boolean",
              "value": true
            },
            "employment_type": {
              "name": "Employment Type",
              "type": "single_select",
              "value": "Full-time"
            },
            "salary_range": {
              "name": "SalaryRange",
              "type": "currency_range",
              "value": {
                "unit": "USD",
                "min_value": "10000.0",
                "max_value": "20000.0"
              }
            }
          }
        }
      ],
      "custom_fields": {
        "custom_application_field": {
          "name": "Custom Application Field",
          "type": "short_text",
          "value": "Example123"
        }
      },
      "offer": {
        "id": 506409,
        "version": 2,
        "created_at": "2014-11-20T22:49:14Z",
        "sent_at": "2014-11-10",
        "resolved_at": "2014-11-20T22:49:14Z",
        "starts_at": "2015-01-23",
        "custom_fields": {
          "salary": {
            "name": "Salary",
            "type": "currency",
            "value": {
              "amount": 80000,
              "unit": "USD"
            }
          },
          "seasons": {
            "name": "Seasons",
            "type": "multi_select",
            "value": [
              "Season 1",
              "Season 2"
            ]
          }
        }
      }
    }
  }
}
```

The Hire Candidate event occurs when an offer is accepted. This is triggered by clicking the "Accept Offer" button on the candidate's Private tab.

### Noteworthy attributes

See web hook [common attributes](#common-attributes).

| Attribute | Note |
|-----------|------|
| `application.offer.id` | Unique Greenhouse identifier of the offer. Information not included in the web hook can be retrieved via [Harvest API - GET Offers](/harvest.html#offers)
| `application.offer.created_at` | Date when this offer was drafted.
| `application.offer.sent_on` | Date when this offer was sent to the candidate.
| `application.offer.resolved_at` | Date the offer was accepted.
| `application.offer.starts_at` | The candidate's start date. Expected format is YYYY-MM-DD
| `application.job` | Deprecated. Use `application.jobs[]` instead
| `application.job.close_date` | Deprecated. Use `application.jobs[].closed_at` instead.
| `application.job.open_date` | Deprecated. Use `application.jobs[].opened_at` instead.

## Candidate merged

This web hook will fire when a candidate or prospect is merged with another candidate.  This process should fire for regular manual merges and auto-merges.  It will also fire per candidate for a bulk merge.  This web hook supersedes the candidate deleted web hook.  If both candidate deleted and candidate merged are configured on your site, only the candidate merged web hook will fire when candidate records are removed via merge.  If a candidate deleted web hook is configured but candidate merged is not, then the candidate deleted web hook will fire when a candidate record is deleted via merge.  The payload for a candidate merged web hook matches the payload for candidate deleted except it contains the ID of the winning candidate record.

```json
{
  "action": "merge_candidate",
  "payload": {
    "person": {
        "id": 37031511,
        "first_name": "Jack",
        "last_name": "Sparrow",
        "company": "Pirate Shipping",
        "title": "Captain",
        "created_at": "2013-03-22T00:00:00Z",
        "headline": "Eager to find a new commission",
        "is_private": false,
        "recruiter_user_id": 123,
        "coordinator_user_id": 456,
        "can_email": false,
        "new_candidate_id": 457456
    }
  }
}
```

### Noteworthy response attributes

| Attribute | Note |
|------------|--------|
| `deleted_application_ids` | In many merge cases, this section will be blank, as applications will have been merged into the new candidate. |
| `new_candidate_id` | The ID of the candidate to whom this candidate has been merged |

## Candidate stage change

```json
{
  "action": "candidate_stage_change",
  "payload": {
    "application": {
      "id": 265277,
      "rejected_at": null,
      "prospect": false,
      "status": "active",
      "applied_at": "2013-03-22T00:00:00Z",
      "last_activity_at": "2015-02-09T16:38:36Z",
      "url": "https://app.greenhouse.io/people/265772?application_id= 265277",
      "source": {
        "id": 31,
        "name": "Agency"
      },
      "credited_to": {
        "id": 15,
        "email": "ada@example.com",
        "name": "Ada Lacey"
      },
      "rejection_reason": null,
      "rejection_details": null,
      "current_stage": {
        "id": 71416,
        "name": "Assessment",
        "interviews": [
          {
            "id": 113101,
            "name": "Assessment",
            "status": "to_be_scheduled",
            "interview_kit": {
              "url": "https://app.greenhouse.io/guides/113153/people/265772",
              "content": "Assess their skills",
              "questions": []
            },
            "interviewers": [
              {
                "id": 2622,
                "display_name": "Carl Buddha",
                "status": "tentative"
              }
            ]
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
        "id": 265772,
        "first_name": "Giuseppe",
        "last_name": "Hurley",
        "title": "Great Person",
        "company": null,
        "created_at": "2013-10-04T01:24:44Z",
        "external_id": "241b399ce4b0fd1c84e5528d",
        "photo_url": "https://prod-heroku.s3.amazonaws.com/...",
        "url": "https://app.greenhouse.io/people/265772",
        "phone_numbers": [
          {
            "value": "330-281-8004",
            "type": "home"
          }
        ],
        "email_addresses": [
          {
            "value": "giuseppe.hurley@example.com",
            "type": "personal"
          }
        ],
        "addresses": [
          {
            "value": "123 Fake St.",
            "type": "home"
          }
        ],
        "website_addresses": [
          {
            "value": "ghurley.example.com",
            "type": "personal"
          }
        ],
        "social_media_addresses": [
          {
            "value": "linkedin.example.com/ghurley"
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
        "employments": [
          {
            "company_name": "Greenhouse",
            "title": "Engineer",
            "start_date": "01/01/2012",
            "end_date": "01/01/2016"
          }
        ],
        "recruiter": {
          "id": 3128,
          "email": "alicia.flopple.3128@example.com",
          "name": "Alicia Flopple"
        },
        "coordinator": {
          "id": 3128,
          "email": "alicia.flopple.3128@example.com",
          "name": "Alicia Flopple"
        },
        "attachments": [
          {
            "filename": "resume.pdf",
            "url": "https://prod-heroku.s3.amazonaws.com/...",
            "type": "resume"
          },
          {
            "filename": "cover_letter.pdf",
            "url": "https://prod-heroku.s3.amazonaws.com/...",
            "type": "cover_letter"
          },
          {
            "filename": "portfolio.pdf",
            "url": "https://prod-heroku.s3.amazonaws.com/...",
            "type": "attachment"
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
          "id": 3485,
          "name": "Designer",
          "requisition_id": null,
          "notes": "Digital and print",
          "job_post_id": 553282,
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

### Noteworthy response attributes

See web hook [common attributes](#common-attributes).

| Attribute | Note |
|-----------|------|
| `application.current_stage.interviews[].interviewers.status` | One of: `needs_action`, `declined`, `tentative`, `accepted`
| `application.current_stage.interviews[].status` | One of: `to_be_scheduled`, `scheduled`, `awaiting_feedback`, `complete`, `skipped`, `collect_feedback`, `to_be_sent`, `sent`, `received`

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
        "employments": [
          {
            "company_name": "Greenhouse",
            "title": "Engineer",
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
      "url": "https://app.greenhouse.io/people/265788?application_id=265293",
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
      "rejection_details": {
        "custom_fields": {
          "custom_rejection_question_field": {
            "name": "Custom Rejection Question Field",
            "type": "short_text",
            "value": "Example"
          }
        }
      },
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
        "employments": [
          {
            "company_name": "Greenhouse",
            "title": "Engineer",
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

The Reject Candidate event occurs when a prospect or candidate is rejected for a position.

See web hook [common attributes](#common-attributes).

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
        "employments": [
          {
            "company_name": "Greenhouse",
            "title": "Engineer",
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
      "url": "https://app.greenhouse.io/people/15696179",
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
      "employments": [
        {
          "company_name": "Greenhouse",
          "title": "Engineer",
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
        "employments": [
          {
            "company_name": "Greenhouse",
            "title": "Engineer",
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
