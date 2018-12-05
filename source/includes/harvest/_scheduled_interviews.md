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

## Post: Create Interview

```shell
curl -X POST 'https://harvest.greenhouse.io/v1/scheduled_interviews/{id}'
-H "Content-Type: application/json"
-H "On-Behalf-Of: {greenhouse user ID}"
-H "Authorization: Basic MGQwMzFkODIyN2VhZmE2MWRjMzc1YTZjMmUwNjdlMjQ6"
```

> The above command takes a JSON request, structured like this:

```json
{
	"application_id": 102717462,
	"interview_id": 8055374,
	"organizer": {
		"user_id": 102361
	},
	"interviewers": [
		{ "user_id": 102361, "response_status": "accepted" },
		{ "email": "lucius.barbarossa.46444@example.com", "response_status": "declined" }
	],
	"start": "2018-12-12T13:15:00Z",
	"end": "2018-12-12T14:15:00Z",
	"external_event_id": "external_event_id_1",
	"location": "Big Conference Room"
}
```
> The above returns a JSON response, structured like this:

```json
{
  "id": 109170954,
  "application_id": 102717457,
  "external_event_id": "external_event_id_1",
  "start": {
    "date_time": "2018-12-12T13:15:00.000Z"
  },
  "end": {
    "date_time": "2018-12-12T14:15:00.000Z"
  },
  "location": "Big Conference Room",
  "status": "scheduled",
  "created_at": "2018-10-17T19:22:07.302Z",
  "updated_at": "2018-12-03T20:45:14.320Z",
  "interview": {
    "id": 8055374,
    "name": "Executive Interview"
  },
  "organizer": {
    "id": 102361,
    "first_name": "Champ",
    "last_name": "Telluride",
    "name": "Champ Telluride",
    "employee_id": null
  },
  "interviewers": [
    {
      "id": 102361,
      "employee_id": null,
      "name": "Champ Telluride",
      "email": "champ.telluride.102361@example.com",
      "response_status": "accepted",
      "scorecard_id": null
    },
    {
      "id": 46444,
      "employee_id": "AAA1",
      "name": "Lucius Barbarossa",
      "email": "lucius.barbarossa.46444@example.com",
      "response_status": "declined",
      "scorecard_id": null
    }
  ]
}
```

Create a new Scheduled Interview. 

