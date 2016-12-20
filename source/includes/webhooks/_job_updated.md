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

The Job Updated event is triggered any time a job is changed.
