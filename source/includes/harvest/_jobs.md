# Jobs

## The job object

```json
{
  "id": 6404,
  "name": "Archaeologist",
  "requisition_id": "abc123",
  "notes": "<p>Resistance to electro-magnetic radiation a plus!</p>",
  "status": "closed",
  "created_at": "2013-12-10T14:42:58Z",
  "opened_at": "2013-12-11T14:42:58Z",
  "closed_at": "2013-12-12T14:42:58Z",
  "departments": [
    {
      "id": 562,
      "name": "Exploration"
    }
  ],
  "offices": [
    {
      "id": 175,
      "name": "San Francisco",
      "location": {
        "name": "San Francisco, CA"
      }
    }
  ],
  "custom_fields": {
    "employment_type": "Full-Time",
    "maximum_budget": "$81.5k",
    "salary_range": {
      "min_value": 70000,
      "max_value": 90000,
      "unit": "USD"
    }
  }
}
```

### Noteworthy attributes

| Attribute | Description |
|-----------|-------------|
| id | The job's unique identifier |
| status | One of `open`, `closed`, `draft`.
| departments | An array containing the [department](#departments) which this job belongs to.
| offices | An array containing the [offices](#offices) this job is associated with.
| custom_fields | Contains any custom job fields which have been defined by your organization.

## List jobs

```shell
curl 'https://harvest.greenhouse.io/v1/jobs' \
-H "Authorization: Basic MGQwMzFkODIyN2VhZmE2MWRjMzc1YTZjMmUwNjdlMjQ6"
```

```json
[
  {
    "id": 6404,
    "name": "Archaeologist",
    "requisition_id": "abc123",
    "notes": "<p>Resistance to electro-magnetic radiation a plus!</p>",
    "status": "closed",
    "created_at": "2013-12-10T14:42:58Z",
    "opened_at": "2013-12-11T14:42:58Z",
    "closed_at": "2013-12-12T14:42:58Z",
    "departments": [
      {
        "id": 562,
        "name": "Exploration"
      }
    ],
    "offices": [
      {
        "id": 175,
        "name": "San Francisco",
        "location": {
          "name": "San Francisco, CA"
        }
      }
    ],
    "custom_fields": {
      "employment_type": "Full-Time",
      "maximum_budget": "$81.5k",
      "salary_range": {
        "min_value": 70000,
        "max_value": 90000,
        "unit": "USD"
      }
    }
  },
]
```

List all of your organization's jobs.

### HTTP Request

`GET https://harvest.greenhouse.io/v1/jobs`

### Optional querystring parameters

| Parameter | Description |
|-----------|-------------|
| per_page | Return up to this number of objects per response.  Must be an integer between 1 and 100.  Defaults to 100.
| page | A cursor for use in pagination.  Returns the n-th chunk of `per_page` objects.


## Retrieve a job

```shell
curl 'https://harvest.greenhouse.io/v1/jobs/{id}' \
-H "Authorization: Basic MGQwMzFkODIyN2VhZmE2MWRjMzc1YTZjMmUwNjdlMjQ6"
```

```json
{
  "id": 6404,
  "name": "Archaeologist",
  "requisition_id": "abc123",
  "notes": "<p>Resistance to electro-magnetic radiation a plus!</p>",
  "status": "closed",
  "created_at": "2013-12-10T14:42:58Z",
  "opened_at": "2013-12-11T14:42:58Z",
  "closed_at": "2013-12-12T14:42:58Z",
  "departments": [
    {
      "id": 562,
      "name": "Exploration"
    }
  ],
  "offices": [
    {
      "id": 175,
      "name": "San Francisco",
      "location": {
        "name": "San Francisco, CA"
      }
    }
  ],
  "custom_fields": {
    "employment_type": "Full-Time",
    "maximum_budget": "$81.5k",
    "salary_range": {
      "min_value": 70000,
      "max_value": 90000,
      "unit": "USD"
    }
  }
}
```

### HTTP Request

`GET https://harvest.greenhouse.io/v1/jobs/{id}`


### URL Parameters

Parameter | Description
--------- | -----------
id | The ID of the job to retrieve