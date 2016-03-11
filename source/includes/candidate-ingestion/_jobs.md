# Jobs

## Retreive Jobs

```shell
curl 'https://api.greenhouse.io/v1/partner/jobs'
-H "Authorization: Basic MGQwMzFkODIyN2VhZmE2MWRjMzc1YTZjMmUwNjdlMjQ6"
```

```json
[
  {
    "id": 146859,
    "name": "Auror",
    "status": "open",
    "public": true
  },
  {
    "id": 150050,
    "name": "Professor",
    "status": "open",
    "public": true
  },
  {
    "id": 147886,
    "name": "Caretaker",
    "status": "open",
    "public": false
  },
]
```

Retrieve jobs that are visible for the current user, including all jobs listed on their organization’s public careers page and unpublished jobs the user can access.

`GET https://api.greenhouse.io/v1/partner/jobs`


*scope: jobs.view*


### Response Parameters

Property Name | Type | Required | Description
-------------- | -------------- | -------------- | -------------- 
id | Integer | Yes | The ID of the job.
name | String | Yes | The name as it appears in Greenhouse, NOT necessarily how it appears on the public job board.
status | String | Yes | Always ‘open’.
public | Boolean | Yes | True if this job is published on the organization’s careers page.