[See noteworthy response attributes.] (#the-scheduled-interview-object)

### HTTP Request

`POST https://harvest.greenhouse.io/v1/scheduled_interviews`

### Headers

Header | Description
--------- | -----------
On-Behalf-Of | ID of the user issuing this request. Required for auditing purposes.

### JSON Body Parameters

Parameter | Required | Type | Description
--------- | ----------- | ----------- | -----------
organizer | Yes | user | The organizer of the event. Can be specified by user_id, email, or employee_id.
interviewers[] | Yes | interviewer | Array of interviewers. Each must specify a user by user_id, email, or employee_id. Each must include a response status (one of needs_action, declined, tentative, or accepted).
start | Yes | string | A datetime specifying when the interview starts. Must be provided in ISO-8601 (#general-considerations) format (e.g. 2018-11-05T13:12:14Z).
end | Yes | string | A datetime specifying when the interview ends. Must be provided in ISO-8601 (#general-considerations) format (e.g. 2018-11-05T13:12:14Z).
external_event_id | Yes | string | A unique identifer for this interview.
location| No | string | A textual description of the location of the interview.

<aside class="notice">
    There may be a delay between when Greenhouse receives the POST: Create Scheduled Interview request and when Greenhouse creates the full Scheduled Interview record, which will result in a truncated API response. The truncated response body will contain the id of the newly Scheduled Interview. You can retrieve the full Scheduled Interview record by requesting the Scheduled Interview ID with the GET: Scheduled Interview endpoint. If you receive a 404 error from the GET: Scheduled Interview endpoint, this indicates that the full Scheduled Interview record is still not available. Until the Scheduled Interview record has been made fully-available in the API, please continue to request the record until the API returns a successful response. Our recommendation is to perform this check every 30 seconds until the data becomes available.
</aside>

## Patch: Update Interview

```shell
curl -X PATCH 'https://harvest.greenhouse.io/v1/scheduled_interviews/{id}'
-H "Content-Type: application/json"
-H "On-Behalf-Of: {greenhouse user ID}"
-H "Authorization: Basic MGQwMzFkODIyN2VhZmE2MWRjMzc1YTZjMmUwNjdlMjQ6"
```

> The above command takes a JSON request, structured like this:

```json
{
	"organizer": {
		"user_id": 102361
	},
	"interviewers": [
		{ "user_id": 102361, "response_status": "needs_action" },
		{ "email": "lucius.barbarossa.46444@example.com", "response_status": "declined" }
	],
	"start": "2018-11-12T13:15:00Z",
	"end": "2018-11-12T14:15:00Z",
	"external_event_id": "external_event_id_0",
	"location": "Dunder Mifflin, Scranton"
}
```
> The above returns a JSON response, structured like this:

```json
{
  "id": 109170954,
  "application_id": 102717457,
  "external_event_id": "external_event_id_0",
  "start": {
    "date_time": "2018-12-12T13:15:00.000Z"
  },
  "end": {
    "date_time": "2018-12-12T14:15:00.000Z"
  },
  "location": "Big Conference Room",
  "status": "scheduled",
  "created_at": "2018-10-17T19:22:07.302Z",
  "updated_at": "2018-12-03T20:45:14.320Z",
  "interview": {
    "id": 8055374,
    "name": "Executive Interview"
  },
  "organizer": {
    "id": 102361,
    "first_name": "Champ",
    "last_name": "Telluride",
    "name": "Champ Telluride",
    "employee_id": null
  },
  "interviewers": [
    {
      "id": 102361,
      "employee_id": null,
      "name": "Champ Telluride",
      "email": "champ.telluride.102361@example.com",
      "response_status": "accepted",
      "scorecard_id": null
    },
    {
      "id": 46444,
      "employee_id": "AAA1",
      "name": "Lucius Barbarossa",
      "email": "lucius.barbarossa.46444@example.com",
      "response_status": "declined",
      "scorecard_id": null
    }
  ]
}
```

Update a Scheduled Interview. Note that only Scheduled Interviews created through harvest can be updated. Additionally, you can 
only update Scheduled Interviews in the following statues: Scheduled, Awaiting Feedback.

[See noteworthy response attributes.] (#the-scheduled-interview-object)

### HTTP Request

`PATCH https://harvest.greenhouse.io/v1/scheduled_interviews/{id}`

### Headers

Header | Description
--------- | -----------
On-Behalf-Of | ID of the user issuing this request. Required for auditing purposes.

### JSON Body Parameters

Parameter | Required | Type | Description
--------- | ----------- | ----------- | -----------
organizer | No | user | The organizer of the event. Can be specified by user_id, email, or employee_id.
interviewers[] | No | interviewer | Array of interviewers. Each must specify a user by user_id, email, or employee_id. Each must include a response status (one of needs_action, declined, tentative, or accepted).
start | No | string | A datetime specifying when the interview starts. Must be provided in ISO-8601 (#general-considerations) format (e.g. 2018-11-05T13:12:14Z).
end | No | string | A datetime specifying when the interview ends. Must be provided in ISO-8601 (#general-considerations) format (e.g. 2018-11-05T13:12:14Z).
external_event_id | No | string | A unique identifer for this interview.
location| No | string | A textual description of the location of the interview.

## Delete: Remove Interview

```shell
curl -X DELETE 'https://harvest.greenhouse.io/v1/scheduled_interviews/{id}'
-H "On-Behalf-Of: {greenhouse user ID}"
-H "Authorization: Basic MGQwMzFkODIyN2VhZmE2MWRjMzc1YTZjMmUwNjdlMjQ6"
```

> The above returns a JSON response, structured like this:

```json
{
  "message": "Interview 109170954 has been deleted."
}
```

Delete a Scheduled Interview by `id`. Note that only Scheduled Interviews created through harvest can be deleted. Additionally, you can 
only delete Scheduled Interviews in the following statues: Scheduled, Awaiting Feedback.

### HTTP Request

`DELETE https://harvest.greenhouse.io/v1/scheduled_interviews/{id}`

### Headers

Header | Description
--------- | -----------
On-Behalf-Of | ID of the user issuing this request. Required for auditing purposes.

<br>