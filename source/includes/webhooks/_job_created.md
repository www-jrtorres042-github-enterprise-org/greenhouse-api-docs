## Job created

```json
{
  "action": "job_created",
  "payload": {
    "job": {
      "id": 20,
      "name": "Software Engineer",
      "created_at": "2016-10-20T18:16:32Z",
      "opened_at": "2016-10-20T18:16:32Z",
      "closed_at": null,
      "requisition_id": null,
      "notes": "Looking for the best!",
      "job_post_id": 2154,
      "status": "open",
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
          "location": {
            "name": "New York, NY"
          }
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
  }
}
```

The Job Created event is triggered when a new job is created from scratch or copied from another job.

### Noteworthy attributes

See web hook [common attributes](#common-attributes).