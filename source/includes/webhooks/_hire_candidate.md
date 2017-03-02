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
        "hiring_team": {
          "hiring_managers": [
  	    {"user_id": 1234, "employee_id": "abc-123"}
	  ],
	  "sourcers": [],
	  "recruiters": [
	    {"user_id": 2345, "employee_id": null},
	    {"user_id": 3456, "employee_id": "abc-234"}
	  ],
 	  "coordinators": [],
        },
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
          "hiring_team": {
            "hiring_managers": [
	      {"user_id": 1234, "employee_id": "abc-123"}
	    ],
	    "sourcers": [],
	    "recruiters": [
	      {"user_id": 2345, "employee_id": null},
	      {"user_id": 3456, "employee_id": "abc-234"}
	    ],
	    "coordinators": [],
          },
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
| `job.hiring_team` | Field contains the Greenhouse users responsible for this job.  Each field contains the user's Greenhouse user id and the user's external employee id from the customer's system.  The employee id will be null if it has not been set in Greenhouse.