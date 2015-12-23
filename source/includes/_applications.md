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
| candidate_id | integer | ID of the candidate associated with the application |
| prospect | boolean | If true, this candidate is a prospect

## List all applications

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

List all of an organization's applications.

### HTTP Request

`GET https://harvest.greenhouse.io/v1/applications`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
per_page | 10 | optional
page | 1 | optional

## Retrieve an application

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