# Applications

## The application object

```json
{
  "id": 4341,
  "candidate_id": 23123,
  "prospect": true,
  "applied_at": "2014-03-26T18:03:45Z",
  "last_activity_at": "2014-03-27T16:12:02Z",
  "source": null,
  "credited_to": {
    "id": 4080,
    "name": "Kate Austen"
  },
  "rejected_at": null,
  "rejection_reason": null,
  "jobs": [],
  "status": "active",
  "current_stage": null,
  "answers": []
}
```

Applications tie candidates to jobs. There are 2 kinds of applications: candidates and prospects. Candidate applications always have exactly 1 job. Prospect applications can have 0 or more jobs.

### Attributes

| Attribute | Data type | Description |
| --------- | --------- | ----------- |
| id | integer | Application object ID |



### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
per_page | 10 | optional
page | 1 | optional


<aside class="success">
Remember — a happy kitten is an authenticated kitten!
</aside>






## GET All Applications

```shell
curl 'https://harvest.greenhouse.io/v1/applications' \
  -H "Authorization: Basic MGQwMzFkODIyN2VhZmE2MWRjMzc1YTZjMmUwNjdlMjQ6"
```

```json
[
  {
    "id": 4341,
    "candidate_id": 23123,
    "prospect": true,
    "applied_at": "2014-03-26T18:03:45Z",
    "last_activity_at": "2014-03-27T16:12:02Z",
    "source": null,
    "credited_to": {
      "id": 4080,
      "name": "Kate Austen"
    },
    "rejected_at": null,
    "rejection_reason": null,
    "jobs": [],
    "status": "active",
    "current_stage": null,
    "answers": []
  },
  {...}
]
```

Retreive your organization's applications.

### HTTP Request

`GET https://harvest.greenhouse.io/v1/applications`





## GET Application

```shell
curl 'https://harvest.greenhouse.io/v1/applications/4341' \
  -H "Authorization: Basic MGQwMzFkODIyN2VhZmE2MWRjMzc1YTZjMmUwNjdlMjQ6"
```

```json
{
  "id": 4341,
  "candidate_id": 23123,
  "prospect": true,
  "applied_at": "2014-03-26T18:03:45Z",
  "last_activity_at": "2014-03-27T16:12:02Z",
  "source": null,
  "credited_to": {
    "id": 4080,
    "name": "Kate Austen"
  },
  "rejected_at": null,
  "rejection_reason": null,
  "jobs": [],
  "status": "active",
  "current_stage": null,
  "answers": []
}
```

Retrieve an application by its `id`.

### HTTP Request

`GET https://harvest.greenhouse.io/v1/applications/{id}`

### Query Parameters

Parameter | Description
--------- | -----------
id | ID of the application to retrieve




## GET All Offers

```shell
curl 'https://harvest.greenhouse.io/v1/offers/{id}' \
-H "Authorization: Basic MGQwMzFkODIyN2VhZmE2MWRjMzc1YTZjMmUwNjdlMjQ6"
```

```json
[
{
"id": 4949,
"version": 1,
"application_id": 1234,
"created_at": "2014-02-13T22:30:58Z",
"resolved_at": null,
"sent_at": "sent_on",
"status": "deprecated",
"custom_fields": {
"employment_type": "Contractor",
"favorite_station": "The Swan",
"best_seasons": null,
"start_date": null,
"willing_to_negotiate": null,
"salary": null,
"notes": null
}
},
{
"id": 5318,
"version": 1,
"application_id": 2345,
"created_at": "2014-05-12T18:02:34Z",
"resolved_at": "2014-05-12T20:52:35Z",
"sent_at": "sent_on",
"status": "accepted",
"custom_fields": {
"employment_type": "Part-Time",
"favorite_station": "The Looking Glass",
"best_seasons": ["Season 1", "Season 2"],
"start_date": "2014-05-01",
"willing_to_negotiate": true,
"salary": {
"value": 42000,
"currency": "EUR"
},
"notes": "Very excited to start working with this candidate"
}
}
]
```

All offers made by your organization ordered by application `id`.

### HTTP Request

`GET https://harvest.greenhouse.io/v1/offers/{id}`

### Query Parameters

Parameter | Description
--------- | -----------
id | ID of the application to retrieve




## GET Offers for Applications

```shell
curl 'https://harvest.greenhouse.io/v1/applications/{id}/offers(/current_offer)' \
-H "Authorization: Basic MGQwMzFkODIyN2VhZmE2MWRjMzc1YTZjMmUwNjdlMjQ6"
```

