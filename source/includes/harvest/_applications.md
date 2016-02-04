# Applications

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