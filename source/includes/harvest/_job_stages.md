# Job Stages

An organization's job stages.

## The job stage object

```
{
  "id": 72200,
  "name": "Face to Face",
  "interviews": [
    {
      "id": 6001,
      "name": "Cultural Fit Interview",
      "interview_kit": {
        "id": 9123,
        "content": "<h5>Purpose</h5><span>Determine whether or not the candidate would be a strong fit.</span>",
        "questions": [
          {
            "id": 11052,
            "question": "Is this person really a good fit?"
          }
        ]
      }
    },
    {
      "id": 6002,
      "name": "Executive Interview",
      "interview_kit": {
        "id": 9124,
        "content": "<h5>Purpose</h5><span>See if they can work with the boss.</span>",
        "questions": [
          {
            "id": 11053,
            "question": "What's their favorite color?"
          },
          {
            "id": 11054,
            "question": "Do they really want to work here?"
          }
        ]
      }
    }
  ]
}
```

### Noteworthy attributes

| Attribute | Description |
|-----------|-------------|
| id | The job stage's unique identifier |
| interviews | An array of interviews associated with this job stage.


## GET: List Job Stages

```shell
curl 'https://harvest.greenhouse.io/v1/job_stages' 
-H "Authorization: Basic MGQwMzFkODIyN2VhZmE2MWRjMzc1YTZjMmUwNjdlMjQ6"
```

> The above command returns JSON structured like this:

```json
[
  {
    "id": 6001,
    "name": "Cultural Fit Interview",
    "created_at": "2015-11-22T05:31:37.263Z",
    "updated_at": "2015-11-22T05:31:37.263Z",
    "job_id": 12345,
    "interviews": [
      {
        "id": 7890,
        "name": "Cultural Fit Interview",
        "interview_kit": {
          "id": 9124,
          "content": "<h5>Purpose</h5><span>Determine whether or not the candidate would be a strong fit.</span>",
          "questions": [
              {
                "id": 11052,
                "question": "Is this person really a good fit?"
              }
            ]        
          }
        }
      ]
    },
  {
    "id": 6002,
    "name": "Executive Interview",
    "created_at": "2015-11-22T05:31:37.263Z",
    "updated_at": "2015-11-22T05:31:37.263Z",
    "job_id": 34567,
    "interviews": [
      {
        "id": 7345,
        "name": "Executive Interview",
        "interview_kit": {
          "id": 9125,
          "content": "<h5>Purpose</h5><span>Determine whether or not the candidate would be a strong fit.</span>",
          "questions": [
              {
                "id": 11053,
                "question": "What's their favorite color?"
              },
              {
                "id": 11054,
                "question": "Do they really want to work here?"
              }
            ]        
          }
        }
      ]
    }
  ]
```

List all of an organization's job stages.

### HTTP Request

`GET https://harvest.greenhouse.io/v1/job_stages`

### Querystring parameters

| Parameter | Description |
|-----------|-------------|
| per_page | Return up to this number of objects per response. Must be an integer between 1 and 500. Defaults to 100.
| page | A cursor for use in pagination.  Returns the n-th chunk of `per_page` objects.

<br>
[See noteworthy response attributes.](#the-job-stages-object)

## GET: List Job Stages for Job

```shell
curl 'https://harvest.greenhouse.io/v1/jobs/{id}/stages' 
-H "Authorization: Basic MGQwMzFkODIyN2VhZmE2MWRjMzc1YTZjMmUwNjdlMjQ6"
```

> The above command returns JSON structured like this:

```json
[
  {
    "id": 72200,
    "name": "Face to Face",
    "created_at": "2015-11-22T05:31:37.263Z",
    "updated_at": "2015-11-22T05:31:37.263Z",
    "job_id": 146218,
    "interviews": [
      {
        "id": 6001,
        "name": "Cultural Fit Interview",
        "interview_kit": {
          "id": 9128,
          "content": "<h5>Purpose</h5><span>Determine whether or not the candidate would be a strong fit.</span>",
          "questions": [
            {
              "id": 11052,
              "question": "Is this person really a good fit?"
            }
          ]
        }
      },
      {
        "id": 6002,
        "name": "Executive Interview",
        "created_at": "2015-11-22T05:31:37.263Z",
        "updated_at": "2015-11-22T05:31:37.263Z",
        "job_id": 146219,
        "interview_kit": {
          "id": 9129,
          "content": "<h5>Purpose</h5><span>See if they can work with the boss.</span>",
          "questions": [
            {
              "id": 11053,
              "question": "What's their favorite color?"
            },
            {
              "id": 11054,
              "question": "Do they really want to work here?"
            }
          ]
        }
      }
    ]
  },
  {
    "id": 72199,
    "name": "Offer",
    "created_at": "2015-11-22T05:31:37.263Z",
    "updated_at": "2015-11-22T05:31:37.263Z",
    "job_id": 146220,
    "interviews": []
  },
  {
    "id": 72194,
    "name": "Application Review",
    "created_at": "2015-11-22T05:31:37.263Z",
    "updated_at": "2015-11-22T05:31:37.263Z",
    "job_id": 146221,
    "interviews": [
      {
        "id": 8004,
        "name": "Application Review",
        "interview_kit": {
          "id": 9130,
          "content": null,
          "questions": []
        }
      }
    ]
  }
]
```

Retrieve the stages for the specified job id.

### HTTP Request

`GET https://harvest.greenhouse.io/v1/jobs/{id}/stages`

### URL Parameters

Parameter | Description
--------- | -----------
| id | The ID of the job whose job stages you want to retrieve.

### Querystring parameters

Parameter | Description
--------- | -----------
| created_before | Return only job stages that were created before this timestamp. Timestamp must be in in [ISO-8601] (#general-considerations) format.
| created_after | Return only job stages that were created after this timestamp. Timestamp must be in in [ISO-8601] (#general-considerations) format.
| updated_before | Return only job stages that were updated before this timestamp. Timestamp must be in in [ISO-8601] (#general-considerations) format.
| updated_after | Return only job stages that were updated after this timestamp. Timestamp must be in in [ISO-8601] (#general-considerations) format.

<br>
[See noteworthy response attributes.](#the-job-stage-object)

## GET: Retrieve Job Stage

```shell
curl 'https://harvest.greenhouse.io/v1/job_stages/{id}' 
-H "Authorization: Basic MGQwMzFkODIyN2VhZmE2MWRjMzc1YTZjMmUwNjdlMjQ6"
```

> The above command returns JSON structured like this:

```json
{
  "id": 6001,
  "name": "Cultural Fit Interview",
  "created_at": "2015-11-22T05:31:37.263Z",
  "updated_at": "2015-11-22T05:31:37.263Z",
  "job_id": 12345,
  "interviews": [
    {
      "id": 7890,
      "name": "Cultural Fit Interview",
      "interview_kit": {
        "id": 9127,
        "content": "<h5>Purpose</h5><span>Determine whether or not the candidate would be a strong fit.</span>",
        "questions": [
            {
              "id": 11052,
              "question": "Is this person really a good fit?"
            }
          ]        
        }
      }
    ]
  }
```

Retreieve a job stage by its `id`.

### HTTP Request

`GET https://harvest.greenhouse.io/v1/job_stages/{id}`

### URL Parameters

Parameter | Description
--------- | -----------
id | The ID of the job stage to retrieve


<br>
[See noteworthy response attributes.](#the-job-stages-object)