```json
[
{
"id": 4949,
"version": 1,
"application_id": 1234,
"created_at": "2014-02-13T22:30:58Z",
"resolved_at": null,
"sent_at": "sent_on",
"status": "deprecated",
"custom_fields": {
"employment_type": "Contractor",
"favorite_station": "The Swan",
"best_seasons": null,
"start_date": null,
"willing_to_negotiate": null,
"salary": null,
"notes": null
}
},
{
"id": 5318,
"version": 2,
"application_id": 1234,
"created_at": "2014-05-12T18:02:34Z",
"resolved_at": "2014-05-12T20:52:35Z",
"sent_at": "sent_on",
"status": "accepted",
"custom_fields": {
"employment_type": "Part-Time",
"favorite_station": "The Looking Glass",
"best_seasons": ["Season 1", "Season 2"],
"start_date": "2014-05-01",
"willing_to_negotiate": true,
"salary": {
"value": 42000,
"currency": "EUR"
},
"notes": "Very excited to start working with this candidate"
}
}
]
```

The offers associated with this application. Greenhouse keeps offer history has updates are made over time. To fetch only the most recent offer, append `/current_offer` to the url.

### HTTP Request

`GET https://harvest.greenhouse.io/v1/applications/{id}/offers(/current_offer)`

### Query Parameters

Parameter | Description
--------- | -----------
id | ID of the application to retrieve




## GET Scorecards for Applications

```shell
curl 'https://harvest.greenhouse.io/v1/applications/{id}/scorecards' \
-H "Authorization: Basic MGQwMzFkODIyN2VhZmE2MWRjMzc1YTZjMmUwNjdlMjQ6"
```

```json
[
{
"id": 123,
"interview": "Application Review",
"interviewed_at": "2014-03-26T04:00:00Z",
"candidate_id": 1234,
"submitted_by": {
"id": 4080,
"name": "Kate Austen"
},
"submitted_at": "2014-03-26T21:59:51Z",
"overall_recommendation": "yes",
"attributes": [
{
"name": "Communication",
"type": "Skills",
"note": "What a great communicator!",
"rating": "yes"
},
{
"name": "Adaptable",
"type": "Skills",
"note": null,
"rating": "yes"
},
{
"name": "Relationship Manager",
"type": "Skills",
"note": null,
"rating": "mixed"
},
{
"name": "Project Management",
"type": "Skills",
"note": null,
"rating": "mixed"
},
{
"name": "Problem Solver",
"type": "Skills",
"note": null,
"rating": "no"
},
{
"name": "Analytical",
"type": "Skills",
"note": null,
"rating": "definitely_not"
}
],
"ratings": {
"definitely_not": [
"Analytical"
],
"no": [
"Problem Solver"
],
"mixed": [
"Relationship Manager",
"Project Management"
],
"yes": [
"Communication",
"Adaptable"
],
"strong_yes": []
},
"questions": [
{
"id": null,
"question": "Key Take-Aways",
"answer": "Seems like a decent candidate."
},
{
"id": null,
"question": "Private Notes",
"answer": "Seems like a decent candidate."
}
]
},
{
"id": 124,
"interview": "Recruiter Phone Screen",
"interviewed_at": "2014-03-26T04:00:00Z",
"candidate_id": 1234,
"submitted_by": {
"id": 4081,
"name": "Desmond Hume"
},
"submitted_at": "2014-03-26T22:15:29Z",
"overall_recommendation": "no",
"attributes": [
{
"name": "Adaptable",
"type": "Skills",
"note": null,
"rating": "mixed"
},
{
"name": "Problem Solver",
"type": "Skills",
"note": "Couldn't figure out how to tie their own shoes.",
"rating": "definitely_not"
}
],
"ratings": {
"definitely_not": [
"Problem Solver"
],
"no": [],
"yes": [],
"strong_yes": [],
"mixed": [
"Adaptable"
]
},
"questions": [
{
"id": null,
"question": "Key Take-Aways",
"answer": ""
},
{
"id": null,
"question": "Private Notes",
"answer": ""
},
{
"id": 11051,
"question": "Does this candidate like long vacations and deserted islands?",
"answer": "Absolutely!"
},
{
"id": 11050,
"question": "Is there anything particularly interesting about this candidate?",
"answer": "Not particularly..."
}
]
}
]
```

All submitted scorecards for the requested application..

### HTTP Request

`GET https://harvest.greenhouse.io/v1/applications/{id}/scorecards`

### Query Parameters

Parameter | Description
--------- | -----------
id | ID of the application to retrieve




## GET Scheduled Interviews

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




## POST Advance Application

