# Scheduled Interviews

## The scheduled interview object 

Interviews that have been scheduled for the specified application.

```json
{
  "id": 9128481,
  "application_id": 4684156,
  "start": {
    "date_time": "2014-03-26T22:15:00.000Z"
  },
  "end": {
    "date_time": "2014-03-26T22:30:00.000Z"
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

### Noteworthy attributes

| Attribute | Description |
|-----------|-------------|
| id | The scheduled interview's unique identifier |
| start | A date_time value if this interview has a precise start time, or a date value if this is an all-day event.
| end | A date_time value if this interview has a precise start time, or a date value if this is an all-day event.
| location | The location of the interview.
| status | One of: `to_be_scheduled`, `scheduled`, `awaiting_feedback`, `complete`, `skipped`, `collect_feedback`, `to_be_sent`, `sent`, `received`.
| organizer | The [user](#users) who is the organizer for this interview
| interviewers | An array containing the [users](#users) who have interviews with this candidate, including, if applicable, the ID of the scorecard they completed.

## GET: List Interviews

```shell
curl 'https://harvest.greenhouse.io/v1/scheduled_interviews'
-H "Authorization: Basic MGQwMzFkODIyN2VhZmE2MWRjMzc1YTZjMmUwNjdlMjQ6"
```

```json

[
  {
    "id": 9128481,
    "application_id": 432904,
    "start": {
      "date_time": "2014-03-26T22:15:00.000Z"
    },
    "end": {
      "date_time": "2014-03-26T22:30:00.000Z"
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
    "application_id": 432905,
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

List all of an organization's scheduled interviews.

### HTTP Request

`GET https://harvest.greenhouse.io/v1/scheduled_interviews`

### Optional querystring Parameters

Timestamps must be in in [ISO-8601](#general-considerations) format.

Parameter | Description
--------- | -----------
| per_page | Return up to this number of objects per response. Must be an integer between 1 and 500. Defaults to 100.
| page | A cursor for use in pagination.  Returns the n-th chunk of `per_page` objects.
| created_before | Only return scheduled interviews that were created before this timestamp.
| created_after | Only return scheduled interviews that were created after this timestamp.
| updated_before | Only return scheduled interviews that were updated before this timestamp.
| updated_after | Only return scheduled interviews that were updated after this timestamp.
| starts_before | Only return scheduled interviews scheduled to start before this timestamp.
| starts_after | Only return scheduled interviews scheduled to start after this timestamp.
| ends_before | Only return scheduled interviews scheduled to end before this timestamp.
| ends_after | Only return scheduled interviews scheduled to end after this timestamp.

## GET: List Interviews for Application

```shell
curl 'https://harvest.greenhouse.io/v1/applications/{id}/scheduled_interviews'
-H "Authorization: Basic MGQwMzFkODIyN2VhZmE2MWRjMzc1YTZjMmUwNjdlMjQ6"
```

```json
[
  {
    "id": 9128481,
    "application_id": 432904,
    "start": {
      "date_time": "2014-03-26T22:15:00.000Z"
    },
    "end": {
      "date_time": "2014-03-26T22:30:00.000Z"
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
    "application_id": 432904,
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

### Querystring Parameters

Parameter | Description
--------- | -----------
| id | ID of the application to retrieve
| per_page | Return up to this number of objects per response. Must be an integer between 1 and 500. Defaults to 100.
| page | A cursor for use in pagination.  Returns the n-th chunk of `per_page` objects.
| created_before | Return only scheduled interviews that were created before this timestamp. Timestamp must be in in [ISO-8601] (#general-considerations) format.
| created_after | Return only scheduled interviews that were created after this timestamp. Timestamp must be in in [ISO-8601] (#general-considerations) format.
| updated_before | Return only scheduled interviews that were updated before this timestamp. Timestamp must be in in [ISO-8601] (#general-considerations) format.
| updated_after | Return only scheduled interviews that were updated after this timestamp. Timestamp must be in in [ISO-8601] (#general-considerations) format.

<br>
[See noteworthy response attributes.] (#the-scheduled-interview-object)

## GET: Retrieve Interview

```shell
curl 'https://harvest.greenhouse.io/v1/scheduled_interviews/123'
-H "Authorization: Basic MGQwMzFkODIyN2VhZmE2MWRjMzc1YTZjMmUwNjdlMjQ6"
```

```json
{
  "id": 9128481,
  "application_id": 4684156,
  "start": {
    "date_time": "2014-03-26T22:15:00.000Z"
  },
  "end": {
    "date_time": "2014-03-26T22:30:00.000Z"
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

Retrieve an interview by its ID.

### HTTP Request

`GET https://harvest.greenhouse.io/v1/scheduled_interviews/{id}`

### URL Parameters

Parameter | Description
--------- | -----------
id | The ID of the scheduled interview to retrieve
