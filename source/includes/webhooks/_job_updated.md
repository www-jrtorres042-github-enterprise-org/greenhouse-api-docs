## Job updated

```json
{
  "action": "job_updated",
  "payload": {
    "job": {
      "id": 100445,
      "name": "Assistant Store Manager, NYC",
      "requisition_id": null,
      "notes": "<p>Looking for the best!<\/p>",
      "job_post_id": 88010,
      "status": "open",
      "created_at": "2015-08-11T23:02:09Z",
      "opened_at": "2015-08-11T23:02:09Z",
      "closed_at": null,
      "departments": [
        {
          "id": 74,
          "name": "Guideshops"
        }
      ],
      "offices": [
        {
          "id": 104,
          "name": "New York",
          "location": "New York, NY"
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
        "bonus": {
          "name": "Bonus",
          "type": "short_text",
          "value": null
        },
        "employment_type": {
          "name": "Employment Type",
          "type": "single_select",
          "value": null
        },
        "options": {
          "name": "Options",
          "type": "short_text",
          "value": null
        },
        "salary": {
          "name": "Salary",
          "type": "short_text",
          "value": null
        }
      }
    }
  }
}
```

The Job Updated event is triggered any time one or more of the following fields are changed for a job: Internal Job Name, Department, Office, Level, Open Date, Status, Notes, Team and Responsibilities, and How To Sell This Job. Changes to custom job fields will not trigger this event.

| Attribute | Note |
|-----------|------|
| `hiring_team` | Field contains the Greenhouse users responsible for this job.  Each field contains the user's Greenhouse user id and the user's external employee id from the customer's system.  The employee id will be null if it has not been set in Greenhouse.