```shell
curl 'https://harvest.greenhouse.io/v1/applications/{id}/advance' \
-H "Authorization: Basic MGQwMzFkODIyN2VhZmE2MWRjMzc1YTZjMmUwNjdlMjQ6"
```

```json
{
"id": 985314,
"person_id": 978031,
"prospect": false,
"applied_at": "2014-03-26T20:11:39Z",
"last_activity_at": "2014-03-27T16:13:15Z",
"source": {
"id": 1871,
"public_name": "Happy Hour"
},
"credited_to": {
"id": 4080,
"name": "Kate Austen"
},
"jobs": [
{
"id": 123,
"name": "Accounting Manager"
}
],
"status": "active",
"current_stage": {
"id": 2,
"name": "Recruiter Phone Screen"
}
}
```

Move this application to the next stage. The response is populated with the application's information which will reflect its new state. Note that only applications in the 'active' state can be advanced.

### HTTP Request

`POST https://harvest.greenhouse.io/v1/applications/{id}/advance`

### Query Parameters

Parameter | Required | Type | Description
--------- | ----------- | ----------- | -----------
id | Yes | integer | ID of the application to retrieve
from_stage_id | Yes | integer | The ID of the job stage this application is currently in.




## POST Move Application

```shell
curl 'https://harvest.greenhouse.io/v1/applications/{id}/move' \
-H "Authorization: Basic MGQwMzFkODIyN2VhZmE2MWRjMzc1YTZjMmUwNjdlMjQ6"
```

> The above command takes a JSON request, structured like this:

```json
{
"from_stage_id": 1,
"to_stage_id": 2
}
```

> The above returns a JSON response, structured like this:

```json
{
"id": 985314,
"person_id": 978031,
"prospect": false,
"applied_at": "2014-03-26T20:11:39Z",
"last_activity_at": "2014-03-27T16:13:15Z",
"source": {
"id": 1871,
"public_name": "Happy Hour"
},
"credited_to": {
"id": 4080,
"name": "Kate Austen"
},
"jobs": [
{
"id": 123,
"name": "Accounting Manager"
}
],
"status": "active",
"current_stage": {
"id": 2,
"name": "Recruiter Phone Screen"
}
}
```

Move this application from one stage to another. The response is populated with the application's information which will reflect its new state. Note that only applications in the 'active' state can be moved.

### HTTP Request

`POST https://harvest.greenhouse.io/v1/applications/{id}/move`

### Query Parameters

Parameter | Required | Type | Description
--------- | ----------- | ----------- | ----------- | -----------
id | Yes | integer | ID of the application to retrieve
from_stage_id | Yes | integer | The ID of the job stage this application is currently in.
to_stage_id | Yes | integer | The ID of the job stage this application should be moved to.




## POST Reject Application

```shell
curl 'https://harvest.greenhouse.io/v1/applications/{id}/reject' \
-H "Authorization: Basic MGQwMzFkODIyN2VhZmE2MWRjMzc1YTZjMmUwNjdlMjQ6"
```

> The above command takes a JSON request, structured like this:

```json
{
"rejection_reason_id": 815,
"notes": "The candidate is not qualified for this position.",
"rejection_email": {
"send_email_at": "2014-03-26T20:11:39Z",
"email_template_id": 42
}
}
```

> The above returns a JSON response, structured like this:

```json
{
"id": 985314,
"person_id": 978031,
"prospect": false,
"applied_at": "2014-03-26T20:11:39Z",
"last_activity_at": "2014-03-27T16:13:15Z",
"source": {
"id": 1871,
"public_name": "Happy Hour"
},
"credited_to": {
"id": 4080,
"name": "Kate Austen"
},
"jobs": [
{
"id": 123,
"name": "Accounting Manager"
}
],
"status": "rejected",
"current_stage": {
"id": 62828,
"name": "Recruiter Phone Screen"
}
}
```

Reject this application. The response is populated with the application's information which will reflect its new state. Note that only applications in the 'active' state can be rejected.

### HTTP Request

`POST https://harvest.greenhouse.io/v1/applications/{id}/reject`

### Query Parameters

Parameter | Required | Type | Description
--------- | ----------- | ----------- | ----------- | -----------
id | Yes | integer | ID of the application to retrieve
rejection_reason_id | No | integer | The ID of the reason why this application was rejected.
notes | No | string | Notes on why this application was rejected. These will be added to the activity feed.
rejection_email | No | hash | An email will be sent to the candidate notifying them of this rejection.
rejection_email.sent_email_at | Yes, if sending rejection_email | string | The rejection email will be delayed until this time.
rejection_email.email_template_id | No | string | The template the to use for the rejection email.