# Scheduled Interviews

## The scheduled interview object 

```json
{
  "id": 9128481,
  "start": {
    "date_time": "2014-03-26T22:15:00Z"
  },
  "end": {
    "date_time": "2014-03-26T22:30:00Z"
  },
  "location": "Big Conference Room",
  "status": "awaiting_feedback",
  "interview": {
    "id": 7001,
    "name": "Culture Fit"
  },
  "organizer": {
    "id": 2000,
    "name": "Jack Shepard"
  },
  "interviewers": [
    {
      "id": 4080,
      "name": "Kate Austen",
      "email": "kate.austen@example.com",
      "scorecard_id": 11274
    }
  ]
}
```

| Attribute | Description |
|-----------|-------------|
| id | The scheduled interview's unique identifier |

## List scheduled interviews

```shell
curl 'https://harvest.greenhouse.io/v1/applications/{id}/scheduled_interviews' \
-H "Authorization: Basic MGQwMzFkODIyN2VhZmE2MWRjMzc1YTZjMmUwNjdlMjQ6"
```

```json

[
  {
    "id": 9128481,
    "start": {
      "date_time": "2014-03-26T22:15:00Z"
    },
    "end": {
      "date_time": "2014-03-26T22:30:00Z"
    },
    "location": "Big Conference Room",
    "status": "awaiting_feedback",
    "interview": {
      "id": 7001,
      "name": "Culture Fit"
    },
    "organizer": {
      "id": 2000,
      "name": "Jack Shepard"
    },
    "interviewers": [
      {
        "id": 4080,
        "name": "Kate Austen",
        "email": "kate.austen@example.com",
        "scorecard_id": 11274
      }
    ]
  },
  {
    "id": 9128482,
    "start": {
      "date": "2014-07-08"
    },
    "end": {
      "date": "2014-07-09"
    },
    "location": "Small Conference Room",
    "interview": {
      "id": 7002,
      "name": "Whiteboarding Challenge"
    },
    "organizer": {
      "id": 2000,
      "name": "Jack Shepard"
    },
    "status": "complete",
    "interviewers": [
      {
        "id": 3412,
        "name": "Charlie Pace",
        "email": "youalleverybody@example.com",
        "scorecard_id": null
      }
    ]
  }
]
```

Interviews that have been scheduled for this application.

### HTTP Request

`GET https://harvest.greenhouse.io/v1/applications/{id}/scheduled_interviews`

### Query Parameters

Parameter | Description
--------- | -----------
id | ID of the application to retrieve