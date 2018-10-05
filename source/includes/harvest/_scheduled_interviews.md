# Scheduled Interviews

## The scheduled interview object 

Interviews that have been scheduled for the specified application. Note that all-day interviews will have a start and end date with no specified time.

```json
{
  "id": 9128481,
  "application_id": 4684156,
  "external_event_id": "event123",
  "start": {
    "date_time": "2014-03-26T22:15:00.000Z"
  },
  "end": {
    "date_time": "2014-03-26T22:30:00.000Z"
  },
  "location": "Big Conference Room",
  "status": "awaiting_feedback",
  "created_at": "2016-02-10T14:31:51.019Z",
  "updated_at": "2016-05-23T20:43:11.679Z",
  "interview": {
    "id": 7001,
    "name": "Culture Fit"
  },
  "organizer": {
    "id": 2000,
    "first_name": "Jack",
    "last_name": "Shepard",
    "name": "Jack Shepard",
    "employee_id": "12345"
  },
  "interviewers": [
    {
      "id": 4080,
      "employee_id": "employee123",
      "name": "Kate Austen",
      "email": "kate.austen@example.com",
      "response_status": "needs_action",
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
| status | One of: `scheduled`, `awaiting_feedback`, `complete`
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
    "application_id": 4684156,
    "external_event_id": "event123",
    "start": {
      "date_time": "2014-03-26T22:15:00.000Z"
    },
    "end": {
      "date_time": "2014-03-26T22:30:00.000Z"
    },
    "location": "Big Conference Room",
    "status": "awaiting_feedback",
    "created_at": "2016-02-10T14:31:51.019Z",
    "updated_at": "2016-05-23T20:43:11.679Z",
    "interview": {
      "id": 7001,
      "name": "Culture Fit"
    },
    "organizer": {
      "id": 2000,
      "first_name": "Jack",
      "last_name": "Shepard",
      "name": "Jack Shepard",
      "employee_id": "12345"
    },
    "interviewers": [
      {
        "id": 4080,
        "employee_id": "employee123",
        "name": "Kate Austen",
        "email": "kate.austen@example.com",
        "response_status": "needs_action",
        "scorecard_id": 11274
      }
    ]
  },
  {
    "id": 9128482,
    "application_id": 432905,
    "external_event_id": "event456",
    "start": {
      "date": "2017-08-22"
    },
    "end": {
      "date": "2017-08-23"
    },
    "location": "Small Conference Room",
    "status": "complete",
    "interview": {
      "id": 7002,
      "name": "Whiteboarding Challenge"
    },
    "organizer": {
      "id": 2000,
      "first_name": "Jack",
      "last_name": "Shepard",
      "name": "Jack Shepard",
      "employee_id": "12345"
    },
    "interviewers": [
      {
        "id": 3412,
        "employee_id": "employee456",
        "name": "Charlie Pace",
        "email": "youalleverybody@example.com",
        "response_status": "needs_action",
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
| created_after | Only return scheduled interviews that were created at or after this timestamp.
| updated_before | Only return scheduled interviews that were updated before this timestamp.
| updated_after | Only return scheduled interviews that were updated at or after this timestamp.
| starts_before | Only return scheduled interviews scheduled to start before this timestamp.
| starts_after | Only return scheduled interviews scheduled to start at or after this timestamp.
| ends_before | Only return scheduled interviews scheduled to end before this timestamp.
| ends_after | Only return scheduled interviews scheduled to end at or after this timestamp.

## GET: List Interviews for Application

```shell
curl 'https://harvest.greenhouse.io/v1/applications/{id}/scheduled_interviews'
-H "Authorization: Basic MGQwMzFkODIyN2VhZmE2MWRjMzc1YTZjMmUwNjdlMjQ6"
```

```json
[
  {
    "id": 9128481,
    "application_id": 4684156,
    "external_event_id": "event123",
    "start": {
      "date_time": "2014-03-26T22:15:00.000Z"
    },
    "end": {
      "date_time": "2014-03-26T22:30:00.000Z"
    },
    "location": "Big Conference Room",
    "status": "awaiting_feedback",
    "created_at": "2016-02-10T14:31:51.019Z",
    "updated_at": "2016-05-23T20:43:11.679Z",
    "interview": {
      "id": 7001,
      "name": "Culture Fit"
    },
    "organizer": {
      "id": 2000,
      "first_name": "Jack",
      "last_name": "Shepard",
      "name": "Jack Shepard",
      "employee_id": "12345"
    },
    "interviewers": [
      {
        "id": 4080,
        "employee_id": "employee123",
        "name": "Kate Austen",
        "email": "kate.austen@example.com",
        "response_status": "needs_action",
        "scorecard_id": 11274
      }
    ]
  },
  {
    "id": 9128482,
    "application_id": 4684156,
    "external_event_id": "event456",
    "start": {
      "date": "2017-08-22"
    },
    "end": {
      "date": "2017-08-23"
    },
    "location": "Small Conference Room",
    "status": "complete",
    "interview": {
      "id": 7002,
      "name": "Whiteboarding Challenge"
    },
    "organizer": {
      "id": 2000,
      "first_name": "Jack",
      "last_name": "Shepard",
      "name": "Jack Shepard",
      "employee_id": "12345"
    },
    "interviewers": [
      {
        "id": 3412,
        "employee_id": "employee456",
        "name": "Charlie Pace",
        "email": "youalleverybody@example.com",
        "response_status": "needs_action",
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
| created_after | Return only scheduled interviews that were created at or after this timestamp. Timestamp must be in in [ISO-8601] (#general-considerations) format.
| updated_before | Return only scheduled interviews that were updated before this timestamp. Timestamp must be in in [ISO-8601] (#general-considerations) format.
| updated_after | Return only scheduled interviews that were updated at or after this timestamp. Timestamp must be in in [ISO-8601] (#general-considerations) format.

<br>
[See noteworthy response attributes.] (#the-scheduled-interview-object)

## GET: Retrieve Interview

```shell
curl 'https://harvest.greenhouse.io/v1/scheduled_interviews/{id}'
-H "Authorization: Basic MGQwMzFkODIyN2VhZmE2MWRjMzc1YTZjMmUwNjdlMjQ6"
```

```json
{
  "id": 9128481,
  "application_id": 4684156,
  "external_event_id": "event123",
  "start": {
    "date_time": "2014-03-26T22:15:00.000Z"
  },
  "end": {
    "date_time": "2014-03-26T22:30:00.000Z"
  },
  "location": "Big Conference Room",
  "status": "awaiting_feedback",
  "created_at": "2016-02-10T14:31:51.019Z",
  "updated_at": "2016-05-23T20:43:11.679Z",
  "interview": {
    "id": 7001,
    "name": "Culture Fit"
  },
  "organizer": {
    "id": 2000,
    "first_name": "Jack",
    "last_name": "Shepard",
    "name": "Jack Shepard",
    "employee_id": "12345"
  },
  "interviewers": [
    {
      "id": 4080,
      "employee_id": "employee123",
      "name": "Kate Austen",
      "email": "kate.austen@example.com",
      "response_status": "needs_action",
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
