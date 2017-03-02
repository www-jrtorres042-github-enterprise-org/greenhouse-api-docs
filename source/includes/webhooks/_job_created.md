## Job created

```json
{
  "action": "job_created",
  "payload": {
    "job": {
      "id": 371417,
      "name": "Software Engineer",
      "requisition_id": null,
      "notes": "Looking for the best!",
      "job_post_id": 2154,
      "status": "open",
      "created_at": "2016-10-20T18:16:32Z",
      "opened_at": "2016-10-20T18:16:32Z",
      "closed_at": null,
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
  }
}
```

The Job Created event is triggered when a new job is created from scratch or copied from another job.

| Attribute | Note |
|-----------|------|
| `hiring_team` | Field contains the Greenhouse users responsible for this job.  Each field contains the user's Greenhouse user id and the user's external employee id from the customer's system.  The employee id will be null if it has not been set in Greenhouse.
